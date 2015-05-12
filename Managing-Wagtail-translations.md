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

    tx pull -a --minimum-perc=30

and 'git add' any new folders that are created. Then, within each submodule with a 'locale' folder (run `find . -name locale` to find them):

    cd wagtail/wagtailfoo
    django-admin compilemessages

Again, 'git add' any new .mo files that are created.

# Generating new source files for translation

To be done periodically, particularly after any piece of development that involves creating / editing / moving a significant number of translatable strings. Within each submodule with a 'locale' folder (run `find . -name locale` to find them):

    cd wagtail/wagtailfoo
    django-admin makemessages --locale=en

Then, from the root of the Wagtail codebase:

    tx push -s
