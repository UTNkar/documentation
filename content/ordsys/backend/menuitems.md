+++
title = "The menu items table"
menutitle = "Menu items"
date =  2021-07-01T11:44:12+02:00
weight = 3
+++

In the menu items table, a list of all current and past menu items that have been used in events for your organisation can be seen and modified. For each menu item there are also two checkboxes:

* Active - Whether or not the menu item should be displayed in the menu when placing orders in the front-end (ergo, whether they are orderable or not)
* Beverage - Whether or not the menu item is a beverage and therefore should be sent to the tap view instead of the kitchen view in the front-end.

{{% notice warning %}}

Due to the relational nature of the database, deleting a menu item is not recommended, as it will also delete all orders with the given menu item from the order history which affects the statistics view.  
Instead of deleting orders, mark them as not active in case they're not being served at the moment, and reactivate them in the future if the menu item is placed back on the menu.

{{% /notice %}}

![menu items](/images/ordsys/admin/menuitems.png)

## Creating a menu item

To add a new menu item to your organisation, press the "Add menu item" button in the top-right corner. This will take you to a view where you can enter the name of the menu item as well as select whether or not it should be active and a beverage.

![creating a menu item](/images/ordsys/admin/menuitem_create.png)

Simply enter a name and select whether or not it a beverage and you're done! Pressing the create button in the lower right will create the menu item and display it in the front-end (provided *active* is checked).