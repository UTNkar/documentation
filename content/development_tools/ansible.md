+++
date = "2016-08-17T13:14:16+02:00"
title = "Ansible"
toc = true
weight = 25
+++

Although it can be rather tricky to master, [Ansible](https://www.ansible.com)
is probably the most important tool when working with the UTN servers. All
applications have been set up in such a way, that most *server related* tasks
are done using Ansible. By using Ansible, the systems become easily
reproducible, and there is a form of automatic documentation for the steps taken
to launch a system.

### Setting up UTN Ansible

Installation instructions are located on [the GitHub repo](https://github.com/UTNkar/documentation/).

### A Quick Introduction

Ansible is a deployment system. It helps automating the deployment of various
tasks while managing a server pool. Ansible repositories are rather rationally
split up into several parts:

- *Playbooks* are collections of tasks working to a common goal (for the
deployment) of an application. These files can be seen as recipes. These files
are also the main part of the repositories, these files will be run, using the
other files as resources.
- *Roles* are collections of tasks that will most likely be used in various
playbooks. Each role has a similar folder structure to the main Ansible
repository; this means that a role can be self-contained in the resources it
needs.
- *Handlers* are tasks that can be invoked when a tasks actually changes
something. These are usually *reload* or *restart* tasks. Handlers are stored
at the bottom of a playbook, tasks file, or in the `handlers` directory.
- *Variables* are located in among others the `vars` and `host_vars` directories.
The use of variables can help to avoid making duplicate playbooks/roles.
- *Templates* are files that have interleaved variables, these can be used to
easily use the same file for multiple deployments. These files are located in
the `templates`
- *Tags* can be used to perform or skip certain tasks. Use the flags `--tags="tag1,tag2,..."` or `--skip-tags="tag1, tag2,..."` when running a playbook.
- Regular files used are located in the `files` directory.

#### The Vault

Some variables are encrypted with the use of `ansible-vault` such as the passwords. This makes it possible to
share the repository **publicly without sharing the passwords**.

To edit the contents use `ansible-vault edit path/to/file.yml`.

To view the contents use `ansible-vault view path/to/file.yml`.

### UTN Playbooks

These are the playbooks that currently exist within the unions [ansible repository](https://github.com/utnkar/ansible).

#### moore.yml

Sets up dependencies and the database and updates project moore to the latest version on the master branch in the moore github repo.

**Available tags**

- `setup`: runs all steps that setup dependencies and database.
- `deploy`: runs all steps that downloads and installs the latest version of moore.
- `nginx`: runs the nginx role

#### documentation.yml

Gets the latest version from the documentation github repo and updates the documentation on this website.

**Available tags**

- `deploy`: runs all steps that updates the documentation to the latest version
- `nginx`: runs the steps necessary to configure nginx for the documentation website

#### custom_web_babbage.yml

Deploys the applications specified in `vars/custom_installations_babbage.yml` to *babbage*.

**Available tags**

- `nginx`: runs the steps necessary to configure nginx for the documentation website
- `logs`: runs the steps necessary to setup the log files for each application
- `database`: sets up the database for each application

#### Other playbooks

- `common.yml` - Meant to execute initial server configuration (e.g., manage
users, add firewall).
- `custom_web.yml` - Deploys the applications specified in `vars/custom_installations.yml` to *turing*.
These applications aren't made with drupal so they need to be in their own playbook.
- `drupal7.yml` - Deploys all drupal 7 applications specifies in `vars/drupal7_installations.yml` to *babbage*.
- `survey.yml` - Deploys limesurvey to *turing*.
- `upgrade.yml` - Playbook to run `apt-get update` & `apt-get distupgrade` on
all servers.
- `webserver.yml` - Installs and configures extra requirements for the
webservers (e.g., install a mail server).

{{% notice tip %}}

When running playbooks that operate on multiple servers you have to use `ssh-add` to save your passphrase so you don't have to supply it manually. If you can't run `ssh-add` try running `eval $(ssh-agent -s)`.

{{% /notice %}}

### Managing users and logins

Currently the logins are managed using the logins role in Ansible. Most
management is done in the `vars/users.yml` file, which contains all variables
used by the role to determine which user has an account on which server.

Access to accounts is managed using the SSH keys, these keys are stored
in `files/pubkeys` and have the name of the account. To give someone access to
the account, add their public key on a new line in the file. This means that multiple people can have access to the same account. To take away their
access, remove the line in the file containing their public key.

When a committee or section switches to a new group of people, a new public key must be made for every person. This is because only those who should have access shold have access.

#### How to add a user

1. Send the new user the instructions found [here](/developing_for_utn/ssh_key/).
2. When you get a new key from the new person, remove the public key of the old person.
3. Create a new entry in `vars/users.yml` by copying another user and changing the parameters.
4. Apply changes

#### Remove a user

To remove an account, add the account name to the `old_users` variable and remove it from the `user` variable in `vars/users.yml`. Then apply the changes.

#### Apply changes

Apply the changes by running `common.yml`.
