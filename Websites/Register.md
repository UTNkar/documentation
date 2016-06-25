# register.utn.se

The UTN registry website is a terribly old website created to keep track of the
number of members that UTN has and how they are distributed among the sections.
It is also used for applications of to the positions available within UTN and it
keeps track of the held positions of the members.

The application was ported to a new system(NGINX, PHP7, PostgreSQL) in the
summer of 2016 and is since contained in the `register` repository, that can be
found in the GitLab group. Note that the application is only brought into
workable state, it is a plain PHP application that is rather insecure (plain
passwords in code, no framework). However, with a bit of discretion it should do
until an alternative can be found.

The new application is hosted on [Turing](../Digital Ocean/Turing.md). The SSL certificate used for `register.utn.se` is acquired from [Let's Encrypt](../Digital Ocean/SSL.md)
