We maintain a number of official plugins for Wagtail in separate repositories. But a disadvantage of them being in separate repos is we won't be alerted about any incompatibilities with Wagtail core until a release of Wagtail is made.

To remedy this, we recommend configuring the CI server to test plugins against Wagtail's main branch on a nightly basis and report any failures to the #nightly-build-failures Slack channel.

This document explains how to set this up with Circle CI and Github Actions. These instructions might be adaptable to other CI providers but this hasn't been tested.

## CircleCI

1) Go into the CircleCI project settings and add the Slack webhook URL into the `SLACK_WEBHOOK_URL` environment variable.

    You can get this webhook from another project on Circle CI that has this configuration (such as `wagtail-localize`). Or ask Dan (@zerolab) or Matt (@mattwestcott).

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

3) Add a CircleCI Job that runs the tests against Wagtail `main` and schedule it to run nightly

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
                - main
```

## GitHub Actions

(Credit to @zerolab who implemented this first on [wagtailmedia](https://github.com/torchbox/wagtailmedia/))

1) Go into the Gitlab Actions project settings and add the Slack webhook URL into the `SLACK_WEBHOOK_URL` environment variable.

    You can get this webhook from another project on Circle CI that has this configuration (such as `wagtail-localize`). Or ask Dan (@zerolab) or Matt (@mattwestcott).

2) Add `.github/report_nightly_build_failure.py` with the following contents:

```python
"""
Called by GitHub Actions when the nightly build fails.
This reports an error to the #nightly-build-failures Slack channel.
"""
import os
import requests

if "SLACK_WEBHOOK_URL" in os.environ:
    # https://docs.github.com/en/free-pro-team@latest/actions/reference/environment-variables#default-environment-variables
    repository = os.environ["GITHUB_REPOSITORY"]
    run_id = os.environ["GITHUB_RUN_ID"]
    url = f"https://github.com/{repository}/actions/runs/{run_id}"

    print("Reporting to #nightly-build-failures slack channel")
    response = requests.post(
        os.environ["SLACK_WEBHOOK_URL"],
        json={
            "text": f"A Nightly build failed. See {url}",
        },
    )

    print(f"Slack responded with: {response}")

else:
    print(
        "Unable to report to #nightly-build-failures slack channel because SLACK_WEBHOOK_URL is not set"
    )
```

3) Add `.github/workflows/nightly-tests.yml ` with the following contents (replace ``torchbox/wagtailmedia`` on line 13 with your repository name)

```yaml
name: Nightly Wagtail test

on:
  schedule:
    - cron: "0 0 * * *"

  workflow_dispatch:

jobs:
  nightly-test:
    # Cannot check the existence of secrets, so limiting to repository name to prevent all forks to run nightly.
    # See: https://github.com/actions/runner/issues/520
    if: ${{ github.repository == 'torchbox/wagtailmedia' }}
    runs-on: ubuntu-latest

    services:
      postgres:
        image: postgres:10.8
        ports:
          - 5432:5432
        options: --health-cmd pg_isready --health-interval 10s --health-timeout 5s --health-retries 5

    steps:
      - uses: actions/checkout@v2
      - name: Set up Python 3.9
        uses: actions/setup-python@v2
        with:
          python-version: 3.9
      - name: Install dependencies
        run: |
          python -m pip install --upgrade pip
          pip install "psycopg2>=2.6"
          pip install "git+https://github.com/wagtail/wagtail.git@main#egg=wagtail"
          pip install -e .[testing]
      - name: Test
        id: test
        continue-on-error: true
        run: |
          ./runtests.py
        env:
          DATABASE_ENGINE: django.db.backends.postgresql
          DATABASE_HOST: localhost
          DATABASE_USER: postgres
          DATABASE_PASS: postgres

      - name: Send Slack notification on failure
        if: steps.test.outcome == 'failure'
        run: |
          python .github/report_nightly_build_failure.py
        env:
          SLACK_WEBHOOK_URL: ${{ secrets.SLACK_WEBHOOK_URL }}
```
