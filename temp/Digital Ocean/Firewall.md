# Firewall

The firewall of the droplets in Digital Ocean is configured using `ufw`. This is
a wrapper around iptables, making it a lot simpler. Basic usage can be found in
the [third
part](https://www.digitalocean.com/community/tutorials/additional-recommended-steps-for-new-ubuntu-14-04-servers)
of the tutorial mentioned in the new servers documentation.

For most servers the following ports are opened:
- 22 - SSH
- 80 - HTTP
- 443 - HTTPS
If other ports are opened it should be mentioned in the server description.
