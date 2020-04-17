+++
date = "2016-08-02T16:34:09+02:00"
title = "Digital Ocean"
toc = true
weight = 15

+++

UTN currently hosts virtual servers at [DigitalOcean](https://www.digitalocean.com). 
These servers are managed/deployed using [Ansible](/development_tools/ansible), 
for as far as this is possible. The software on these servers is further explained in [Server
Software](/server_software).

To see which pages are hosted where, check the DNS on [cloudflare](https://cloudflare.com).
All settings can be found in their default positions .(e.g., `/etc/nginx/sites-available/`).
The files for the apps are found in `/var/www/`.
All servers run Ubuntu 18.04.

## Babbage

The Babbage server, `babbage.utn.se` is installed with NGINX, PHP7 and MySQL.
It mainly runs Drupal7-based applications but also hosts some custom PHP applications.

## Moore

The Moore server, `moore.utn.se` is installed with NGINX and Postgresql.
It is home to Project Moore and other django-based applications. The

## Turing

The Turing server, `turing.utn.se` is installed with PHP7, nodejs, NGINX and
PostgreSQL. It mainly hosts custom applications that requires postgresql or nodejs.
