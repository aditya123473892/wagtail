New feature releases of Wagtail are released every three months. These releases provide new features, improvements and bugfixes, and are marked by incrementing the second part of the version number (for example, 2.6 to 2.7).

The actual release date will be on the closest working day (in the UK), and depend on the successful testing of release candidates, which are made available at least three weeks ahead of the planned final release date.

Additionally, patch releases will be issued as needed, to fix bugs and security issues. These are marked by incrementing the third part of the version number (for example, 2.6 to 2.6.1). Wherever possible, these releases will remain fully backwards compatible with the corresponding feature and not introduce any breaking changes.

A feature release will usually stop receiving patch release updates when the next feature release comes out. However, selected feature releases are designated as Long Term Support (LTS) releases, and will continue to receive maintenance updates to address any security and data-loss related issues that arise. Typically, a Long Term Support release will happen once every four feature releases and receive updates for five feature releases, giving a support period of fifteen months with a three month overlap.

Also, Long Term Support releases will ensure compatibility with at least one [Django Long Term Support release](https://www.djangoproject.com/download/#supported-versions).

Exceptionally, with 2.0 introducing breaking changes, 1.13 was designated as LTS in addition to 1.12.

| Version        | Release date           | Active support      | Security support    |
| -------------- |-----------------------:| -------------------:| -------------------:|
| 4.4*[^1]       | 1 August 2023          | 1 November 2023     | 1 February 2024     |
| 4.3*[^1]        | 2 May 2023             | 1 August 2023       | 1 November 2023     |
| 4.2*[^1]        | 1 February 2023        | 2 May 2023          | 1 August 2023       |
| **4.1 LTS**    | **1 November 2022**    | **1 February 2024** | **1 February 2024** |
| 4.0            | 31 August 2022         | 1 November 2022     | 1 February 2023     |
| 3.0            | 16 May 2022            | 31 August 2022      | 1 November 2022     |
| 2.16           | 7 February 2022        | 1 May 2022          | 1 August 2022       |
| **2.15 LTS**   | **4 November 2021**    | **1 February 2023** | **1 February 2023** |
| 2.14           | 1 August 2021          | 4 November 2021     | 7 February 2022     |
| 2.13           | 12 May 2021            | 1 August 2021       | 4 November 2021     |
| 2.12           | 2 February 2021        | 12 May 2021         | 1 August 2021       |
| **2.11 LTS**   | **2 November 2020**    | **1 February 2022** | **1 February 2022** |
| 2.10           | 11 August 2020         | 1 November 2020     | 2 February 2021     |
| 2.9            | 4 May 2020             | 11 August 2020      | 2 November 2020     |
| 2.8            | 3 February 2020        | 4 May 2020          | 11 August 2020      |
| **2.7 LTS**    | **6 November 2019**    | **3 February 2021** | **3 February 2021** |
| 2.6            | 1 August 2019          | 1 November 2019     | 3 February 2020     |
| 2.5            | 24 April 2019          | 1 August 2019       | 6 November 2019     |
| 2.4            | 19 December 2018       | April 2019          | 1 August 2019       |
| 2.3 LTS        | October 2018           | 1 February 2020     | 1 February 2020     |
| 1.13 LTS       | October 2017           | April 2019          | April 2019          |
| 1.12 LTS       | August 2017            | November 2018       | November 2018       |
| 1.8 LTS        | December 2016          | August 2017         | August 2017         |
| 1.4 LTS        | March 2016             | December 2016       | December 2016       |
| 0.8 LTS        | November 2014          | March 2016          | March 2016          |

[^1]: \* Future version numbers are provisional - these may receive a major version number increment, depending on the extent of backwards-incompatible changes and significant UI differences.