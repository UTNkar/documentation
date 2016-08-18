+++
date = "2016-08-18T15:22:46+02:00"
next = "/3applications/register"
prev = "/3applications"
title = "Drupal 7-based"
toc = true
weight = 5
+++

All UTN's own websites are based on Drupal7. For these websites a custom
template was developed, that could be customized for every committee. The main
website contains the bar at the top of the page, containing all links to the
other websites, this is automatically used on all the other websites.

### New Drupal 7 website

Because the template is rather peculiar (to say the least), it is best to start
a new Drupal 7 website from an available backup. This backup was provided by the
developers of the Drupal 7 template. It is currently available on the GleSYS
event server. The process of installing is rather easy:

1. Copy the files from backup to website location.
2. Create MySQL database.
3. Restore the database from the backup SQL file.
4. Edit the settings in `sites/default/settings.php` to match the URL and
database.
5. Create/Enable an NGINX configuration for the new website.

{{% notice info %}}

When using [Ansible](/5development_tools/ansible), steps 2 and 5, and part of
step 1 will automatically be done by the `drupal7_area` role.

{{% /notice %}}
