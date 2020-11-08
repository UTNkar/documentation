+++
date = "2016-08-02T16:30:18+02:00"
title = "NGINX"
toc = true
weight = 5

+++

All websites in the UTN infrastructure are hosted using
[NGINX](https://www.nginx.com). NGINX is a efficient web server that can host
many websites efficiently and has options to support almost any need a web
server might have.

{{% notice tip %}}

Most UTN deployments are done using [Ansible](/development_tools/ansible) and
that the NGINX configurations for those applications is located within the
Ansible repository.

{{% /notice %}}

All configurations for the websites that NGINX serves are available on the server in the `/etc/nginx/sites-available` folder. In general we try to give each file the name of the website(FQDN) that it serves. To enable on of the websites we can simply symlink the configuration file to `/etc/nginx/sites-available` (e.g., `ln -s /etc/nginx/sites-available/test.utn.se /etc/nginx/sites-enabled/test.utn.se`).

### Useful commands
The commands you should keep in mind when working with NGINX are the following:

- `nginx -t`, to test if the configurations are valid. (This will avoid blank
pages for users.)
- `systemctl reload nginx`, to start using the configurations currently enabled.
- `systemctl restart nginx`, to restart the whole web server.

{{% notice warning %}}

These commands need to be run as the `root` user.

{{% /notice %}}

#### Further reading:

- [How To Set Up Nginx with HTTP/2 Support on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-set-up-nginx-with-http-2-support-on-ubuntu-18-04)
