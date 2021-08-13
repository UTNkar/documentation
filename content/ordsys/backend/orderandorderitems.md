+++
title = "The orders and order items table"
menutitle = "Orders and order items"
date =  2021-07-08
LastModifierDisplayName = "Albin Antti"
LastModifierEmail = "albin_antti@hotmail.com"
weight = 4
+++

Last but not least in the Django admin interface is the order and the order items table. Due to the relational nature of the database, an order is separated from its contents (meaning that the customer number and the menu items in the order go to different tables). As such, these two tables are very interlinked, but also a bit confusing to understand. Placing an order of a hamburger and a soft drink to customer number 25 will add a row to the *orders* table for the customer number, and create two rows in the *order items* table, linking both to the order in the *orders* table.

#### A note on these two tables
In short, these two tables are a bit confusing to read, and shouldn't really be used for anything other than inspecting individual orders for whatever reason. Even then, using the front-end for inspecting orders (either through the order history view or the statistics view) is recommended, as they will display the orders together with their respective order items.

## The orders table
![orders table](/images/ordsys/admin/orders.png)

In the orders table, you can see a list of all past and present orders placed under your organisation, with their respective customer numbers, order notes, statuses, timestamps and more. Pressing an order will open its inspector, where you can edit values how you see fit (note that a changing of status can only be made in the front-end).

## The order items table
![order items table](/images/ordsys/admin/orderitems.png)
In the order items table, you can see a list of all order items that have been placed, as well as to what order they belong, if they have any modifications (e.g. no onion) and what quantity has been ordered.
