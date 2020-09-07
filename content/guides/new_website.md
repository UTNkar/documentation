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
    * Make sure that the record is proxied through cloudflare (*orange cloud*) unless it's a multilevel domain name. In that case the record should not be proxied since the provided SSL certificate from cloudflare wont work.

3. Create a new user or select a existing one that will become the owner of the website. Instructions for creating a new user can be found on the [ansible page](/development_tools/ansible/#add-a-user).

4. Create a password for the database that will be created by running `ansible-vault edit vars/passwords.yml`. Use a password generator to create the password (at least 16 characters!).

5. Find the correct file in the *ansible/vars* folder and add the new site by copying another site and changing the paremeters. The files in *ansible/vars* are explained on the [ansible page](/development_tools/ansible/).
    * Set the *template* variable to the desired nginx template. List of templates can be found on the [ansible page](/development_tools/ansible/)
    * Set the *user* variable to the user you created/selected in step 3.
    * Set the *password* variable to the name of the variable you created in step 4.

6. Run the playbook that corresponds to the file in the *vars* folder that you added the site to with `ansible-playbook the_corresponding_playbook.yml`

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

7. You might have to run the drupal7 playbook again and change some permissions.

8. Update the website. To do this you must stand in the website's public directory `cd /var/www/<site-name>.utn.se/public`. Now run `drush up`.

9. Go to the login page on the new site `<site-name>.utn.se/user` and request a new password. Your email is [admin@utn.se](mailto:admin@utn.se)

10. Once you've gained access, create a new admin user for the new owner of the website. Use a dummy password that the owner must change.

11. Send an email to the new owner with the good news!

## Instructions for Moore

Moore differs a bit from Turing and Babbage. New sites are created through the admin panel.

1. Create a DNS record on cloudflare in the same way as in the instructions for Babbage and Turing.

2. Add the new domain to the list of server names in the moore playbook in the ansible repository.

3. Run the moore playbook in the ansible repository. You can use the tag `nginx` if you don't want to update moore to the latest version at the same time.

4. Go to moore and create a new site in wagtail admin. Create a homepage and fill in the english and swedish name for the site.

5. Create a new website under settings with the URL created in the first step and select the newly created site.

6. Create a new collection (*samling*) for the owners of the new website so that they have somewhere to place pictures and videos.

7. Create a new group or modify an existing and give that group access to the site and the collection for images, documents and videos.

8. Make sure that the new owner is applied to a position that has the group assigned to it or that the owner is directly assigned to the group.

9. Tell the new owners that their website is available and tell them that they have their own collection where they can put their images, documents and videos.
