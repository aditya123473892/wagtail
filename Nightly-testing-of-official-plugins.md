We maintain a number of official plugins for Wagtail. One disadvantage of them being separate from Wagtail though is we usually won't know about any incompatibilities until a release of Wagtail is made.

This document explains how to set up nightly builds of an official Wagtail plugin against Wagtail master and report any errors to the #nightly-build-failures channel on slack.

In order to set this up, your site should use Circle CI. These instructions might be adaptable to other CI providers but this hasn't been tested.

1) Add `.circleci/report_nightly_build_failure.py` with the following contents:

```python
"""
Called by CircleCI when the nightly build fails.

This reports an error to the #nightly-build-failures Slack channel.
"""
import os
import requests

if 'SLACK_WEBHOOK_URL' in os.environ:
    print("Reporting to #nightly-build-failures slack channel")
    response = requests.post(os.environ['SLACK_WEBHOOK_URL'], json={
        "text": "A Nightly build failed. See " + os.environ['CIRCLE_BUILD_URL'],
    })

    print("Slack responded with:", response)
    print(response.content)

else:
    print("Unable to report to #nightly-build-failures slack channel because SLACK_WEBHOOK_URL is not set")
```

2) Add a CircleCI Job that runs the tests against Wagtail master and schedule it to run nightly

```yaml
jobs:
  # ... after your other jobs


  nightly-wagtail-test:
    docker:
      - image: circleci/python:3.8
    steps:
      - checkout
      - run: git clone git@github.com:wagtail/wagtail.git

      # Install your plugin with its testing requirements. Update this line
      - run: pip install -e .[testing]
      # Replace Wagtail with the one checked out from git
      - run: pip install ./wagtail

      # Run the tests. Update this line too
      - run: python testmanage.py test

      - run:
          when: on_fail
          command: python ./.circleci/report_nightly_build_failure.py


workflows:
    version: 2
    test:
      jobs:
        # your other jobs

    nightly:
      jobs:
        - nightly-wagtail-test
      triggers:
        - schedule:
            cron: "0 0 * * *"
            filters:
              branches:
                only:
                  - master
```

3) Go into the CircleCI project settings and add the Slack webhook URL into the `SLACK_WEBHOOK_URL` environment variable.

You can get this webhook from another project on Circle CI that has this configuration (such as `wagtail-localize`). Or ask Karl (@kaedroho).