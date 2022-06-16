## Before making a new release

* A 'stable' branch should exist in git, e.g. "stable/2.8.x"
* There should be a release notes page about the release in docs/releases/ - ensure that any deprecated features are mentioned in the "Upgrade considerations" section
* CHANGELOG.txt should contain a section about the new release
* The release should be listed in the 'compatible Django / Python versions' table in docs/releases/upgrading.rst
* Update translations - see https://github.com/torchbox/wagtail/wiki/Managing-Wagtail-translations#fetching-new-translations-from-transifex
* **For a release candidate:** Generate new translation strings (https://github.com/wagtail/wagtail/wiki/Managing-Wagtail-translations#generating-new-source-files-for-translation) and **announce through https://www.transifex.com/torchbox/wagtail/announcements/ that a new version is coming soon and needs translations**
* Update `wagtail/__init__.py` with the new version number
  * For a release candidate: `VERSION = (2, 8, 0, 'rc', 1)`
  * For a major release: `VERSION = (3, 0, 0, 'final', 1)`
  * For a minor release: `VERSION = (2, 8, 0, 'final', 1)`
  * For a patch release: `VERSION = (2, 8, 1, 'final', 1)`
* Update `wagtail/project_template/requirements.txt` with the new version number
  * For a release candidate, use the exact version: `wagtail==2.8rc1`
  * For a major, minor or patch release, use a range covering the minor release (e.g. `wagtail>=2.8,<2.9`)
* **For a major, minor or patch release:** fill in the release date in CHANGELOG.txt and remove any IN DEVELOPMENT text from the changelog and the release notes page
* Confirm that the latest revision is passing on [Github Actions CI](https://github.com/wagtail/wagtail/actions)

## Prerequisites

You will need the `wheel` and `twine` packages (`pip install wheel`, `pip install twine` from a fresh empty virtualenv will work fine) and a working Node/NPM build on your host machine.

You will also need to be [authenticated with PyPI](https://pypi.org/help/#apitoken) with a user account that's listed as a maintainer of the `wagtail` project - the sysadmin team at Torchbox have access to the shared `torchbox` account and can add you if necessary.

## Package build

Create a fresh clone of the Wagtail repo, and check out the appropriate 'stable' branch.

    git clone https://github.com/wagtail/wagtail.git
    cd wagtail
    git checkout stable/1.<x>.x

(Using a Vagrant dev instance will not work: running the setup.py command within Vagrant will fail because it creates symlinks, which aren't supported by Virtualbox shared folders; and running it on the host machine will fail because it will try to run the copy of node-sass in node_modules, which is built for the VM's architecture. Also, by creating a fresh clone, we minimise the risk of having random development files floating around the codebase that screw up the package.)

From the root of the wagtail codebase, run:

    nvm use
    npm install
    python ./setup.py sdist bdist_wheel

This will create a .tar.gz package and a .whl package in the 'dist' directory. We now need to test that these installs successfully - from a location other than wagtail root (because the presence of the 'wagtail' directory confuses the installer), run:

    mkvirtualenv wagtailinstalltest
    pip install /path/to/wagtail-0.x.x.tar.gz
    wagtail start myproject
    cd myproject
    ./manage.py migrate
    ./manage.py runserver

and confirm that the site starts up successfully at http://localhost:8000/ . Repeat the test with the .whl package. (Note that bringing up a Vagrant VM will not work at this point, because the provisioning script will try to install a version of Wagtail that isn't on PyPI yet)

## GitHub release

From https://github.com/wagtail/wagtail/releases, click 'Draft a new release':

* Tag version should be of the form "v0.4" - the target should be the stable/0.4.x branch (in practice, for a new 0.x version this will probably be identical to `main`)
* Release title should be "0.4" (without the 'v')
* For the "Describe the release", we usually just paste in the CHANGELOG.txt entry
* Click "Publish release" - this will create a new git tag for the release, and a new entry on https://github.com/torchbox/wagtail/releases

## PyPI

From the root of your checkout, run: `twine upload dist/*`

The new version should now be up on https://pypi.python.org/pypi/wagtail .

### Major version bump classifier

- If this is a major version bump, ensure that the documentation is updated and there is a new classifier created in PyPI - https://pypi.org/help/#new-classifier
- Examples from Wagtail 3.0 https://github.com/wagtail/wagtail/pull/8486 & https://github.com/pypa/trove-classifiers/pull/102

## Testing the release

  - install it in a clean virtualenv and check that "wagtail start myproject" creates a codebase that starts successfully under vagrant
  - bring up a fresh instance of [bakerydemo](https://github.com/wagtail/bakerydemo) with the new version set in `requirements/base.txt`; if successful, commit the version bump to bakerydemo master

## Docs

Readthedocs will spot the addition of a release tag with a newer version number, and automatically publish that as the new 'stable' version.

* For a patch release on an older branch, readthedocs may leave it initially inactive - if so, activate it from https://readthedocs.org/projects/wagtail/versions/
* For a patch release, hide the _previous_ version by going to Edit from https://readthedocs.org/projects/wagtail/versions/ and checking the Hidden checkbox. This way, the list of versions in the readthedocs flyout menu will only include the latest release of each branch.
* If any documentation has been moved around since the previous release, now is a good time to add redirects via https://readthedocs.org/dashboard/wagtail/redirects/ . (Protip: [remember to add leading slashes on URLs](https://github.com/rtfd/readthedocs.org/issues/1826#issuecomment-247995569).)
* Update docs in [Dash-User-Contributions](https://github.com/Kapeli/Dash-User-Contributions/tree/master/docsets/Wagtail) for offline docs apps [Dash](https://kapeli.com/dash) and [Zeal](https://zealdocs.org/).
  * Follow the instructions on the README.md and submit a pull request with updated docs.

## releases.wagtail.io

Once the new release is out, please update https://releases.wagtail.io/latest.txt accordingly. You'll need AWS credentials for the S3 bucket and Cloudfront cache, which are held by the Torchbox sysadmins.

Set up the AWS client, if you haven't already - `pip install awscli`, then `aws configure` and enter the credentials.

Edit scripts/latest.txt with the new version details: `version` is the newest version, `url` is its release notes page, and `minorUrl` is the release notes page for the corresponding minor version, e.g. 2.15 for 2.15.1. (This is shown to users who are running an earlier minor version, so that they see the changelog for the whole minor release rather than just the .1 patch). If this is a new release (major, minor or patch) within an LTS branch, update the `lts` section too. Then, with the AWS client configured, run:

    cd wagtail/scripts
    ./latest.sh put latest.txt

(It will take up to a day for changes to propagate to the Cloudfront cache. If you need it to update faster than that, someone with access to the AWS web console can purge it - the relevant operation to perform is "Create invalidation".)

_The SSL certificate for releases.wagtail.io needs to be manually renewed once a year: https://projects.torchbox.com/projects/sysadmin/notebook/releases.wagtail.io.md_

## Post-release

* Close the milestone on https://github.com/torchbox/wagtail/milestones
* Email wagtail@googlegroups.com with the release announcement
* Blog and tweet about it
  * Share with https://django-news.com/
  * Share with https://www.reddit.com/r/django/
* Test [add-on packages in the Wagtail org](https://paper.dropbox.com/doc/Wagtail-organisation-subprojects--A0vEPub7dKgN_SsWZVYB6CZDAg-15Cg4kQNtE0LaJ6pVTrrQ) for compatibility and update as necessary

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

#### Remove old `versionadded` / `versionchanged` notes in the docs

`versionadded` and `versionchanged` notes for old versions of Wagtail should be removed from the docs. These notes are kept for two releases. If Wagtail 3.5 had just been released, `versionadded` and `versionchanged` notes from version `3.4` should be dropped. This will leave notes for only version 3.5 in the docs, with notes added for 3.6 being added for the next release.