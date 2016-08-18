+++
date = "2016-08-02T16:34:09+02:00"
next = "/2"
prev = "/2infrastructure/google_apps"
title = "Digital Ocean"
toc = true
weight = 15

+++

UTN currently hosts virtual servers at [Digital
Ocean](https://www.digitalocean.com). These servers are managed/deployed using
[Ansible](/5development_tools/ansible), for as far as this is possible. The
software on these servers is further explained in [Server
Software](/4server_software).

## Turing

The Turing server, `turing.utn.se`, runs web apps that use PHP7, NGINX and
PostgreSQL. It runs on Ubuntu 16.04. All settings can be found in their default
positions (e.g., `/etc/nginx/sites-available/`). The files for the apps are
found in `/var/www/`. The following web applications are running on Turing:

- [register.utn.se](https://register.utn.se) - The UTN Registry
- [survey.utn.se](https://survey.utn.se) - LimeSurvey
- [mfk.utn.se](https://mfk.utn.se) - MFK Reception's Website (contact:
[hivemind@mfk.utn.se](mailto:Hivemind@mfk.utn.se))

## Babbage

The Babbage server, `babbage.utn.se`, runs Drupal7-based applications, using
NGINX, PHP7 and MySQL. It runs on Ubuntu 16.04. All settings can be found in
their default positions (e.g., `/etc/nginx/sites-available/`). The files for the
apps are found in `/var/www/`. The following web applications are running on
Babbage:

- [www.utn.se](https://www.utn.se) - UTN's Main Webpage (Drupal7-based)

## New server/droplet

{{% notice warning %}}

The following describes a deprecated way of creating and setting up a new VPS. Use [Ansible](/5development_tools/ansible) instead.

{{% /notice %}}

For convenience, snapshots are available in the Digital Ocean. So the quickest
way to setup a new server/droplet is to select one of these:

- Base: A base Ubuntu 16.04 server.
- Webstack: Ubuntu 16.04 with NginX, PostgreSQL and PHP7 installed

To login to these images the following information is used:

- Username: `jdekker`
- Password: `6J.YjKjgrVD2#?tF8n4AKaw$wD{CZ7`

For the setup, the following tutorial was used for the base steps:
[link](https://www.digitalocean.com/community/tutorial_series/new-ubuntu-14-04-server-checklist?utm_source=Customerio&utm_medium=Email_Internal&utm_campaign=Email_UbuntuDistroApacheWelcome).
After installing from the snapshot, you can rename the user to match your
personal preference (`usermod -l login-name jdekker`). You should then add your
ssh-key (it is explained in the tutorial) to the account and disable password
logins in `/etc/ssh/sshd_config`.

Congratulations, you've now setup a secure server!
