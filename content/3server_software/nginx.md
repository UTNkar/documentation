+++
date = "2016-08-02T16:30:18+02:00"
next = "/3server_software/php"
prev = "/3server_software/"
title = "NGINX"
toc = true
weight = 5

+++

All websites in the UTN infrastructure are hosted using
[NGINX](https://www.nginx.com). NGINX is a efficient web server that can host
many websites efficiently and has options to support almost any need a web
server might have. Note that most UTN deployments are done using
[Ansible](/4development_tools/ansible) and that the NGINX configurations for
those applications is located within the Ansible repository.

All configurations for the websites that NGINX serves are available on the server in the `/etc/nginx/sites-available` folder. In general we try to give each file the name of the website(FQDN) that it serves. To enable on of the websites we can simply symlink the configuration file to `/etc/nginx/sites-available` (e.g., `ln -s /etc/nginx/sites-available/test.utn.se /etc/nginx/sites-enabled/test.utn.se`).

### Useful commands:
The commands you should keep in mind when working with NGINX are the following:

- `nginx -t`, to test if the configurations are valid. (This will avoid blank
pages for users.)
- `systemctl reload nginx`, to start using the configurations currently enabled.
- `systemctl restart nginx`, to restart the whole web server.

Note that these commands need to be run as the `root` user.

### Example configuration:
Most UTN websites are PHP-based applications and use SSL/HTTP2 connections (using
Let's Encrypt certificates). An example configuration for such applications is
the following (based on the NGINX configuration for
[register.utn.se](https://register.utn.se)):

```
server {
  listen 80;
  listen [::]:80;
  server_name  test.utn.se;
  rewrite ^ https://test.utn.se$request_uri? permanent;
}

server {
  listen 443 ssl http2;
  listen [::]:443 ssl http2;
  server_name test.utn.se;

  ssl_certificate /etc/letsencrypt/live/test.utn.se/fullchain.pem;
  ssl_certificate_key /etc/letsencrypt/live/test.utn.se/privkey.pem;

  ssl on;
  ssl_session_cache  builtin:1000  shared:SSL:10m;
  ssl_session_timeout 1h;
  ssl_protocols  TLSv1 TLSv1.1 TLSv1.2;
  ssl_ciphers HIGH:!aNULL:!eNULL:!EXPORT:!CAMELLIA:!DES:!MD5:!PSK:!RC4;
  ssl_prefer_server_ciphers on;

  root /var/www/test.utn.se/public;

  index index.php index.html index.htm;

  # Very rarely should these ever be accessed outside of your lan
  location ~* \.(log)$ {
      allow 192.168.0.0/16;
      deny all;
  }

  location = /robots.txt {
      allow all;
      log_not_found off;
      access_log off;
  }

  # Allow "Well-Known URIs" as per RFC 5785
  location ~* ^/.well-known/ {
      allow all;
  }

  location ~ \..*/.*\.php$ {
      return 403;
  }

  # Block access to "hidden" files and directories whose names begin with a
  # period. This includes directories used by version control systems such
  # as Subversion or Git to store control files.
  location ~ (^|/)\. {
    return 403;
  }

  location ~ \.php(/|$) {
    fastcgi_split_path_info ^(.+?\.php)(|/.*)$;
    include fastcgi_params;
    fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
    fastcgi_param PATH_INFO $fastcgi_path_info;
    fastcgi_intercept_errors on;
    fastcgi_pass unix:/var/run/php/php7.0-fpm.sock;
  }
}
```
