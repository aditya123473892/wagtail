These guidelines should be followed by maintainers of Python packages that are hosted on Wagtail’s GitHub organisation.

These guidelines exist to improve consistency between packages that are maintained by the Wagtail core team. This makes it easier for contributors to submit patches and core team members to perform administrative tasks on any packages in the Wagtail organisation.

Notes on language:

- All guidelines are worded to contain either the word Should or Must.
- Where Must is used in a guideline, this means that not following the guideline will be considered a bug.
- Where Should is used in a guideline, this means that the package maintainer is encouraged to follow it to improve consistency with other packages, but not following it would not be considered a bug.

Adding new guidelines

- To suggest a new guideline, open a Github discussion or add it to the core team meeting agenda
- Guidelines should not be idealistic. Please do not suggest anything that isn’t already in use on multiple packages
- If there is any disagreement about whether a guideline should exist or its wording, it should be left out. We can always add it later

# Documentation

## Readme

- Must be written in Markdown and named `README.md`
- Must be visible on PyPI and renders properly
- Must have badges linking to PyPI and license
- Should have a badge linking to online code coverage results
- Must link to the changelog
- Must mention what versions of Python, Django and Wagtail are supported
- Must include an installation guide. This could be an abridged version of what is in the docs, but it must link to the full guide in the docs if this is the case
- Must link to full documentation (or, for small packages, documentation included directly in the readme)
- Must link to the Github discussions board that should be enabled on the repo (see Support)
- Must mention where to report security issues (security@wagtail.io)

## Documentation

Note: Small packages may use their readme as documentation. These guidelines only apply when documentation separate to the readme exists.

- Must be available on the web
- Must be written in markdown
- Must be linked to from readme
- Must mention what versions of Python, Django and Wagtail are supported
- Must have an installation guide and a usage guide
- Should have reference or explanation, depending on the complexity of the package

## Changelog

- Must have a changelog named `CHANGELOG.md`
- Should follow Keep a Changelog

## Contributing guide

- Must have a contributing guide which is named `CONTRIBUTING.md`

## License

- Must have a permissive licence (such as BSD or MIT, but not GPL)
- Should be licensed under BSD 3-clause, if possible
- Must have a license file at the top of the repo

## `setup.py` / `setup.cfg` / `pyproject.toml`

- Dependency versions should be as wide as possible
- Support for EOL versions of Python, Django and Wagtail should be removed from the earliest minor release of the package following the moment the dependency went EOL. This does not apply if provision is made to maintain support for the EOL dependency.
- Testing and documentation requirements listed in extras
- Must have classifiers for Python, Django and Wagtail versions
- Must have classifier for license
- Must have project URLs linking to Documentation and Changelog

# Development Process

## Branching

- Default branch must be called `main`
- Each major release must have a branch prefixed with “stable”. For example `stable/1.0.x`. This is to allow security fixes to be backported

## Releases

- Version numbers must follow PEP440
- Each release must have a git tag and a github release
- Each release must be mentioned in the changelog
- Each release must be published to PyPI

## PyPI

- Package must have a PyPI page
- At least two core team members must have admin access
    - Note: Everyone who has permission to publish an official Wagtail package must have 2FA enabled on their PyPI account. Remember to check this when adding collaborators (this is visible in the PyPI web UI)

# Automated testing

## Django unit tests

- Should use Django’s built-in test framework
- Must have unit test coverage of at least 85%
- Should aim for unit test coverage of at least 90%
- Migrations and tests must be excluded from coverage reports
- Must have instructions on how to run unit tests

## Continuous Integration

- Must have a Continuous Integration set up with Github Actions, Circle CI, or both
- Should test against Wagtail nightly and report issues to #nightly-build-failures channel
- Must be linted with flake8
- Should be formatted with black and isort

## Support

- Should provide support through Github Discussions

## New packages

- For packages that come with a user interface, reach out to [Wagtail’s accessibility team](https://github.com/wagtail/wagtail/wiki/Accessibility-team) to validate the approach or test the package

## EOL (End of Life) packages

- The repository must be archived and moved to the [wagtail-deprecated](https://github.com/wagtail-deprecated) organisation
- A message must be added to the readme. This should be visible on both PyPI as well

## Github tips

* To remove the 'packages' section from a Github project's about sidebar, click the small cog next to the word 'about', then untick packages.
