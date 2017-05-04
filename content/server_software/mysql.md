+++
date = "2016-08-17T14:13:23+02:00"
title = "MySQL"
toc = true
weight = 35

+++

Older web applications within UTN still use [MySQL](https://www.mysql.com).
Although not the preferred database by the UTN system administrator, it is a
widely use database system that is widely documented. Most applications using a
MySQL database are automatically deployed using
[Ansible](/5development_tools/ansible), and configurations for those database
users and databases should be done within the Ansible repository.

Should any application be ported from MySQL to PostgreSQL, take into account
that there are quite a few differences in the SQL syntax between the two. Make
sure to test the application thoroughly before deploying it.

### Useful commands
The commands you should keep in mind when working with NGINX are the following:

- `mysql -uroot -p [database]`, enter the commandline interface of MySQL as root. (This command will prompt for the root password.)

### Common settings
To accommodate automatic deployments using [Ansible](/5development_tools/ansible), it must have access to MySQL credentials. To keep them safe, Ansible suggests locating them in a file located at `/root/.my.cnf` in the format:

```
[client]
user=root
password=1234test
```
