## Before making a new release

* A 'stable' branch should exist in git, e.g. "stable/0.4.x"
* `wagtail/wagtailcore/__init__.py` should be updated with the new version number
* `wagtail/project_template/requirements.txt` should specify the new version number
* There should be a release notes page about the release in docs/releases/ - ensure that any IN DEVELOPMENT text is removed
* CHANGELOG.txt should contain a section about the new release - ensure that the date is filled in, not left as xx.xx.20xx
* Update translations - see https://github.com/torchbox/wagtail/wiki/Managing-Wagtail-translations#fetching-new-translations-from-transifex
* Confirm that the latest revision is passing on Travis 

## GitHub release

From https://github.com/torchbox/wagtail/releases, click 'Draft a new release':

* Tag version should be of the form "v0.4" - the target should be the stable/0.4.x branch (in practice, for a new 0.x version this will probably be identical to master)
* Release title should be "0.4" (without the 'v')
* For the "Describe the release", we usually just paste in the CHANGELOG.txt entry
* Click "Publish release" - this will create a new git tag for the release, and a new entry on https://github.com/torchbox/wagtail/releases

## PyPi

From the root of the wagtail codebase on your machine - NOT within Vagrant (because it needs to fiddle with symlinks) and with the correct branch checked out, run:

        python ./setup.py register

You will be prompted for a PyPI username/password - search pwman for 'pypi'. (If you're already logged in under your personal pypi account, edit `~/.pypirc` with the Torchbox details. Or ask [@gasman](https://github.com/gasman) to add your own account as a maintainer of wagtail...). Then run:

        python ./setup.py sdist upload

The new version should now be up on https://pypi.python.org/pypi/wagtail .

## Post-release

* Test that it works:
    - install it in a clean virtualenv and check that "wagtail start myproject" creates a codebase that starts successfully under vagrant
    - bring up a fresh instance of wagtaildemo with the new version
* Update readthedocs so that the new version is visible and the 'stable' version points to it; if this is a minor point release, disable the docs for the previous minor release (see 'Documentation versions' below)
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