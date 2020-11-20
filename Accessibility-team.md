# Wagtail #accessibility team

Links: [#accessibility on Slack](https://app.slack.com/client/T0K33F93J/CB7L6L5S6) | [Team charter](https://github.com/wagtail/wagtail/wiki/Accessibility-team) | [Future meetings](https://docs.google.com/document/d/1YUxOs5jYZMd8rX291mDE123xIK7tbD63PzSR9ooFa4c/edit) | [Past meetings](https://github.com/wagtail/wagtail/wiki/Accessibility-team)

## Team charter

The team’s membership is open to all, introduce yourself in [#accessibility on Slack](https://app.slack.com/client/T0K33F93J/CB7L6L5S6) if you’re interested in joining. We currently operate with a membership term of 3 months, so people can commit for a short term, and then decide to proceed or stop.

We meet every two weeks to discuss everyone’s recent progress and next steps. At the end of each meeting, all participants should each have volunteered for an action, which they must complete before the next meeting. We track [team actions](https://github.com/wagtail/wagtail/projects/9) on GitHub. Meeting notes are public for future and past meetings. Meetings happen on Zoom, which is what the Wagtail core team uses, and also seems to be [one of the most accessible video call software](https://www.smashingmagazine.com/2020/06/accessible-video-conferencing-tools/).

In-between meetings, we collaborate via Slack, using the [#accessibility](https://app.slack.com/client/T0K33F93J/CB7L6L5S6) channel as an open forum, and use GitHub to keep track of actions, and collaborate on specific issues & pull requests.

---

<!-- Insert meeting notes here, most recent first: -->

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
