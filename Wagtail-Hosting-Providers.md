THIS DOCUMENT IS A DRAFT

Since there are many ways to host a Wagtail site, and many commercial products available, it is in our interest to help guide Wagtail users with some recommended hosting setups. If you are a hosting provider, we encourage you to support Wagtail, and offer the following framework for listing your hosting platform on the official Wagtail Docs to help gain exposure and drive new potential customers your way.

All providers must meet the minimum requirements below to be listed on the Wagtail docs. Providers will then be listed alphabetically within their class, with First Class ordered first, Second Class ordered second, etc.

## Minimum Wagtail Hosting Support

To be considered a Wagtail hosting provider, your platform must meet the minimum qualifications:
* Ability for new customers to sign up (i.e. open to the public).
* Publicly available pricing guides (i.e. your prices must be clearly posted, not gated behind "contact us" links).
* Officially support at least one non-EOL version of Python (i.e. as of 2023, this means Python 3.8 to 3.11), and a WSGI server.
* Provide a written step-by-step guide for a customer to host a Wagtail site on your platform.

## First Class Support

This encompasses the "Application-as-a-Service" layer. This means the provider directly offers Wagtail support, without the need for the customer to configure a Python installation, hardware, Operating System, or databases. Providers who offer the following features may be considered to have "first class Wagtail support":
* A button, command, or feature which automatically deploys a fully-working customer-owned Wagtail website, publicly hosted on the Internet with a URL. This would most likely be some kind of boilerplate website (i.e. hello world, Wagtail Bakery, etc.). This feature must not require the user to provide their own Wagtail codebase.
* The Wagtail hosting option must include
  * A supported Django database (SQLite, MySQL, MariaDB, PostgreSQL, Oracle).
  * A supported media storage with a provider-supported backend (i.e. Filesystem, object/blob storage buckets)

## Second Class Support

This encompasses the "Platform-as-a-Service" layer. This means you don't offer Wagtail directly, but rather offer generic Python + WSGI support, without the need for the user to configure the hardware or Operating System level.
* A button, command, or feature which automatically deploys a fully-working Python environment.
* The ability for the customer to add a Web and/or WSGI server.
* The ability for the customer to add a supported Django database (SQLite, MySQL, MariaDB, PostgreSQL, Oracle).
* The ability for the customer to add media storage (i.e. recommend the user to use an AWS S3 bucket).

## Third Class Support

This encompasses the "Infrastructure-as-a-Service" layer. This means you offer virtual machines and other resources necessary for the user to "roll their own" Wagtail installation. It is essential to provide the user with a complete guide as to how to install an Operating System, Web Server, Python, Database Server, etc. necessary to run a Wagtail codebase.