---
title: "Setting Up New Websites"
toc: true
weight: 10

---

This guide is intended solely for the system administrator.

Setting up new websites is a common responsibility for the system administrator. The process has been greatly streamlined by using [Ansible](../development-tools/ansible).

## Instructions for Turing and Babbage

1. Determine the requirements of the website and choose the appropriate server for hosting. Information about the servers is available [here](../infrastructure/digital-ocean).

2. Log into Cloudflare and add a new CNAME record for the site.
    - The *name* should be the subdomain (e.g., `polhacks` for `polhacks.utn.se`).
    - The *value* should be the full URL to the chosen server.
    - Ensure the record is proxied (orange cloud) unless it's a multi-level domain, in which case do not proxy it.

3. Choose an existing user or create a new one to own the website. Follow the user creation steps on the [Ansible page](../development-tools/ansible/#add-a-user).

4. Create a database password by running `ansible-vault edit vars/passwords.yml` and use a password generator for a strong password (at least 16 characters long).

5. In the *ansible/vars* folder, add the new site by duplicating an existing site's configuration and modifying the parameters. Check the [Ansible page](../development-tools/ansible/) for explanations of the files and available nginx templates.
    - Assign the desired nginx template to the *template* variable.
    - Set the *user* variable to the user from step 3.
    - Assign the password variable name from step 4 to the *password* variable.

6. Execute the corresponding playbook with `ansible-playbook the_corresponding_playbook.yml`.

The website should now be set up, and you can hand it over to its new owner. If the new site uses **Drupal**, additional steps are required, detailed below.

### Extra Instructions for Drupal

1. Download `base.utn.se.zip` and `base.sql.zip` from the admin's Google Drive to your computer.

2. Transfer these files to Babbage with `scp base.*.zip your_username@babbage.utn.se:/home/your_username`.

3. SSH into Babbage and unzip the files with `unzip 'base.*.zip'`.

4. Copy the unzipped website files to the new site's directory `cp -R --no-preserve=mode,ownership balen.utn.se/public/ /var/www/<site-name>.utn.se/`.

5. Import the SQL data with `mysql -u[user] -p [database] < balen.sql`.
    - Replace *user* with the created/selected user.
    - Use the previously created password when prompted.

6. Update `/var/www/<site-name>.utn.se/public/sites/default/settings.php` with:
    - The base URL.
    - Database name.
    - Database user.
    - Database password.

7. You may need to run the Drupal7 playbook again and adjust permissions.

8. Update Drupal by navigating to the public directory of the site `cd /var/www/<site-name>.utn.se/public` and running `drush up`.

9. Visit `<site-name>.utn.se/user` and request a new password for [admin@utn.se](mailto:admin@utn.se).

10. Once logged in, create a new admin user for the new website owner with a temporary password.

11. Notify the new owner via email that their website is ready.

## Instructions for Moore

Moore is different from Turing and Babbage. New sites on Moore are created via the admin panel.

1. Add a DNS record on Cloudflare following the same steps as for Babbage and Turing.

2. Update the Moore playbook in the Ansible repository with the new domain in the server names list. If you don't want to push the latest changes in the repository, you can use the `nginx` tag.

3. Run the Moore playbook using `ansible-playbook moore.yml --tags nginx` to avoid updating Moore if not necessary.

4. In Moore's admin panel, create a new site and homepage, filling in the English and Swedish names.

5. Add a new website under settings using the URL from step 1 and link it to the newly created site.

6. Create a new collection for the website owners for images and videos.

7. Create or amend a group with access to the new site and collection for images, documents, and videos.

8. Ensure the new owner has the appropriate group assigned to their position or directly to them.

9. Inform the new owners that their website is ready and explain the collection where they can store their images, documents, and videos.
