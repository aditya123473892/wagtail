Steps for syncing translations for the Wagtail backend between Transifex and the Wagtail codebase.

This document is for Wagtail core developers. If you are looking to contribute to Wagtail's translations, use Transifex: https://www.transifex.com/projects/p/wagtail/

# Transifex setup

    pip install transifex-client

Create a `.transifexrc` file in your home directory containing the following:

    [https://www.transifex.com]
    username = myusername
    token =
    password = mypassword
    hostname = https://www.transifex.com

# Fetching new translations from Transifex

To be done periodically, ideally just before a new Wagtail release. From the root of the wagtail codebase:

    cd scripts
    ./fetch-translations.sh

and 'git add' any new folders that are created. However, don't add folders for territory-specific translations (e.g. `es_ES`) that are less complete than the corresponding generic translations (e.g. `es`), as these cause the generic ones to be blocked due to a Django bug: https://github.com/wagtail/wagtail/issues/3600

**Important** - check the output of `fetch-translations.sh` for errors, and sanity-check the changes with `git status` / `git diff` before committing. Failures during the script's run can result in files erroneously being deleted.

Once this is done, run

    python ./get-translator-credits.py

and update CONTRIBUTORS.txt with any translators / languages not already mentioned. Also add a release note in CHANGELOG.txt and docs/releases for any new languages.

All languages with >= 90% coverage should be in the `WAGTAILADMIN_PROVIDED_LANGUAGES` list in [wagtail/admin/utils.py](https://github.com/wagtail/wagtail/blob/master/wagtail/admin/utils.py), whch defines the default list of languages under 'language preferences' in the admin. Compare this list against the progress list at https://www.transifex.com/torchbox/wagtail/languages/ and add any languages with >= 90% coverage not already listed.

# Generating new source files for translation

To be done periodically, particularly after any piece of development that involves creating / editing / moving a significant number of translatable strings. Within each submodule with a 'locale' folder (run `find . -name locale` to find them):

    cd wagtail/wagtailfoo
    django-admin makemessages --locale=en --extension=html,txt,py,js

NOTE: `django-admin` is run from the app's root, NOT the 'locale' folder.

(Specifying js in `--extension` ensures that translations in our JS templates, e.g. /wagtail/wagtailimages/templates/wagtailimages/chooser/chooser.js, are picked up. If in future we eliminate these JS templates, it should be fine to leave the `--extension` switch out here.)

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