+++
date = "2016-08-02T15:40:49+02:00"
next = "/4development_tools"
prev = "/3server_software/mysql"
title = "Let's Encrypt"
toc = true
weight = 45

+++

The SSL certificates for all web applications on the UTN servers are provided by
[Let's Encrypt](https://letsencrypt.org/). This initiative provides free short
term SSL certificates for all websites. The software for Let's Encrypt can
easily be installed using the command: `sudo apt-get install letsencrypt`.

When using NGINX, the certificates can be easily acquired using the following
command `sudo letsencrypt certonly --webroot -w /var/www/XXXXX -d XXXXX`, where
`XXXXX` is replaced by the domain name of the applicaton.

{{% notice note %}}
This assumes that the files are located in the */var/www*
folder in a folder named after the domain name. It also assumes that the
`.well-known` folder in the web root is readable (which it is in the default UTN
NGINX configuration).
{{% /notice %}}

The certificates are automatically renewed using cron. To test the renewal run
`sudo letsencrypt renew --dry-run`. Using `sudo crontab -e` one of the cron
lines should then be similar to `32 6 * * * /usr/bin/letsencrypt renew -q`.

{{% notice note %}}
To increase the reliability of the certificate renewal
process, a random time of day should be used.
{{% /notice %}}
