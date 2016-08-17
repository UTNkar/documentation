+++
date = "2016-08-17T15:17:17+02:00"
prev = "/3server_software/ufw"
title = "Postfix"
toc = true
weight = 65

+++

Sending e-mail on the UTN servers is done using the
[Postfix](http://www.postfix.org) software package. The software has been setup
on the servers in such a way that one can locally simply connect to `localhost`
on port 25 using the SMTP protocol. In the current configuration the servers
only send e-mail; mails send to any `utn.se` domain are handled by [Google
Apps](/2infrastructure/google_apps).

{{% notice note %}}

The installation of Postfix on the servers is done using an
[Ansible](/4development_tools/ansible) role. For more information about the
installation, see the Ansible repository.

{{% /notice %}}
