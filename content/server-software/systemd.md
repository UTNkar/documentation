---
title: "Systemd"
weight: 10
---

Systemd is an integral service management suite that comes pre-installed with Ubuntu. It is capable of starting and maintaining applications running on the server, such as *project moore, ordsys, nginx*, and others. Additionally, systemd can configure applications to launch automatically upon server boot.

To register an application with systemd, a service file must be created in `/etc/systemd/system`. This process is typically automated by [Ansible](../development-tools/ansible) for roles that necessitate it.

## Commands

The following commands interact with systemd services, with *service_name* being the filename of the service in the systemd directory (e.g., `/etc/systemd/system/service_name.service`):

- `systemctl status *service_name*` - Displays the current status of a service.
- `systemctl start/stop *service_name*` - Starts or stops a service.
- `systemctl restart *service_name*` - Restarts a service.
- `systemctl enable/disable *service_name*` - Enables or disables a service to start automatically during server boot.
- `systemctl daemon-reload` - Reloads systemd to apply any changes to service files.

## Logs

Ubuntu includes `journalctl`, a command used to view logs for systemd services. You can access the logs of a specific service with `journalctl -u service_name`.

{{% notice info %}}
Not all applications send their logs to systemd for `journalctl` to capture. Some applications may log messages directly to files located in `/var/log/`, while others might use Sentry for logging.
{{% /notice %}}
