+++
date = "2016-08-02T16:30:14+02:00"
title = "UFW"
toc = true
weight = 55

+++

[UFW](https://help.ubuntu.com/community/UFW) stands for *Uncomplicated Firewall*
and is an easy to manage wrapper for IPTables. UTN systems use this firewall as
their main firewall.

On most UTN systems the following ports/services, referred to as rules, are
allowed (both on IPv4 and IPv6):

- `ssh`, to enable SSH access to the server.
- `80/tcp`, to access the server over HTTP.
- `443/tcp`, to access the server over HTTPS.

{{% notice warning %}}

Do not enable `25/tcp` unless the mail server
([Postfix](/4server_software/postfix)), is secured against foreign
authentication.

{{% /notice %}}

### Useful commands
The commands you should keep in mind when working with UFW are the following:

- `ufw allow [rule]`, to allow access for connections matching the rule.
- `ufw delete allow [rule]`, to delete a previously created rule.
- `ufw show added`, to show the rules to be added on reload.
- `ufw enable`, to enable UFW.
- `ufq status`, to see the currently enforced rules.

{{% notice warning %}}

These commands need to be run as the `root` user.

{{% /notice %}}
