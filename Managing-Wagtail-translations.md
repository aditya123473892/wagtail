Steps for syncing translations for the Wagtail backend between Transifex and the Wagtail codebase.

This document is for Wagtail core developers. If you are looking to contribute to Wagtail's translations, use Transifex: https://www.transifex.com/projects/p/wagtail/

# Transifex setup

Install the Transifex CLI following the instructions on https://github.com/transifex/cli#installation. Be aware that the `curl` script will dump the `tx` executable in _your current directory_ and add a `PATH` export to your profile. If you think this is a stupid way to install software, you can either download the binary directly (but then I ran into Mac OS security dialogs not letting me run it), or run the script from an empty directory, move `tx` somewhere sensible on your path like `/usr/local/bin/`, and remove the `PATH` line from your profile.

Generate an API token through https://www.transifex.com/user/settings/api/ if you don't have one already, and create a `.transifexrc` file in your home directory containing the following:

    [https://www.transifex.com]
    rest_hostname = https://rest.api.transifex.com
    token         = <your API token>

Create a `logs` directory alongside the root of your Wagtail codebase. (This will help manage the output of fetch-translations.sh, which is liable to produce more output than your console history can handle...)

# Fetching new translations from Transifex

To be done periodically, ideally just before a new Wagtail release. From the root of the wagtail codebase:

    ./fetch-translations.sh > ../logs/translation.out 2>../logs/translation.err

and 'git add' any new folders that are created.

**Important** - check the log files in `logs/` for errors, and sanity-check the changes with `git status` / `git diff` before committing. Failures during the script's run can result in files erroneously being deleted.

Run:

    python ./scripts/check-translation-strings.py

to check for any inconsistencies in format strings - if any issues are reported, fix them in Transifex and re-run fetch-translations.

Once this is done, run

    python ./get-translator-credits.py > ../../logs/translators-YYYYMMDD.txt
    diff -U10 ../../logs/translators-LAST_YYYYMMDD.txt ../../logs/translators-YYYYMMDD.txt

and update CONTRIBUTORS.txt with any new translators / languages that show up in the diffs.

All languages with >= 90% coverage should be in the `WAGTAILADMIN_PROVIDED_LANGUAGES` list in [wagtail/admin/localization.py](https://github.com/wagtail/wagtail/blob/master/wagtail/admin/localization.py), which defines the default list of languages under 'language preferences' in the admin. Compare this list against the progress list at https://www.transifex.com/torchbox/wagtail/languages/ and add any languages with >= 90% coverage not already listed.

# Generating new source files for translation

To be done periodically, particularly after any piece of development that involves creating / editing / moving a significant number of translatable strings. From `scripts`, run:

    ./rebuild-translation-sources.sh

and commit the updated files to git.

Then, from the root of the Wagtail codebase:

    tx push -s

# Setting up translations for a new app

This assumes that strings have already been marked for translation throughout the app codebase (using `ugettext`, `{% trans %}` etc). From the app root, run:

    mkdir locale
    django-admin makemessages --locale=en --extension=html,txt,py

(Add `js` to the `--extension` list if this app uses JS templates. New apps really shouldn't though!)

Edit the file `.tx/config` to add a new section (replace `myapp` and `/path/to/myapp` as appropriate):

    [wagtail.myapp]
    file_filter = wagtail/path/to/myapp/locale/<lang>/LC_MESSAGES/django.po
    source_file = wagtail/path/to/myapp/locale/en/LC_MESSAGES/django.po
    source_lang = en
    type = PO

Commit the updated config file and new locale files to git.

From https://www.transifex.com/torchbox/wagtail/content/, click "Add a new resource", and upload the django.po file, setting the name to 'myapp' and specifying 'PO File' as the file type.