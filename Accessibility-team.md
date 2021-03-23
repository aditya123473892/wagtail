# Wagtail accessibility team

Find us in [#accessibility on Slack](https://app.slack.com/client/T0K33F93J/CB7L6L5S6).

## Team charter

The team’s membership is open to all, introduce yourself in [#accessibility on Slack](https://app.slack.com/client/T0K33F93J/CB7L6L5S6) if you’re interested in joining. We currently operate with a membership term of 6 months, so people can commit for a short term, and then decide to proceed or stop.

We meet every two weeks to discuss everyone’s recent progress and next steps. At the end of each meeting, all participants should each have volunteered for an action, which they must strive to complete before the next meeting. Meeting notes and actions are public for future and past meetings. Meetings happen on Google Meet.

In-between meetings, we collaborate via Slack, using the [#accessibility](https://app.slack.com/client/T0K33F93J/CB7L6L5S6) channel as an open forum, and use GitHub to keep track of actions, and collaborate on specific issues & pull requests.

## Team members

Current members:

- Scott Cranfill ([@Scotchester](https://github.com/Scotchester)), UTC - 4 or 5
- Thibaud Colas ([@thibaudcolas](https://github.com/thibaudcolas)), UTC + 0 or 1
- Jesse Menn ([@jessemenn](https://github.com/jessemenn)), UTC - 4 or 5
- Kyle Bayliss ([@kbayliss](https://github.com/kbayliss)), UTC + 0 or 1
- Storm Heg ([@Stormheg](https://github.com/Stormheg), UTC + 1 or 2

Past members: Andreas Bernacca, Scott Cranfill, Thibaud Colas

---

Next meetings: [see agenda](https://docs.google.com/document/d/1YUxOs5jYZMd8rX291mDE123xIK7tbD63PzSR9ooFa4c/edit)

Past meetings:

<!-- Insert meeting notes here, most recent first: -->

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
