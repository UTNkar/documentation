---
title: "PostgreSQL"
toc: true
weight: 25
---

For certain applications within the UTN infrastructure, [PostgreSQL](https://www.postgresql.org) is the preferred database system. Its efficiency, widespread use, and robust tooling make PostgreSQL a top choice. Applications that utilize a PostgreSQL database are typically deployed automatically using [Ansible](../development-tools/ansible), with the necessary configurations for database users and databases handled within the Ansible repository.

### Useful Commands

Here are several useful commands for managing PostgreSQL:

- `psql [database]`: Opens the PostgreSQL command line interface for a specific database.
- `createuser -P`: Creates a new PostgreSQL user and prompts for a password.
- `dropuser [username]`: Deletes a user from PostgreSQL.
- `createdb --encoding=UNICODE --owner=[username] [database]`: Creates a new database with Unicode encoding and assigns ownership to the specified user.
- `dropdb [database]`: Deletes a database from the server.

{{% notice info %}}
PostgreSQL automatically sets up a default superuser named `postgres`. This user does not have a set password, so you should use `sudo -u postgres` when running PostgreSQL commands.
{{% /notice %}}

### Further Reading

For more in-depth information about PostgreSQL, refer to:

- [The PostgreSQL Documentation](https://www.postgresql.org/docs/9.5/static/index.html)
