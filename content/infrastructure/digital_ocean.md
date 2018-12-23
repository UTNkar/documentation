+++
date = "2016-08-02T16:34:09+02:00"
title = "Digital Ocean"
toc = true
weight = 15

+++

UTN currently hosts virtual servers at [Digital
Ocean](https://www.digitalocean.com). These servers are managed/deployed using
[Ansible](/development_tools/ansible), for as far as this is possible. The
software on these servers is further explained in [Server
Software](/server_software).

## Babbage

The Babbage server, `babbage.utn.se`, mainly runs Drupal7-based applications, using
NGINX, PHP7 and MySQL. It runs on Ubuntu 16.04. All settings can be found in
their default positions (e.g., `/etc/nginx/sites-available/`). The files for the
apps are found in `/var/www/`. The following web applications are running on
Babbage:

- [www.utn.se](https://www.utn.se) - UTN's main website (Drupal7-based)
- [balen.utn.se](https://balen.utn.se) - The Bal committee website
(Drupal7-based)
- [basar.utn.se](https://basar.utn.se) - The Basmottagningen website
(Drupal7-based)
- [es.utn.se](https://es.utn.se) - The ES section website (Drupal7-based)
- [forsranningen.utn.se](https://forsranningen.utn.se) - The River Rafting
website (Drupal7-based)
- [h.utn.se](https://h.utn.se) - The H section website (Drupal7-based)
- [k.utn.se](https://k.utn.se) - The K section website (Drupal7-based)
- [master.utn.se](https://master.utn.se) - The masters' reception website
(Drupal7-based)
- [nvk.utn.se](https://nvk.utn.se) - The NVK section website (Drupal7-based)
- [polhacks.utn.se](https://polhacks.utn.se) - The Polhacks website
(Drupal7-based)
- [rally.utn.se](https://rally.utn.se) - The Rebus Rally website
(Drupal7-based)
- [rallybot.utn.se](https://rallybot.utn.se) - The API for the Rebus Rally bot (Custom)
- [recce.utn.se](https://recce.utn.se) - The TD reception website
(Drupal7-based)
- [sts.utn.se](https://sts.utn.se) - The STS section website (Drupal7-based)
- [utnarm.utn.se](https://utnarm.utn.se) - The UTNarm website (Drupal7-based)
- [w.utn.se](https://w.utn.se) - The W section website (Drupal7-based)
- [x.utn.se](https://x.utn.se) - The X section website (Drupal7-based)

## Moore

The Moore server, `moore.utn.se`, is home to Project Moore: an Django project
intent on replacing several part of the UTN application infrastructure. The
server runs on Ubuntu 16.04. All files for Project Moore are located in the
`/var/www/` folder. The following urls are used by Project Moore:

- [apply.utn.se](https://dev.utn.se) - Application website
- [dev.utn.se](https://dev.utn.se) - The Tests website
- [grus.utn.se](https://grus.utn.se) - The GRUS section website

## Turing

The Turing server, `turing.utn.se`, runs web apps that use PHP7, NGINX and
PostgreSQL. It runs on Ubuntu 16.04. All settings can be found in their default
positions (e.g., `/etc/nginx/sites-available/`). The files for the apps are
found in `/var/www/`. The following web applications are running on Turing:

- [register.utn.se](https://register.utn.se) - The UTN Registry
- [survey.utn.se](https://survey.utn.se) - LimeSurvey
- [mfk.utn.se](https://mfk.utn.se) - MFK reception's website (contact:
[hivemind@mfk.utn.se](mailto:Hivemind@mfk.utn.se))
- [nvm.utn.se](https://nvm.utn.se) - NVM section website (contact:
[nvm-tech@utn.se](mailto:nvm-tech@utn.se))
