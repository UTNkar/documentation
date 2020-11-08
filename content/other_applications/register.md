+++
date = "2016-08-18T15:22:50+02:00"
title = "Member registry"
toc = true
weight = 15

+++

The union uses a member registry called Melos which is managed by USMOS. It is a joint system used by
the nations and unions in Uppsala. Melos features an API for retreiving a user from the member registry
and checking if a person is a member of UTN or not. The system administrator has more details on how to use
this api. The information officer also has the ability to access the member registry.

{{% notice warning %}}

The old registry described below (*register.utn.se*) has been deprecated in favor of the unions new member system MELOS and should be removed.

{{% /notice %}}

The UTN registry website is a terribly old custom web application created to
keep track of the number of members that UTN has and how they are distributed
among the sections. It is also used for applications of to the positions
available within UTN and it keeps track of the held positions of the members.

The application was ported to a new system(NGINX, PHP7, PostgreSQL) in the
summer of 2016 and is since contained in the `register` repository, that can be
found in the GitLab group. Note that the application is only brought into
workable state, it is a plain PHP application that is rather insecure (plain
passwords in code, no framework). However, with a bit of discretion it should do
until an alternative can be found.

The application itself requires a few tasks being added to cron:

```
23,43 * * * * /usr/bin/wget --no-check-certificate --timeout=0 -P /tmp -q --delete-after https://register.utn.se/_maintenance.php
12 * * * * /usr/bin/wget --no-check-certificate --timeout=0 -P /tmp -q --delete-after https://register.utn.se/_email_batch.php
```

These tasks ensure that e-mails are send and perform general maintenance tasks
on the system.
