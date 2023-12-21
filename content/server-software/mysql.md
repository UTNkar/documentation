---
title: "MySQL"
toc: true
weight: 35
---

Older web applications within UTN may still utilize [MySQL](https://www.mysql.com), a database system that is extensively documented despite not being the system administrator's preferred choice. These applications are typically deployed automatically using [Ansible](../development-tools/ansible), and any configurations for database users and databases should be managed within the Ansible repository.

If an application is transitioning from MySQL to PostgreSQL, be aware of the significant differences in SQL syntax between the two database systems. It is important to conduct comprehensive testing of the application prior to deployment.

### Useful Commands

When working with MySQL, the following command is essential:

- `mysql -uroot -p [database]`: This command allows you to access the MySQL command-line interface as the root user. You will be prompted to enter the root password.

### Common Settings

For Ansible to perform automatic deployments, it needs to have access to MySQL credentials. To secure these credentials, Ansible recommends storing them in a file at `/root/.my.cnf` using the following format:

```toml
[client]
user=root
password=1234test
```
