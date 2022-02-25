> 🚧 Our application for 2022 is pending approval.

Links: 
* [#gsoc on Slack, open to ask us anything](https://github.com/wagtail/wagtail/wiki/Slack)
* [Documentation](http://docs.wagtail.org/)
* [Wagtail Developer Page](https://wagtail.org/developers/)
* [Wagtail Blog](https://wagtail.org/blog/)
* Wiki: [Google Summer of Code 2021](https://github.com/wagtail/wagtail/wiki/Google-Summer-of-Code-2021)

# About Wagtail

Wagtail is a popular content management system. It's built on Python, by an active and engaged open source community, which has grown rapidly since Wagtail's release in 2014. Wagtail is available in over 40 languages, and used by some of the world's best-known organizations, including NASA, Google, Mozilla, MIT, and the UK's National Health Service, as well as museums, universities, non-profits, governments, banks, studios, restaurants, startups and bloggers around the world.

Like Python and Django, the technologies which underpin it, Wagtail is known for its welcoming community. We're keen to increase the geographic and cultural diversity of our core team, who are currently spread across Europe, Africa and North America. We seek to offer friendly support on Slack, StackOverflow and Github, and we encourage the community to meet in real life where possible, with recent sprints and conferences held in South Africa, Iceland, the USA, Belarus and the UK.

Wagtail has moved fast in the last few years, with particular focus on the editor experience, the refinement of APIs for headless CMS architectures and accessibility. We have adopted a regular quarterly release cycle, which aims to minimise upgrade time while providing compelling new features and improvements with each point releases. We're seeking help to deliver some of our more ambitious plans, many of which are expressed as [RFCs]. We're also open to your ideas for making Wagtail the best open source CMS for the 2020s!

# Participants

Applicants should have a basic familiarity with Python, Django and Git. They should have completed the initial Wagtail Tutorial and have created a developer environment for working on Wagtail itself. They should join the [Wagtail Slack](https://github.com/wagtail/wagtail/wiki/Slack) and introduce themselves on the #gsoc channel. They are welcome to seek advice from mentors on suitable projects and topics, which should then be submitted to the project issue list with our [Google Summer of Code issue template](https://github.com/wagtail/wagtail/issues/new?template=GSOC.md).

Write a motivation and submit your CV. Tell us about your experience with Python/Django/Wagtail

---

# Project ideas

Most RFCs are suitable GSoC projects https://github.com/wagtail/rfcs/pulls?q=is%3Apr+label%3AActive+



## RTL support for Wagtail

### Summary 

Wagtail’s administration interface currently has poor support for right-to-left languages, such as Arabic and Hebrew. We have been wanting to fix this for a while ([#1240](https://github.com/wagtail/wagtail/issues/1240), and now have a great opportunity to do so with [CSS logical properties](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Logical_Properties).

### Expected outcomes

The Wagtail UI supports Arabic, Hebrew, and other right-to-left languages.

### Implementation

We want to refactor Wagtail’s stylesheets to use CSS logical properties, Flexbox, and Grid layout, so the styles can be written agnostic to the writing direction of the language – browsers would then automatically display the correct end-user layout based on the target language.

### Skills

HTML and CSS. Bonus: user experience, visual design, Django.

### Mentors

Thibaud Colas https://github.com/thibaudcolas
Coen van der Kamp https://github.com/allcaps

We will supply a primary mentor and at least two secondary mentors to support the participant.

### Size

Expected size of project approximately 350 hours.

### Difficulty rating

Medium

## Toolkit for StreamField data migrations in Wagtail

### Summary 

Wagtail provides a field type for semi-freeform data, StreamField, which uses a JSON representation to store "blocks" of data. While flexible for editors, a pain point for developers has been writing data migrations when changes are made to the block definitions, due to its nested format. This project aims to provide a set of reusable utilities to allow Wagtail implementors to easily generate data migrations for changes to StreamField block structure. It could be extended to cover another common pain point when updating stored data: dealing with live and draft revisions.

### Expected outcomes

Create a package which provides utilities for easily updating StreamFields within data migrations.

### Implementation

- Investigate the existing problems when making a change to StreamField structure
- Set up a new Python package
- Create utilities for recursing through different types of StreamField structure, recognising blocks, and making changes
- Create a set of functions to make appropriate changes for the most common data migration use cases (eg adding a new block with required value, changing the type of a block, or moving a block to within a StructBlock)
- Add documentation for the new library
- Extension: add utilities for updating both the live and draft versions of pages

### Skills

Django, Python.

### Mentors

- Jacob Topp-Mugglestone https://github.com/jacobtoppm
- Karl Hobley https://github.com/kaedroho

We will supply a primary mentor and at least two secondary mentors to support the participant.

### Size

175 hours (basic version), but could be extended to deal with more migration types, and to make dealing with live and draft revisions easier.

### Difficulty

Medium

### Create and select related content

### Summary
Django has a 'search loop', 'add plus', and 'modal' to search, select and create related objects. This without navigating away from the current form.

Search loop:
https://docs.djangoproject.com/en/4.0/ref/contrib/admin/#django.contrib.admin.ModelAdmin.raw_id_fields

Add plus:
https://docs.djangoproject.com/en/4.0/ref/contrib/admin/#django.contrib.admin.ModelAdmin.fieldsets

### Expected outcomes

Have the Django 'add plus', 'search loop', and 'modal/popup' pattern in Wagtail.

### Skills

- Django
- Wagtail
- HTML/CSS/JS

### Mentors

* Coen van der Kamp https://github.com/allcaps
* Dan Braghis https://github.com/zerolab

### Size

Expected size of project 175 hours.

### Difficulty rating

Medium

## Make Wagtail editor guide a stand-alone project

### Summary

- The goal is to [pull out the existing editor's guide](https://github.com/wagtail/wagtail/discussions/7824) from static documentation to a stand-alone project that can be translated, built upon and even used to generate custom guides for more complex usages of Wagtail.
- The current guide is part of the existing Wagtail technical documentation - [Using Wagtail: an Editor's guide](https://docs.wagtail.org/en/stable/editor_manual/index.html).
- The audience of the main technical documentation (those who are building with Wagtail) is very different to the audience of the editor's guide (those who are using the editor to edit content, manage permissions, non-technical users).

### Expected outcomes

A dedicated User Guide website with content editors as targeted audience. 

### Implementation

- Pull out the existing RST/MD files into a stand-alone project, starting with the [Wagtail project cookiecutter](https://github.com/wagtail/cookiecutter-wagtail-package)
- Break up the existing content and screenshots into Django views and URLs so that the content can be used in translation tools such as transifex, the output should be a static HTML/CSS/JS bundle. This could use some of the Wagtail primitives for page editing but it does not have to.
- From here, improve the guide 
- target specific audiences
- make translatable
- make it version-able (so that older versions of the Wagtail editor's can be available)
- potentially rework content to be less nested or easier to read through, see [Firefox's How do I Wagtail](https://foundation.mozilla.org/en/docs/how-do-i-wagtail/) for inspiration
- Make the guide maintainable 
- automatic screenshots
- accept contributions from non-technical users
- set up a nightly CI that runs against Wagtail master
- add feedback option (measure happiness)
- Make it customisable
- allow for the project to be imported into existing Wagtail projects and document how it can be built, customised and run (automatic screenshots) against those custom Wagtail installations
- allow for additional pages/header/footer/feedback to be integrated

### Skills

* Django
* Wagtail
* Translations - speaking a second language would be helpful
* Static site building (with Django or Node tooling)

### Mentors

* Coen van der Kamp https://github.com/allcaps
* Dan Braghis https://github.com/zerolab

We will supply a primary mentor and at least two secondary mentors to support the participant.

### Size

Expected size of project 175 hours.

### Difficulty rating

Medium 

## Apply new page editor style to all views 

### Summary

Wagtail is currently redesigning the page editor. But has many other views that are out of scope. However, those out of scope views should get the same styling and use the same components and techniques.

### Expected outcomes

Consistent UI throughout the whole of Wagtail.

### Skills

- Django
- Wagtail
- HTML/JS/CSS

### Mentors

TBD, We are committed to supply a primary mentor and at least two secondary mentors to support the participant.

### Size

Expected size of project approximately 350 hours.

### Difficulty rating

Medium 

## Change page type

### Summary

Make it possible for a content editor to change the content type of a page.

This is an often requested feature, but is technically hard to implement. 

### Expected outcomes

A user interface and backend logic to allow switching page type.

### Skills

- Django
- Wagtail
- Django Treebeard
- Some HTML/CSS/JS

### Mentors

- Scott Cranfill https://github.com/Scotchester
- Coen van der Kamp https://github.com/allcaps

### Size

Expected size of project 175 hour

### Difficulty rating

Hard

---


# 2021 GSoC projects (done)
<details>
<summary>Click to expand</summary>

## Wagtail Live
### Summary

High speed content delivery. A live blog from chat applications to a Wagtail site.

Content editors will enter their content into Slack (or any other messaging application) and this will live update the Wagtail live-blog page.

- **Live example**: [https://www.theguardian.com/politics/live/2020/feb/05/pmqs-boris-johnson-corbyn-bbc-could-end-up-as-defunct-as-blockbuster-unless-it-adapts-to-digital-era-says-culture-secretary-nicky-morgan-live-news](https://www.theguardian.com/politics/live/2020/feb/05/pmqs-boris-johnson-corbyn-bbc-could-end-up-as-defunct-as-blockbuster-unless-it-adapts-to-digital-era-says-culture-secretary-nicky-morgan-live-news) 
- **POC (Proof Of Concept)**: [https://github.com/allcaps/wagtail-live](https://github.com/allcaps/wagtail-live)
- **Video**: [https://www.youtube.com/watch?v=JL-MlNl2Buc&feature=youtu.be](https://www.youtube.com/watch?v=JL-MlNl2Buc&feature=youtu.be)

## Implementation
- Input a chat application / third party product
- Output on a live blog page
- Message server (Django Channels)

## Skills
- Python, Django, Wagtail
- Message server
- Consume Chat API’s

## Mentors
Tom Dyson and Coen van der Kamp

## Aims
To produce a Wagtail package to deliver content fast

## New database search backend

### Summary 

A new search backend that makes use of the search features of the current database. With support for SQLite and PostgreSQL search features.

This will replace the existing database and PostgreSQL search backends in Wagtail.

### Implementation

- Create a search backend that creates a separate database table for each search index (pages, images, and documents). These tables should make use of whatever search specific types and indexes are available in the currently used database engine
- Implement the search query interface to allow retrieving data from these search backends
- (optional) Create a test suite that tests the quality of the results that each search backend returns

### Skills

- Databases
- Search / PostgreSQL FTS / SQLite FTS / MySQL FTS

### Mentors

Karl Hobley

### Aims

- Improve the quality of results for the existing PostgreSQL search backend
- Add support for SQLite and MySQL search into Wagtail core

## Bulk admin actions
### Summary
Enable bulk actions in a variety of Wagtail administrative interfaces

### Implementation
- Allow performing common tasks (such as delete, publish etc) in bulk for Wagtail Pages, Images and Documents
- Provide an extension mechanism that will enable developers to provide custom actions

### Skills
- Django, Python and front-end

### Mentors
Karl Hobley

### Aims

To enhance the Wagtail administrative interface  

</details>

# Project ideas template
<details>
<summary>Click to expand</summary>

## Idea title

### Summary 

More detailed description of the project (2-5+ sentences)

### Expected outcomes

TBS

### Implementation

Optional section, technical hints.

### Skills

TBD required/preferred 

### Mentors

TBD

### Size

Expected size of project (175 or 350 hour)

### Difficulty rating

Easy, Medium or Hard 

</details>
