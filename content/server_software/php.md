+++
date = "2016-08-02T16:31:19+02:00"
title = "PHP"
toc = true
weight = 15

+++

PHP based application on the UTN infrastructure are served using `php-fpm` and
[NGINX](/server_software/nginx). Most new deployments are using PHP 7.2 but some
are using 7.3 or 7.4. To see which one is used, check the nginx configuration
for that particular website.

So far, no special settings have been set for the PHP installation, should this
be necessary, the PHP settings are available in `/etc/php/{7.2|7.3|7.4}/fpm/php.ini`.

### Useful commands
The commands you should keep in mind when working with NGINX are the following:

- `systemctl restart php7.2-fpm`, to restart the PHP7.2 deamon.
- `systemctl restart php7.3-fpm`, to restart the PHP7.3 deamon.
- `systemctl restart php7.4-fpm`, to restart the PHP7.4 deamon.
