Links: 
* [#gsoc on Slack, open to ask us anything](https://app.slack.com/client/T0K33F93J/CB7L6L5S6)
* [Documentation](http://docs.wagtail.io/?_ga=2.187979182.70138337.1613670607-1853036869.1613138867)
* [Wagtail Developer Page](https://wagtail.io/developers/)
* [Wagtail Blog](https://wagtail.io/blog/)

## About Wagtail

Wagtail is a popular content management system. It's built on Python, by an active and engaged open source community, which has grown rapidly since Wagtail's release in 2014. Wagtail is available in over 40 languages, and used by some of the world's best-known organizations, including NASA, Google, Mozilla, MIT, and the UK's National Health Service, as well as museums, universities, non-profits, governments, banks, studios, restaurants, startups and bloggers around the world.

Like Python and Django, the technologies which underpin it, Wagtail is known for its welcoming community. We're keen to increase the geographic and cultural diversity of our core team, who are currently spread across Europe, Africa and North America. We seek to offer friendly support on Slack, StackOverflow and Github, and we encourage the community to meet in real life where possible, with recent sprints and conferences held in South Africa, Iceland, the USA, Belarus and the UK.

Wagtail has moved fast in the last few years, with particular focus on the editor experience, the refinement of APIs for headless CMS architectures and accessibility. We have adopted a regular quarterly release cycle, which aims to minimise upgrade time while providing compelling new features and improvements with each point releases. We're seeking help to deliver some of our more ambitious plans, many of which are expressed as [RFCs]. We're also open to your ideas for making Wagtail the best open source CMS for the 2020s!

## Students

Applicants should have a basic familiarity with Python, Django and Git. They should have completed the initial Wagtail Tutorial and have created a developer environment for working on Wagtail itself. They should join the [Wagtail Slack](https://github.com/wagtail/wagtail/wiki/Slack) and introduce themselves on the #gsoc channel. They are welcome to seek advice from mentors on suitable projects and topics, which should then be submitted to the project issue list with our [Google Summer of Code issue template](https://github.com/wagtail/wagtail/issues/new?template=GSOC.md).

Write a motivation and submit your CV. Tell us about your experience with Python/Django/Wagtail

## Project ideas

### Wagtail Live
#### Summary

High speed content delivery. A live blog from chat applications to a Wagtail site.

Content editors will enter their content into Slack (or any other messaging application) and this will live update the Wagtail live-blog page.

- **Live example**: [https://www.theguardian.com/politics/live/2020/feb/05/pmqs-boris-johnson-corbyn-bbc-could-end-up-as-defunct-as-blockbuster-unless-it-adapts-to-digital-era-says-culture-secretary-nicky-morgan-live-news](https://www.theguardian.com/politics/live/2020/feb/05/pmqs-boris-johnson-corbyn-bbc-could-end-up-as-defunct-as-blockbuster-unless-it-adapts-to-digital-era-says-culture-secretary-nicky-morgan-live-news) 
- **POC (Proof Of Concept)**: [https://github.com/allcaps/wagtail-live](https://github.com/allcaps/wagtail-live)
- **Video**: [https://www.youtube.com/watch?v=JL-MlNl2Buc&feature=youtu.be](https://www.youtube.com/watch?v=JL-MlNl2Buc&feature=youtu.be)

**Implementation**
- Input a chat application / third party product
- Output on a live blog page
- Message server (Django Channels)

**Skills**
- Python, Django, Wagtail
- Message server
- Consume Chat API’s

**Mentors**
Tom Dyson and Coen van der Kamp

**Aims**
To produce a Wagtail package to deliver content fast

----------------------------------

### Bulk admin actions
#### Summary
Enable bulk actions in a variety of Wagtail administrative interfaces

**Implementation**
- Allow performing common tasks (such as delete, publish etc) in bulk for Wagtail Pages, Images and Documents
- Provide an extension mechanism that will enable developers to provide custom actions

**Skills**
- Django, Python and front-end

**Mentors**
Karl Hobley

**Aims**

To enhance the Wagtail administrative interface

-------------------------------------


### Enhanced file manager
#### Summary 
TBD

**Implementation**

TBD

**Skills**

TBD

**Mentors**

TBD

**Aims**

TBD

-------------------------------------