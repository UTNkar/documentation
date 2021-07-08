+++
title = "Database structure"
date =  2021-06-08T11:44:12+02:00
weight = 1
+++

As OrdSys is a Django-based system (at least for the back-end), the database structure is defined in `./backend/models.py`.

The following, as such, is a surface-level explanation of the database tables and how they relate to each other. For more in-depth information about the respective tables, their functions, meta descriptions and their attributes, look in the models file.

![database tables](/images/ordsys/technical/db_table.png)

Below is a short description of the different database tables:

### The User table
The User table contains the system's different user account. It was implemented as an override to Django's default user engine.

The User table has the following attributes:

| Attribute    | Description                                                                  |
| :----------- | :--------------------------------------------------------------------------- |
| **id**       | Unique numerical user ID. Automatically generated.                           |
| **username** | The user's username.                                                         |
| **password** | The user's password, hashed and salted by the Django authentication backend. |
| **is_staff** | Whether or not the user should be able to access the Django admin interface. |
| **org**      | The ID of the organisation the user belongs to.                              |

### The Order table
The Order table contains the rudimentary information about all placed orders, such as their customer number, status and eventual notes. Due to the database's relational nature, the actual food and drink contents of an order is not found in the Order table, but rather in the OrderItem table.

If someone places an order for a hamburger and a soda to customer #23, a row will be added to the Order table with customer number 23, and two rows will be added to the OrderItem table connecting a soda and a hamburger to the order in the Order table using its ID.

The Order table has the following attributes:

| Attribute            | Description                                                                                 |
| :------------------- | :------------------------------------------------------------------------------------------ |
| id                   | Unique numerical order ID. Automatically generated.                                         |
| beverages_only       | Whether or not the order is a beverage order.                                               |
| customer_number      | The number given to the customer when placing the order.                                    |
| created_timestamp    | Datetime stating when the order was created. Automatically updated.                         |
| delivered_timestamp* | Datetime stating when (if) the order was marked as delivered. Automatically updated.        |
| note*                | Additional information provided by the customer.                                            |
| status               | The status of the order. Can be either waiting, in progress, done, in transit or delivered. |
| user                 | The ID of the user that created the order.                                                  |
|                      | **Can be null.*                                                                             |

### The OrderItem table
The OrderItem table contains food and drink items belonging the orders in the Order table. Each row represents a certain quantity of a given menu item with any eventual special requests, connecting it to the ID of an order from the Order table.

One row could for example be *1x Hamburger (no onion) to Order #21*.

{{% notice note %}}

Since the menu attribute can't be null (we didn't want the database to fill with orders of 1x NULL to Order #NULL), rows in the OrderItem table are deleted in a cascading fashion if either their contained order or menu item is deleted. This is why it's preferable when changing the menu items for a given event to deactivate menu items rather than deleting them, as deleting a menu item will delete all order

{{% /notice %}}

The OrderItem table has the following attributes:

| Attribute         | Description                                                           |
| :---------------- | :-------------------------------------------------------------------- |
| menu              | ID of the menu item this specific row relates to.                     |
| order             | ID of the order the order item belongs to.                            |
| quantity          | Quantity of the menu item ordered.                                    |
| special_requests* | If the item has any special requests (e.g. "no onion", or "Breznak"). |
|                   | **Can be null.*                                                       |



### The MenuItem table
The MenuItem table contains all of the menu items (what items an order can contain) that are available for ordering within a given organisation. The menu item can either be a food item or a beverage item, changing where an order containing the item is sent.

A menu item can also be active or inactive. Inactive menu items are not displayed in the system (except for already placed orders containing it). This is preferable over deleting menu items for the reasons mentioned above.

The MenuItem table has the following attributes:

| Attribute | Description                                                                             |
| :-------- | :-------------------------------------------------------------------------------------- |
| id        | Unique numerical menu item ID. Automatically generated.                                 |
| item_name | The name of the menu item.                                                              |
| active    | Whether or not the menu item should be displayed in the front-end order views.          |
| beverage  | Whether or not the menu item is a beverage and should therefore be handled differently. |
| org       | The ID of the organisation the menu item belongs to.                                    |


### The Organisation table
The Organisation table contains all the different organisation that are currently in the system. The only information an organisation inherently contains is a name and which theme users belonging to that organisation should use, but they are used in many parts of the system to separate data.

{{% notice info %}}

All users need to belong to an organisation, meaning after a database wipe a superuser can't be created before adding an organisation. To solve this, use the *createorganisation* command found in manage.py.

{{% /notice %}}

The Organisation table has the following attributes:

| Attribute | Description                                                      |
| :-------- | :--------------------------------------------------------------- |
| id        | Unique numerical organisation ID. Automatically generated.       |
| name      | The name of the organisation.                                    |
| theme     | What theme the organisation should use. See [themes](../themes). |
