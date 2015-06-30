Steps for syncing translations for the Wagtail backend between Transifex and the Wagtail codebase.

This document is for Wagtail core developers. If you are looking to contribute to Wagtail's translations, use Transifex: https://www.transifex.com/projects/p/wagtail/

# Transifex setup

    pip install transifex-client

(You may need to switch to a Python 2 virtualenv - Python 3 is not supported as of transifex-client version 0.10)

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

and 'git add' any new folders that are created.

**Important** - check the output of `fetch-translations.sh` for errors, and sanity-check the changes with `git status` / `git diff` before committing. Failures during the script's run can result in files erroneously being deleted.

# Generating new source files for translation

To be done periodically, particularly after any piece of development that involves creating / editing / moving a significant number of translatable strings. Within each submodule with a 'locale' folder (run `find . -name locale` to find them):

    cd wagtail/wagtailfoo
    django-admin makemessages --locale=en

Then, from the root of the Wagtail codebase:

    tx push -s
