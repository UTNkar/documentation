---
title: "Handing Over"
weight: 15
toc: true
---

This guide is intended specifically for the system administrator of UTN.

There may come a time when a system administrator needs to pass on their responsibilities to a successor. The following steps are designed to ensure a smooth transition.

## Handover Checklist

When transferring the role to a new administrator, ensure the following actions are taken:

### Admin Access and Orientation

The incoming admin must be granted access to and be familiarized with the following accounts and services:

- Google Account (<admin@utn.se>), which provides access to:
  - Cloudflare
  - Digital Ocean
  - Sentry
- GitHub (UTNkar organization, should be given owner status)
- Project Moore (must be granted admin rights through the Wagtail interface)
- The Facebook page "Digitaliseringsgruppen"
- The Instagram account "digitaliseringsgruppen"

### Server Access and Administration

The incoming admin must also obtain SSH access to the servers and an admin account on each server:

- The new admin should generate an SSH key, which the current admin will add via Ansible.
- The current admin logs into the servers via SSH and creates a new account for the new admin:
  - Use `adduser [username]` to create the new user.
  - Use `usermod -aG sudo [username]` to grant admin privileges.
- Verify that the new admin can SSH into the server and escalate to root using `sudo su`.

### Ansible Setup

The incoming admin must set up Ansible on their local machine:

- Install Ansible following the instructions [here](https://docs.ansible.com/ansible/latest/installation-guide/intro-installation.html). For Windows users, WSL (Windows Subsystem for Linux) can be used to install Ansible.
- Follow the installation instructions for the UTN Ansible repository detailed [here](../development-tools/ansible/).

### Documentation Editing

The new admin should install Hugo to manage the documentation. Instructions for installing Hugo can be found [here](https://gohugo.io/getting-started/installing).

### Awareness and Security

The new admin should be conscious of the following:

- Access should be granted strictly on a need-to-know basis. Exercise caution with user permissions.
- There is a mailing group [it-gang@utn.se](mailto:it-gang@utn.se) that reaches all IT responsible individuals in UTN's committees. Use this for communications related to IT matters.

By following these steps, the new system administrator should be well-equipped to take over the role effectively.
