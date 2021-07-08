+++
title = "The Django admin interface"
menutitle = "Django admin"
date =  2021-07-08
LastModifierDisplayName = "Albin Antti"
LastModifierEmail = "albin_antti@hotmail.com"
weight = 1
+++

OrdSys uses Django's built-in admin interface panel for accessing and editing the contents of the database. This admin interface can be accessed at [ordsys.utn.se/admin](https://ordsys.utn.se/admin "Take me there!").

When visiting the page in a new session, you must first authenticate yourself using an account. The accounts used for the admin interface are the same accounts as those used in the front-end (which is why usernames must be unique regardless of organisation). As this admin page can be used to modify a lot of the database contents, a user must have the staff status to log in.

![login screen](/images/ordsys/admin/login.png?width=20pc)

A staff member of an organisation can create and edit accounts within their organisation, meaning each organisation should be pretty self-governing. If an organisation is missing a staff user however, one must be appointed by a superuser (usually the sysadmin). If no superuser exists, one can be created by running `python manage.py createsuperuser`.

Once you've authenticated, you'll be brought to the following home screen showing a list of all database tables.

![home screen](/images/ordsys/admin/index.png)
