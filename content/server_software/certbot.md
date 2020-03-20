+++
date = "2016-08-02T15:40:49+02:00"
title = "Certbot"
toc = true
weight = 45

+++

The SSL certificates for all web applications on the UTN servers are provided by
[Let's Encrypt](https://letsencrypt.org/). This initiative provides free short
term SSL certificates for all websites. Let's Encrypt certificates can be
aquired using certbot, an automated Let's Encrypt client. Installation
instructions can be found on the [certbot website](https://certbot.eff.org/#ubuntuxenial-other). We currently do not
use the automatic NGINX configuration functionality of certbot. This is because certbot overrides the NGINX configuration we have added via ansible when we created the sites.

{{% notice warning %}}
If you add, update or remove a certificate you must reload nginx afterwards for the changes to take effect. Use `nginx -s reload`.
{{% /notice %}}

### Create a new certificate

A new certificate can be easily acquired using the following command 
`sudo certbot certonly --webroot -w /var/www/XXXXX/public -d XXXXX`, where `XXXXX` is replaced by the domain name of the applicaton.

#### Moore

On moore, you must use the following command since the structure is a bit different: `sudo certbot certonly --webroot -w /var/www/moore/src/media --cert-name moore.utn.se -d moore.utn.se`. To add more domain names, add `-d domain.name.se` to the end of the command for all domains you want to add.
To remove a domain, run this command with all current domains except for the ones you want to remove. [[documentation](https://certbot.eff.org/docs/using.html?highlight=domain#changing-a-certificate-s-domains)]

### Remove an existing certificate

Removing an existing certificate is also easy. Use the following command `sudo certbot delete --cert-name XXXXX.utn.se`, where XXXXX is replaced by the domain name of the application.

{{% notice note %}}
This assumes that the files are located in the */var/www*
folder in a folder named after the domain name. It also assumes that the
`.well-known` folder in the web root is readable (which it is in the default UTN
NGINX configuration).
{{% /notice %}}

The certificates are automatically renewed using cron. To test the renewal run
`sudo certbot renew --dry-run`. In newer version of certbot the a crontask is
included in `/etc/cron.d/certbot`, which runs the renew command twice a day.
