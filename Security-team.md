**Please follow [Wagtail’s security policy](https://github.com/wagtail/wagtail/security/policy) when contacting this team**. For security discussions that aren’t related to vulnerabilities, find us in [#security](https://app.slack.com/client/T0K33F93J/C015Y7T4MQR) on the [Wagtail Slack](https://github.com/wagtail/wagtail/wiki/Slack).

## Team charter

The security team’s membership is restricted, as we discuss sensitive issues such as [0-day vulnerabilities](https://en.wikipedia.org/wiki/Zero-day_(computing)) in Wagtail. Membership is on invitation only, with an indefinite term revokable at any point.

We meet as-needed only. The team organises the response to security vulnerability reports in private channels according to [Wagtail’s security policy (SECURITY.md)](https://github.com/wagtail/wagtail/security/policy), and uses [#security](https://app.slack.com/client/T0K33F93J/C015Y7T4MQR) for discussions which aren’t deemed sensitive.

## Team members

Current members:

- Coen van der Kamp ([@allcaps](https://github.com/allcaps)), UTC + 1 or 2, since January 2022
- Matt Westcott ([@gasman](https://github.com/gasman)), UTC + 0 or 1, since January 2022
- Neal Todd ([@nealtodd](https://github.com/nealtodd)), UTC + 0 or 1, since January 2022
- Thibaud Colas ([@thibaudcolas](https://github.com/thibaudcolas)), UTC + 0 or 1, since January 2022
- Tom Dyson ([@tomdyson](https://github.com/tomdyson)), UTC + 0 or 1, since January 2022
- Jake Howard ([@RealOrangeOne](https://github.com/RealOrangeOne)), UTC + 0 or 1, since March 2023
- Dan Braghiș ([@zerolab](https://github.com/zerolab)), UTC + 01 or 1, since October 2023

Past members:

- Karl Hobley ([@kaedroho](https://github.com/kaedroho)), January 2022 – November 2022

## Vulnerability report response guide

Here are quick guidelines on responding to vulnerability reports. This guide is mostly aimed at team members to help us deal with incidents professionally, and reduce the risk of mistakes. This is especially important because security risks are stressful and can involve significant time pressure.

### Where to start

We receive a lot of spam. This only covers legitimate reports.

1. Thank the reporter for their time investigating the issue, and for reporting it to us. Clarify any potential doubts about the process.
2. Establish a clear understanding of:
  - Which component exactly is vulnerable
  - What the impact is (loss of confidentiality, availability, integrity – see [NIST CVSS metrics](https://nvd.nist.gov/vuln-metrics/cvss/v3-calculator)).
  - How exploitable the vulnerability is for a given vulnerable Wagtail site. NIST’s [CVSS exploitability metrics](https://nvd.nist.gov/vuln-metrics/cvss/v3-calculator) can help frame this.
  - What severity the vulnerability is according to [Django’s security policy](https://docs.djangoproject.com/en/dev/internals/security/#how-django-discloses-security-issues)
  - How many sites this is likely to affect as a proportion, based on which component / configuration is vulnerable.
3. Discuss this understanding with other team members.
4. Attempt to exploit the vulnerability yourself to confirm your understanding.

Based on this, you can then decide to:

- Treat the report as a bona fide vulnerability: security advisory, CVE, patch releases.
- Treat the report as a security issue which isn’t a definite vulnerability: public GitHub issues and pull requests.
- Do nothing, if the vulnerability isn’t confirmed, or is outside of Wagtail’s remit.

Share your plans with the initial reporter, and proceed.

### Confirmed vulnerabilities

Once there is team consensus to treat the report as a vulnerability, you can:

1. Create an advisory in GitHub, filling in all relevant details. Make sure to grant access to `@wagtail/security`.
2. Work on the patch in the advisory’s attached private fork.
3. Request a CVE from GitHub once the vulnerability is described clearly enough.
4. Ultimately publish the advisory, merging the patch.