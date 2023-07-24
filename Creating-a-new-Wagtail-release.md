## Before making a new release

* A 'stable' branch should exist in git, e.g. `stable/5.1.x`. Switch to that branch.
  * If making the first release candidate for a new Wagtail version, we will create this later. Use the `main` branch for now.
* There should be a release notes page about the release in `docs/releases/`, e.g. `5.1.md`.
  * Ensure that any deprecated features are mentioned in the "Upgrade considerations" section.
  * If there are a large number of upgrade considerations, consider organising them by largest impact first, and breaking them down into:
    * Changes affecting all projects
    * Deprecation of old functionality
    * Changes affecting Wagtail customisations
* `CHANGELOG.txt` should contain a section for the new release.
* The minor version of the release should be listed in the 'compatible Django / Python versions' table in `docs/releases/upgrading.md`.
* Update translation files.
  * See https://github.com/torchbox/wagtail/wiki/Managing-Wagtail-translations#fetching-new-translations-from-transifex.
* **For a release candidate:**
  * **Generate new translation strings**
    * See https://github.com/wagtail/wagtail/wiki/Managing-Wagtail-translations#generating-new-source-files-for-translation
    * Announce through https://app.transifex.com/torchbox/communication/?q=project%3Awagtail that a new version is coming soon and needs translations.
      * To get the number of new strings, you can run:
        ```shell
        git show <commit ID here> | grep '+msgid' | wc -l
        ```
        Note: not sure if this is accurate, can someone please verify?
  * **Push the new and updated translation files to the `main` branch.**
  * **Create a new branch for the new version, e.g. `stable/5.1.x`. We will be working on this branch from this point forward.**
  * **Update the Help menu item.**
    * Sign in to https://guide.wagtail.org
    * Go to https://guide.wagtail.org/releases/latest/
    * If it already redirects to the page for the correct minor release, skip this step. Otherwise:
      * From the userbar, click "Edit this page"
      * From the three-dot menu in the header, click "Copy this page"
      * Update the page title and slug for the new release, e.g. `What's new in Wagtail 5.1` and `new-in-wagtail-5-1`.
      * Make sure it's copied as a child of the "Releases" page.
      * Click "Copy this page"
      * Go to the "Releases" page in the page explorer and edit the newly-created "What's new in Wagtail 5.1" page.
      * Update any mentions and links of the previous version e.g. 5.0 to the current version e.g. 5.1.
      * Update the rest of the content based on the rendered release notes in the developer docs, but only include parts that are relevant for content editors.
      * Publish the page.
      * Update `wagtail.admin.wagtail_hooks.register_whats_new_in_wagtail_version_menu_item` so the `version`'s value is correct, e.g. `"5.1"` and `wagtail.templatetags.wagtailcore_tags.wagtail_feature_release_whats_new_link` so that the link points to the page we just published.
        * For example, see https://github.com/wagtail/wagtail/commit/15f652c9efe3a1b3ddc6afd79857e1152892a405
      * Commit the changes to the `stable/5.1.x` branch, e.g. `git commit -m "Update What's new in Wagtail version menu item to 5.1"`.
* Update `wagtail/__init__.py` with the new version number.
  * For a release candidate: `VERSION = (5, 1, 0, 'rc', 1)`
  * For a major release: `VERSION = (6, 0, 0, 'final', 1)`
  * For a minor release: `VERSION = (5, 1, 0, 'final', 1)`
  * For a patch release: `VERSION = (5, 1, 1, 'final', 1)`
* Update `wagtail/project_template/requirements.txt` with the new version number.
  * For a release candidate, use the exact version: `wagtail==5.1rc1`
  * For a major, minor or patch release, use a range covering the minor release (e.g. `wagtail>=5.1,<5.2`)
* Commit the changes, e.g. `git commit -m "Version bump to 5.1.2"`.
* **For a major, minor or patch release:**
  * **Fill in the release date, and remove any `IN DEVELOPMENT` text, in:**
    * `CHANGELOG.txt`
    * the release notes page in `docs/releases/`
* **For a minor release:**
  * **Update the redirect on the guide.wagtail.org.**
    * Go to https://guide.wagtail.org/admin/redirects/133/
    * Update the redirect target to the correct page for the new release
* Confirm that the latest revision is passing on [GitHub Actions CI](https://github.com/wagtail/wagtail/actions)

You can do the above steps with your existing clone of the Wagtail repository.

## Prerequisites

You will need the `wheel` and `twine` packages (`pip install wheel`, `pip install twine` from a fresh empty virtualenv will work fine) and a working Node/NPM build on your host machine.

You will also need to be [authenticated with PyPI](https://pypi.org/help/#apitoken) with a user account that's listed as a maintainer of the `wagtail` project - the sysadmin team at Torchbox have access to the shared `torchbox` account and can add you if necessary.

## Package build

Create a fresh clone of the Wagtail repository, and check out the appropriate 'stable' branch. By creating a fresh clone, we minimise the risk of having random development files floating around the codebase that screw up the package.

**If you're creating multiple releases (e.g. patch releases for different minor releases), create a fresh clone for each release.** This ensures that we do not keep any files that have been moved/deleted.

```bash
git clone https://github.com/wagtail/wagtail.git
cd wagtail
git checkout stable/1.<x>.x
```

(Using a Vagrant dev instance will not work: running the setup.py command within Vagrant will fail because it creates symlinks, which aren't supported by Virtualbox shared folders; and running it on the host machine will fail because it will try to run the copy of node-sass in `node_modules`, which is built for the VM's architecture.)

From the root of the wagtail codebase, run:

```bash
nvm use
npm install
python ./setup.py sdist bdist_wheel
```

This will create a `.tar.gz` package and a `.whl` package in the 'dist' directory. We now need to test that these installs successfully - from a location other than wagtail root (because the presence of the `wagtail` directory confuses the installer), run:

```bash
mkvirtualenv wagtailinstalltest
pip install /path/to/wagtail-0.x.x.tar.gz
wagtail start myproject
cd myproject
./manage.py migrate
./manage.py runserver
```

and confirm that the site starts up successfully at http://localhost:8000/ . Repeat the test with the `.whl` package. (Note that bringing up a Vagrant VM will not work at this point, because the provisioning script will try to install a version of Wagtail that isn't on PyPI yet.)

## GitHub release

From https://github.com/wagtail/wagtail/releases, click 'Draft a new release':

* Tag version should be of the form `v5.1` - the target should be the `stable/5.1.x` branch (in practice, for a new `5.x` version this will probably be identical to `main`)
* Release title should be `5.1` (without the `v`)
* For the "Describe the release", we usually just paste in the `CHANGELOG.txt` entry
* **For a release candidate:** Check the "Set as pre-release box" checkbox
* Click "Publish release" - this will create a new git tag for the release, and a new entry on https://github.com/torchbox/wagtail/releases

## PyPI

From the root of your checkout, run: `twine upload dist/*`

The new version should now be up on https://pypi.python.org/pypi/wagtail .

### Major version bump classifier

- If this is a major version bump, ensure that the documentation is updated and there is a new classifier created in PyPI - https://pypi.org/help/#new-classifier
- Examples from Wagtail 3.0 https://github.com/wagtail/wagtail/pull/8486 & https://github.com/pypa/trove-classifiers/pull/102

## Testing the release

- Install it in a clean virtualenv and check that `wagtail start myproject` creates a codebase that starts successfully (test with Vagrant as well if necessary)
- Bring up a fresh instance of [bakerydemo](https://github.com/wagtail/bakerydemo) with the new version set in `requirements/base.txt`; if successful, commit the version bump to bakerydemo master

## Docs

Readthedocs will spot the addition of a release tag with a newer version number, and automatically publish that as the new 'stable' version.

* **For a release candidate:** no changes to Readthedocs are made. You can skip this section.
* For a patch release on an older branch, readthedocs may leave it initially inactive - if so, activate it from https://readthedocs.org/projects/wagtail/versions/
* For a patch release, hide the _previous_ version by going to Edit from https://readthedocs.org/projects/wagtail/versions/ and checking the Hidden checkbox. This way, the list of versions in the readthedocs flyout menu will only include the latest release of each branch.
* If any documentation has been moved around since the previous release, now is a good time to add redirects via https://readthedocs.org/dashboard/wagtail/redirects/ . (Protip: [remember to add leading slashes on URLs](https://github.com/rtfd/readthedocs.org/issues/1826#issuecomment-247995569).)
* Update docs in [Dash-User-Contributions](https://github.com/Kapeli/Dash-User-Contributions/tree/master/docsets/Wagtail) for offline docs apps [Dash](https://kapeli.com/dash) and [Zeal](https://zealdocs.org/).
  * Follow the instructions on the README.md and submit a pull request with updated docs.

If you made a mistake in the documentation before the git tag was created and would like to update the documentation for the release, you can do the following steps:

<details>

<summary>Steps</summary>

- Delete the tag via https://github.com/wagtail/wagtail/tags
  - If a GitHub release has been created, you need to delete it before deleting the tag
- Delete the tag locally with `git tag -D v5.0.1`
- Create a new tag with `git tag v5.0.1`
- Push the new tag with `git push upstream --tags`
- Trigger a new rebuild of the documentation for the release's branch on readthedocs

</details>

## releases.wagtail.org

**For a release candidate:** you can skip this section.

Once the new release is out, please update https://releases.wagtail.org/latest.txt accordingly. You'll need AWS credentials for the S3 bucket and Cloudfront cache, which are held by the Torchbox sysadmins.

Set up the AWS client, if you haven't already - `pip install awscli`, then `aws configure` and enter the credentials.

Edit `scripts/latest.txt` with the new version details: `version` is the newest version, `url` is its release notes page, and `minorUrl` is the release notes page for the corresponding minor version, e.g. 2.15 for 2.15.1. (This is shown to users who are running an earlier minor version, so that they see the changelog for the whole minor release rather than just the .1 patch). If this is a new release (major, minor or patch) within an LTS branch, update the `lts` section too. Then, with the AWS client configured, run:

```bash
cd wagtail/scripts
./latest.sh put latest.txt
```

(It will take up to a day for changes to propagate to the Cloudfront cache. If you need it to update faster than that, someone with access to the AWS web console can purge it - the relevant operation to perform is "Create invalidation".)

_The SSL certificates for releases.wagtail.org and releases.wagtail.io needs to be manually renewed once a year: https://projects.torchbox.com/projects/sysadmin/notebook/releases.wagtail.io.md_

## Post-release

* Close the milestone on https://github.com/wagtail/wagtail/milestones
* Email wagtail@googlegroups.com with the release announcement
* Announce on #announcements on Wagtail slack (and #wagtail on Torchbox slack, if you're there)
* Blog and tweet about it
  * Share with https://django-news.com/
  * Share with https://www.reddit.com/r/django/
* Test [add-on packages in the Wagtail org](https://paper.dropbox.com/doc/Wagtail-organisation-subprojects--A0vEPub7dKgN_SsWZVYB6CZDAg-15Cg4kQNtE0LaJ6pVTrrQ) for compatibility and update as necessary

### Housekeeping for the next release

Switch back to the `main` branch of your Wagtail development clone. Make sure it's up-to-date by running `git pull upstream main`.

Create and switch to a new branch from `main`, e.g. `admin/start-wagtail-5.2`.

#### Update deprecated features

 - Delete features deprecated in this release
 - Update `wagtail.utils.deprecation`

For example, let's say we are releasing Wagtail 6.0:

1. Look for `RemovedInWagtail60Warning` messages and remove the features they are warning about
2. In `wagtail.utils.deprecation`:
    - Delete `RemovedInWagtail60Warning`
    - Change `RemovedInWagtail70Warning` to a `DeprecationWarning`
    - Create a new warning called `RemovedInWagtail80Warning` which inherits from `PendingDeprecationWarning`
3. Look for `RemovedInWagtail60`, which may exist in client-side code that needs to be removed but does not emit a deprecation warning.

#### Drop support for old versions of Django

Search the code base for `django.VERSION` and `DJANGO_VERSION`. Remove any code for versions of Django that are no longer supported in future releases. Look in `setup.py` to check which versions of Django are currently supported.

#### Remove old `versionadded` / `versionchanged` notes in the docs

`versionadded` and `versionchanged` notes for old versions of Wagtail should be removed from the docs. These notes are kept for two releases. If Wagtail 6.2 had just been released, `versionadded` and `versionchanged` notes from version `6.1` should be dropped. This will leave notes in the docs only for the `stable/6.1.x` and `stable/6.2.x` branches, with notes added for 6.3 being added for the next release (the `main` branch).

#### Bump the version

* Update `wagtail/__init__.py` with the new version number, e.g. `VERSION = (5, 2, 0, 'alpha', 1)`
* Update `wagtail/project_template/requirements.txt` with the new version number, e.g. `wagtail==5.2a0`
* Commit the changes e.g. `git commit -m "Version bump to start work on 5.2"`

#### Set up release notes

Update `CHANGELOG.txt` with a new section:

```
5.2 (xx.xx.xxxx) - IN DEVELOPMENT
~~~~~~~~~~~~~~~~

 * ...
```

Create a new file in `docs/releases/` with the following template:

<details>

<summary>Template</summary>

````
# Wagtail 5.2 release notes - IN DEVELOPMENT

_Unreleased_

```{contents}
---
local:
depth: 1
---
```

## What's new


### Other features

 * ...

### Bug fixes

 * ...

### Documentation

 * ...

### Maintenance

 * ...


## Upgrade considerations - changes affecting all projects

## Upgrade considerations - deprecation of old functionality

## Upgrade considerations - changes affecting Wagtail customisations
````

Update `docs/releases/index.rst` to include the new version.

Update the Wagtail/Django/Python version compatibility table in `docs/releases/upgrading.md` to include the new version.

Commit the changes e.g. `git commit -m "Set up release notes for 5.2"`

</details>

#### Make a new PR

Make a new PR from this branch. Core team member approval is optional.

See https://github.com/wagtail/wagtail/pulls?q=is%3Apr+is%3Aclosed+in%3Atitle+housekeeping+start for past examples.