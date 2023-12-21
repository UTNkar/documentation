---
title: "Menu Items"
weight: 3
---

In the menu items table of OrdSys, you can view and edit a list of all menu items that have been offered by your organisation during past events. Each menu item entry includes two checkboxes with specific functions:

- **Active**: This checkbox indicates whether the menu item is currently available for order in the front-end interface. If unchecked, the item will not appear as an option when placing orders.
- **Beverage**: This checkbox designates whether the item is a beverage, which determines if it should be displayed in the tap view rather than the kitchen view in the front-end.

![menu items](/images/ordsys/admin/menuitems.png)

{{% notice warning %}}
Due to the interconnected structure of the database, deleting a menu item is not advisable. Doing so would remove all orders containing that item from the order history, impacting statistical data. Instead of deletion, items that are currently not offered should be marked as inactive. This way, they can be easily reactivated if they return to the menu in the future.
{{% /notice %}}

## Creating a Menu Item

To introduce a new menu item for your organisation, click the "Add menu item" button located in the top-right corner of the menu items table. This action will lead you to a form where you can specify the item's name and its status as active and/or a beverage.

![creating a menu item](/images/ordsys/admin/menuitem-create.png)

Enter the name of the item, and select the appropriate options for whether it's a beverage. Finalize the process by clicking the "Save" button at the bottom right. The new menu item will be created and, if marked as active, will immediately be listed as an available choice in the front-end.
