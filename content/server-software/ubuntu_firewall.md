---
title: "Ubuntu Firewall (UFW)"
toc: true
weight: 55
---

[UFW](https://help.ubuntu.com/community/UFW), which stands for *Uncomplicated Firewall*, is a user-friendly front-end for managing IPTables. It is the primary firewall used across UTN systems.

Commonly allowed ports/services, also known as rules, on most UTN systems (applicable to both IPv4 and IPv6) include:

- `ssh`: Allows SSH access to the server.
- `80/tcp`: Permits HTTP traffic to the server.
- `443/tcp`: Enables HTTPS traffic to the server.

{{% notice warning %}}
Avoid enabling `25/tcp` for SMTP traffic unless the mail server ([Postfix](./postfix)) is properly secured against unauthorized access.
{{% /notice %}}

### Useful Commands

Here are some essential UFW commands to remember:

- `ufw allow [rule]`: Opens the firewall to allow traffic that matches the specified rule.
- `ufw delete allow [rule]`: Removes an allow rule that was previously set.
- `ufw show added`: Displays the rules that will be activated upon the next reload.
- `ufw enable`: Activates the UFW firewall.
- `ufw status`: Shows the rules currently enforced by the firewall.

{{% notice warning %}}
Execute these commands with `root` privileges.
{{% /notice %}}
