Timeline of development priorities for the Wagtail core team. Please note that these are provided as a general guide for project planning, and should not be regarded as a commitment to deliver features by a given date. Wagtail development is highly dependent on outside contributions and sponsorship, and plans are liable to change as a result.

* ### Nested collections - Q4 2020 ✅
  [RFC 48](https://github.com/wagtail/rfcs/pull/48) - completed in Wagtail 2.11.
* ### Internationalisation of Wagtail content - Q1 2021 ✅
  [RFC 54](https://github.com/wagtail/rfcs/blob/master/text/054-internationalisation.md) - initial work completed in Wagtail 2.11 and [wagtail-localize](https://github.com/wagtail/wagtail-localize), with further work being tracked in [#6378](https://github.com/wagtail/wagtail/issues/6378).
* ### Streamfield UI and performance improvements - Q1 2021 ✅
  Feature parity with [react-streamfield](https://github.com/wagtail/wagtail-react-streamfield), but with an upgrade path for Python-defined blocks and a JavaScript extension API - see [Telepath - the next evolution of StreamField](https://wagtail.io/blog/telepath/)
* ### Commenting in the page edit view - Q1 2021 ✅
  [RFC 50](https://github.com/wagtail/rfcs/pull/50)
* ### Multi-tenancy - Q2 2021
  Ability to configure the admin so that editors with permission for one site are fully isolated from others - [#7521](https://github.com/wagtail/wagtail/discussions/7521)
* ### Drop IE support - Q3 2021  ✅
  [Support dropped in Wagtail 2.15](https://docs.wagtail.io/en/stable/editor_manual/browser_issues.html#ie11).
* ### Object usage reporting - Q4 2022   ✅
  "This image is used on the following pages..." [#4702](https://github.com/wagtail/wagtail/issues/4702) / [#4481](https://github.com/wagtail/wagtail/issues/4481) / [#9279](https://github.com/wagtail/wagtail/pull/9279)
* ### Page content analysis - ~Q1 2021~ 2022
  Support within the page editor for spellchecking, tone guidance etc - [RFC 60](https://github.com/wagtail/rfcs/pull/60)
* ### Accessibility - ~2021~ 2022 🚧
  Aiming for full WCAG2.1 AA compliance across the Wagtail admin. Tracked in [WCAG2.1 AA compliance](https://github.com/orgs/wagtail/projects/9/views/1) and [#4199](https://github.com/wagtail/wagtail/issues/4199).