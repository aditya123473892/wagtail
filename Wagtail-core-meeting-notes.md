## 03.08.2016

### Attendees
* [Matthew Westcott](https://github.com/gasman)
* [Karl Hobley](https://github.com/kaedroho)
* [Tom Dyson](https://github.com/tomdyson)
* [Mikalai Radchuk](https://github.com/m1kola)

### Discussions

#### 1.6rc1

The release candidate for Wagtail 1.6 was released on 1st of August, as planned.

Please try this version on your projects and report [an issue](https://github.com/torchbox/wagtail/issues if you find any problems.

#### Django 1.10 support

Django 1.10 was released on 1st of August. Wagtail 1.6 will have full support.

Please try Wagtail 1.6rc1 together with Django 1.10.

#### Roadmap

[Roadmap](https://trello.com/b/h9qi3N6V/wagtail-roadmap) had been updated, and now contains planned features for 1.7.

1.7rc1 is planned for October 1st.

#### wagtailmedusa (static site generation)

We need to decide what to do about wagtailmedusa (see [#2504](https://github.com/torchbox/wagtail/issues/2504) for details).

Ideas:
* Remove from the main repo and leave as is (django-medusa is also unmaintained)
* Replace with an alternative (probably based on django-bakery)
* Update django-medusa and wagtailmedusa to be compatible with Django 1.8+

### Actions

**Tom Dyson**
* Ask Josh re Draft progress (PR?) and React Explorer progress
* Write on reviewers needed, contact developers / agencies directly
* Seek funding for medusa replacement

**Matthew Westcott**
* Write short blog post on limiting explorer

**Karl Hobley**
* Write blog post on cropping


#### Uncompleted actions
**Matthew Westcott**
* Send initial email to wagtail-developers to get people back in the loop - everyone to announce things on there when appropriate
* Collect thoughts on RTE / Draft next steps

**Tom Dyson**
* Create a style guide for screenshots in docs
* Promote [wagtailsurveys](https://github.com/torchbox/wagtailsurveys) and [wagtailmedia](https://github.com/torchbox/wagtailmedia) modules
    * There is [the pull request](https://github.com/torchbox/wagtail/pull/2617) that backports this functionality into the Wagtail core (into `wagtailforms`)


## 06.07.2016

### Attendees
* [Matthew Westcott](https://github.com/gasman)
* [Karl Hobley](https://github.com/kaedroho)
* [Tom Dyson](https://github.com/tomdyson)
* [Mikalai Radchuk](https://github.com/m1kola)

### Actions

**Tom Dyson**
* Promote [wagtailsurveys](https://github.com/torchbox/wagtailsurveys) and [wagtailmedia](https://github.com/torchbox/wagtailmedia) modules
    * There is [the pull request](https://github.com/torchbox/wagtail/pull/2617) that backports this functionality into the Wagtail core (into `wagtailforms`)

#### Uncompleted actions
**Matthew Westcott**
* Send initial email to wagtail-developers to get people back in the loop - everyone to announce things on there when appropriate
* Collect thoughts on RTE / Draft next steps

**Tom Dyson**
* Create a style guide for screenshots in docs


## 29.06.2016

### Attendees
* [Matthew Westcott](https://github.com/gasman)
* [Karl Hobley](https://github.com/kaedroho)
* [Tom Dyson](https://github.com/tomdyson)
* [Mikalai Radchuk](https://github.com/m1kola)

### Discussions

#### Public meeting notes

Starting 29.06.2016 we will share meeting notes. We're starting them on this Wiki page, but we'll probably move them into a separate repo with pull requests for discussions (something like [reactjs/core-notes](https://github.com/reactjs/core-notes)).

#### Wagtail 1.6rc1 and 1.7rc1 release dates
* 1.6 - August 1st
* 1.7 - October 1st

#### Release process

* Wagtail now uses 8 week release cycles for feature releases.
    * 6 weeks - Development phase
    * 2 weeks - RC phase
* Create stable branch at the start of the RC phase
    * `master` branch can receive new features, to be released in the following cycle
*  Development of a new version can begin during RC phase (if there's nothing more important to deal with in the RC) and won't count towards the 8 weeks
* RCs always come on the 1st of the even months

#### Draft.js
* [Demo](https://youtu.be/fFySTY4hPaw) of [Josh Barr](https://github.com/JoshBarr)'s work on Draft.js integration
* We need to collect thoughts on RTE / Draft.js next steps

### Actions
**Matthew Westcott**
* Send initial email to wagtail-developers to get people back in the loop - everyone to announce things on there when appropriate
* Collect thoughts on RTE / Draft next steps

**Tom Dyson**
* Create a style guide for screenshots in docs
* Move roadmap to Trello

**Mikalai Radchuk**
* Create meeting notes on Github wiki