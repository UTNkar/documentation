+++
date = "2016-08-02T16:31:19+02:00"
next = "/3server_software/nginx"
prev = "/3server_software/postgresql"
title = "PHP"
toc = true
weight = 15

+++

PHP based application on the UTN infrastructure are served using `php-fpm` and
[NGINX](/3server_software/nginx). Currently all new deployments are done using
PHP 7.

So far, no special settings have been set for the PHP installation, should this
be necessary, the PHP settings are available in `/etc/php/7.0/fpm/php.ini`.

### Useful commands:
The commands you should keep in mind when working with NGINX are the following:

- `systemctl restart php7.0-fpm`, to restart the PHP7 deamon.
