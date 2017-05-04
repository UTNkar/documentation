+++
date = "2016-08-02T16:31:29+02:00"
title = "PostgreSQL"
toc = true
weight = 25

+++

For some applications within the UTN infrastructure our preferred database is
used, [PostgreSQL](https://www.postgresql.org). This database is preferred
because of its efficiency, availability, and superior system tooling. Most
applications using a PostgreSQL database are automatically deployed using
[Ansible](/5development_tools/ansible), and configurations for those database
users and databases should be done within the Ansible repository.

### Useful Commands
{{% notice info %}}

PostgreSQL automatically creates a standard user with the root rights for the
databases on the server, named `postgres`. This user does not have a password,
thus `sudo -upostgres` should be used to run postgreSQL commands.

{{% /notice %}}

The following commands are useful when working with PostgreSQL:

- `psql [database]`, enter the command line interface of PostgreSQL.
- `createuser -P`, create a new PostgreSQL user (with password).
- `dropuser [username]`, remove user from PostgreSQL.
- `createdb --encoding=UNICODE --owner=[username] [database]`, create a unicode
database owned by specified user.
- `dropdb [database]`, remove database from the server.

### Further reading
- [The PostgreSQL Documentation](https://www.postgresql.org/docs/9.5/static/index.html)
