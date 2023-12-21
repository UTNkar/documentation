---
title: "Postfix"
toc: true
weight: 65
---

Sending emails from the UTN servers is handled by the [Postfix](http://www.postfix.org) software package. It has been configured to allow local connections to `localhost` on port 25 using the SMTP protocol. The current server setup is configured only to send out emails; incoming emails for any `utn.se` domain are managed by [Google Workspace](/infrastructure/google-workspace).

{{% notice note %}}
Postfix installation on the servers is carried out using an [Ansible](../development-tools/ansible) role. For detailed information about the setup, consult the Ansible repository.
{{% /notice %}}

### SMTP

In 2018, there were issues with email delivery failures, which were resolved by utilizing the SMTP relay service provided by Google Workspace. Extra configuration was necessary within the union's Google Workspace settings. You can find the setup on the [Google Admin Page](https://admin.google.com) by navigating to `Gmail -> Advanced Settings` and locating `SMTP-relay service` under the `Forwarding` section.
