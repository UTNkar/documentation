+++
date = "2016-08-25T22:05:07+02:00"
prev = "/1developing_for_utn/filezilla"
title = "Database Access (Datagrip)"
toc = true
weight = 25

+++

If you are not comfortable using the SQL prompt (`psql` or `mysql`), you might
want to consider accessing your database using a GUI. One such GUI is
[DataGrip](https://www.jetbrains.com/datagrip/), a database IDE for which
students can get a free license.

Connecting to a UTN database in DataGrip is relatively easy.

1. Once DataGrip is installed and started, add a new *Data Source*. (Make sure
you pick the right database software).

2. In the *General* tab, change the *Database*, *User*, and the *Password*, but
leave the *Host* and *Port* untouched.
![General Tab](/images/datagrip/general.png)

3. In the *SSH/SSL* tab, enable and fill in all settings for the *SSH Tunnel*.
![SSH Tunnel](/images/datagrip/ssh.png)

4. Test the connection in the *General* tab.

5. Congratulations! You are now connected to your UTN database.
