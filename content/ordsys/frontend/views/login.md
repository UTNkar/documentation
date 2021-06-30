+++
title = "Login view"
date =  2021-06-08T11:44:12+02:00
weight = 1
+++

The login view is automatically displayed if a user opens the system without being authenticated.

![login view](/images/ordsys/views/login.png)

If a user is not authenticated, they will first be taken to the login screen.

The login screen essentially consists of three form fields. A drop-down list of **organisations**, which enables a drop-down list of **users** within that organisation and lastly a **password** field.

The user accounts are managed by their respective organisation's administrator. More on this can be found in the backend section.

{{% notice info %}}

Due to a bug, sometimes logging in yields the message "An unknown error occured, please try again". If this happens, try clearing all cookies from the utn.se domain in your browser.

{{% /notice %}}
