---
title: "Updating Drupal 7 with Drush"
weight: 15
toc: true
---

## Introduction

Drupal 7 comes with a built-in updater for maintaining the core and contributed modules. However, this built-in updater requires FTP access, which is not available since UTN uses SFTP. To update Drupal 7 installations, we use [Drush](../other-applications/drupal7), a command-line shell and scripting interface for Drupal.

### Instructions

1. Access the server using SSH: `ssh <your-username>@babbage.utn.se`.

2. Navigate to the directory containing the Drupal installation, typically the public folder: `cd public`.

3. Execute the update with Drush: `drush -y up`.

Allow Drush to complete the process, and your Drupal website should be fully updated.

{{% notice warning %}}
Before updating, review the release notes for each module to understand the changes. Some updates may require additional steps or modifications.
{{% /notice %}}
