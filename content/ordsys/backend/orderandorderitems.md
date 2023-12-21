---
title: "Orders & Order Items"
weight: 4
---

Within the Django admin interface, the orders and order items tables are essential components that handle the details of transactions. These tables, due to the relational database structure, separate the overarching details of an order from the specific items within that order.

When an order is placed, for example, an order of a hamburger and a soft drink for customer number 25, a new row is entered into the *orders* table to represent the customer number, and two additional rows are created in the *order items* table. These rows in the order items table will link back to the corresponding order entry in the *orders* table, creating a relational structure.

{{% notice note %}}
These tables can be somewhat complex to navigate and are generally not intended for regular use beyond inspecting specific order details when necessary. For a more intuitive overview of orders, the front-end interfaces, such as the order history view or the statistics view, are advised. These front-end tools present orders and their associated items in a more consolidated and user-friendly format.
{{% /notice %}}

## Orders

The orders table displays a comprehensive list of all orders associated with your organization. This includes information like customer numbers, any notes attached to the orders, their statuses, and timestamps, among other details.

![orders table](/images/ordsys/admin/orders.png)

By selecting an individual order, you can access its inspector for detailed viewing and editing, although it's worth noting that changes to order status should be conducted through the front-end interface.

## Order Items

The order items table lists out all the individual items that have been ordered. It provides information about which order each item belongs to, any specific modifications requested (such as "no onion"), and the quantity of each item ordered.

![order items table](/images/ordsys/admin/orderitems.png)

In summary, while the orders and order items tables in the Django admin interface provide a detailed look at the ordering data, they are best used for specific administrative purposes, with the front-end serving as the preferred method for general order review and management.
