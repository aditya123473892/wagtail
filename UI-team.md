
Find us in [#ui on Slack](https://app.slack.com/client/T0K33F93J/C0P6APKH9).

## Team charter

The team’s membership is open to all, introduce yourself in [#ui on Slack](https://app.slack.com/client/T0K33F93J/C0P6APKH9) if you’re interested in joining. We currently operate with a membership term of 6 months, so people can commit for a short term, and then decide to proceed or stop.

We meet every two weeks on Zoom, rotating between three time slots to offer meetings within work hours in the Americas, Europe, Australia. Between meetings, we keep track of our work on Slack and via a [UI team project board](https://github.com/wagtail/wagtail/projects/13).

## Team members

Current members:

- Thibaud Colas ([@thibaudcolas](https://github.com/thibaudcolas)), UTC + 0 or 1, since December 2021
- Scott Cranfill ([@Scotchester](https://github.com/Scotchester)), UTC - 4 or 5, since December 2021
- Naomi I. Morduch Toubman ([@nmorduch](https://github.com/nmorduch)), UTC - 4 or 5, since December 2021
- LB (Ben Johnston) ([@lb-](https://github.com/lb-)), UTC + 10, since December 2021
- Fabien Le Frapper ([@fabienheureux](https://github.com/fabienheureux)), UTC + 1 or 2, since December 2021
- Coen van der Kamp ([@allcaps](https://github.com/allcaps)), UTC + 1 or 2, since December 2021
- Steve Steinwand ([@stevedya](https://github.com/stevedya)), UTC - 7 or 8, since December 2021

---

Next meetings: [see agenda](https://docs.google.com/document/d/1SRXjlZ3_f48XGpJrtUaNO80sz_qp_ECAs2p0gFZAO0g/edit)

Past meetings:

<!-- Insert meeting notes here, most recent first: -->

## 2021-12-16

Attendees: Thibaud, Fabien, Steven, LB, Coen

Apologies: Naomi

### Actions

- Thibaud Share good resource on design tokens
- Fabien Review Thibaud's RTL plans
- Thibaud First draft of feasibility review with build per component
- LB Follow up on Django-friendly frontend customisations in chat
- General gist - we need to make sure we support lots of customisations through Django
- A simple example, adding classes - this should work for lots of things and be able to be done in Django land

### Discussions

- Backlog review!
  - Below -- everything  Thibaud is planning to do ahead of starting the page editor redesign's builds in February
  - Areas you'd like to be involved with: 🥭 Naomi, 🍎Coen, 🍐 Fabien, 🍑 LB, 🍒 Scott, 🍓 Steve
  - 🍋 immediate priority for Thibaud
  - 💥: needs further validation / sounds silly / are you sure about this?
- [Page editor 2022](https://github.com/wagtail/wagtail/discussions/7739) backlog -- planning
  - Design feasibility review🍋 🍓
  - Design accessibility review🍋
  - Project scoping / backlog refinement🍋
  - Spikes / PoC for specific features (quick nav / minimap)
  - Breaking changes review🍋
  - GitHub issues / existing PRs review 🍑
- [Page editor 2022](https://github.com/wagtail/wagtail/discussions/7739) backlog -- code changes
  - Design tokens setup🍓
    - Design tokens as JS files
    - Tailwind theme to reuse design tokens in stylesheets🍓
    - npm package to share design tokens (& eventually UI components) to maintain consistency across other projects 🍎🍓
  - Design system's UI components setup
    - Sass + BEM + ITCSS for UI component styles🍓
    - Tailwind for basic utility classes (spacing, grid) and dead CSS removal. 🍓
    - Django templates + vanilla JS/TS OR React (TS only) for UI component markup & behavior 🍐 🍓
    - django-pattern-library + Storybook to🍋 🍎🍐 🍓
    - RTL 🍐
  - Static analysis overhaul
    - Prettier for automated formatting 🍐 🍑 🍋
    - djhtml for automated formatting 🍐 🍋
    - Stylelint config ++: disallow hard-coding any value that is a design token, consistent spacing, consistent usage of RTL-friendly styles 🍑 🍋
    - ESLint config ++: update to recent version of current setup 🍑 🍋
  - UI testing
    - Using the `tests` project within Wagtail as a manual UI testing environment with dedicated fixtures 🍎
    - <https://github.com/wagtail/wagtail/pull/7751> 🍋🍎
  - Tech debt
    - Gulp -> Webpack
    - Windows compatibility
    - IE11 hacks / cruft removal🍋
- Design tokens --fundamental units of design systems reuse
- jQuery future?
  - Disallow with linting rule
  - Not necessarily a goal on its own but we want to do this alongside other work
  - Also makes it easier to write unit tests for this code
- React -- where do we want to use it?
  - Choosers?
  - htmx -- is there a place for it?
  - Potentially -- more lightweight than React, easier to work with for Django devs
  - Alpine? Same question
  - htmx --AJAX calls
- POC? 🍐
- Windows compatibility
  - Frequent questions on Slack
- Wagtail as a platform
  - Collaborative editing & autosave
- RTL support
  - Fabien has clients needing this
  - And some experience
- Wagtail as a Django CMS
  - For example needing to do forms in a Django formset/widget/field friendly way

## 2021-12-02 -- new team kickoff

### Actions

- Not this time

### Discussions

Attendees:

- Welcome & introductions
- What do we all want to achieve with the new team?
  - Thibaud
    - Automated tests
    - Pattern library / design system setup
    - Stronger baseline for UI enhancements
    - Having a group of people to run things past at the planning level & code review
  - Naomi
    - Return to CSS refactoring from however many years ago :)
    - Modular CSS
    - Pattern library
    - A robust enough design system set up so developers can reuse components as-is
    - Utilities for things like e.g. spacing, not semantic
    - Sass vs SCSS (Naomi "SCSS is the better choice (for an open source project")
  - Scott
    - Using Wagtail for 6 years now! Pre 1.0
    - Core team since 2020
    - Working at NASA JPL, Wagtail users in federal govt
    - Headless Wagtail! w/ Nuxt & Vue
    - UI team -- continuation of accessibility team
    - HTML semantics & quality designs FTW
  - Fabien
    - Based in France! Worked with Torchbox a few months ago
    - Also headless!
    - Also Google Meet refreshes :)
    - Keeping track of front-end discussions for a bit. Wanting to see a Wagtail design system happen
    - Could be useful for client work
    - React experience & JS in general
  - LB
    - Core team for 4 years!
    - Also a 2 year old :)
    - Full time job 100% front-end, React, Sass (SCSS!).
    - Getting this set up so they are easy to develop
    - Making JS stuff in Wagtail as easy to customise & extend as the Python
    - Making JS customisations more approachable
    - Keen on design systems, & accessibility
  - Coen
  - Ben
  - Steve
- IE11!
  - Officially out
  - But still a problem for some teams
- How the team works
  - Initial plan: open membership, 45-min chats every so often, 6 months term
  - Video software
    - Zoom 👍(Naomi)(LB)(Scott)
    - Meet 👍👍(LB)
  - Other options very welcome?
  - Meeting schedule options:
    - Every week -- Align with core team meetings? 👍
      - Technically every other week for people in the US & Australia
      - Either right before or right after
    - Every week -- Identical time but opposite week of core team meetings? 👍
      - Technically every other week for people in the US & Australia
      - UTC morning core team meeting = UTC afternoon UI team, & vice versa
    - Every week -- switching between 3 slots? 👍👍
      - Thursdays
      - Tuesdays or thursdays (wednesday & friday for LB)
      - UTC morning (Asia + Pacific + Europe)
      - UTC afternoon (Europe + Americas)
      - UTC evening (Americas + Asia + Pacific) 👍
    - Kickoff time + 30min
  - Change the core team to rotate between three times
  - Something else?
  - 6 months membership?
- Core team meeting at 9pm UTC? Ideally 9:30pm
- Pros & cons of pattern libraries
  - Makes it easier to add components, but harder to make new components
- Board!
  - <https://github.com/wagtail/wagtail/projects/13>
- Accept access requests
