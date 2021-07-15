# Wagtail performance team

Find us in [#performance-working-group on Slack](https://app.slack.com/client/T0K33F93J/C023WG6FB7C).

## Team charter

## Team members

Current members:

- Karl Hobley (@kaedroho), UK
- Matthew Westcott (@gasman), UK
- Jake Howard (@RealOrangeOne), UK
- Tom Usher (@tomusher), UK
- Jacob Topp-Mugglestone (@jacobtoppm), UK

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
