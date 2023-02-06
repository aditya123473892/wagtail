Our application for 2023 is pending.

**Links**

* [GSoC 2023 timeline](https://developers.google.com/open-source/gsoc/timeline)
* [#gsoc on Slack, open to ask us anything](https://github.com/wagtail/wagtail/wiki/Slack)
* [Documentation](http://docs.wagtail.org/)
* [Wagtail blog](https://wagtail.org/blog/)
* Our past projects: [GSoC 2022](https://github.com/wagtail/wagtail/wiki/Google-Summer-of-Code-2022), [GSoC 2021](https://github.com/wagtail/wagtail/wiki/Google-Summer-of-Code-2021)

**Table of Contents**

* [About Wagtail](#about-wagtail)
* [Contributors](#contributors)
* [Organisation admins](#organisation-admins)
* [Mentors](#mentors)
* [Project ideas](#project-ideas)
  * [Dark theme for Wagtail admin](#dark-theme-for-wagtail-admin)
  * [RFC 72: Background workers](#rfc-72-background-workers)
  * [Greener coding: Wagtail’s climate impact](#greener-coding-wagtails-climate-impact)


## About Wagtail

Wagtail is a popular content management system. It's built on Python, by an active and engaged open source community, which has grown rapidly since Wagtail's release in 2014. Wagtail is available in over 40 languages, and used by some of the world's best-known organizations, including NASA, Google, Mozilla, MIT, and the UK's National Health Service, as well as museums, universities, non-profits, governments, banks, studios, restaurants, startups and bloggers around the world.

Like Python and Django, the technologies which underpin it, Wagtail is known for its welcoming community. We're keen to increase the geographic and cultural diversity of our core team, who are currently spread across Europe, Africa and North America. We seek to offer friendly support on Slack, StackOverflow and Github, and we encourage the community to meet in real life where possible, with recent sprints and conferences held in South Africa, Iceland, the USA, Belarus and the UK.

Wagtail has moved fast in the last few years, with particular focus on the editor experience, the refinement of APIs for headless CMS architectures and accessibility. We have adopted a regular quarterly release cycle, which aims to minimise upgrade time while providing compelling new features and improvements with each point releases. We're seeking help to deliver some of our more ambitious plans, many of which are expressed as [RFCs]. We're also open to your ideas for making Wagtail the best open source CMS for the 2020s!

## Contributors

GSoC is an activity that a contributor (participant) performs as an independent developer. Contributors get a stipend from Google. 

Wagtail contributors should:

- Have a good understanding of how GSoC works. Read [Contributor advice](https://developers.google.com/open-source/gsoc/help/student-advice), [Contributor guide](https://google.github.io/gsocguides/student/) and [FAQ](https://developers.google.com/open-source/gsoc/faq).
- Have a basic familiarity with Python, Django and Git.
- Go through the [Wagtail tutorial](https://docs.wagtail.org/en/stable/getting_started/tutorial.html). Let us know if you encounter blockers.
- Create a [development environment](https://docs.wagtail.org/en/stable/contributing/developing.html) for working on Wagtail. There are good instructions in our [official documentation](https://docs.wagtail.org/en/stable/contributing/index.html).
- Join [Wagtail Slack](https://github.com/wagtail/wagtail/wiki/Slack) and introduce yourself on the [#gsoc](https://wagtailcms.slack.com/archives/CTL4SFX29) channel.
- Get to know the Wagtail community. Consider contributing to Wagtail already. Show that you understand how open-source projects work.
- Invest time to discover what project fits you.
- Try to contribute to the project discussion.

### Improve your chances of being accepted

The best thing you can do to improve your chances of being accepted as a Wagtail GSoC contributor is to start contributing now. Make yourself known to the community for your contributions. Try to contribute to an area related to your proposal. When the time comes to evaluate applications, you will be a known individual.

We're looking for candidates who can demonstrate that they can engage in the Wagtail project. We're here to help, but we can't watch you every step of the way. We need to see motivation from you. Your activities before the submissions process are the best way to demonstrate this.

## Organisation admins

Thibaud Colas (@Thibaud on Slack) is our Wagtail organisation admin. Organisation admins oversee mentors, contributors, and are the point of contact for Google. You can contact them on [Slack](https://github.com/wagtail/wagtail/wiki/Slack).

## Mentors

If you're interested in mentoring -- supervising a contributor in work on Wagtail-related activities -- let us know by direct messaging the [organisation admins](#organisation-admins).

---

## Project ideas

### Dark theme for Wagtail admin

#### Summary

Roll out a new dark theme across the Wagtail admin UI. This is a continuation of past projects to make Wagtail’s color theme configurable, and accessibility improvements for Windows High Contrast mode users.

#### Expected outcomes

The whole of the Wagtail administration interface will be viewable in a dark color scheme, which a lot of our users will opt to use. Wagtail’s UI development methodology now takes it into account for future features, in a sustainable way.

#### Implementation

We’re wondering if we should consider greater theme-ability as part of this – delivering not just a dark theme but also potentially support for lots of different themes ("dark high contrast", "light high c0ontrast"). Aside from this decision, we can already:

1. Research how leading projects are doing this.
2. Review how the admin UI works currently with Google Chrome’s auto dark mode.
3. Update our contributor documentation with appropriate guidelines.
4. Update our tooling to make it easier to support and test those types of changes.
5. Roll out fixes & improvements to existing UI components.

We are expecting the types of changes needed to be simple once identified, but there is an important planning element here to make sure we do the most sensible changes, at the appropriate level of abstraction.
We also want to make sure any changes to add dark theme support are made in a way that works for future development.

#### Skills

- HTML, CSS, SVG
- JavaScript
- Accessibility
- UI development tooling

#### Mentors

- Lead: Thibaud Colas https://github.com/thibaudcolas
- Support: Sage Abdullah https://github.com/laymonage

#### Size

175 hours

#### Difficulty rating

Medium

### RFC 72: Background workers

#### Summary

See [RFC 72: Background workers](https://github.com/RealOrangeOne/wagtail-rfcs/blob/wagtail-background-workers/text/072-background-workers.md)

Wagtail currently doesn't have a first-party solution for long-running tasks. Other CMSs in the ecosystem such as WordPress and Drupal have background workers, allowing them to push tasks into the background to be processed at a later date, without requiring the end user to wait for them to occur.

One of the key goals for this project is removing the requirement for the user to wait for tasks they don't need to.

#### Background

Some tasks done as part of certain Wagtail requests don't need to block the user, and could instead be pushed to the background, improving the perceived responsiveness of the application. Having a first-party solution would also remove the need for downstream users to build a background worker pipeline themselves.

A prime example of this kind of improvement is re-indexing pages. Currently, when a user publishes a page, the "Publish" action also re-indexes the page, which slows down the request unnecessarily. The user doesn't need to wait for the indexes to be updated, meaning they could continue with whatever they need to do next faster. By moving tasks into the background, it also means longer tasks don't tie up the application server, meaning it should be able to handle more editor traffic.

Other CMSs such as WordPress and Drupal have background workers to accelerate these kinds of non-blocking tasks. These APIs allow both for the tools themselves to push tasks to the background, but also for users to submit tasks themselves.

#### Requirements

- Wagtail's background tasks should be opt-in, and Wagtail should function as it does now without it.
- Users should be able to choose from either running a persistent background process, or periodic execution with cron
- Users should have multiple options for task backends, depending on their scale and hosting environment. By default, Redis and Django's ORM should be supported.
- Users should be able to easily add their own tasks to be executed, whether through Wagtail hooks or entirely manually.
- Tasks should be able to specify a priority, so they can be executed sooner, regardless of when they were submitted.
- Users should need to neither know nor care about the specific implementation details. This includes both the implementation details, and which backend is being used (mostly applicable to library authors)

#### Implementation plan

- Create the basic plumbing and base classes required
- Implement ImmediateBackend
- Enable creating wagtail hooks as tasks
- Implement an ORM backend
- Begin migrating background-compatible bits of Wagtail to tasks
- Documentation
- Initial release?
- Complete migrating background-compatible bits of Wagtail to tasks

#### Skills

- Python
- Django
- Performance
- DevOps

#### Mentors

Final list TBC

- Lead: TBC Jake Howard https://github.com/RealOrangeOne
- Support: TBC either Thibaud, Sage, or other core team member

#### Size

175 hours

#### Difficulty rating

Medium

### Greener coding: Wagtail’s climate impact

#### Summary

We’re starting to have a better understanding of the [climate impact of Wagtail](https://github.com/wagtail/wagtail/discussions/8843) as a CMS, and how we can reduce it. We want to integrate our findings into Wagtail’s direction, and make concrete improvements to the project to reduce related carbon emissions.

#### Expected outcomes

The climate impact of Wagtail sites will be measurable with agreed-upon methodologies, and we will do so on a regular basis. By the end of the project, we will have released a number of energy efficiency improvements reducing the impact of Wagtail sites (image optimisation, better caching, scale-to-zero setup).

#### Implementation

We’re wondering if we should consider greater theme-ability as part of this – delivering not just a dark theme but also potentially support for lots of different themes ("dark high contrast", "light high c0ontrast"). Aside from this decision, we can already:

1. Research how leading CMS projects are doing this.
2. Produce a report on the climate impact of Wagtail sites at this point in time.
3. Update our tooling to make it easier to evaluate energy efficiency on a regular basis.
4. Plan 5-10 sustainability-related changes to Wagtail
5. Implement 3-5 of these changes

#### Skills

This project is suitable with a wide range of skillsets, we can adjust tasks accordingly.

- Python
- Django
- Performance
- DevOps

#### Mentors

- Lead: Thibaud Colas https://github.com/thibaudcolas
- Support: TBC either Sage, Chris, or performance team member

#### Size

175 hours

#### Difficulty rating

Medium

### Project proposal

You can also propose your own idea. Your proposal should:

- Have a concrete task.
- Give a solid idea of what will constitute success. You tell us.
- Present a detailed design specification.
- Give insight into who you are. If you propose something ambitious, convince us that you are up to the task.
- Give insight into your previous projects and experience.
- Tell us about your experience with Python/Django/Wagtail.
- Provide a schedule, including a detailed work breakdown and major milestones.
- Contain your motivation and curriculum vitae.

Here is an example of [an accepted proposal](https://gist.github.com/chrismedrela/82cbda8d2a78a280a129).

Note:

- The project ideas below are starting points for your submission, but aren’t enough by themselves. You’ll need to come up with a more complete project plan, and use your own words.
- Do not feel limited to the project ideas below.
- If you have a project idea not listed, please direct message the [organisation admins](#organisation-admins). They can test the project eligibility and pair you with a mentor for initial feedback.

Project proposals should fall into one of three categories:

- Work on Wagtail itself. The core product.
- Work on tools to support Wagtail. Example: Editor guide as a Wagtail website.
- Wagtail third-party libraries. Example: [Wagtail Live](https://github.com/wagtail/wagtail-live) is a GSOC 2021 project.

The project you propose should be:

- Something useful for the Wagtail project
- A single well-scoped project
- Achievable within the time of GSoC
- And something the core developers can help mentor you on.

Contribution guidelines:

- The [code of conduct](https://github.com/wagtail/wagtail/blob/main/CODE_OF_CONDUCT.md) applies to all contributors.
- The [contribution guidelines](https://docs.wagtail.org/en/latest/contributing/index.html#) apply to all contributions.
