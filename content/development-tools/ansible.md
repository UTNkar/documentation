---
title: "Ansible"
toc: true
weight: 25
---

Ansible is an open-source automation tool used to manage configurations, deploy applications, and orchestrate complex IT tasks. It simplifies repetitive tasks and ensures that environments are configured consistently.

Before diving into the UTN Ansible setup, ensure Ansible is installed on your system. For installation instructions and initial setup, refer to the [UTN documentation GitHub repository](https://github.com/UTNkar/documentation/).

Ansible's architecture includes several components that work together:

- **Playbooks**: YAML files that describe the tasks to be performed on the servers. They are the starting point for Ansible automation.
- **Roles**: Pre-defined tasks for accomplishing a specific part of a configuration or setup. Roles can be included in playbooks.
- **Handlers**: Special tasks within a playbook or role that run when notified by another task if a change occurs.
- **Variables**: These allow you to manage dynamic values within your playbooks and roles.
- **Templates**: Files that contain variable placeholders that are replaced with actual values during playbook execution.
- **Tags**: Labels that can be applied to tasks, allowing you to run a specific part of a configuration without executing the whole playbook.
- **Files**: Static files or scripts that can be deployed to servers.

### Vault

`ansible-vault` is used to securely store sensitive data like passwords. You can edit (`ansible-vault edit file.yml`) or view (`ansible-vault view file.yml`) encrypted files with the appropriate ansible-vault commands.

### Playbooks

UTN's Ansible repository contains several playbooks designed for specific purposes. To run a playbook, use the `ansible-playbook` command followed by the playbook name, like so: `ansible-playbook moore.yml`. This will execute the tasks defined in the `moore.yml` playbook. To run a playbook with specific tags, include the `--tags` option: `ansible-playbook playbook.yml --tags "tag1,tag2"`. To exclude tags, use the `--skip-tags` option.

{{% notice tip %}}

When running playbooks that operate on multiple servers you have to use `ssh-add` to save your passphrase so you don't have to supply it manually. If you can't run `ssh-add` try running `eval $(ssh-agent -s)`.

{{% /notice %}}

 Here is a detailed list along with explanations for the available tags:

#### moore.yml

Deploys Project Moore and sets up necessary dependencies. **Available tags**:

- `setup`: Installs dependencies and sets up the database.
- `deploy`: Downloads and installs the latest version of Project Moore.
- `nginx`: Configures NGINX for Project Moore.

#### documentation.yml

Updates the UTN documentation website. **Available tags**:

- `deploy`: Fetches and deploys the latest documentation updates.
- `nginx`: Configures NGINX for the documentation site.

#### bocken.yml

Manages the Bocken system, a vehicle booking system for UTN. **Available tags**:

- `setup`: Sets up dependencies and database.
- `deploy`: Installs the latest version of Bocken.
- `nginx`: Configures NGINX for Bocken.
- `cron`: Sets up cron jobs for periodic tasks.

#### custom_web_babbage.yml

Deploys custom applications to the Babbage server. **Available tags**:

- `nginx`: Sets up NGINX for the custom web applications.
- `logs`: Configures logging for each application.
- `database`: Manages databases for the applications.

#### common.yml

Performs initial server configurations. **Available tags**:

- `users`: Manages user accounts on the server.
- `firewall`: Sets up firewall rules for security.

#### custom_web.yml

Deploys non-Drupal applications to the Turing server.

#### drupal7.yml

Deploys Drupal 7 applications to the Babbage server.

#### survey.yml

Deploys LimeSurvey to the Turing server.

#### upgrade.yml

Updates all servers with the latest packages and security patches.

#### webserver.yml

Installs additional requirements for webservers, like mail servers.

### Managing Users and Logins

Ansible manages user logins primarily through the `logins` role. SSH keys provided in `files/pubkeys` are associated with user accounts. Adding a public key grants access, and removing it revokes access.

When transferring responsibilities within UTN, ensure that new public keys are distributed and old ones are removed to maintain security and proper access.

#### Adding a User

1. Guide the new user to generate an SSH key following [these instructions](../developing-for-utn/ssh-keys).
2. Receive the user's public key and add it to the appropriate file in `files/pubkeys`.
3. Create an entry in `vars/users.yml` for the new user.
4. Apply changes by running the `common.yml` playbook with the necessary tags.

#### Removing a User

1. Add the user's name to the `old_users` list in `vars/users.yml`.
2. Remove their public key from `files/pubkeys`.
3. Apply changes by running the `common.yml` playbook with the necessary tags.

{{% notice warning %}}

Always ensure that you have the latest version of the repository and that you are aware of any changes that might affect the server environment before running any playbooks.

{{% /notice %}}
