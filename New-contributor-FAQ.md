## This page has been replaced by [#10070](https://github.com/wagtail/wagtail/issues/10070)

### How can I start contributing?

* Start simple -- pick something small first. The [good first issue](https://github.com/wagtail/wagtail/issues?q=is%3Aopen+is%3Aissue+label%3A%22good+first+issue%22) label is a good place to look.
* Read the entire issue, all comments (links) and related issues
* Someone may have started work (that work may have stalled)
* Check if assigned, **we do not assign issues to someone outside of the core team**

If you have done all of that and think you can give it a go just a comment with something like 'I will give this a go', no need to ask for permission.

### Do I need to ask for permission to work on an issue?

**No.** However, check if there is an existing pull request (PR). If there is nothing, you can optionally add a comment mentioning that you're starting work on it.

### Where can I find more information about setting up?

See the [Contributing](https://docs.wagtail.org/en/stable/contributing/index.html) section of the Wagtail documentation.

### What should I include in my pull requests

0. The fix or feature you are working on
1. Tests
2. Linted code (we make use of [pre-commit](https://pre-commit.com/). You can run all formatting with `make format`)
3. Updated documentation where relevant (e.g. when adding a new feature)

### When do I need to write unit tests for a PR?

Unless you are updating the documentation, the PR should contain tests.

If you are new to writing tests in Django, start by reading the [Django documentation on testing](https://docs.djangoproject.com/en/4.0/topics/testing/overview/). Re-read the [Wagtail documentation notes on testing](https://docs.wagtail.org/en/stable/contributing/developing.html#testing) and have a look at [existing tests](https://cs.github.com/?scopeName=All+repos&scope=&q=repo%3Awagtail%2Fwagtail+path%3A**%2Ftests%2F**).

### Where can I get help with my PR?

In the `#support` channel in [Slack](https://github.com/wagtail/wagtail/wiki/Slack)
