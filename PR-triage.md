Here are links to the various bottlenecks of the contribution funnel, which core team members can use to unblock contributions. All of the filters below are built with `is:pr is:open sort:updated-desc` as a baseline.

## Needs triage

This queue should be easy to empty (😉). Take the time to label PRs according to the component they touch, their type, status. This is also a good time to make a first comment on the PR to thank the contributor, and flag anything obviously amiss with the PR – absence of description of the changes (or screenshots?), missing documentation updates or tests, broken tests in CI.

[`no:label`](https://github.com/wagtail/wagtail/pulls?q=is%3Apr+is%3Aopen+sort%3Aupdated-desc+no%3Alabel)

## Ready to merge?

This either can be merged, or needs to be relabeled.

[`review:approved -label:"status:Needs Review" -label:"status:Needs Work"`](https://github.com/wagtail/wagtail/pulls?q=is%3Apr+is%3Aopen+sort%3Aupdated-desc+review%3Aapproved+-label%3A%22status%3ANeeds+Review%22+-label%3A%22status%3ANeeds+Work)

## Design decision needed

We should aim to have this empty, as those PRs either need confirmation to go ahead, or should be closed to get a complete re-implementation. However it requires at least two core team members to meaningfully decide on these.

[`label:"status:Needs Design Decision"`](https://github.com/wagtail/wagtail/pulls?q=is%3Apr+is%3Aopen+sort%3Aupdated-desc+label%3A%22status%3ANeeds+Design+Decision%22)

## Needs review

The PR needs a review. Depending on the state of the PR it might be helpful for it to get a first high-level "in the browser" review, or more in-depth "checkout locally and try" review.

[`label:"status:Needs Review"`](https://github.com/wagtail/wagtail/pulls?q=is%3Apr+is%3Aopen+sort%3Aupdated-desc+label%3A%22status%3ANeeds+Review%22)

---

## Going further

If you are interested to invest more time into unblocking others’ contributions, here are PRs you can consider.

### Needs docs or tests (but not work)

- Needs docs: [`label:"status:Needs Docs" -label:"status:Needs Work"`](https://github.com/wagtail/wagtail/pulls?q=is%3Apr+is%3Aopen+sort%3Aupdated-desc+label%3A%22status%3ANeeds+Docs%22+-label%3A%22status%3ANeeds+Work%22+)
- Needs tests: [`label:"status:Needs Tests" -label:"status:Needs Work"`](https://github.com/wagtail/wagtail/pulls?q=is%3Apr+is%3Aopen+sort%3Aupdated-desc+label%3A%22status%3ANeeds+Tests%22+-label%3A%22status%3ANeeds+Work%22+)
