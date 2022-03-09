In February 2022 Wagtail's code formatting toolchain was updated to use Black, Prettier and DJHTML. This will invariably generate merge conflicts against PRs that were open before the formatting updates. The following steps (tested on macOS with zsh) will bring those branches up to date with the current formatting:

```sh
# Make a copy of your branch
git branch save/my-existing-branch my-existing-branch
# Make sure you have the latest `main` from Wagtail
git remote add upstream git@github.com:wagtail/wagtail.git
git checkout main
git pull upstream main
# Rebase onto the commit preceding the Prettier reformatting to resolve conflicts that would have been present anyway.
git checkout my-existing-branch
git rebase af942a27e41b47e257b6cd46c01a13cd381fed04^1
# Install Prettier and other Wagtail development dependencies
# Make sure you use Node v16 and npm v8
node --version
npm --version
npm install --no-save
# Test-run Prettier – this should show formatting errors.
npm run lint:format
# Rebase again, this time with the reformatting as the base,
# always preserving your changes in case of conflicts, and automatically reformatting with Prettier.
git rebase --strategy-option=theirs --exec '(npm run format || true) && git add . && git commit --amend --no-edit --no-verify' af942a27e41b47e257b6cd46c01a13cd381fed04
# Test-run Prettier – this should show no formatting errors.
npm run lint:format
# Rebase onto the commit before the djhtml reformatting.
git rebase  01986cfa1702929352ac8b6d58ada6070da2c700^1
# Install djhtml
pip install -e '.[testing]'
# Test-run djhtml – this should show formatting errors.
git ls-files '*.html' | xargs djhtml --check
# Rebase again, this time with the reformatting as the base,
# always preserving your changes in case of conflicts, and automatically reformatting with djhtml.
git rebase --strategy-option=theirs --exec '(git ls-files "*.html" | xargs djhtml -i || true) && git add . && git commit --amend --no-edit --no-verify' 01986cfa1702929352ac8b6d58ada6070da2c700
# Test-run djhtml – this should show no formatting errors.
git ls-files '*.html' | xargs djhtml --check

# Rebase onto the commit before the black reformatting.
git rebase d10f15e55806c6944827d801cd9c2d53f5da4186^1

# Install dependencies
## pre-commit via pip and initialize
pip install pre-commit && pre-commit install
## black/flake8 directly via Wagtail's testing dependencies (either in a VM or a virtual environment)
pip install -e '.[testing]'

# Run black and flake8
## with pre-commit:
pre-commit run black && pre-commit run flake8
## without:
# black . && flake8 .

# Rebase again, this time with the reformatting as the base,
# always preserving your changes in case of conflicts, and automatically linting and reformatting.
## pre-commit
git rebase \
  --strategy-option=theirs \
  --exec '(pre-commit run black --all-files || true) && git add . && git commit --amend --no-edit --no-verify' \
  d10f15e55806c6944827d801cd9c2d53f5da4186
## or, directly
# git rebase \
#   --strategy-option=theirs \
#   --exec '(black --target-version py37 . || true) && git add . && git commit --amend --no-edit --no-verify' \
#   d10f15e55806c6944827d801cd9c2d53f5da4186

# Lint again, this should not show any errors
## using precommit
pre-commit run --all-files
## or, directly
# black --target-version py37 .
# flake8 .

# Finally rebase onto the latest version from Wagtail main, as per usual.
git rebase main
```