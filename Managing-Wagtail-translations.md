Steps for syncing translations for the Wagtail backend between Transifex and the Wagtail codebase.

This document is for Wagtail core developers. If you are looking to contribute to Wagtail's translations, use Transifex: https://www.transifex.com/projects/p/wagtail/

## gettext setup

Make sure that you have an installation of the `gettext` program on your machine. Most package managers have it under the `gettext` package, e.g. `brew install gettext`.

To be extra sure, you can run the following commands on a clean branch:

```bash
# From the repository root, enter the `wagtail` directory
cd wagtail
django-admin makemessages --locale=en
django-admin compilemessages
```

If `gettext` has been installed correctly, the commands should exit gracefully. Note that the above may cause changes to the translation source files, so you may have to run `git restore .` to undo them. (Make sure you don't have any uncommitted changes you'd like to keep before running the `git restore` command!) 

## Transifex setup

Install the Transifex CLI following the instructions on https://github.com/transifex/cli#installation. Be aware that the `curl` script will dump the `tx` executable in _your current directory_ and add a `PATH` export to your profile. If you don't like installing it this way, you can do either of the following:
- Download the binary directly. If you use macOS, you may encounter a warning from macOS when you try to run it for the first time. You'll have to allow the executable from the "Security & Privacy" setting.
  - For more details, see https://support.apple.com/en-us/HT202491 (scroll down to "If you want to open an app that hasn’t been notarized or is from an unidentified developer").
- Run the script from an empty directory, move `tx` somewhere sensible on your path like `/usr/local/bin/`, and remove the added `PATH` line from your profile.

Generate an API token through https://www.transifex.com/user/settings/api/ if you don't have one already, and create a `.transifexrc` file in your home directory containing the following:

```ini
[https://www.transifex.com]
rest_hostname = https://rest.api.transifex.com
token         = <your API token>
```

Create a `logs` directory alongside the root of your Wagtail codebase. (This will help manage the output of `scripts/fetch-translations.sh`, which is liable to produce more output than your console history can handle.)

## Fetching new translations from Transifex

To be done periodically, ideally just before a new Wagtail release. From the root of the wagtail codebase:

```bash
./scripts/fetch-translations.sh > ../logs/translation.out 2>../logs/translation.err
```
and `git add` any new folders that are created.

**Important** - check the log files in `logs/` for errors, and sanity-check the changes with `git status` / `git diff` before committing. Failures during the script's run can result in files erroneously being deleted. You can monitor the log while the `fetch-translations` script is in progress by running `tail -f logs/translation.err` (or `translation.out` for the output).

Run:

```bash
python ./scripts/check-translation-strings.py
```

to check for any inconsistencies in format strings - if any issues are reported, fix them in Transifex and re-run `fetch-translations`.

Once this is done, run

```bash
python ./scripts/get-translator-credits.py > ./scripts/translators.txt
```

and update `CONTRIBUTORS.txt` with any new translators / languages that show up in the `git diff` of `translators.txt`.

All languages with >= 90% coverage should be in the `WAGTAILADMIN_PROVIDED_LANGUAGES` list in [wagtail/admin/localization.py](https://github.com/wagtail/wagtail/blob/master/wagtail/admin/localization.py), which defines the default list of languages under 'language preferences' in the admin. Compare this list against the progress list at https://app.transifex.com/torchbox/wagtail/dashboard/ and add any languages with >= 90% coverage not already listed.

## Generating new source files for translation

To be done periodically, particularly after any piece of development that involves creating / editing / moving a significant number of translatable strings. From `scripts`, run:

```bash
./scripts/rebuild-translation-sources.sh
```

and commit the updated files to git.

Then, from the root of the Wagtail codebase:

```bash
tx push -s
```

## Setting up translations for a new app

This assumes that strings have already been marked for translation throughout the app codebase (using `ugettext`, `{% trans %}` etc). From the app root, run:

```bash
mkdir locale
django-admin makemessages --locale=en --extension=html,txt,py
```

(Add `js` to the `--extension` list if this app uses JS templates. New apps really shouldn't though!)

Edit the file `.tx/config` to add a new section (replace `myapp` and `/path/to/myapp` as appropriate):

```ini
[wagtail.myapp]
file_filter = wagtail/path/to/myapp/locale/<lang>/LC_MESSAGES/django.po
source_file = wagtail/path/to/myapp/locale/en/LC_MESSAGES/django.po
source_lang = en
type = PO
```

Commit the updated config file and new locale files to git.

From https://www.transifex.com/torchbox/wagtail/content/, click "Add a new resource", and upload the `django.po` file, setting the name to `myapp` and specifying 'PO File' as the file type.