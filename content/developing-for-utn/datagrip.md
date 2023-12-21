---
title: "Database IDE (DataGrip)"
toc: true
weight: 25
---

For those who prefer not to use the SQL command line (`psql` or `mysql`), a graphical user interface (GUI) like [DataGrip](https://www.jetbrains.com/datagrip/) can be a user-friendly alternative. DataGrip is a database IDE available for free to students.

To connect to a UTN database using DataGrip, follow these steps:

1. Install and launch DataGrip. Add a new *Data Source*. Make sure to select the correct database software.

2. Go to the *General* tab. Update the *Database*, *User*, and *Password* fields. Keep the *Host* and *Port* settings as they are.
   ![General Tab](/images/datagrip/general.png)

3. Switch to the *SSH/SSL* tab. Enable the *SSH Tunnel* and enter all the necessary settings.
   ![SSH Tunnel](/images/datagrip/ssh.png)

4. Use the *General* tab to test the connection.

5. If the test is successful, you are now connected to your UTN database.
