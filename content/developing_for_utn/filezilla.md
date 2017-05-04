+++
date = "2016-08-25T21:11:41+02:00"
title = "File Access (FileZilla)"
toc = true
weight = 15

+++

If you don't like accessing your website's files through `ssh` and `scp`, you
might want to use a GUI. The following steps should be followed to access the
files using [FileZilla](https://filezilla-project.org).

1. Install and open FileZilla.

2. Open the *Site Manager* and click *New Site*.

3. You need to change the following settings
  - Enter the server *Host*
  - Select the *SFTP* protocol
  - Select the *Key file* logon type
  - Enter your *User*
  - Enter the location of your [*Key file*](/developing_for_utn/ssh_key)
![New Site](/images/filezilla/site_window.png)

4. Now click **Connect**.

5. You'll prompted with the question to convert the key. You should click **yes**,
and save the converted key in a convenient location.
![Convert Key](/images/filezilla/convert_key.png)

6. You'll get prompted for the password used for the key pair, enter the
password.

7. You should now be connected to the UTN server.
