# Setting up a new Server/Droplet at Digital Ocean

For convenience, snapshots are available in the Digital Ocean. So the quickest
way to setup a new server/droplet is to select one of these:

- Base: A base Ubuntu 16.04 server.
- Webstack: Ubuntu 16.04 with NginX, PostgreSQL and PHP7 installed

To login to these images the following information is used:

- Username: jdekker
- Password: 6J.YjKjgrVD2#?tF8n4AKaw$wD{CZ7

For the setup, the following tutorial was used for the base steps:
[link](https://www.digitalocean.com/community/tutorial_series/new-ubuntu-14-04-server-checklist?utm_source=Customerio&utm_medium=Email_Internal&utm_campaign=Email_UbuntuDistroApacheWelcome).
After installing from the snapshot, you can rename the user to match your
personal preference (`usermod -l login-name jdekker`). You should then add your
ssh-key (it is explained in the tutorial) to the account and disable password
logins in `/etc/ssh/sshd_config`.

Congratulations, you've now setup a secure server!
