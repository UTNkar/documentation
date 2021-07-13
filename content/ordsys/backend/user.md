+++
title = "The users table"
menutitle = "Users"
date =  2021-07-08
LastModifierDisplayName = "Albin Antti"
LastModifierEmail = "albin_antti@hotmail.com"
weight = 2
+++

The users table is accessed by logging in to the admin panel with your account and pressing the *Users* table. This will show you a list of all users belonging to your organisation. For each user you can also see their staff status. If a user has a green checkbox for their staff status, it means that the user account can be used to log in to the Django admin interface.

![user list](/images/ordsys/admin/userlist.png)

## Creating a user

As an organisation admin (Web(b) in the river rafting committee or Binär in the TD-reception committee among others), creating users for your organisation is useful. Although an organisation could get by with a single user (since accounts can be shared), using multiple users allow you to get more detailed statistics if using more than one bar, for example.

To create a new user, press the Add user button in the top right of the users table. This will take you to the user creation screen where you'll firstly be prompted for a username and a password for the user. Note that the username has to be unique, regardless of which organisation it belongs to.

### User permissions

As an organisation admin, there are in essence three different account types you can create. A normal user, a manager or an admin.

{{%expand "The different user types (Expandable)" %}}

Normal users can only access the front-end and are, as the name implies, intended to be used by regular staff.

A manager account is meant to be used by kitchen and bar managers (köks- och barchef) to change the available menu items in the system. These do not have access to the organisation's accounts.

An admin account is the account type with the most permissions, and is intended to be used by the users mentioned at the top of this page. Normally, there shouldn't have to be more than one admin account per organisation.

{{% /expand%}}

To create a normal account, you need only enter the username and password and press create.

To create an manager or admin account, first ensure that the "Staff" checkbox is checked. Without it, the account won't be able to access the Django admin interface. Then, select the corresponding user group in the left box and move it to the right, giving the user account the permissions for that account type. Done!

![groups](/images/ordsys/admin/groups.png)

Users can also be edited in this window, but doing so will require re-entering their password.

### Example user setups

An example of users for an organisation can be the following for Klubbverket:

* Eventmästare - staff account belonging to *admin* group. This account is responsible for managing the other accounts.
* Köksmästare - staff account belonging to *manager* group. This account is responsible for adding and removing menu items for each thursday's pub.
* Bar - normal account used to take orders in the bar.
* Kök - normal account used to prepare orders in the kitchen.
* Utebar - normal account used during the battle of the sections when food and drink can be ordered outdoors as well.
