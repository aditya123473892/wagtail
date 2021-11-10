Find us in [#accessibility on Slack](https://app.slack.com/client/T0K33F93J/CB7L6L5S6).

## Team charter

The team’s membership is open to all, introduce yourself in [#accessibility on Slack](https://app.slack.com/client/T0K33F93J/CB7L6L5S6) if you’re interested in joining. We currently operate with a membership term of 6 months, so people can commit for a short term, and then decide to proceed or stop.

We meet every two weeks to discuss everyone’s recent progress and next steps. At the end of each meeting, all participants should each have volunteered for an action, which they must strive to complete before the next meeting. Meeting notes and actions are public for future and past meetings. Meetings happen on Google Meet.

In-between meetings, we collaborate via Slack, using the [#accessibility](https://app.slack.com/client/T0K33F93J/CB7L6L5S6) channel as an open forum, and use GitHub to keep track of actions, and collaborate on specific issues & pull requests.

## Team members

Current members:

- Scott Cranfill ([@Scotchester](https://github.com/Scotchester)), UTC - 4 or 5, since June 2020
- Thibaud Colas ([@thibaudcolas](https://github.com/thibaudcolas)), UTC + 0 or 1, since June 2020
- Jesse Menn ([@jessemenn](https://github.com/jessemenn)), UTC - 4 or 5, since February 2021
- Kyle Bayliss ([@kbayliss](https://github.com/kbayliss)), UTC + 0 or 1, since February 2021
- Storm Heg ([@Stormheg](https://github.com/Stormheg)), UTC + 1 or 2, since February 2021
- Saptak Sengupta ([@SaptakS](https://github.com/SaptakS)), since July 2021

Past members: Andreas Bernacca (June 2020 – January 2021)

---

Next meetings: [see agenda](https://docs.google.com/document/d/1YUxOs5jYZMd8rX291mDE123xIK7tbD63PzSR9ooFa4c/edit)

Past meetings:

<!-- Insert meeting notes here, most recent first: -->

## 2021-10-15 -- retrospective

Attendees: Scott, Thibaud, Saptak

### Actions

- Saptak Share research on uppercase / capitalized text
- ✅ Thibaud Trial removing all uppercase
- <https://wagtailcms.slack.com/archives/CB7L6L5S6/p1634332413035500?thread_ts=1634249236.029900&cid=CB7L6L5S6>
- ✅ Thibaud Share retrospective with core team

### Discussions

- CI / automated checks on PR
  - Start Set up automated accessibility tests for the whole admin
  - Start/Continue  making stricter a11y related CI checks to prevent UI features with a11y issues getting released?
  - Start implementing automated accessibility testing on PRs.
  - Stop allowing features that involve UI to be merged without meeting some list of accessibility standards.
  - Discussion
    - Check diff from PR?
- Design phase
  - Continue Review of all designs for accessibility considerations
  - Continue paying close attention to editor UI overhaul for accessibility issues.
  - bring up things that need review from a11y team.
  - Continue  implementing a11y at the design phase itself instead of in the review phase for new features?
  - Start UI dev direction on all headline release features at inception
  - Discussion
    - Recurring item in our team's agenda, so we keep in touch with the core team and set the expectation we're expecting to be reviewing features / designs
    - Keep in mind we don't necessarily want to mandate designs -- it's ok to code first, just want to make sure there is room for accessibility review
- Core team
  - Start UI dev team in addition to accessibility
  - Start evolving into the proposed UI Team??
  - Continue paying close attention to editor UI overhaul for accessibility issues.
  - Continue raising awareness of accessibility issues and goals during Core Team discussions.
- Accessibility team
  - Start Systematic review of all UI PRs by either UI dev or accessibility team
  - Start publicising more about a11y efforts that are being taken (e.g. a11y statement, progress in a11y improvements done) to make more people aware and interested to give feedbacks
  - Continue doing meeting biweekly to discuss different things and bring up things that need review from a11y team.
  - Continue having a team of about a half dozen, which usually results in at least 3 people in attendance for regular meetings.
- Current work
  - Continue the great work knocking out the Windows High Contrast Mode issues.
  - Continue pushing the SVG icon boulder up the hill :)
  - Start tackling low-hanging fruit in existing codebase (e.g., capitalized button text issue).
    - Pretty frequent issue
- Misc
  - Continue Triage & curation of accessibility issues backlog, with good first issues in particular
  - Continue Fully remove all IE11 / legacy code so we can leverage more modern browser features
  - Continue Make the styles linting config stricter for common accessibility issues
    - Disallow px units for font-size
    - Disallow hover styles without focus
- Release notes
  - Typed table block release notes / experimental nature
  - High contrast mode

## 2021-10-01

Attendees: Thibaud, Jesse, Saptak, Scott, Kyle

### Actions

- Thibaud Review draft from Saptak
- Thibaud Blog post about high-contrast mode & Saptak joining our team
- ✅ Thibaud Test bulk-actions work about to be merged, currently in <https://github.com/wagtail/wagtail/tree/feature/bulk-actions>
- Add test plan for issue
- ✅ Saptak Add extra notes to accessibility review issue for bulk actions
- ✅ Thibaud Raise accessibility statement at next core team meeting
- ✅ Thibaud Share plan of UI / accessibility work over next 3 months
- ✅ Thibaud Check DjangoCon US plans outside of sprints (not happening)

### Discussions

- Actions review
  - Thibaud Review draft from Saptak
  - Thibaud Review [Fix userbar tabbing behaviour #7507](https://github.com/wagtail/wagtail/pull/7507)
  - Thibaud Look into Squash.io usage
    - ✅Issue with ports fixed: [#7523](https://github.com/wagtail/wagtail/pull/7523)
  - Thibaud Blog post about high-contrast mode & Saptak joining our team
  - ✅ Saptak Add notes from review of bulk actions
  - Thibaud Test bulk-actions work about to be merged, currently in <https://github.com/wagtail/wagtail/tree/feature/bulk-actions>
  - Scott Raise accessibility statement at next core team meeting
  - Thibaud will do next week if this hasn't happened
  - ✅Thibaud Review whether there is upcoming work on More dropdown
    - Yes -- from January onwards
  - ✅Storm Triage issues for Hacktoberfest
    - Has happened even if not Storm

## 2021-09-17

Attendees: Saptak, Scott, Jesse, Storm, Thibaud

### Actions

- Thibaud Review draft from Saptak
- Thibaud Review [Fix userbar tabbing behaviour #7507](https://github.com/wagtail/wagtail/pull/7507)
- Thibaud Look into Squash.io usage
  - ✅Issue with ports fixed: [#7523](https://github.com/wagtail/wagtail/pull/7523)
- Thibaud Blog post about high-contrast mode & Saptak joining our team
- Saptak Add notes from review of bulk actions
- Thibaud Test bulk-actions work about to be merged, currently in <https://github.com/wagtail/wagtail/tree/feature/bulk-actions>
- Scott Raise accessibility statement at next core team meeting
- Thibaud Review whether there is upcoming work on More dropdown
- Storm Triage issues for Hacktoberfest

### Discussions

- Actions review
  - ✅Saptak Review accessibility statements from other projects & outline of page contents for Wagtail
  - ✅Storm Work on last change for userbar ARIA menu practice
  - [Fix userbar tabbing behaviour #7507](https://github.com/wagtail/wagtail/pull/7507)  - ready for review
    - Scott trying out with squash.io?
  - Thibaud Blog post about high-contrast mode & Saptak joining our team
  - ✅Saptak Test bulk-actions work about to be merged, currently in <https://github.com/wagtail/wagtail/tree/feature/bulk-actions>
  - Thibaud Test bulk-actions work about to be merged, currently in <https://github.com/wagtail/wagtail/tree/feature/bulk-actions>
- [Accessibility statement](https://docs.google.com/document/u/1/d/1D07GcfmH6R6ZbawomAje5TpcsGASxLi4dz5r_ZirQiA/edit)
- SVG icons
  - Scott & Thibaud
  - One more thing!
    - More dropdown [#6281](https://github.com/wagtail/wagtail/issues/6281)
    - Potentially refactored as part of editor UI?
- Hacktoberfest
  - Good first issues on high-contrast mode
  - Curate ahead of the event?
  - Add to blog post?
  - Issue triage & review of existing Good first PRs ahead of Hacktoberfest

## 2021-09-03

Attendees: Storm, Thibaud, Jesse, Saptak, Scott

### Actions

- Saptak Review accessibility statements from other projects & outline of page contents for Wagtail
- Storm Work on last change for userbar ARIA menu practice
- Thibaud Blog post about high-contrast mode & Saptak joining our team
- Saptak Test bulk-actions work about to be merged, currently in <https://github.com/wagtail/wagtail/tree/feature/bulk-actions>
- Thibaud Test bulk-actions work about to be merged, currently in <https://github.com/wagtail/wagtail/tree/feature/bulk-actions>

### Discussions

- Actions review
  - ✅ Thibaud Review high-contrast mode audit from Kyle
    - <https://trello.com/c/YOEpYngg/29-comment-buttons-should-use-button-text-colour>
    - Blog post
    - Assistiv Labs
  - ✅ Thibaud Update CONTRIBUTING.md with accessibility opportunities
    - <https://github.com/wagtail/wagtail/pull/7462>
  - Saptak Review accessibility statements from other projects & outline of page contents for Wagtail
    - More work on this over the next week
  - ✅ Thibaud Review & merge <https://github.com/wagtail/wagtail/pull/7408>
  - ✅ Thibaud Update footer actions issue with recommendation for ARIA markup based on review ([https://w3c.github.io/aria-practices/examples/menubar/menubar-navigation.html](https://w3c.github.io/aria-practices/examples/menubar/menubar-navigation.html_)) <https://github.com/wagtail/wagtail/issues/7366>
  - Storm Work on last change for userbar ARIA menu practice
    - Evaluating two different ways to do this
      - Roving tabindex (considering this for now)
      - aria-activedescendants
  - ✅ Thibaud Add Saptak to accessibility team roster & invite to GitHub team
- High-contrast mode -- 20 issues
  - Planning a blog post to spread the word about high-contrast mode, our recent work, Saptak's involvement, and encourage participations from potential users of high-contrast mode.
  - [High-contrast mode: Dashboard icons are hard to see and should use link text color #7325](https://github.com/wagtail/wagtail/issues/7325)
  - [High-contrast mode: SVG icons within links should match link text colour #7326](https://github.com/wagtail/wagtail/issues/7326)
  - [Hamburger menu doesn't work for keyboard and high-contrast mode users #7327](https://github.com/wagtail/wagtail/issues/7327)
  - [High-contrast mode: Breadcrumb separator should match link text colour #7328](https://github.com/wagtail/wagtail/issues/7328)
  - [High-contrast mode: Explorer wagtail icon is hard to see on dark background #7329](https://github.com/wagtail/wagtail/issues/7329)
  - [High-contrast mode: Comments icon should match link colour #7331](https://github.com/wagtail/wagtail/issues/7331)
  - [Collapsible panels in edit UIs are impossible to open or close with keyboards or screen readers #7332](https://github.com/wagtail/wagtail/issues/7332)
  - [High-contrast mode: Success/Warning/Error help-block content needs a border to be more identifiable #7447](https://github.com/wagtail/wagtail/issues/7447)
  - [High-contrast mode: icon buttons with no text appear squashed #7448](https://github.com/wagtail/wagtail/issues/7448)
  - [High-contrast mode: buttons with .disabled class look active in high-contrast mode #7449](https://github.com/wagtail/wagtail/issues/7449)
  - [High-contrast mode: dropdown menu needs custom styles #7450](https://github.com/wagtail/wagtail/issues/7450)
  - [High-contrast mode: Switches do not visually convey their state #7451](https://github.com/wagtail/wagtail/issues/7451)
  - [High-contrast mode: Search form should define a border #7452](https://github.com/wagtail/wagtail/issues/7452)
  - [High-contrast mode: active tab can't be determined #7453](https://github.com/wagtail/wagtail/issues/7453)
  - [High-contrast mode: tag field shouldn't override background #7454](https://github.com/wagtail/wagtail/issues/7454)
  - [High-contrast mode: vertical separation between field panels is lost #7455](https://github.com/wagtail/wagtail/issues/7455)
  - [High-contrast mode: sidebar needs vertical separation with main content #7456](https://github.com/wagtail/wagtail/issues/7456)
  - [High-contrast mode: StreamField block chooser menu buttons do not look like buttons #7457](https://github.com/wagtail/wagtail/issues/7457)
  - [High-contrast mode: comments dropdown needs a border #7458](https://github.com/wagtail/wagtail/issues/7458)
  - [High-contrast mode: Comment buttons should use button text colour #7459](https://github.com/wagtail/wagtail/issues/7459)
- Accessibility time in October
  - UI architecture tech debt: <https://github.com/wagtail/wagtail/issues/3804>
  - Looking for 2-3 people to contribute
- Review accessibility of new checkbox design
  - Raised by Storm (bulk actions mentor)
  - Current unchecked checkboxes don't have a lot of contrast against background.
  - New design (for bulk actions): <https://www.figma.com/file/q6DeuoBXGCtYdf7GdGJs8D/Wagtail-Design-Toolkit?node-id=972%3A53>
  - Bulk actions team requests a11y team expertise: is this new design accessible? Are there any recommendations we should consider when implementing this design?
  - Bulk actions follow-up
    - Running out of time
  - Keen on more thorough
    - Saptak & Thibaud split testing
    - Demo site: <https://wagtaildemo-bulk-actions.herokuapp.com/admin/>
    - Do testing on <https://github.com/wagtail/wagtail/tree/feature/bulk-actions>
    - Report issues on GitHub
- 2.15 release!
  - Bulk actions
  - Wagtail Live
  - New search backends
  - New sidebar -- feature flag
  - Icons PR
    - Monday, Tuesday next week, for Thibaud w/ Scott reviewing

## 2021-08-20

Attendees: Thibaud, Saptak

### Discussions

- CONTRIBUTING.md update [#7462](https://github.com/wagtail/wagtail/pull/7462)
- Accessibility statement

## 2021-08-06

Attendees: Thibaud, Saptak, Scott

### Actions

- Thibaud Review high-contrast mode audit from Kyle
- <https://trello.com/c/YOEpYngg/29-comment-buttons-should-use-button-text-colour> 
- Thibaud Update CONTRIBUTING.md with accessibility opportunities
- Saptak Review accessibility statements from other projects & outline of page contents for Wagtail
- Thibaud Review & merge <https://github.com/wagtail/wagtail/pull/7408> 
- Thibaud Update footer actions issue with recommendation for ARIA markup based on review (<https://w3c.github.io/aria-practices/examples/menubar/menubar-navigation.html_>) <https://github.com/wagtail/wagtail/issues/7366> 
- Storm Work on last change for userbar ARIA menu practice
- Thibaud Add Saptak to accessibility team roster & invite to GitHub team

### Discussions

- Actions review
    - Thibaud Review high-contrast mode audit from Kyle
        - <https://trello.com/c/YOEpYngg/29-comment-buttons-should-use-button-text-colour> 
    - ✅ Saptak Review proposal for contributor call to action <https://github.com/wagtail/wagtail/pull/7330#pullrequestreview-703416391>
    - ✅ Storm review Jesse's <https://github.com/wagtail/wagtail/pull/7346>
    - ✅ Thibaud review issue <https://github.com/wagtail/wagtail/issues/7333> 
    - Storm Work on last change for userbar ARIA menu practice
    - ✅ Thibaud Review recommendations for action menus with mixed links and buttons
    - ✅ Thibaud Check whether we have an open issue for actions menu keyboard & SR support
        - <https://github.com/wagtail/wagtail/issues/7366> 
- Accessibility statement & contributing
    - CONTRIBUTING.md update
    - Accessibility statement
        - On the website
        - We care
        - Review other CMSes' statements?
- Icons transition!
    - Change icon source files to use <svg> elements rather than <symbol>
    - Makes the files usable as-is in CSS content attributes (as URLs)
    - Convert to <symbol> elements for sprites in Wagtail core
    - Same for icons added by Wagtail implementers
    - Scott interested in working on this but on holidays soon (7--15 Aug.)
    - 3-4 days on Wagtail for Thibaud in early September (or late September)

## 2021-07-23

Attendees: Saptak, Storm, Scott, Jesse, Thibaud, Kyle

### Actions

- Thibaud Review high-contrast mode audit from Kyle
- <https://trello.com/c/YOEpYngg/29-comment-buttons-should-use-button-text-colour> 
- Team Review proposal for contributor call to action <https://github.com/wagtail/wagtail/pull/7330#pullrequestreview-703416391>
- Storm review Jesse's <https://github.com/wagtail/wagtail/pull/7346>
- Thibaud review issue <https://github.com/wagtail/wagtail/issues/7333> 
- Storm Work on last change for userbar ARIA menu practice
- Thibaud Review recommendations for action menus with mixed links and buttons
- Thibaud Check whether we have an open issue for actions menu keyboard & SR support

### Discussions

- Actions review
    - ✅ Thibaud Userbar keyboard support blog post / screen recording demo
    - <https://www.youtube.com/watch?v=m6ybdesbaFk> 
    - Thibaud Review high-contrast mode audit from Kyle
    - <https://trello.com/c/YOEpYngg/29-comment-buttons-should-use-button-text-colour> 
    - ✅ Jesse Open ModelAdmin issue (edit unreachable with keyboard only)
    - Storm Work on last change for userbar ARIA menu practice
    - Thibaud Review recommendations for action menus with mixed links and buttons
    - Thibaud Check whether we have an open issue for actions menu keyboard & SR support
- Update on sidebar
    - Not working on this right now, taken over by Karl
    - Storm reviewing
- Keyboard shortcuts for common actions?
    - Right now
        - Ctrl + P for publish
        - Ctrl + M for 
        - Common actions: <https://github.com/wagtail/wagtail/issues/3949> 
- How to make this happen?
    - Way to register shortcuts?
    - Accessibility or usability thing?
    - Keyboard support is good
- Assistiv Labs for Wagtail -- update next week
- DjangoCon US 2021 -- October 2021
    - <https://2021.djangocon.us/>
    - 21-23 October
    - Keen: Thibaud, Scott, Kyle, Saptak, (Storm?)
- Icons came up in last core team meeting
    - We're not that far from finishing this off
    - There are a lot of icons which will be reworked anyway as part of the sidebar UI overhaul

## 2021-07-09

Attendees: Storm, Saptak, Thibaud, Jesse

### Actions

- Thibaud Userbar keyboard support blog post / screen recording demo
- Thibaud Review high-contrast mode audit from Kyle
- <https://trello.com/c/YOEpYngg/29-comment-buttons-should-use-button-text-colour>
- Jesse Open ModelAdmin issue (edit unreachable with keyboard only)

### Discussions

- On the agenda today
- Hello Saptak!
- Actions review
  - ✅ Thibaud Try out styling overrides fix for userbar ul and li [#6994](https://github.com/wagtail/wagtail/pull/6994)
    - Follow-up [#7290](https://github.com/wagtail/wagtail/issues/7290)
  - ✅ Thibaud Update Figma file with Space key from menu ARIA practices
    - Storm working on the implementation in 2 weeks
  - Thibaud Review high-contrast mode audit from Kyle
    - <https://trello.com/c/YOEpYngg/29-comment-buttons-should-use-button-text-colour>
  - Scott Review accessibility of search autocompletes in docs theme -- built-in, and Algolia
  - ✅ Storm Make Scott a maintainer of docs theme package in PyPI
    - And released
  - ✅ Scott Release new version of docs theme & update Wagtail docs to use the new release
- Storm: Google Summer of Code mentor for Wagtail Bulk Actions
- Uses a dropdown menu to decide which action to use
- ModelAdmin -- can't reach edit button
- [#7330 accessibility targets](https://github.com/wagtail/wagtail/pull/7330)
- Launching flagship site on Wagtail

## 2021-06-25

Attendees: Scott, Kyle, Thibaud, Storm

### Actions

- Thibaud Try out styling overrides fix for userbar ul and li [#6994](https://github.com/wagtail/wagtail/pull/6994)
- Thibaud Update Figma file with Space key from menu ARIA practices
- Thibaud Review high-contrast mode audit from Kyle
    - <https://trello.com/c/YOEpYngg/29-comment-buttons-should-use-button-text-colour>
- Scott Review accessibility of search autocompletes in docs theme -- built-in, and Algolia
- Storm Make Scott a maintainer of docs theme package in PyPI
- Scott Release new version of docs theme & update Wagtail docs to use the new release
- Kyle Review next-gen editor wireframes / progress
- Storm Review next-gen editor wireframes / progress

### Discussions

- Actions review
    - Thibaud & Storm Follow up on userbar PR progress [#6994](https://github.com/wagtail/wagtail/pull/6994)
        - Done some work. Not yet mergeable
        - Potential styling overrides
    - Thibaud Update Figma file with Space key from menu ARIA practices
    - ✅ Thibaud Talk to users of Transifex (Andy for wagtailmenus) about using it for docs translations
        - Confirmation from core team
        - Not sure when we go through the next steps
    - Thibaud Review high-contrast mode audit from Kyle
        - <https://trello.com/c/YOEpYngg/29-comment-buttons-should-use-button-text-colour>
    - ✅ Scott Address low-hanging fruit in docs
        - <https://github.com/wagtail/sphinx_wagtail_theme/pull/109>
        - Some next steps on manual checks
    - Slim sidebar
        - Demo
        - Discuss peeking behavior
    - ARIA landmarks in the admin (@stormheg)
        - [Rework the admin UI's landmark based on established best practices - Issue #5411 - wagtail/wagtail](https://github.com/wagtail/wagtail/issues/5411)
    - Next-gen Wagtail editor
    - Revisit high-contrast mode with slim menu
        - Should be straightforward?
        - Thibaud backlog issues

## 2021-06-11

Attendees: Kyle, Jesse, Thibaud, Storm, Scott

### Actions

- Thibaud & Storm Follow up on userbar PR progress
- Thibaud Update Figma file with Space key from menu ARIA practices
- Thibaud Talk to users of Transifex (Andy for wagtailmenus) about using it for docs translations
- Thibaud Review high-contrast mode audit from Kyle
  - <https://trello.com/c/YOEpYngg/29-comment-buttons-should-use-button-text-colour>

### Actions review

- ✅ Storm PR for userbar recommendations
  - ✅ 👉[Move userbar before navigation in example](https://github.com/wagtail/wagtail/blob/6428820df23b70411a02f1a573f414f480830a16/docs/topics/writing_templates.rst#wagtail-user-bar)
  - 🚧Still need to apply suggestions from code review
- ✅ Thibaud Image upload audit review
  - Jesse & Thibaud also moved findings to [main spreadsheet](https://docs.google.com/spreadsheets/d/1l7tnpEyJiC5BWE_JX0XCkknyrjxYA5T2aee5JgPnmi4/edit)
- ✅ Thibaud Reach out on Twitter for Wagtail high-contrast users
- ✅ Thibaud Ask Torchboxers for high-contrast mode experience
- ✅ Storm & Thibaud Put draft annotations for keyboard support for Simon's work
- ✅ Thibaud Proposal for RTL support for sidebar rewrite
  - <https://github.com/wagtail/wagtail/issues/1240>
  - CSS logical properties
- ✅ Scott Accessibility audit for new docs theme
- ✅ Thibaud Open issue about docs translations in theme repository (or Wagtail?)
- ✅ Kyle High-contrast mode resources / look into what applies to Wagtail
  - Best practices
  - Compare default install

### Discussions

- Menu pattern for Wagtail sidebar
  - Missing Space key
  - <https://dribbble.com/shots/6269661-Accessibility-Bluelines>
- Scott Accessibility audit for new docs theme
  - Started it with WAVE
  - Reported a couple of errors
  - Axe DevTools
- High-contrast mode audit
  - <https://trello.com/c/YOEpYngg/29-comment-buttons-should-use-button-text-colour>
  - Highlights some semantic issues in our markup as well as the contrast issues
- Userbar pull request (@stormheg)
  - Needs a bit of refactoring in a few places
  - How to deal with focus outline
  - [Discussion on Github](https://github.com/wagtail/wagtail/pull/6994#discussion_r646115480)
  - Ensure it is visible against any background
  - Outline provided by browsers not necessarily accessible (e.g. Firefox on Windows)
  - Suggestion -- use the GOV.UK thick yellow? Already used in the Wagtail admin
    - Let's go with thick yellow
  - Research option to use "invert color" feature that might have some browser support?
- ARIA landmarks in the admin (@stormheg)
  - [Rework the admin UI's landmark based on established best practices - Issue #5411 - wagtail/wagtail](https://github.com/wagtail/wagtail/issues/5411)
- We4Authors Cluster project
  - <https://accessibilitycluster.com/main-results/selection-of-features>

## 2021-05-28: skipped (Slack updates)

## 2021-05-14

Attendees: Thibaud, Scott, Jesse, Kyle, Storm

### Actions

- Storm PR for userbar recommendations
- Move userbar before navigation in example
- Thibaud Image upload audit review
- Thibaud Reach out on Twitter for Wagtail high-contrast users
- Thibaud Ask Torchboxers for high-contrast mode experience
- Storm & Thibaud Put draft annotations for keyboard support for Simon's work
- Thibaud Proposal for RTL support for sidebar rewrite
- Scott Accessibility audit for new docs theme
- Thibaud Open issue about docs translations in theme repository (or Wagtail?)
- Kyle High-contrast mode resources / look into what applies to Wagtail
- Best practices
- Compare default install

### Actions review

- ✅ Thibaud userbar PR review [#6994](https://github.com/wagtail/wagtail/pull/6994)
- ✅ Storm PR for userbar recommendations
- ✅ Jesse Audit image upload in Safari VoiceOver <https://bakerydemo-thibaudcolas4.herokuapp.com/admin/images/multiple/add/>
- ✅ Thibaud Share testing site details (admin / changeme)
- ✅ Storm High-contrast mode audit of Dashboard
  - <https://bakerydemo-thibaudcolas4.herokuapp.com/admin/>
  - <https://assistivlabs.com/assistive-tech/display/high-contrast-mode>
- ✅ Thibaud Get in touch with [Assistiv Labs](https://assistivlabs.com/) to get a Torchbox account
- ~~Thibaud Get in touch with Assistiv Labs to get a Wagtail sponsorship~~
- ✅ Scott Review [#7142](https://github.com/wagtail/wagtail/pull/7142)

### Discussions

- Thibaud gave his PyCon talk!
- Got lots of good questions that we should review
- Discuss actions
  - Userbar recommendations
    - Nav then userbar, or userbar then nav?
    - <https://github.com/wagtail/wagtail/pull/6994/files?w=1#diff-bcb0c5f7c94df35f501163b0756512f7a1909f783eaf0d2f1103d286e3c3f4f3>
- Image upload
  - "ADD" Potential fix: [https://css-tricks.com/lets-talk-speech-css/](https://css-tricks.com/lets-talk-speech-css/#the-reality-of-the-situation)
- High-contrast mode audit of Dashboard
  - Logo
  - Search input different color in Edge
  - Different color inheritance for SVG and font icons
  - Interactive Admin menu isn't styled as interactive
  - Jesse different results -- Yellow in Firefox?
  - Which high-contrast modes are meant to be used for testing?
- Assistiv Labs
- Accessibility audit for upcoming sidebar rewrite?
  - <https://paper.dropbox.com/doc/Wagtail-sidebar-rewrite--BKuIZKetNCugApTjr4XzafCJAg-Wn81olplMadAC5eUEokXu>
  - role="menu"
    - A bit daunting but would be the best target
  - Annotate designs with expected accessibility / keyboard behavior?
- Accessibility audit for new docs theme?
  - Most of the markup copied from Typo3 theme
  - Thibaud noted that collapsible sidebar items could not be expanded, had to first load the top level page and then go through the pre-opened menu
  - Version picker KB access should be checked -- Storm thinks provided by ReadTheDocs and may not be able to modify its markup
  - There's no skip link!
  - Open issues at <https://github.com/wagtail/sphinx_wagtail_theme/>

## 2021-04-30

Attendees: Jesse, Scott, Storm, Thibaud

### Actions

- Thibaud userbar PR review [#6994](https://github.com/wagtail/wagtail/pull/6994)
- Storm PR for userbar recommendations
- Thibaud Share draft of automated tests on publish
- Jesse Audit image upload in Safari VoiceOver <https://bakerydemo-thibaudcolas4.herokuapp.com/admin/images/multiple/add/> 
- Thibaud Share testing site details (admin / changeme)
- Storm High-contrast mode audit of Dashboard
- <https://bakerydemo-thibaudcolas4.herokuapp.com/admin/> 
- <https://assistivlabs.com/assistive-tech/display/high-contrast-mode> 
- Thibaud Get in touch with [Assistiv Labs](https://assistivlabs.com/) to get a Torchbox account
- Thibaud Get in touch with Assistiv Labs to get a Wagtail sponsorship
- Scott Review [#7142](https://github.com/wagtail/wagtail/pull/7142) 

### Actions review

- ✅ Storm userbar PR [#6994](https://github.com/wagtail/wagtail/pull/6994)
- Thibaud userbar PR review [#6994](https://github.com/wagtail/wagtail/pull/6994)
- Thibaud Share draft of automated tests on publish
- ✅ Thibaud Share draft of accessibility audit formats with expected scope
- ✅ Thibaud Review new switch components
- The issue I had spotted is with all checkboxes in Wagtail, not specific to switch
- ✅ Thibaud Update Wagtail contribution guidance, and PR template, to make it clear individual pull requests should include accessibility testing. Review issue templates as well

### Discussions

- Userbar
- Where should it be on the page?
    - <https://github.com/wagtail/wagtail/blob/9630967e0e3de3469fd858d2cf6fd656be7c491e/docs/topics/writing_templates.rst#L266> 
    - Recommend putting it "towards the top, but not first"
- <https://github.com/wagtail/wagtail/pull/7142> 
- Audits methodology
    - Thibaud to further define / document ahead of sharing results
    - High level for now? To validate results, but no need to have the whole audit be replicable.
    - Scope of audit: things that are likely to be actionable in the near term.
- PR review methodology
    - Not as controversial as Thibaud thinks :)
    - We strongly encourage™ this.
- PyCon
- [Storybook in Wagtail (#7097)](https://github.com/wagtail/wagtail/pull/7097) 
    - Ongoing internal conversations at Torchboxb

## 2021-04-16

Attendees: Storm, Thibaud

### Actions

-   Storm userbar PR [#6994](https://github.com/wagtail/wagtail/pull/6994)
-   Thibaud userbar PR review [#6994](https://github.com/wagtail/wagtail/pull/6994)
-   Thibaud Share draft of automated tests on publish
-   Thibaud Share draft of accessibility audit formats with expected scope
-   Thibaud Review new switch components
-   Thibaud Update Wagtail contribution guidance, and PR template, to make it clear individual pull requests should include accessibility testing. Review issue templates as well

### Discussions
-   [SVG icons rework #6107](https://github.com/wagtail/wagtail/issues/6107)
    -   [#6998](https://github.com/wagtail/wagtail/pull/6998) 
-   [Improve userbar accessibility #6994](https://github.com/wagtail/wagtail/pull/6994)
    -   Menu + menuitem ARIA implementation
    -   Updating docs to mention usage
-   Automated accessibility checks as part of publishing pages
    -   [Initial review](https://docs.google.com/document/d/12Hrq0EtzoXcqC9U7sFUcmwuQ4TWS9XYZpHE5OH_cBww/edit#)
    -   Demo that goes a bit beyond than Tota11y: [Sa11y](https://ryersondmp.github.io/sa11y/)
    -   [Axe + WordPress integration](https://docs.google.com/presentation/d/e/2PACX-1vROBCmDyBQI2Zez1hoVBSV1rUp_9Xad6K2J3-KDEr0IbewMqbKePoSwgicLpIHIgnw9v9cgwNu7furx/pub?start=false&loop=false&delayms=3000&slide=id.g2fbab35998_0_62)
    -   [ARRM project](https://www.w3.org/WAI/EO/wiki/ARRM_Project_-_Accessibility_Roles_and_Responsibilities_Mapping)
-   Accessibility audit
    -   Option 1: manual, [Template](https://docs.google.com/spreadsheets/d/1DfqPIVfQYgj2bxxWS4nPs4lrwmWF1wzrtvLwgtVp5kI/edit?usp=sharing)
    -   Option2: automated, [Pa11y + Lighthouse demo](https://thibaudcolas.github.io/django_admin_tests/) 
-   Scope:
    -   Dashboard
    -   Main menu
    -   Pages menu
    -   Pages search
    -   Both manual and automated

## 2021-03-19 -- new team chat

Attendees: Thibaud, Scott, Storm, Kyle, Jesse

- Welcome & introductions: Thibaud, Scott, Storm, Kyle, Jesse
- Intro to current accessibility effort
  - [Wagtail admin WCAG2.1 AA](https://github.com/wagtail/wagtail/projects/5), [RFC](https://github.com/wagtail/rfcs/pull/37)
  - [WCAG2.1 AA for sites](https://github.com/wagtail/wagtail/projects/10)
  - And docs, one-off projects, etc.
- How the team works
  - Initial plan: open membership, 45-min chats every two weeks to provide feedback and take actions.
  - 6months membership
  - Friday morning, afternoon to evening Europe/Africa
- What do we all want to achieve with the accessibility team?
- Thibaud
  - Another audit of Wagtail
  - Automated accessibility checks as part of publishing pages
  - [SVG icons rework #6107](https://github.com/wagtail/wagtail/issues/6107)
- Scott
  - [SVG icons rework #6107](https://github.com/wagtail/wagtail/issues/6107)
  - [Contextual alt text RFC #51](https://github.com/wagtail/rfcs/pull/51)
  - aria-label on links (give more helpful link text to screen reader users)
    - [Feature: ability to set links as "nofollow" rel via the WYSIWG editor's link chooser #4474](https://github.com/wagtail/wagtail/issues/4474)
  - Being able to use the same link chooser outside of rich text fields
    - [Single interface for choosing links to anything #381](https://github.com/wagtail/wagtail/issues/381)
- Storm
  - [Wagtail userbar is not accessible - Issue #6108](https://github.com/wagtail/wagtail/issues/6108)
  - Review existing accessibility related pull requests.
  - [SVG icons rework #6107](https://github.com/wagtail/wagtail/issues/6107)
  - ["Unpublished" styles in pages listings are very hard / impossible to see - Issue #5370](https://github.com/wagtail/wagtail/issues/5370)
  - [Implement focus management for chooser modals - Issue #5338](https://github.com/wagtail/wagtail/issues/5338)
- Kyle
  - All buttons visible all the time
  - Incorporated as Wagtail customisations in previous agency
  - Look into this further since we know there are people who struggle with this
  - Get up to speed with Wagtail contributions!
  - Read through open issues & raise anything missing
- Jesse
  - Getting up to speed with issues and contributions
- User testing with users of assistive technology
  - Would be good in addition to doing an audit of our own
  - Reach out to Wagtail contributors to use assistive tech
  - Share via Django Newsletter?
  - Share in accessibility communities?
  - Could reach out to <https://makeitfable.com/>
  - Jesse check user testing plan / results from Syracuse University's upcoming Wagtail build
- Another audit
  - Has Wagtail ever been professionally audited?
    - Outline steps to get a more professional audit?
    - Crowdfund :)?
- Jesse check with coworkers for interest in accessibility / Wagtail contributions

## 2021-02-17 -- Team 6-monthly report

- 5 people active during the last 6 months, but only 2 attending meetings on average
  - Initially Scott Cranfill (core team, CFPB), Thibaud Colas (core team, Torchbox), Andreas Bernacca (Fröjd)
  - Joined by Nick Smith (Torchbox) and Helen Chapman (Torchbox) over the last couple of months for specific tasks
- Met 9 times. We had initially decided on a 3-month membership, but ended up extending to 6 months.
- Focused on 3 areas:
  - Completing the SVG icons conversion to improve accessibility of icons in the CMS admin
  - Documenting [accessibility considerations](https://docs.wagtail.io/en/stable/advanced_topics/accessibility_considerations.html) for Wagtail sites
  - Curating a backlog of accessibility improvements for sites <https://github.com/wagtail/wagtail/projects/10>
- We were also keen to do more automated tests and manual auditing but didn't get around to it.

### Agenda / changes for next 6 months

- Create plan to recruit 5 members
  - Open office hours?
- Create and publish accessibility audits of Wagtail to have a clear record of our current state
- Update Wagtail contribution guidance, and PR template, to make it clear individual pull requests should include accessibility testing. Review issue templates as well
- 45min meetings in the future.
- Thibaud draft RFC for automated accessibility tests

## 2021-01-22 -- Team retrospective

Attendees: Scott, Thibaud

### Actions review

- ✅ Thibaud Report forms issues to Django
  - <https://code.djangoproject.com/ticket/32338>
  - <https://code.djangoproject.com/ticket/32339>
  - <https://code.djangoproject.com/ticket/32340>

### Discussions

- Django forms issues -- need to follow up to provide more specific guidance and devise the fixes
- Retrospective
  - Arrived at the term of our team commitment
  - An occasion to take stock of what we achieved over the last 6 months
  - And what we want to do next?
  - Resuming team activity 5th of March

### Retrospective

- **Start**
  - I would love to get reminders of my TODOs between meetings.
    - Action: Thibaud happy to volunteer to do weekly reminders
  - Recruit more aggressively?
    - Target: 5 members
    - How: posting more
    - Do what we’ve done before but more aggressively?
    - Torchbox internal project helped
    - Outreach / wider audience events to get people interested
    - Action: create plan to recruit 5 members
  - Get people from the #accessibility Slack more involved
  - Create and publish accessibility audits of Wagtail that clearly state how far ahead we are.
    - Action: Create and publish accessibility audits of Wagtail to have a clear record of our current state
  - Reach out to specific people who could be interested in contributing
  - Report back to core team
    - Action: Accessibility team report to core team
- **Stop**
  - Using Zoom? (Can’t access on my work computer.)
    - Action: Switch over to Google Meet.
  - The team’s activity can make it feel like accessibility for Wagtail is solved / handled by us, even though we’re far from it
    - Attitude we want to discourage: “the accessibility team will take care of making this work”
    - Action: Update Wagtail contribution guidance, and PR template. Review issue templates as well
  - Saying yes to other Wagtail activities even though I want to spend time on this
- **Continue**
  - 30 minute meetings every two weeks seems like a good cadence. Could maybe be 45.
    - Action: 45min meetings in the future.
  - Meeting format works well, I think. (Reviewing actions, discussions, adding new actions.)
  - Accessibility-focused sprint was good (January 2020)
  - 6 months felt like a pretty good commitment
  - The “automated accessibility tests when publishing” feels like the most promising way to improve outcomes for users of Wagtail sites
    - Action: Thibaud draft RFC for automated accessibility tests

Actions recap:

- Thibaud happy to volunteer to do weekly reminders
- Create plan to recruit 5 members
- Create and publish accessibility audits of Wagtail to have a clear record of our current state
- Accessibility team report to core team
- Switch over to Google Meet.
- Update Wagtail contribution guidance, and PR template. Review issue templates as well
- 45min meetings in the future.
- Thibaud draft RFC for automated accessibility tests

## 2021-01-08

Attendees: Nick, Thibaud

### Actions

- Thibaud Report forms issues to Django

### Actions review

- No actions last meeting

### Discussions

- Docs sprint
- Django forms markup suggested changes review
    - Remove support for as_table. While deprecated, update all documentation to state that it shouldn't be used, and if used the table should be marked as role="presentation".
    - Remove support for as_ul. While deprecated, update all documentation to state that it shouldn't be used, and if used the ul should be marked as role="presentation".
    - For as_p and the {{ form }} shortcut -- these work as expected for screen reader users. It would be good to document these shouldn't be used for larger forms, where it's important to group fields in fieldset with appropriate legends for accessibility, for all users, but particularly for screen reader users.
    - Django's markup doesn't follow accessibility best practices for RadioSelect ChoiceFields -- it should use a fieldset with legend (and no ul). Change the markup
        - accessible=False for deprecation period (breaks old code at the end of deprecation period, not code that was updated at the end of it)
        - Potentially -- may be able to achieve this once deprecated/removed via a project-level template override (assess how feasible)
    - DateField should always come with the pattern required for the date. Documentation only?
        - Yes
        - Format for display in form: input_formats, <https://docs.djangoproject.com/en/3.1/ref/forms/fields/#datefield> 
        - <https://github.com/django/django/blob/master/django/forms/fields.py#L389> 
    - DateTimeField should ideally be removed / at least discouraged from being used without / needs a JS widget
        - Messaging / Docs only
    - TimeField needs further consideration
        - Messaging
    - Django's markup doesn't follow accessibility best practices for CheckboxSelectMultiple MultipleChoiceField -- it should use a fieldset with legend (and no ul). Change the markup
    - Deprecation: move to deprecated/legacy config app
    - Suggest as-is replacement as part of request to remove it
    - Template to use to replicate the functionality
    - Removing things is easier than simply changing them

## 2020-12-18

Attendees: Nick, Thibaud

### Actions

No actions this time

### Actions review

-   ✅ Thibaud SVG icons for [Settings menu item](https://github.com/wagtail/wagtail/blob/70bb9d934b086d8c2c34f1363c12e9acec970816/wagtail/contrib/settings/registry.py#L12-L19)  [@thibaudcolas](https://github.com/thibaudcolas) ([#6649](https://github.com/wagtail/wagtail/pull/6649))
-   Scott SearchArea PR review [#6493](https://github.com/wagtail/wagtail/pull/6493) (in progress)
-   Scott Comment on [#6535](https://github.com/wagtail/wagtail/issues/6535)
-   ✅ Thibaud Explore idea of validating document outline within individual rich text fields ([#6535](https://github.com/wagtail/wagtail/issues/6535))
-   ✅ Thibaud Review issues relating to publish success redirection
-   Scott Icons PR .url_field .input
-   Thibaud Icons PR edit panel title-wrapper
-   ✅ Thibaud Fill sprint attendance survey

### Discussions

-   Docs sprint (remote)
-   Validating document outlines ([#6535](https://github.com/wagtail/wagtail/issues/6535) follow-up)
    -   Interested in broader accessibility tests first
    -   Preferred approach: rely on page preview to get "end to end" tests
    -   Similar to <https://github.com/Aleksi44/wagtailyoast/blob/fa9e64ed758921cdac701c68f0c6002c02522229/wagtailyoast/static/wagtailyoast/src/js/common/Panel.js#L49-L59> 
    -   Integrate Axe, or Tota11y, or IBM Equal Access checker, or h123
    -   For end users -- move preview inline in the admin so end users can see the issues with appropriate context
-   Publish success redirection
    -   <https://github.com/wagtail/wagtail/blob/master/wagtail/admin/views/pages/edit.py>
    -   <https://github.com/thibaudcolas/wagtail/blob/master/wagtail/admin/views/pages/create.py>  
    <https://github.com/wagtail/wagtail/issues/694>

## 2020-12-04 

Attendees: Scott, Thibaud

### Actions

- Thibaud SVG icons for [Settings menu item](https://github.com/wagtail/wagtail/blob/70bb9d934b086d8c2c34f1363c12e9acec970816/wagtail/contrib/settings/registry.py#L12-L19)  [@thibaudcolas](https://github.com/thibaudcolas) (in progress)
- Scott SearchArea PR review [#6493](https://github.com/wagtail/wagtail/pull/6493) (in progress)
- Scott Comment on [#6535](https://github.com/wagtail/wagtail/issues/6535)
- Thibaud Explore idea of validating document outline within individual rich text fields (#6535)
- Thibaud Review issues relating to publish success redirection
- Scott Icons PR .url_field .input
- Thibaud Icons PR edit panel title-wrapper
- Thibaud Fill sprint attendance survey

### Actions review

- Thibaud SVG icons for [Settings menu item](https://github.com/wagtail/wagtail/blob/70bb9d934b086d8c2c34f1363c12e9acec970816/wagtail/contrib/settings/registry.py#L12-L19)  [@thibaudcolas](https://github.com/thibaudcolas) (in progress)
- Scott SearchArea PR review [#6493](https://github.com/wagtail/wagtail/pull/6493) (in progress)
- ✅ Scott draft PR for paginations icons [#6573](https://github.com/wagtail/wagtail/pull/6573)
- ✅ Thibaud review PR for paginations icons [#6573](https://github.com/wagtail/wagtail/pull/6573)
- ✅ Scott Review [sites accessibility](https://github.com/wagtail/wagtail/projects/10) proposal & highlight top 3
- Andreas Review [sites accessibility](https://github.com/wagtail/wagtail/projects/10) proposal & highlight top 3

### Discussions

- [Review WCAG2.1 AA for sites](https://github.com/wagtail/wagtail/projects/10)
    - Heading levels
        - StreamField charblock or structblock
        - (custom icon prefix for heading text)
        - Scott add comment
        - Option to explore -- validation of heading levels outline
        - Publish next page -- why parent?
            - <https://github.com/wagtail/wagtail/issues/694>
            - <https://github.com/wagtail/wagtail/issues/3348> 
        - Draft idea -- accessibility tests on publish / save draft
    - Forms -- review default output
        - Also review extra field types to support #6611
- Icons [#6107](https://github.com/wagtail/wagtail/issues/6107)

## 2020-11-20

Attendees: Andreas, Thibaud, Scott

### Actions

- Thibaud SVG icons for [Settings menu item](https://github.com/wagtail/wagtail/blob/70bb9d934b086d8c2c34f1363c12e9acec970816/wagtail/contrib/settings/registry.py#L12-L19) [@thibaudcolas](https://github.com/thibaudcolas)
- Scott SearchArea PR review <https://github.com/wagtail/wagtail/pull/6493>
- Scott draft PR for paginations icons
- Thibaud review draft PR for paginations icons
- Scott Review sites accessibility proposal & highlight top 3 <https://github.com/wagtail/wagtail/projects/10>
- Andreas Review sites accessibility proposals & highlight top 3 <https://github.com/wagtail/wagtail/projects/10>

### Agenda

- Actions review
  - ✅ Thibaud Finish SearchArea <https://github.com/wagtail/wagtail/pull/6493>
  - Scott  Pagination from 6107
    - ModelAdmin markup generated in Python
  - ✅ Thibaud Finish accessibility considerations doc <https://github.com/wagtail/wagtail/pull/6272>
  - ✅ Thibaud Ask Coen to join next accessibility team meeting
  - Thibaud Propose UI architecture rework to core team -- RFC
    - I haven't done this because I don't think django-pattern-library is ready yet, but close
    - <https://github.com/torchbox/django-pattern-library/releases/tag/v0.3.0>
- Discussions
  - Icons
  - Wagtail sites fixes
  - <https://docs.wagtail.io/en/latest/advanced_topics/accessibility_considerations.html>
  - <https://github.com/wagtail/wagtail/projects/10>
  - Embed titles
    - Torchbox backport
  - Heading levels validation
    - Don't underestimate editors
    - Validation for rich text fields?
    - Highlight empty blocks directly in the field
    - Error message at the end?
    - Potential for automated remediation by stripping all empty heading blocks server-side or client-side
  - Heading levels availability
    - Scott: prefer editors have awareness of the semantics of heading levels
  - Feature request: Support for declaring language on elements in rich text. #4694
    - Everyone supportive
    - CFPB does block-level translations
    - Would be nice to do this at the rich text field (or rich text block?) level

## 2020-10-23

Attendees: Scott, Thibaud

### Actions

- Thibaud Finish SearchArea<https://github.com/wagtail/wagtail/pull/6493>
- Scott Pagination from 6107
- Thibaud Finish accessibility considerations doc<https://github.com/wagtail/wagtail/pull/6272>
- Thibaud Ask Coen to join next accessibility team meeting
- Thibaud Propose UI architecture rework to core team – RFC

### Agenda

- Actions review
  - WIP Thibaud Take on SearchArea from<https://github.com/wagtail/wagtail/issues/6107>
  - Thibaud Take on SettingsMenuItem from<https://github.com/wagtail/wagtail/issues/6107>
  - ✅ Scott Help text from 6107
  - WIP Scott Pagination from 6107
  - ✅ Thibaud Attempt to revive<https://github.com/thibaudcolas/bakerydemo/commits/bakerydemo-thibaudcolas> but with nightly releases
  - Thibaud Ask Coen to join next accessibility team meeting

- Discussions
  - Accessibility compliance dashboard
  - SVG icons
    - <https://github.com/wagtail/wagtail/issues/6107>
    - <https://github.com/wagtail/wagtail/pull/6493>
  - Accessibility considerations
  - bakerydemo nightly
    - Weekly Travis cron builds of<https://github.com/thibaudcolas/bakerydemo/tree/bakerydemo-thibaudcolas-cron>
    - Pushes ready-to-deploy<https://github.com/thibaudcolas/bakerydemo/blob/bakerydemo-thibaudcolas-nightly/requirements/base.txt>
    - Heroku pipeline with review apps & multiple staging apps<https://dashboard.heroku.com/pipelines/4e9fd4e0-0aac-440f-a6cb-2ab13e2e277f>
  - UI architecture rework RFC
    - Waiting for new release of django-pattern-library, ETA early November
  - Team future
    - 3-month commitment ends next week
      - 4 meetings so far
      - Revisit this beginning of the year?
      - Talk to Coen? Find somebody else?
      - 3 people is a good minimum
    - What do the next 3 months hold?
      - Get the icons rework finished
    - Next project ideas
      - Fixes for Wagtail accessibility footguns
        - It’s most important of all for us to encourage the development of accessible websites with Wagtail
        - Raw numbers
      - Automated accessibility tests?
        - Monitoring
        - CI
      - Accessibility audits
        - Chooser modals
        - StreamField
        - More rich text
        - Professional audit?
          - With AT users
- Detecting Wagtail sites
  - Thibaud experiments
  - We 4 authors cluster
  - <https://digital.gov/resources/content-management-systems-used-by-government-agencies/> 

## 2020-09-25

Attendees: Thibaud, Scott

### Actions

- Thibaud Take on SearchArea from <https://github.com/wagtail/wagtail/issues/6107>
- Thibaud Take on SettingsMenuItem from <https://github.com/wagtail/wagtail/issues/6107>
- Scott  Help text from 6107
- Scott  Pagination from 6107
- Scott Review accessibility considerations docs WIP PR <https://github.com/wagtail/wagtail/pull/6272>
- Thibaud Propose UI architecture rework to core team -- RFC
- Thibaud Attempt to revive <https://github.com/thibaudcolas/bakerydemo/commits/bakerydemo-thibaudcolas> but with nightly releases
- Thibaud Ask Coen to join next accessibility team meeting

### Agenda

- Actions review
  - ✅ Thibaud to caption Wagtail Space US accessibility & pattern library talks
  - Thibaud Share DjangoCon on Slack
  - ✅ Thibaud Review & merge localstorage icons implementation <https://github.com/wagtail/wagtail/pull/6243>
  - ✅ Scott Look into ModelAdmin SVG icon support <https://github.com/wagtail/wagtail/issues/6379>
  - PR: <https://github.com/wagtail/wagtail/pull/6402>
  - Thibaud Take on a couple items from <https://github.com/wagtail/wagtail/issues/6107>
  - Andreas Take on "Breadcrumb (home icon)" + 1 extra item if time from <https://github.com/wagtail/wagtail/issues/6107>
  - Thibaud Propose UI architecture rework to core team -- RFC
  - Andreas Review accessibility considerations docs WIP PR <https://github.com/wagtail/wagtail/pull/6272>
  - Scott Review accessibility considerations docs WIP PR <https://github.com/wagtail/wagtail/pull/6272>
- Automated accessibility tests
  - <https://github.com/thibaudcolas/wagtail-tooling>
  - <https://github.com/thibaudcolas/django_admin_tests>
  - Bakerydemo running on Wagtail nightly?
    - Needs locking down of content if used for automated tests
- Discussions
  - Icons progress for 2.11
    - Still achievable
    - Contact Coen
    - About 2-3 weeks before the RC

## 2020-09-11

Attendees: Andreas, Scott, Thibaud

### Actions

- Thibaud to caption Wagtail Space US accessibility & pattern library talks
- Thibaud Share DjangoCon on Slack
- Thibaud Review & merge localstorage icons implementation <https://github.com/wagtail/wagtail/pull/6243>
- Scott Look into ModelAdmin SVG icon support <https://github.com/wagtail/wagtail/issues/6379>
- Thibaud Take on a couple items from <https://github.com/wagtail/wagtail/issues/6107>
- Andreas Take on "Breadcrumb (home icon)" + 1 extra item if time from <https://github.com/wagtail/wagtail/issues/6107>
- Thibaud Propose UI architecture rework to core team -- RFC
- Andreas Review accessibility considerations docs WIP PR <https://github.com/wagtail/wagtail/pull/6272>
- Scott Review accessibility considerations docs WIP PR <https://github.com/wagtail/wagtail/pull/6272>

### Agenda

- Actions review
  - ✅ Get in touch with colleagues / potential people interested in helping with accessibility -- Everyone
    - Jane from Torchbox, not participating in this very group, but working on accessibility of Wagtail sites with Thibaud over 3 months
    - Scott one colleague, not for now :)
    - Andreas no luck
  - ✅ Identify Wagtail Space US accessibility good first issues @thibaudcolas
  - ✅ Prepare Wagtail Space US accessibility talk @thibaudcolas
    - WIP: #6090 Document accessibility considerations
  - ✅ [Accessibility issue for dropdowns in Wagtail Admin](https://github.com/wagtail/wagtail/issues/6072) -- Andreas
    - Merged!
  - ✅ SVG Icons -- Scott
- Discussions
    - <https://github.com/fregante/github-issue-link-status>
    - <https://github.com/wagtail/wagtail/issues/3804>
    - [django-pattern-library](https://github.com/torchbox/django-pattern-library) for Wagtail
        - Feedback from Naomi would be great, as well as other people with Wagtail UI architecture experience, Jonny, Janneke
        - Mix of React and non-React code needs clarifying
        - Jinja macros vs template tags?
        - Jinja makes it possible to put more logic in templates
        - Advise for caution
        - Consider switching to Jinja? But not go so far as to fall into the "logic in templates" trap
        - Testing logic in templates is tough (compared to Python)
        - Scott's Wagtail solution: move logic to page models' get_context
        - Refactoring justified for testability
        - Would make it easier for people to understand the codebase (and contribute)
        - <https://github.com/wagtail/wagtail/pull/6272>

## 2020-07-17

Attendees: Scott, Andreas, Thibaud

### Actions

- Thibaud Identify Wagtail Space US accessibility good first issues
  - Either have different labels, or Projects board for “Websites’ accessibility”
- Thibaud Prepare Wagtail Space talk
- Andreas Finish PR for Site settings dropdown icon confusion
- Scott Review icon transition PRs
- Everyone Get in touch with colleagues / potential people interested in helping with accessibility
- Bonus
  - Scott Open a new icon transition PRs
  - Thibaud What’s the most accessible video call software?

### Agenda

Poll:<https://doodle.com/poll/euv4mfh2mhfqnmtp>

- Welcome & introductions
  - Thibaud – happy for Torchbox to make time for this, and focusing on accessibility
  - Andreas – Wagtail dev for 3 years at Fröjd
    - Came up from legal requirements with clients
    - Internal accessibility group for WCAG2.1 AA compliance
  - Scott – CFPB, interested in accessibility for years
    - Aiming for WCAG 2.1 AA too
    - Not just public websites but also tools for employees, equally as liable
- Intro to current accessibility effort
  - [Wagtail admin WCAG2.1 AA](https://github.com/wagtail/wagtail/projects/5),[RFC](https://github.com/wagtail/rfcs/pull/37)– Andreas: 1, Scott: 1B, Thibaud: 2
  - [Issues for Wagtail websites #6090](https://github.com/wagtail/wagtail/issues/6090) – Andreas: 2, Scott: 1A, Thibaud: 1
  - [Accessibility features ideas](https://docs.google.com/document/d/1rFw5S4vJa4As6aH-k1QNnEZTmE1jkLOM8ABh7X8WZOQ/edit) – Andreas: 3, Scott: 3, Thibaud: 3
  - Thibaud’s Wagtail Space talk
    - The above, and
    - Tooling
- What do we all want to achieve with the #accessibility team?
  - Personal accountability :)
  - The bi-weekly nudge
  - Thibaud about 5h per week on Wagtail
  - Priorities are different for people who are very experienced and already aware of Wagtail gotchas
  - Future vision:
    - Wagtail is the best CMS to build accessible websites
    - Great selling point for companies proposing Wagtail
    - Contrast with Episerver for Fjörd
  - WebAim 1 million & Gatsby
  - What’s the most accessible video call software?
    - <https://www.smashingmagazine.com/2020/06/accessible-video-conferencing-tools/>
- How the team works
  - Initial plan: open membership, collaboration via Slack first, 30-min chats to provide feedback and take actions.
  - 3 months membership?
  - MVP
  - 30min every two weeks
  - Friday morning , afternoon to evening Europe/Africa
  - 11h eastern, 4pm Thibaud, 5pm Andreas
- Timezones
  - Scott: EDT (UK-5)
  - Andreas: CET/CEST (UTC+2?)
  - Thibaud: BST
- What do we all want to do next?
  - See actions above
- See you all at the next Wagtail Space :)
  - Timezones work!
