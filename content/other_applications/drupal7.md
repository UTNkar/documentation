+++
date = "2016-08-18T15:22:46+02:00"
title = "Drupal 7-based"
toc = true
weight = 5
+++

All UTN's own websites are based on Drupal7. For these websites a custom
template was developed, that could be customized for every committee. The main
website contains the bar at the top of the page, containing all links to the
other websites, this is automatically used on all the other websites.

### Drush

[Drush](https://github.com/drush-ops/drush), short for Drupal Shell, is a small
tool that can be used to help manage Drupal installations. The application has
been installed on *Babbage*. For full usage, see the documentation, but the
following commands can be usefull:

- `drush core-status`, shows the core status and locational settings.
- `drush up`, update drupal core and modules (including database).

{{% notice info %}}
When using drush you must be in the `public/` folder.
{{% /notice %}}


Drush will automatically make backups of the code before installing the new
versions.

#### Creating a new admin account via Drush

If you need to create a new admin account you can do so with drush using these commands:

1. `drush user-create username --mail="mail@example.se" --password="your_password";`
2. `drush user-add-role "administrator" username;`

### New Drupal 7 website

Instructions on how to setup a new website with Drupal 7 can be found in the [guides](/guides/new_website).
