# Wagtail performance team

Find us in [#performance-working-group on Slack](https://app.slack.com/client/T0K33F93J/C023WG6FB7C).

## Team charter

The team’s membership is open to all, introduce yourself in [#performance-working-group](https://app.slack.com/client/T0K33F93J/C023WG6FB7C). on Slack if you’re interested in joining.

We meet every two weeks to discuss everyone’s recent progress and next steps. Meeting notes and actions are public for future and past meetings. Meetings happen on Zoom.

In-between meetings, we collaborate via Slack, using the elf in [#performance-working-group](https://app.slack.com/client/T0K33F93J/C023WG6FB7C channel as an open forum, and use GitHub to keep track of actions, and collaborate on specific issues & pull requests.

## Team members

Current members:

- Karl Hobley (@kaedroho), UK
- Matthew Westcott (@gasman), UK
- Jake Howard (@RealOrangeOne), UK
- Tom Usher (@tomusher), UK
- Jacob Topp-Mugglestone (@jacobtoppm), UK
- Dan Braghis (@zerolab), UK

## 2021-07-29

Attendees: Karl, Jacob, Tom, Matthew, Jake

### Actions

- Dan will look into Drupal approach for background tasks
- Karl speak to Tom D about getting a box to benchmarks
- Jacob will look at writing some initial benchmarks for next meeting
- Karl to put together a list of areas on Wagtail we could optimise with this

### Notes

#### Search benchmarking

- Aldan Creo interested in working on benchmarking search and teaming up with someone else. Tom U happy to tag up

#### Bulk actions

- can be potentially expensive, e.g. saving a page → reindexing in the same request. Jake suggested we’d move that away. Jake has been thinking and researching potential avenues (and dependencies to core)
- Plenty of libraries out there. The issue is around batching up tasks (e.g. 5 people save pages at the same time.) While ES could handle that, no libraries support that (or that Jake could find). Either we give on that approach or write something ourselves, but is should be non-Wagtail specific. The implementation detail — ♾️ number of queues. Questions around workers. Lots of it relates to infrastructure. We need to make it work without queues, so it is not a huge breaking change
- Q: how deep a rabbit hole should this be?
- Q: when talking about batching what are the issues? we should consider a batch everything that happens in the request (e.g. moving a page with 100 children). Note on treebeard operations not doing in bulk vs logging.
- We need separation of what a task is.
- Noticing when we can bundle tasks is independent of sync/async
- Note: anything that provides immediate user feedback should happen sync, ancillary bits can happen async
- Have we looked at non-django projects doing this? Drupal has a built-in queueing system
- How about offloading ancillary things to a background thread?
  - It’s a dirty hack
  - can have hosting ramifications, no easy way to monitor
- Next steps
  - Bundling separate queue tasks may not be a big problem
  - Look at other systems and draw some learnings
  - Put together a list of areas on Wagtail we could optimise with this

#### Regression testing

- 1st thought - env site to run various perf tools, but you can’t rely on consistency
- other CMSes don’t seem to do so. Shout if you know otherwise
- djangobench → airspeed velocity (asv) — may be useful for us to use on a separate server, rather than CI
- Links
  - https://github.com/django/djangobench
   - Notable discussion https://github.com/django/djangobench/issues/38
   - https://github.com/airspeed-velocity/asv 
   - https://pythonspeed.com/articles/consistent-benchmarking-in-ci/ 
- How would a benchmark suite for Wagtail Look like?
  - Been testing using Django test environment and calling URLs. Seems workable
  - We would need to come up with a reasonably large dataset
  - And we need to do a Javascript test somehow
- Next steps
  - Unsure about where to host the benchmark system yet
     - Needs to run a 30 minute task once a week, probably not expensive

## 2021-07-15

Attendees: Karl, Jacob, Tom, Matthew, Jake

### Actions

- Karl to speak to Thibaud about whether we should follow 6-month membership
- Matthew to tag performance issues
- Karl to set up zoom call. Make sure it allows people to join
- Jake to look into options for scheduling bulk actions (Celery, django-lightweight-queue etc)
- Tom will have a look into options for regression testing in CI
- Jacob will look at writing some initial benchmarks for the meeting after next (got a lot on in next two weeks)
- Karl add a Github team

### Notes

#### Team charter

- Copy accessibility team
- All happy with a 30-minute meeting on Thursdays at 2 PM every other week
- In terms of membership, we think people should join and leave when they like instead of 6-month memberships. Karl will check with Thibaud if this is a good idea
- We won't make people volunteer for actions

#### Managing performance issues on GitHub

- Shall we use a GitHub project or a label?
- Agreed on using the existing "Performance" label
- Currently, only one issue uses the "Performance" label. Matthew will look for other performance issues as an action

#### Performance regression monitoring

- Could we automatically monitor and record performance somewhere, so we can check for regressions?
- Rust does this: https://arewefastyet.com/win10/benchmarks/overview?numDays=60
- What should we measure?
    - Timing the whole test suite
        - Would get slower as we add tests so not good long term
        - Individual tests use only small amounts of data so the tests might not pick up scaling issues
        - Having a single chart makes it difficult to see the impact of multiple performance issues
    - Rust has a separate test suite designed for benchmarks. We could use something like ``pytest-benchmark``. Or we could make use of Wagtail’s ``runtests.py` --bench``
    - Set up bakerydemo on Heroku and run Locust tests against it
- Issues with testing on CI
    - Making it reliable would be tricky as noisy neighbours can make a difference of a whole minute between test runs
    - Another issue with CI s that we don’t control the platform so hardware changes might add blips to our charts
- Should we measure on each day/commit/release?
- TU to look into options for regression testing on CI

#### Other potential areas for performance improvements

- Images
- Caching
- Things that affect large pages (such the StreamField issues solved by Telepath)
- Tracking the template size being outputted
- JS Performance — Selenium tests?
- Bulk actions

#### Performance of bulk actions

- Some actions could create many logs, emails or separate requests for indexing in Elasticsearch or purging pages from a frontend cache. But these requests usually happen separately
- Could we detect when combinable actions are happening in the same request and automatically run them in bulk?
    - We are doing this for audit logging
- Move these bulk actions into a background worker?
    - It does require people to set up their infrastructure in a specific way
    - Could we abstract over async backends (such as ``celery``, ``django-rq``), and one of those options is to do it synchronously in the request
    - Could queue tasks in the database and run with cron
    - We could use separate queues for each type of thing to allow bulk running of async actions (eg a queue for ES index updates, and one for email)
    - Functionality could be exposed for users to use on their own sites
- Using Celery instead?
    - Does it support running synchronous actions without a worker?
    - Might be an issue for people who already use a different package, since they would need a separate worker just for Wagtail
- What about just a thin wrapper on top of ``celery``/``django-rq``/``synchronous``?
    - Doesn’t appear to exist
    - Maybe we could write one? (as long as it doesn’t end up as rewriting celery!)
    - Jake will take a look into  ``django-lightweight-queues``. It has a synchronous mode too!
- We should be careful when doing benchmarking bulk actions that we don’t forget to count background queries too
- We should make sure that moving things into the background doesn’t make things worse for the overall UX
