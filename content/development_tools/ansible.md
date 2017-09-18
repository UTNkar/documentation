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

The UTN Ansible files are located in a repository on
[GitHub](/5development_tools/github). Once you've installed Ansible, on your
local machine, and cloned the repository, you have to take the following steps:

- Create a file called `password.txt`, that contains the vault password (handed
over from one system administrator to the next).
- In the folder `host_vars`, create a file for each of the servers, named
according to the FQDN of the server (e.g., `turing.utn.se`), containing your
sudo password for that host.

You should now be able to run all playbooks in the repository using
`ansible-playbook [playbook]`.

### A Quick Introduction

Ansible is a deployment system. It helps automating the deployment of various
tasks while managing a server pool. Ansible repositories are rather rationally
split up into several parts:

- Playbooks are collections of tasks working to a common goal (for the
deployment) of an application. These files can be seen as recipes. These files
are also the main part of the repositories, these files will be run, using the
other files as resources.
- Roles are collections of tasks that will most likely be used in various
playbooks. Each role has a similar folder structure to the main Ansible
repository; this means that a role can be self-contained in the resources it
needs.
- Handlers are tasks that can be invoked when a tasks actually changes
something. These are usually *reload* or *restart* tasks. Handlers are stored
at the bottom of a playbook, tasks file, or in the `handlers` directory.
- Variables are located in among others the `vars` and `host_vars` directories.
The use of variables can help to avoid making duplicate playbooks/roles. (Some
variables might be encrypted using `ansible-vault`, this makes it possible to
share the repository publicly without sharing the passwords used)
- Templates are files that have interleaved variables, these can be used to
easily use the same file for multiple deployments. These files are located in
the `templates`
- Regular files used are located in the `files` directory.

### UTN Playbooks

Most Playbooks in UTN Ansible repository are simple deployments of applications
named after the application they deploy. However, there are a few special
playbooks. Here follows a list of the playbooks and their function:

- `common.yml` - Meant to execute initial server configuration (e.g., manage
users, add firewall).
- `upgrade.yml` - Playbook to run `apt-get update` & `apt-get distupgrade` on
all servers.
- `webserver.yml` - Installs and configures extra requirements for the
webservers (e.g., install a mail server)

### Managing logins

Currently the logins are managed using the logins role in Ansible. Most
management is done in the `vars/users.yml` file, which contains all variables
used by the role to determine which user has an account on which server.

Most accounts are shared by a committee, these account have the name of the
(abbreviation of the) committee. However, management at UTN, like the system
administrator, get their own personal account. To add an account create a new
entry in the `users` variable. To remove an account add the account name to the
`old_users` variable.

Access to shared accounts is managed using the SSH keys, these keys are stored
in `files/pubkeys` and have the name of the account. To give someone access to
the account, add their public key on a new line in the file. To take away their
access, remove the line in the file containing their public key.

After changes to the variables have been made, the `common.yml` playbook can be
executed to call the role.

{{% notice tip %}}

If you are having problems with ssh and supplying your passphrase try executing
`ssh-add` to save your passphrase so you don't have to supply it every time.

{{% /notice %}}
