Here are links to the various bottlenecks of the contribution funnel, which core team members can use to unblock contributions.

## Needs triage

This queue should be easy to empty (😉). Take the time to label PRs according to the component they touch, their type, status. This is also a good time to make a first comment on the PR to thank the contributor, and flag anything obviously amiss with the PR – absence of description of the changes (or screenshots?), missing documentation updates or tests, broken tests in CI.

[`sort:updated-desc no:label`](https://github.com/wagtail/wagtail/pulls?q=is%3Apr+is%3Aopen+sort%3Aupdated-desc+no%3Alabel)

## Design decision needed

We should aim to have this empty, as those PRs either need confirmation to go ahead, or should be closed to get a complete re-implementation. However it requires at least two core team members to meaningfully decide on these.

[`sort:updated-desc label:"status:Needs Design Decision"`](https://github.com/wagtail/wagtail/pulls?q=is%3Apr+is%3Aopen+sort%3Aupdated-desc+label%3A%22status%3ANeeds+Design+Decision%22)

## Needs review

The PR needs a review. Depending on the state of the PR it might be helpful for it to get a first high-level "in the browser" review, or more in-depth "checkout locally and try" review.

[`sort:updated-desc label:"status:Needs Review"`](https://github.com/wagtail/wagtail/pulls?q=is%3Apr+is%3Aopen+sort%3Aupdated-desc+label%3A%22status%3ANeeds+Review%22)