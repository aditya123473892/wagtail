_Work in progress_

Wagtail has been born out of many years of experience building websites, learning approaches that work and ones that don't, and striking a balance between between power and simplicity, structure and flexibility. We hope you'll find that Wagtail is in that sweet spot. However, as a piece of software, Wagtail can only take that mission so far - it's now up to you to create a site that's beautiful and a joy to work with. So, while it's tempting to rush ahead and start building, it's worth taking a moment to understand the design principles that Wagtail is built on.

In the spirit of ["The Zen of Python"](https://www.python.org/dev/peps/pep-0020/), The Zen of Wagtail is a set of guiding principles, both for building websites in Wagtail, and for the ongoing development of Wagtail itself.

## Wagtail is not an instant website in a box.
You can't make a beautiful website by plugging off-the-shelf modules together - expect to write HTML.

## Always wear the right hat.
More than anything else, the task of a content management system is to encourage clear separation of responsibilities between the people involved in creating a website: the content author, site administrator, developer and designer. These are not always different people, of course - if you're building your personal blog, you may well find yourself hopping between those different roles. Even so, it's important to be aware of which of those hats you're wearing at any moment - . It's certainly possible to write a novel with a paintbrush, but the sooner you realise that's what you're doing and pick up a pen instead, the more effort you'll save.

## A CMS should get information out of an editor's head and into a database, as efficiently and directly as possible.

## The best user interface for a programmer is usually a programming language.

A common sight in content management systems is a point-and-click interface to let you define the data model that makes up a page:

![Drupal interface for defining a content type](https://d7j863fr5jhrr.cloudfront.net/wp-content/uploads/2014/12/drupal-fields.jpg?x71388)

It looks nice in the sales pitch, but in reality, no CMS end-user can realistically make that kind of fundamental change - on a live site, no less - unless they have a programmer's insight into how the site is built, and what impact the change will have. As such, it will always be the programmer's job to negotiate that point-and-click interface - all you've done is taken them away from the comfortable world of writing code, where they have a whole ecosystem of tools, from text editors to version control systems, to help them develop, test and deploy their code changes.
