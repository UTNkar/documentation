---
title: "Drupal 7 Applications"
toc: true
weight: 5
---

All of UTN's own websites are built on Drupal7. A custom template was created for these sites, allowing for customization by each committee. The main website features a top bar with links to all other UTN websites. This top bar is automatically included in all other websites.

### Drush

[Drush](https://github.com/drush-ops/drush), also known as Drupal Shell, is a tool for managing Drupal installations. It is installed on the server named *Babbage*. Although complete instructions are available in the documentation, the following commands are particularly useful:

- `drush core-status`: Displays the status of Drupal core and location settings.
- `drush up`: Updates Drupal core and modules, including the database.

{{% notice info %}}
Make sure you are in the `public/` directory when using Drush.
{{% /notice %}}

Before installing new versions, Drush will automatically back up the existing code.

#### Creating a New Admin Account via Drush

To create a new admin account with Drush, use the following commands:

1. `drush user-create username --mail="mail@example.se" --password="your_password"`
2. `drush user-add-role "administrator" username`

### New Drupal 7 Website

For instructions on setting up a new website with Drupal 7, refer to the [guides](/guides/new-website).
