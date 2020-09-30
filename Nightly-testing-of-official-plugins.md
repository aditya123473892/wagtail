We maintain a number of official plugins for Wagtail in separate repositories. But a disadvantage of them being in separate repos, is we won't be alerted about any incompatibilities with Wagtail core until a release of Wagtail is made.

To remedy this, we recommend configuring the CI server to test plugins against Wagtail's master branch on a nightly basis and report any failures to the #nightly-build-failures Slack channel.

This document explains how to set this up with Circle CI. These instructions might be adaptable to other CI providers but this hasn't been tested.

1) Go into the CircleCI project settings and add the Slack webhook URL into the `SLACK_WEBHOOK_URL` environment variable.

    You can get this webhook from another project on Circle CI that has this configuration (such as `wagtail-localize`). Or ask Karl (@kaedroho).

2) Add `.circleci/report_nightly_build_failure.py` with the following contents:

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

    else:
        print("Unable to report to #nightly-build-failures slack channel because SLACK_WEBHOOK_URL is not set")
    ```

3) Add a CircleCI Job that runs the tests against Wagtail master and schedule it to run nightly

    ```yaml
    jobs:
      # ... after your other jobs

      # Add this bit
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

        # Add this bit
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