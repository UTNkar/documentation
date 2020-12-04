+++
title = "Systemd"
date =  2020-12-04T11:03:58+01:00
weight = 10
+++

Systemd is a service that comes pre-installed with Ubuntu. Systemd can start and keep applications running on the server e.g. *project moore, ordsys, nginx etc*. 
Systemd can also start the applications automatically when the server starts.

To add an application to systemd, a service file needs to be added to `/etc/systemd/system`. This done automatically by [ansible](/development_tools/ansible/) for the roles that require it.

## Commands

The commands listed below uses the argument *service_name*. This is the name of the service file in the systemd folder i.e. `/etc/systemd/system/service_name.service`:

- `systemctl status *service_name*` - See the status of an application
- `systemctl start/stop *service_name*` - Start or stop an application
- `systemctl restart *service_name*` - Restart an application
- `systemctl enable/disable *service_name*` - Enable or disable automatic start when server starts
- `systemctl daemon-reload` - Reload systemd (usually needed if any of the service files has been changed)

## Logs

Ubuntu also comes with the command `journalctl` which can show logs for systemd services. You can view the logs of a service using `journalctl -u service_name`.

{{% notice info %}}

Not all applications log messages in a way that can be viewed with `journalctl`. Some directly to a file in `/var/log/` while some applications log to Sentry.

{{% /notice %}}
