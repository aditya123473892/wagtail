## Table of Contents

* [Resources](#resources)
* [About Wagtail](#about-wagtail)
* [Contributors](#contributors)
  * [Contributor initial checklist](#contributor-initial-checklist)
  * [Documentation contributors checklist](#documentation-contributors-checklist)
  * [Accessibility project checklist](#accessibility-project-checklist)
  * [Stimulus project checklist](#stimulus-project-checklist)
* [Improve your chances of being accepted](#improve-your-chances-of-being-accepted)
* [Your first contribution](#your-first-contribution)
* [Organisation coordinator](#organisation-coordinator)
* [Frequently asked questions](#frequently-asked-questions)

## Resources

* [outreachy.org](https://www.outreachy.org/)
* [#outreachy channel on Slack, for any questions](https://github.com/wagtail/wagtail/wiki/Slack)
* [Wagtail documentation](http://docs.wagtail.org/)
* [Wagtail blog](https://wagtail.org/blog/)
* [Video: Contributing to Open Source for the first time](https://youtu.be/c6b6B9oN4Vg)

## About Wagtail

Wagtail is a popular content management system. It's built on Python, by an active and engaged open source community, which has grown rapidly since Wagtail's release in 2014. Wagtail is available in over 40 languages, and used by some of the world's best-known organizations, including NASA, Google, Mozilla, MIT, and the UK's National Health Service, as well as museums, universities, non-profits, governments, banks, studios, restaurants, startups and bloggers around the world.

Like Python and Django, the technologies which underpin it, Wagtail is known for its welcoming community. We're keen to increase the geographic and cultural diversity of our core team, who are currently spread across Europe, Africa and North America. We seek to offer friendly support on Slack, StackOverflow and Github, and we encourage the community to meet in real life where possible, with recent sprints and conferences held in South Africa, Iceland, the USA, Belarus and the UK.

Wagtail has moved fast in the last few years, with particular focus on the editor experience, the refinement of APIs for headless CMS architectures and accessibility. We have adopted a regular quarterly release cycle, which aims to minimise upgrade time while providing compelling new features and improvements with each point releases. We're seeking help to deliver some of our more ambitious plans, many of which are expressed as [RFCs]. We're also open to your ideas for making Wagtail the best open source CMS for the 2020s!

## Contributors

We expect participants to go through a few initial tasks as part of the Outreachy contribution period, ahead of their final application. This is for you to get to know Wagtail as a project and community, and get a sense of how we can work together. It also helps mentors assess the skills of candidates, so we can decide which projects we can take on with you.

Based on your preferred project idea(s), go through the relevant tasks lists below.

### Contributor initial checklist

For **all** projects – participants to Outreachy should:

1. [ ] Have a good understanding of how Outreachy works.
2. [ ] Join the [Wagtail Slack](https://github.com/wagtail/wagtail/wiki/Slack) and introduce yourself on the #new-contributors channel. Let us know a bit about you (what you’re comfortable with!), skills you have and skills you want to practice, which projects you’re interested in.
3. [ ] Update your profile image in Slack to be something other than the default image (can be a photo of you or any image you like).
4. [ ] Invest time to discover what project(s) you like.
5. [ ] Ask questions about the project(s) you are interested in.
6. [ ] Get to know the Wagtail community.
7. [ ] Join GitHub, if you have not already, ensure you have an image on your profile and your preferred public name set.
8. [ ] Make small contributions to Wagtail already. Show that you understand how open-source projects work. This can be all sorts of different kinds of tasks – helping orient people on Slack, identifying problems with Wagtail, our documentation. Making changes to the code, documentation, translation, etc.
9. [ ] Attend one of our Outreachy Q&A sessions (more details to come)

### Documentation contributors checklist

For people interested in contributing to project 2 _"Improve user guide documentation for Wagtail"_, we expect you to go through the following initial tasks as part of getting up to speed with Wagtail as a community:

- [ ] Use [Wagtail Gitpod](https://wagtail.org/blog/gitpod/) to go through the [Wagtail tutorial](https://docs.wagtail.org/en/latest/getting_started/tutorial.html). Let us know if you encounter blockers.
- [ ] Use Gitpod again, this time to [set up our fully-fledged bakerydemo website](https://github.com/wagtail/bakerydemo#setup-with-gitpod). This will allow you to test more Wagtail features
- [ ] Read through some of our [documentation for developers](https://docs.wagtail.org/en/stable/) and [documentation for users](https://docs.wagtail.org/en/stable/editor_manual/index.html), to get a sense of our voice and tone, and writing style.
- [ ] Read about [Diátaxis](https://diataxis.fr/), the documentation structure we use for Wagtail.
- [ ] Write a **short blog post** describing your Outreachy involvement so far, and share it with us. The post must be in English, include at least one image, be less than 500 words, and score a Grade 4 or better on <https://hemingwayapp.com/>. It can be a public post on your own blog or a blogging site, or a Google Docs document you share with us (make sure commenting is enabled). You can talk about anything Outreachy – things you’re doing with Wagtail but also before, or any other Outreachy community you’re also trying to work with. To share the post, DM Thibaud Colas on Slack or @-mention [@thibaud_colas](https://twitter.com/thibaud_colas) on Twitter.
- [ ] Review our [new user guide website](https://wagtail.org/editor-guide-site) and its contents, and provide feedback proposing specific improvements in the [Outreachy: Improve user guide documentation for Wagtail](https://github.com/wagtail/guide/discussions/116) discussion thread. Those can be improvements to the existing content, or addition of new content you think is missing based on trying out Wagtail. You may also suggest features that would make the site nicer to use, or make the documentation more accessible to users.
- [ ] Using your local copy of Wagtail, or [gitpod-wagtail-develop](https://github.com/wagtail/gitpod-wagtail-develop), or the GitHub editing interface, make contributions to the existing documentation in the [`docs/` folder](https://github.com/wagtail/wagtail/tree/main/docs) of our project. See a list of [issues tagged "Documentation"](https://github.com/wagtail/wagtail/issues?q=is%3Aopen+label%3ADocumentation+sort%3Aupdated-desc).

### Accessibility project checklist

For people interested in contributing to projects 1 _"Develop tools to help Wagtail editors create accessible content"_, we expect you to go through the following tasks:

- [ ] Confirm you have a basic familiarity with Git and GitHub.
- [ ] Go through the [Wagtail tutorial](https://docs.wagtail.org/en/latest/getting_started/tutorial.html) on your own computer (no Gitpod). Let us know if you encounter blockers.
- [ ] Create a [development environment](https://docs.wagtail.org/en/latest/contributing/developing.html) for working on Wagtail. Again, without Gitpod. There are good instructions in our [official documentation](https://docs.wagtail.org/en/latest/contributing/index.html).
- [ ] Make at least one bug fix or feature enhancement to Wagtail as a pull request, excluding documentation changes, following our documentation for contributors.
- [ ] Go through the [Sa11y documentation](https://sa11y.netlify.app/)
- [ ] Read the [ATAG standard](https://www.w3.org/TR/ATAG20/), which we are trying to meet as part of this project

### Stimulus project checklist

For people interested in contributing to project 3 _"Introduce Stimulus for interactive widgets within Wagtail"_, we expect you to go through the following tasks:

- [ ] Confirm you have a basic familiarity with Git and GitHub.
- [ ] Go through the [Wagtail tutorial](https://docs.wagtail.org/en/latest/getting_started/tutorial.html) on your own computer (no Gitpod). Let us know if you encounter blockers.
- [ ] Create a [development environment](https://docs.wagtail.org/en/latest/contributing/developing.html) for working on Wagtail. Again, without Gitpod. There are good instructions in our [official documentation](https://docs.wagtail.org/en/latest/contributing/index.html).
- [ ] Make at least one bug fix or feature enhancement to Wagtail as a pull request, excluding documentation changes, following our documentation for contributors.
- [ ] Go through the [Stimulus handbook](https://stimulus.hotwired.dev/handbook/origin)
- [ ] Read our [Stimulus RFC (Request For Comments)](https://github.com/wagtail/rfcs/blob/rfc/stimulus/text/078-adopt-stimulus-js.md)

Here are additional resources which you may find helpful to better understand this project:

- https://github.com/hotwired/stimulus-starter
- https://dev.to/lb/creating-an-interactive-event-budgeting-tool-within-wagtail-53b3
- https://dev.to/lb/creating-a-schematic-editor-within-the-wagtail-cms-with-stimulusjs-n5j

## Improve your chances of being accepted

The best thing you can do to improve your chances of being accepted as an Outreachy contributor with Wagtail is to start contributing now. Make yourself known to the community for your contributions. Do general contributions, and try to contribute to an area related to your proposal. When the time comes to evaluate applications, you will be a known individual.

We're looking for candidates who can demonstrate that they can engage in the Wagtail project. We're here to help, but we can't watch you every step of the way. We need to see motivation from you. Your activities before the submissions process are the best way to demonstrate this.

## Your first contribution

- [ ] I have read and been through the [contributor checklist](#contributor-checklist)
- [ ] I have identified a good first task, either on my own, or one of the [good first issues](https://github.com/wagtail/wagtail/issues?q=is%3Aissue+is%3Aopen+sort%3Aupdated-desc+label%3A%22good+first+issue%22), or one tagged [Outreachy](https://github.com/wagtail/wagtail/issues?q=is%3Aissue+is%3Aopen+sort%3Aupdated-desc+label%3AOutreachy), or looking at [5 simple ways anyone can contribute to Wagtail](https://wagtail.org/blog/5-simple-ways-anyone-can-contribute-to-wagtail/)
- [ ] For GitHub issues – no one else is working on the issue I selected, so I’ve added a comment stating I’m working on it.
- [ ] I have read [Ten tasty ingredients for a delicious pull request](https://wagtail.org/blog/ten-tasty-ingredients-for-a-delicious-pull-request/)
- [ ] I have opened a pull request following those guidelines, mentioning my involvement with Outreachy, the name I want to be credited with in the release notes, and describing my changes (following the template provided by Wagtail)
- [ ] 🙌 Nice one! Share your pull request in our #outreachy channel on Slack so we can celebrate

## Projects

## Wagtail people

### Organisation coordinator

Thibaud Colas is the coordinator for Wagtail, overseeing mentors, contributors, and the point of contact for Outreachy.

To contact Thibaud, direct message them on [Slack](https://github.com/wagtail/wagtail/wiki/Slack) @Thibaud.

## Frequently asked questions

### Contributing

#### Is it okay for me to work on a task someone else has already claimed?

No. We want contributors to be able to take their time when they pick a task, and not feel stressed that someone else might decide to tackle the same issue.

#### If I’m unable to complete a task on time and someone else shows interest in it, will it be assigned to the person?

No. You can keep working on an issue as long as you want and we’ll keep it assigned to you. Though if you’re unable to complete a task you might prefer to work on something else.

#### I’m not as active as other participants. Do I have a chance?

We’re looking for candidates who can demonstrate their ability to engage with our community and contribute to their project, but quality beats quantity. Ask thoughtful questions, make realistic project plans, and go through a few meaningful contributions. That’s all we need.