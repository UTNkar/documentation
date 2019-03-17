+++
title = "Create a new Website"
date = 2019-03-16T19:24:25+01:00
toc = true
weight = 10

+++

## Introduction

**This guide is only for the system administrator!**

A common task for the system administrator is to setup new webistes. Thankfully this has been simplified a lot by [ansible](/development_tools/ansible/).

## Instructions for Turing and Babbage

1. Idenfify what the website requires and choose which server to place the site on. Details about the servers can be found [here](/infrastructure/digital_ocean/).

2. Log in to Cloudflare and add a new CNAME record for the new site. Look at the other CNAME records if you get confused.
    * The *name* should be the name of the subdomain, *e.g*. the name of the subdomain `polhacks.utn.se` is `polhacks`.
    * The *value* should be the full link to the server that you will place the website on.
    * Some sites need to have Cloudflares proxy (the cloud) activated and some need it to be turned off. Look at simillar records to see if it should be turned on or off.

3. Create a new user or select a existing one that will become the owner of the website. Instructions for creating a new user can be found on the [ansible page](/development_tools/ansible/#add-a-user).

4. Create a password for the database that will be created by running `ansible-vault edit vars/passwords.yml`. Use a password generator to create the password (at least 16 characters!).

5. Find the correct file in the *ansible/vars* folder and add the new site by copying another site and changing the paremeters. The files in *ansible/vars* are explained on the [ansible page](/development_tools/ansible/).
    * Set the *template* variable to `temp-http`. This is because all other templates requires SSL certificates which we will create in a later step.
    * Set the *user* variable to the user you created/selected in step 3.
    * Set the *password* variable to the name of the variable you created in step 4.

6. Run the playbook that corresponds to the file in the *vars* folder that you added the site to with `ansible-playbook the_corresponding_playbook.yml`

7. Go to the server you selected by using *SSH* and create a SSL certificate for the new site. Instructions can be found [here](/server_software/certbot/).

8. Exit the server and change the *template* variable to the template that you want to use. List of templates can be found on the [ansible page](/development_tools/ansible/).

You should now have a fully functional website and you can now hand over the new website to its new owner.

{{% notice info %}}
If you are creating a new site with **Drupal** you must perform the steps bellow.
{{% /notice %}}

### Extra instructions for Drupal

1. On the admins google drive there are two zip files called `base.utn.se.zip` and `base.sql.zip`. Downloads these to your computer.

2. Copy these two files to *Babbage* by running `scp base.*.zip your_username@babbage.utn.se:/home/your_username`

3. SSH into Babbage and unzip the files you copied with `unzip 'base.*.zip'`.

4. Copy the extracted files to the new site with `cp -R --no-preserve=mode,ownership balen.utn.se/public/ /var/www/<site-name>.utn.se/`

5. Import data to the database from the extracted sql file with `mysql -u[user] -p [database] < balen.sql`
    * *user* is the user you created/selected before.
    * When you get prompted for a password, use the password you created before.

6. Edit the following settings in `/var/www/<site-name>.utn.se/public/sites/default/settings.php`
    * The base url
    * The name of the database
    * The name of the user for the database
    * The passowrd to the database

7. You might have to run the drupal7 playbook again and change some permissions. TODO

7. Update the website. To do this you must stand in the website's public directory `cd /var/www/<site-name>.utn.se/public`. Now run `drush up`.

8. Go to the login page on the new site `<site-name>.utn.se/user` and request a new password. Your email is [admin@utn.se](mailto:admin@utn.se)

9. Once you've gained access, create a new admin user for the new owner of the website. Use a dummy password that the owner must change.

10. Send an email to the new owner with the good news!

## Instructions for Moore

Moore differs a bit from Turing and Babbage. New sites are created through the admin panel.

TODO: Add instructions
