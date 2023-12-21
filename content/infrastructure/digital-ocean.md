---
title: "DigitalOcean"
toc: true
weight: 15
---

UTN uses virtual servers hosted at [DigitalOcean](https://www.digitalocean.com). These servers are managed and deployed using [Ansible](../development-tools/ansible) where applicable. Detailed information about the software on these servers is available in the [Server Software](/server-software) chapter.

To determine the hosting locations of various pages, refer to the DNS settings on [Cloudflare](https://cloudflare.com). Configuration settings are located in their default directories, such as `/etc/nginx/sites-available/`. Website files are stored in `/var/www/`. All servers operate on Ubuntu 18.04.

## Babbage

The Babbage server, addressed as `babbage.utn.se`, runs NGINX, PHP7, and MySQL. It primarily supports Drupal7-based applications and some custom PHP applications.

## Moore

The Moore server, known as `moore.utn.se`, is equipped with NGINX and PostgreSQL. This server is designated for Project Moore and other Django-based applications.

## Turing

Turing server, `turing.utn.se`, hosts PHP7, Node.js, NGINX, and PostgreSQL. It is primarily used for custom applications that require PostgreSQL or Node.js.
