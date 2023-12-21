---
title: "PHP"
toc: true
weight: 15
---

PHP-based applications on the UTN infrastructure are served using `php-fpm` alongside [NGINX](/server-software/nginx). While many new deployments utilize PHP 7.2, some applications may run on PHP 7.3 or 7.4. To verify which version is in use, refer to the NGINX configuration for the specific website.

Currently, no special configurations have been applied to the PHP installations. If adjustments become necessary in the future, you can find the PHP settings in `/etc/php/{7.2|7.3|7.4}/fpm/php.ini`.

### Useful Commands

When managing PHP versions with NGINX, keep the following commands in mind:

- `systemctl restart php7.2-fpm`: This command restarts the PHP 7.2 daemon.
- `systemctl restart php7.3-fpm`: Use this to restart the PHP 7.3 daemon.
- `systemctl restart php7.4-fpm`: This will restart the PHP 7.4 daemon.
