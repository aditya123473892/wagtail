## Before making a new release

* A 'stable' branch should exist in git, e.g. "stable/0.4.x"
* `wagtail/wagtailcore/__init__.py` should be updated with the new version number
* `wagtail/project_template/requirements.txt` should specify the new version number, as a range (e.g. `wagtail>=1.5,<1.6`)
* There should be a release notes page about the release in docs/releases/ - ensure that any IN DEVELOPMENT text is removed
* CHANGELOG.txt should contain a section about the new release - ensure that the date is filled in, not left as xx.xx.20xx
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

## releases.wagtail.io

Once the new release is out, please update https://releases.wagtail.io/latest.txt accordingly.

Set up the AWS client, if you haven't already - `pip install awscli`, then `aws configure` and enter the credentials from pwman (Others -> Amazon -> Amazon Web Services).

With the AWS client configured, run:

    cd wagtail/scripts
    ./make-latest.sh --version=1.1 --url=http://docs.wagtail.io/en/v1.1/releases/1.1.html

replacing the version number as appropriate.

(It will take up to a day for changes to propagate to the Cloudfront cache. If you need it to update faster than that, you can purge it through the horrible AWS interface... log in with the "Sysadmin Amazon" details from pwman, and the relevant operation to perform is "Create invalidation".)

## Post-release

* Update readthedocs so that the new version is visible and the 'stable' version points to it; if this is a minor point release, disable the docs for the previous minor release (see 'Documentation versions' below)
* Close the milestone on https://github.com/torchbox/wagtail/milestones
* Email wagtail@googlegroups.com with the release announcement
* Blog and tweet about it

### Clean-up

* Update deprecated features:
    - Delete features deprecated in this release
    - Update wagtail.utils.deprecation

For example, lets say we are releasing wagtail 0.5:

1. Look for RemovedInWagtail05Warning messages and remove the features they are warning about
2. In wagtail.utils.deprecation:
    - Delete RemovedInWagtail05Warning
    - Change RemovedInWagtail06Warning to a DeprecationWarning
    - Create a new warning called RemovedInWagtail07Warning which inherits from PendingDeprecationWarning

## Documentation versions

The Wagtail [documentation](http://docs.wagtail.io) is now versioned. To control which versions show up:

* Go to [Read The Docs versions](https://readthedocs.org/dashboard/wagtail/versions/)
    - Tick or untick the "active" checkbox next to the relevant tag (or branch) and save the form.
* Go to ["Builds"](https://readthedocs.org/builds/wagtail/)
  - Select the new version to build from the dropdown and click "Build version"