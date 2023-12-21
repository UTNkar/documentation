---
title: "NGINX"
toc: true
weight: 5
---

All websites in the UTN infrastructure are hosted using [NGINX](https://www.nginx.com), an efficient web server capable of hosting multiple websites and offering a wide range of server needs.

{{% notice tip %}}
Most UTN deployments are conducted using [Ansible](../development-tools/ansible), and the NGINX configurations for those applications are located within the Ansible repository.
{{% /notice %}}

NGINX configurations for the hosted websites are stored on the server in the `/etc/nginx/sites-available` directory. Typically, each configuration file is named after the website (FQDN) it serves. To activate a website, create a symlink from the configuration file to `/etc/nginx/sites-enabled`. For example: `ln -s /etc/nginx/sites-available/test.utn.se /etc/nginx/sites-enabled/test.utn.se`.

### Useful Commands

Here are some important commands to use when working with NGINX:

- `nginx -t`: Tests the NGINX configuration files for correctness, preventing downtime or blank pages for users.
- `systemctl reload nginx`: Applies changes by reloading the NGINX configurations without restarting the service.
- `systemctl restart nginx`: Fully restarts the NGINX service, applying changes and restarting all worker processes.

{{% notice warning %}}
You must execute these commands with `root` user privileges.
{{% /notice %}}

#### Further Reading

For additional information and tutorials on configuring NGINX, consider the following resource:

- [How To Set Up Nginx with HTTP/2 Support on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-set-up-nginx-with-http-2-support-on-ubuntu-18-04)
