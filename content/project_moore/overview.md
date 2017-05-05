+++
date = "2017-05-05T12:39:34+02:00"
title = "Overview"
toc = true
weight = 5

+++

Project Moore is an web application that was build using
[Django](https://www.djangoproject.com/) and [Wagtail](https://wagtail.io/).
Django is a Python web framework. It provides the basic structure for the
application and handles all interactions between receiving a user request and
serving the content. Wagtail is a CMS system built on top of Django. It provides
a lot of functionality for Moore out-of-the-box and is very extendible. The
administration part of the website is part of the Wagtail CMS.

### Structure

The project follows the basic structure of any Django project. To quickly learn
about the Django structure you take a look at [Django at a
glance](https://docs.djangoproject.com/en/dev/intro/overview/) or [Follow the
Tutorial](https://docs.djangoproject.com/en/dev/intro/tutorial01/).

Like every Django project, Project Moore is split into various _apps_:

- `branding`: Logos and site specific settings.
- `home`: Everything concerning the `HomePage` type.
- `involvement`: Everything concerning active members within UTN.
- `materialize`: Helpers for the MaterializeCSS framework.
- `members`: All members information.
- `utils`: Loose python helpers.
- `website`: Main website configuration and templates.
