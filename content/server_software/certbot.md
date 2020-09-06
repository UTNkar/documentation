+++
date = "2016-08-02T15:40:49+02:00"
title = "Certbot"
toc = true
weight = 45

+++

{{% notice warning %}}
Certbot is only used on the servers hosted on [Glesys](/infrastructure/glesys/). It was used on the servers hosted on [DigitalOcean](/infrastructure/digital_ocean/) but has now been replaced by [Cloudflares origin certificates](/infrastructure/cloudflare/)
{{% /notice %}}

Certbot is a tool provided by [Let's Encrypt](https://letsencrypt.org/) and provides free short
term SSL certificates. Installation instructions can be found on the [certbot website](https://certbot.eff.org/#ubuntuxenial-other). 
We currently do not use the automatic NGINX configuration functionality of certbot. This is because certbot overrides the NGINX configuration we have added via ansible when we created the sites.

{{% notice info %}}
If you add, update or remove a certificate you must reload nginx afterwards for the changes to take effect. Use `nginx -s reload`.
{{% /notice %}}

### Create a new certificate

A new certificate can be easily acquired using the following command
`sudo /certbot-0.30.2/certbot-auto --no-self-upgrade certonly --webroot -w /var/www/XXXXX/public -d XXXXX`, where `XXXXX` is replaced by the domain name of the applicaton.

{{% notice warning %}}
You must use **ALWAYS** run `/certbot-0.30.2/certbot-auto --no-self-upgrade` on the Glesys servers. This is because they are running Ubuntu 12.04 and higher versions of certbot are incompatible with Ubuntu 12.04
{{% /notice %}}

### Remove an existing certificate

Removing an existing certificate is also easy. Use the following command `sudo certbot delete` which will then ask which domains you want to remove

### Automatic renewals

The certificates are automatically renewed using cron. The renewal task is
included in `/etc/cron.d/certbot`, which runs the renew command twice a day.
