---
title: "File Access (FileZilla)"
weight: 15
---

For those who prefer a graphical user interface (GUI) instead of using `ssh` and `scp` for file access, FileZilla is an option. Follow these steps to access your website's files using [FileZilla](https://filezilla-project.org):

1. Download and open FileZilla.

2. Access the *Site Manager* and click on *New Site*.

3. Update the following settings:
   - Specify the server *Host*.
   - Choose the *SFTP* protocol.
   - For logon type, select *Key file*.
   - Input your *User* name.
   - Provide the path to your [*Key file*](./ssh-keys).
   ![New Site](/images/filezilla/site-window.png)

4. Click **Connect** to proceed.

5. When prompted to convert the key, click **Yes**. Save the converted key to a location of your choice.
   ![Convert Key](/images/filezilla/convert-key.png)

6. Enter the password associated with your key pair when prompted.

7. You should now be connected to the UTN server.
