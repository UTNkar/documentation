---
title: "Django Admin Interface"
weight: 1
---

OrdSys utilizes Django's built-in admin panel for database content management. Admin users can access this interface at [ordsys.utn.se/admin](https://ordsys.utn.se/admin "Take me there!").

Authentication is required when starting a new session. The same accounts used for the front-end are applicable here, necessitating unique usernames across organisations. Due to the extensive capabilities of the admin page, which include modifying database contents, users must have staff status to log in.

A staff member from an organisation is empowered to create and manage accounts within their respective organisation, fostering self-sufficiency. If an organisation lacks a staff user, a superuser, typically the system administrator, must appoint one. To create a superuser when none exists, you can execute the command `python manage.py createsuperuser`.

After successful authentication, you'll arrive at the home screen displaying all the database tables.

![home screen](/images/ordsys/admin/index.png)

This administrative interface is important for event managers to perform necessary tasks efficiently and maintain the integrity and functionality of the OrdSys database.
