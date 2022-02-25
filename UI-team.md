
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
- Dawn Wages ([@dawnwages](https://github.com/dawnwages)), UTC - 4 or 5, since January 2022
- Harris Lapiroff ([@harrislapiroff](https://github.com/harrislapiroff)), UTC - 4 or 5, since January 2022
- Ben Enright ([@benenright](https://github.com/benenright)), UTC + 0 or 1, since February 2022

---

Next meetings: [see agenda](https://docs.google.com/document/d/1SRXjlZ3_f48XGpJrtUaNO80sz_qp_ECAs2p0gFZAO0g/edit)

Past meetings:

<!-- Insert meeting notes here, most recent first: -->

## 2022-02-10 UTC morning

Attendees: Coen, LB, Fabien, Thibaud

### Actions

- Scott & Thibaud Finish <https://github.com/wagtail/wagtail/pull/6790>
- Thibaud Set up Windows-only build of front-end tooling once #6790 is merged
- Thibaud Try out [Storybook composition](https://storybook.js.org/docs/react/workflows/storybook-composition)
- Coen Review list of components from Django perspective [Wagtail | Page editor 2022 UI overview](https://docs.google.com/spreadsheets/d/134icHJUzr-0q42cvWhYGXtFN77mnauOT5x32sAKpW_Q/edit#gid=702715712)
- Steve Review designs for multilingual issues / talk to Ben
- Coen Raise PO files methodology & blocktrans trimmed issue
- Thibaud Implement auto-fixable ordering of declaration blocks in CSS
- Thibaud Try out Normalize.css upgrade with [visual regressions](https://github.com/thibaudcolas/wagtail-tooling)
  - Please also review this PR as it explains the issue encountered when upgrading previously <https://github.com/wagtail/wagtail/pull/7626>
- Thibaud Read LB's investigation & provide feedback
- Thibaud Ask Karl, Jacob, (?) for input on UI frameworks
- Steve Follow up on design tokens definition
- Thibaud Pass on feedback re opening contributions outside of current team

### Discussions

- Actions review
- Multilingual issues
  - PO files should be done earlier? Should be part of PRs
  - Sync script happening before releases
- Lightweight UI framework
  - Transition could be gradual
  - Also considering Turbo? (Coen tried)
    - Works well in the Django paradigm
    - Stimulus Reflex = Stimulus + Turbolinks
    - Can be considered in the future -- nice to know there is a bigger ecosystem
- Styleguide -- online or embedded in Wagtail?
  - Online first
  - Embedded in Wagtail -- what's the use case?
  - Problem with current styleguide is it's out of date
  - Where should it be hosted?
    - Would be nice if it was versioned?
    - Good questions
  - Removing the current styleguide -- hopefully minimal
  - Do we need versioning?
    - Can just check out a different branch if needed
    - Landing page with instructions on how to run it locally for a specific version
    - Publish latest by default
- Page editor 2022 impact on existing backlog
  - <https://github.com/orgs/wagtail/projects/1/views/4>
- Scope for other parts of Wagtail?
  - Gradual is the way to go
  - Make sure other people can pick up the work elsewhere
  - (non-Torchbox)
- Review of jQueryUI usage
  - Main one: Hallo
  - File uploads (way beyond support)
  - Tagit
  - Code complexity is also because browser support from 10 years ago
- <https://github.com/wagtail/wagtail/projects/13#card-76521029>
- ✅ [Removal of Hallo](https://github.com/wagtail/wagtail/issues/6228)
  - Discussed in core team
  - Next release (will be 3.0)
- Deprecations / breaking changes
  - Make the Stimulus decision as soon as possible
  - Coen is keen based on concepts / working well for Wagtail in particular

## 2022-02-03 UTC afternoon

Attendees: Naomi, Scott, Thibaud, Steve, Harris

### Actions

- Scott & Thibaud Finish <https://github.com/wagtail/wagtail/pull/6790>
- Thibaud Set up Windows-only build of front-end tooling once #6790 is merged
- ✅ Thibaud Merge Prettier PR in 24hours & share steps to fix conflicts on Slack
- Thibaud Try out [Storybook composition](https://storybook.js.org/docs/react/workflows/storybook-composition)
- Coen Review list of components from Django perspective [Wagtail | Page editor 2022 UI overview](https://docs.google.com/spreadsheets/d/134icHJUzr-0q42cvWhYGXtFN77mnauOT5x32sAKpW_Q/edit#gid=702715712)
- Steve Review designs for multilingual issues / talk to Ben
- Thibaud Implement auto-fixable ordering of declaration blocks in CSS
- Thibaud Try out Normalize.css upgrade with [visual regressions](https://github.com/thibaudcolas/wagtail-tooling)
  - Please also review this PR as it explains the issue encountered when upgrading previously <https://github.com/wagtail/wagtail/pull/7626>
- ✅ Thibaud Ask for system font stack feedback in #ui as part of implementation
- Naomi, Thibaud Read LB's investigation & provide feedback
- ✅ Thibaud Ask Karl, Jacob, (?) for input on UI frameworks
- ✅ Steve Make spreadsheet with design tokens
- ✅ Steve Schedule serious bikeshedding meeting
  - With spreadsheet with design tokens
  - Comments on spreadsheet

### Discussions

- Actions review
- UI framework discussions
  - HTMX & plain JS -- still on the table? (tweet)
  - Pick one of the two options on the Web Components
  - Further look into options set aside by LB
  - Score against use cases LB drafted?
  - Scott interested in seeing how HTMX works even outside of Wagtail admin
- Prettier
  - Worth the heads' up
  - See actions
- Design tokens naming
  - Colors - numbers sound good
  - Text
  - Generic label1, label2, label3?
  - Alias to what the style actually is used
  - Document what they are for?
- Page editor 2022 impact on existing backlog
  - <https://github.com/orgs/wagtail/projects/1/views/4>

## 2022-01-27 UTC evening

Attendees: Naomi, Harris, LB, Scott, Steve, Thibaud, Dawn, Coen

### Actions

- Thibaud Review and merge <https://github.com/wagtail/wagtail/pull/6790>
- LB Review Prettier PR
- Coen Review Prettier PR
- Thibaud Try out [Storybook composition](https://storybook.js.org/docs/react/workflows/storybook-composition)
- Coen Review [list of components](https://docs.google.com/spreadsheets/d/1l7tnpEyJiC5BWE_JX0XCkknyrjxYA5T2aee5JgPnmi4/edit#gid=702715712) from Django perspective
- Thibaud Next version of declaration-strict-value PR
- LB Review afterwards
- Thibaud Research ways to help enforce usage of flexible-width components
- Thibaud Implement auto-fixable ordering of declaration blocks in CSS
- Thibaud Try out Normalize.css upgrade with [visual regressions](https://github.com/thibaudcolas/wagtail-tooling)
    - Please also review this PR as it explains the issue encountered when upgrading previously <https://github.com/wagtail/wagtail/pull/7626>
- Thibaud Ask for system font stack feedback in #ui as part of implementation
- Dawn, Naomi, Harris, Scott, Steve Read LB's investigation & provide feedback

### Discussions

- Internet submarine cables topology
- New members! 🌈
    - Welcome Harris!
        - Principal dev @ Freedom of the Press foundation
        - Want to help with this -- something that feels smaller than core team!
    - Hey Dawn :)
        - SWE at Wharton, Philadelphia, core team
        - Keen to be involved with this. Maybe with two mentees too
    - Rounds of intros! Thibaud, Steve, LB, Naomi, Scott
- Actions review
- CSS resets
    - > The version we're using is very old and rather different from the current one, but the current one looks reasonable. I (Naomi) think we should update to the current version, but either we'll have to test well since some things are affirmatively different (like going from b and strong having font-weight: bold to having font-weight: bolder). I agree with Normalize's approach of not being opinionated. I think that if we want something opinionated, we should go with using an entire accessibility-focused design system such as [uswds](https://designsystem.digital.gov/), which I've never used before, but they're legally required to be serious about accessibility.
    - Potential breakage? (this is good timing if there is any)
    - Decision needed: introduce this side by side with supporting existing CSS / UI components? Or separate
    - Thibaud to test how much is changing in practice
- Building upon USWDS design system?
    - More accessibility fundamentals to be built upon
    - Need to be careful with our dependencies
    - Need to achieve bespoke UIs, but also don't want to reinvent the wheel for utils
    - Dropdown implementation
    - Tabs implementation
    - Modal
    - Tooltips
    - Date picker
- System font stack
    - Go for it
    - Check which guidance is the most recent (follow that)
    - Roboto
    - Scott has all the devices :)
    - Chinese or Japanese testing
    - Ask in #watercooler
    - Use Squash for this
    - Ask in #translators channel / look at Transifex contributors
    - <https://infinnie.github.io/blog/2017/systemui.html>
    - Roboto issue
    - system-ui
- [LB's lightweight frameworks review](https://github.com/wagtail/wagtail/discussions/7689#discussioncomment-2037913)
    - 💯💯💯💯💯💯💯💯💯💯💯💯💯💯💯💯💯💯💯💯💯💯💯
    - 🌈🌈🌈🌈🌈🌈🌈🌈🌈🌈🌈🌈🌈🌈🌈🌈🌈🌈🌈🌈🌈🌈🌈
    - Ask for others to review, particularly people involved with Telepath
    - RFC?
    - ES6 modules RFC overlap?
    - Look at thread from people with production experience
- 45min meetings!
- Recurring meetings for

## 2022-01-20 UTC morning

Attendees: Thibaud, LB

### Actions

- ✅ Steve Share and demo Alpine implementation of dropdown
- Thibaud Review and merge <https://github.com/wagtail/wagtail/pull/6790>
- LB Review Prettier PR
- Coen Review Prettier PR
- Thibaud Try out [Storybook composition](https://storybook.js.org/docs/react/workflows/storybook-composition)
- Coen Review [list of components](https://docs.google.com/spreadsheets/d/1l7tnpEyJiC5BWE_JX0XCkknyrjxYA5T2aee5JgPnmi4/edit#gid=702715712) from Django perspective
- ✅ Scott Stylelint declaration-strict-value PR review
- Thibaud Research ways to help enforce usage of flexible-width components
- Thibaud Implement auto-fixable ordering of declaration blocks in CSS
- ✅ Naomi Research normalize.css & other resets
- ✅ Scott Research system font stack for Wagtail ([#7724](https://github.com/wagtail/wagtail/issues/7724))
- Naomi looked into this a bit and commented. It looks like yes we should do this and we should be careful about testing font weights

### Discussions

- Actions review
- jQuery deprecations
- JS framework for Wagtail

## 2022-01-13 UTC afternoon

Attendees: Naomi, Scott, Fabien, Thibaud, Steve

### Actions

- Steve Share and demo Alpine implementation of dropdown
- Thibaud Review and merge <https://github.com/wagtail/wagtail/pull/6790>
- LB Review Prettier PR
- Coen Review Prettier PR
- Thibaud Try out [Storybook composition](https://storybook.js.org/docs/react/workflows/storybook-composition)
- Thibaud Review page editor related issues and PRs
- Coen Review [list of components](https://docs.google.com/spreadsheets/d/1l7tnpEyJiC5BWE_JX0XCkknyrjxYA5T2aee5JgPnmi4/edit#gid=702715712) from Django perspective
- LB Stylelint declaration-strict-value PR review
- ⏳ Scott Stylelint declaration-strict-value PR review
- Thibaud Research ways to help enforce usage of flexible-width components
- Thibaud Implement auto-fixable ordering of declaration blocks in CSS
- Naomi Research normalize.css & other resets
- Scott Research system font stack for Wagtail ([#7724](https://github.com/wagtail/wagtail/issues/7724))

### Discussions

- Actions review
  - ✅ Thibaud Ask an Alpine.js / htmx expert to pitch us
    - ​​<https://codepen.io/thibaudcolas/pen/rNGrPjz>
  - Thibaud Review and merge <https://github.com/wagtail/wagtail/pull/6790>
  - LB Review Prettier PR
  - Coen Review Prettier PR
  - ✅ Thibaud Prettier semi-automated PR conflict fixes step-by-step
    - git rebase  --strategy-option=theirs  --exec '(djhtml -i `git show --name-only --pretty="" HEAD "*.html"` || true) && git add `git show --name-only --pretty="" HEAD "*.html"` && git commit --amend --no-edit --no-verify'  origin/master
  - Thibaud Try out [Storybook composition](https://storybook.js.org/docs/react/workflows/storybook-composition)
  - ✅ Fabien Review [RTL support plans](https://github.com/wagtail/wagtail/discussions/7793)
  - ✅ Thibaud Review CSS refactoring list <https://github.com/wagtail/wagtail/projects/4#card-17060767>
  - Coen Review [list of components](https://docs.google.com/spreadsheets/d/1l7tnpEyJiC5BWE_JX0XCkknyrjxYA5T2aee5JgPnmi4/edit#gid=702715712) from Django perspective
  - LB Stylelint declaration-strict-value PR review
  - ⏳ Scott Stylelint declaration-strict-value PR review
  - Thibaud Research ways to help enforce usage of flexible-width components
  - Thibaud Implement auto-fixable ordering of declaration blocks in CSS
- Wagtail 2.16
  - Slim sidebar
  - TypedTableBlock
  - Modal choosers bug fix
  - Breaking changes expected in Wagtail 2.17
    - SVG icons
    - Modernizr
    - jQuery Datetimepicker
    - Good idea
- [Wagtail design system components list](https://docs.google.com/spreadsheets/d/1l7tnpEyJiC5BWE_JX0XCkknyrjxYA5T2aee5JgPnmi4/edit#gid=702715712)
- Modern CSS reset
  - Example: <https://www.joshwcomeau.com/css/custom-css-reset/>
  - Pick one and move on :)
  - Or... careful because of the potential breakage
  - Box-sizing
  - <https://necolas.github.io/normalize.css/> consider first
  - UI regression test suite would be nice
  - Percy + Browserstack sponsorship
  - <https://github.com/thibaudcolas/wagtail-tooling>
- System font stack ([Wagtail brand font #7724](https://github.com/wagtail/wagtail/issues/7724))
  - Who has done research? / wants to
  - Customisable system font
  - Dyslexia font support / browser extensions or browser-level font  customization
  - Good resources on this?
  - web-a11y
- Browser support & testing goals
  - iOS Safari 12?
  - Windows testing
  - Windows: yes, Edge (scrollbar)
  - Safari last 3 major versions
  - Device management issues & Safari version tied to OS

## 2022-01-06 UTC evening

Attendees: Steve, Scott, Naomi, Thibaud

### Actions

- Thibaud Ask an Alpine.js / htmx expert to pitch us
- Thibaud Review and merge <https://github.com/wagtail/wagtail/pull/6790>
- LB Review Prettier PR
- Coen Review Prettier PR
- Thibaud Prettier semi-automated PR conflict fixes step-by-step
- Thibaud Try out [Storybook composition](https://storybook.js.org/docs/react/workflows/storybook-composition)
- ✅ Fabien Review [RTL support plans](https://github.com/wagtail/wagtail/discussions/7793)
- Thibaud Review CSS refactoring list <https://github.com/wagtail/wagtail/projects/4#card-17060767>
- Coen Review [list of components](https://docs.google.com/spreadsheets/d/1l7tnpEyJiC5BWE_JX0XCkknyrjxYA5T2aee5JgPnmi4/edit#gid=702715712) from Django perspective
- LB Stylelint declaration-strict-value PR review
- Scott Stylelint declaration-strict-value PR review
- Thibaud Research ways to help enforce usage of flexible-width components
- Thibaud Implement auto-fixable ordering of declaration blocks in CSS

### Discussions

- Quick recap of last meeting
  - Alpine.js!!! and htmx
  - Boring tools = good
  - How would this be for new contributors?
  - Compared to React & vanilla JS
  - Looking at Wagtail’s contributor base in particular
- Actions review
  - ✅ Thibaud Share good resource on design tokens (thank you Coen, <https://spectrum.adobe.com/page/design-tokens/>)
  - ✅ Thibaud Look into ways to automate checking which PRs might have UI changes
  - Thibaud Prettier semi-automated PR conflict fixes step-by-step
  - Thibaud Try out [Storybook composition](https://storybook.js.org/docs/react/workflows/storybook-composition)
  - Fabien Review [RTL support plans](https://github.com/wagtail/wagtail/discussions/7793)
  - ✅ Thibaud First draft of feasibility review with build per component
    - <https://docs.google.com/spreadsheets/d/1l7tnpEyJiC5BWE_JX0XCkknyrjxYA5T2aee5JgPnmi4/edit#gid=702715712>
  - ✅ LB Follow up on Django-friendly frontend customisations in chat
    - General gist - we need to make sure we support lots of customisations through Django
    - A simple example, adding classes - this should work for lots of things and be able to be done in Django land
- Prettier
  - Spaces for HTML? 4
  - Spaces for JS? 2
  - Spaces for CSS? 2
  - Single quotes
  - We want to be different (but don’t care that much)
  - <https://github.com/wagtail/wagtail/compare/main...thibaudcolas:chore/prettier-setup?expand=1>
  - JSON, YAML: yes
  - Markdown: no
  - djhtml
- Components review
  - <https://docs.google.com/spreadsheets/d/1l7tnpEyJiC5BWE_JX0XCkknyrjxYA5T2aee5JgPnmi4/edit#gid=702715712>
  - Django review
  - Messages -- use vanilla Django
  - Error lists
  - StructBlock validation -- can only attach error messages to blocks within StructBlock, not at the StructBlock level
    - Potentially the same for StreamBlock, ListBlock
  - "It's very functional if you are sighted and have good motor skills"
  - Styleguide
    - (It's not very good)
- Webpack + other tooling upgrades
  - Stylelint
  - Stylelint declaration-strict-value: <https://github.com/wagtail/stylelint-config-wagtail/pull/9>
  - Stylelint RTL styles enforcement: <https://github.com/wagtail/stylelint-config-wagtail/pull/10>
  - RTL
  - Consideration of word width
  - Order of properties: <https://github.com/hudochenkov/stylelint-order>
    - Would be nice if automate-able, otherwise might not be worth it? Yes it's auto-fixable
    - Mixins first
    - Sample: <https://github.com/thibaudcolas/stylelint-config-cookbook/blob/main/src/config.js#L93>
  - Modern CSS: <https://github.com/ismay/stylelint-no-unsupported-browser-features>

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
