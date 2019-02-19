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

Your working directory needs to be within your drupal installation to execute
any drush commands. This is the `public/` folder for our installations.

{{% /notice %}}


Drush will automatically make backups of the code before installing the new
versions.

#### Creating a new admin account via Drush

If you need to create a new admin account you can do so with drush using these commands:
1. `drush user-create username --mail="mail@example.se" --password="your_password";`
1. `drush user-add-role "administrator" username;`

### New Drupal 7 website

Because the template is rather peculiar (to say the least), it is best to start
a new Drupal 7 website from an available backup. This backup was provided by the
developers of the Drupal 7 template. It is currently available on the GleSYS
event server and Admin Google Drive. The process of installing is as follows:

1. Create a user for the new drupal site. This is done by adding a new user to the `ansible/vars/users.yml`. To do this copy an already existing user and change the parameters.
   * Run the ansible common playbook to add the user `ansible-playbook common.yml`
   * You might also have to create a public key for the playbook to run
1. In the `ansible/vars/drupal7_installations.yml` file create a new drupal 7 site. This can be done by coping and pasting an existing site and changing the parameters. Use the user you created in step 1.
    * Here you might also have to generate a password for the database
    * `ansible-vault edit /Users/jsnider/ansible/vars/passwords.yml`

    * Will let you edit the passwords.yml file
    * After this run the `ansible-playbook ansible/drupal7.yml` playbook
1. Now you should have a blank drupal installation for the site you are creating. Copy the files from a backup to the website location.
  1. Use scp to move files from a local computer to the server_name:
    * `scp base.utn.se.zip admin@babbage.utn.se:/home/admin`
    * `scp base.sql.zip admin@babbage.utn.se:/home/admin`
  1. Unzip with
    * `unzip base.utn.se.zip base.sql.zip`
  1. On the server use cp to move the 'public' folder to the root directory of the new drupal site:
    * `cp -R public/ ../../../var/www/<site-name>.utn.se/public`
3. Restore the database from the backup SQL file.
    * `mysql -u[user] -p [database] < balen.sql`
    * Where user is the user created in step 1 and the database is the name of the database. And `balen.sql` is what was unzipped from the `base.sql.zip`
4. Edit the settings in `sites/default/settings.php` to match the URL and
database.
    * You have to edit the base url information. Be careful to use http if you haven't setup certbot and use https: if you have setup certbot.
    * Also change the information for the database
5. (Create/Enable an NGINX configuration for the new website.) This is taken care of by ansible.
6. Update Drupal, and all installed modules, to the most current version
   * to become the user for a specific section:
   * `sudo -u [user] -g www-data -H`
   * to become the root user:
   * `sudo -u root -g www-data -H -i`
   * To see what users own which drupal sites run:
   * `ls -lah /var/www`
