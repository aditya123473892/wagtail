## Before making a new release

* A 'stable' branch should exist in git, e.g. "stable/0.4.x"
* `wagtail/__init__.py` should be updated with the new version number
* `wagtail/project_template/requirements.txt` should specify the new version number, as a range (e.g. `wagtail>=1.5,<1.6`)
* There should be a release notes page about the release in docs/releases/ - ensure that any IN DEVELOPMENT text is removed
* Ensure that any deprecated features are mentioned in the "Upgrade considerations" section of the release notes
* CHANGELOG.txt should contain a section about the new release - ensure that the date is filled in, not left as xx.xx.20xx
* The release should be listed in the 'compatible Django / Python versions' table in docs/releases/upgrading.rst
* Update translations - see https://github.com/torchbox/wagtail/wiki/Managing-Wagtail-translations#fetching-new-translations-from-transifex
* Confirm that the latest revision is passing on Travis (including Elasticsearch tests, which are marked as 'allow failures' to avoid false alarms during routine dev work, but we really do want to see them pass here)

## Prerequisites

You will need the `wheel` and `twine` packages (`pip install wheel`, `pip install twine` from a fresh empty virtualenv will work fine) and a working Node/NPM build on your host machine.

## Package build

Create a fresh clone of the Wagtail repo, and check out the appropriate 'stable' branch.

    git clone https://github.com/torchbox/wagtail.git
    cd wagtail
    git checkout stable/1.<x>.x

(Using a Vagrant dev instance will not work: running the setup.py command within Vagrant will fail because it creates symlinks, which aren't supported by Virtualbox shared folders; and running it on the host machine will fail because it will try to run the copy of node-sass in node_modules, which is built for the VM's architecture. Also, by creating a fresh clone, we minimise the risk of having random development files floating around the codebase that screw up the package.)

From the root of the wagtail codebase, run:

    npm install
    python ./setup.py sdist
    python ./setup.py bdist_wheel

This will create a .tar.gz package and a .whl package in the 'dist' directory. We now need to test that these installs successfully - from a location other than wagtail root (because the presence of the 'wagtail' directory confuses the installer), run:

    mkvirtualenv wagtailinstalltest
    pip install /path/to/wagtail-0.x.x.tar.gz
    wagtail start myproject
    cd myproject
    ./manage.py migrate
    ./manage.py runserver

and confirm that the site starts up successfully at http://localhost:8000/ . Repeat the test with the .whl package. (Note that bringing up a Vagrant VM will not work at this point, because the provisioning script will try to install a version of Wagtail that isn't on PyPI yet)

## GitHub release

From https://github.com/torchbox/wagtail/releases, click 'Draft a new release':

* Tag version should be of the form "v0.4" - the target should be the stable/0.4.x branch (in practice, for a new 0.x version this will probably be identical to master)
* Release title should be "0.4" (without the 'v')
* For the "Describe the release", we usually just paste in the CHANGELOG.txt entry
* Click "Publish release" - this will create a new git tag for the release, and a new entry on https://github.com/torchbox/wagtail/releases

## PyPI

_At the moment (Aug 2016) PyPI and Python deployment tools seem to be totally in limbo over whether they require HTTP vs HTTPS, which API endpoints to use and so on. The following steps work, even if they're a bit rubbish:_

* Log in to https://pypi.python.org/ (search pwman for 'pypi', or ask [@gasman](https://github.com/gasman) to add your own account as a maintainer of wagtail) and visit https://pypi.python.org/pypi?%3Aaction=submit_form
* Under option 2 "upload your PKG-INFO file", select the file wagtail.egg-info/PKG-INFO from your checkout and 'Add Package Info'
* From the root of your checkout, run: `twine upload dist/*`

The new version should now be up on https://pypi.python.org/pypi/wagtail .

## Testing the release

  - install it in a clean virtualenv and check that "wagtail start myproject" creates a codebase that starts successfully under vagrant
  - bring up a fresh instance of wagtaildemo with the new version

## Docs

* Update readthedocs so that the new version is active by default:
  * Go to https://readthedocs.org/dashboard/wagtail/versions/ and set 'Default version' to the new release
  * Go to https://readthedocs.org/projects/wagtail/builds/ and republish all versions from 1.8 onward - this will update the 'canonical' URL in the HTML to point to the new version, hopefully preventing old versions from being indexed by Google. (Older versions can no longer be built due to broken dependencies in docs/requirements.txt)
  * If any documentation has been moved around since the previous release, now is a good time to add redirects via https://readthedocs.org/dashboard/wagtail/redirects/ . (Protip: [remember to add leading slashes on URLs](https://github.com/rtfd/readthedocs.org/issues/1826#issuecomment-247995569).)
  * If this is a minor point release, disable the docs for the previous minor release by unticking it on https://readthedocs.org/dashboard/wagtail/versions/

## releases.wagtail.io

Once the new release is out, please update https://releases.wagtail.io/latest.txt accordingly.

Set up the AWS client, if you haven't already - `pip install awscli`, then `aws configure` and enter the credentials from pwman (Others -> Amazon -> Amazon Web Services).

With the AWS client configured, run:

    cd wagtail/scripts
    ./make-latest.sh --version=1.1 --url=http://docs.wagtail.io/en/v1.1/releases/1.1.html

replacing the version number as appropriate.

(It will take up to a day for changes to propagate to the Cloudfront cache. If you need it to update faster than that, you can purge it through the horrible AWS interface... log in with the "Sysadmin Amazon" details from pwman, and the relevant operation to perform is "Create invalidation".)

_The SSL certificate for releases.wagtail.io needs to be manually renewed once a year: https://projects.torchbox.com/projects/sysadmin/notebook/releases.wagtail.io.md_

## Post-release

* Close the milestone on https://github.com/torchbox/wagtail/milestones
* Email wagtail@googlegroups.com with the release announcement
* Blog and tweet about it

### Clean-up

#### Update deprecated features

 - Delete features deprecated in this release
 - Update wagtail.utils.deprecation

For example, lets say we are releasing wagtail 3.5:

1. Look for RemovedInWagtail35Warning messages and remove the features they are warning about
2. In wagtail.utils.deprecation:
    - Delete RemovedInWagtail35Warning
    - Change RemovedInWagtail36Warning to a DeprecationWarning
    - Create a new warning called RemovedInWagtail37Warning which inherits from PendingDeprecationWarning

#### Drop support for old versions of Django

Search the code base for `django.VERSION` and `DJANGO_VERSION`. Remove any code for versions of Django that are no longer supported in future releases. Look in `setup.py` to check which versions of Django are currently supported.

#### Remove old `versionadded` notes in the docs

`versionadded` notes for old versions of Wagtail should be removed from the docs. `versionadded` tags are kept for two releases. If Wagtail 3.5 had just been released, `versionadded` notes from version `3.4` should be dropped. This will leave `versionadded` notes for only version 3.5 in the docs, with notes added for 3.6 being added for the next release.