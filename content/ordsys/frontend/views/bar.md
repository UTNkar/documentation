+++
title = "Bar view"
date =  2021-06-08T11:44:12+02:00
weight = 2
+++

The bar view is the main view for placing orders in OrdSys, intended to be used on a laptop placed in the bar during an event. A lot of the other views, such as the delivery view, waiter view and order history view are in fact just alternative renders of the bar view.

![bar view](/images/ordsys/views/bar.png)

##### 1. Organisation logotype
The logotype of whichever organisation you are signed in as. This can be pressed to return to the [index view](../).

##### 2. Current order area
In the current order area you can see whichever items are placed in your current order, together with how many of each and any eventual modifications to them. You can add more of a certain item by incrementing it with the plus sign, or remove it by reducing it's count to zero with the minus sign.

Should you wish to completely start over with an order, you can press the red reset button next to the Current Order heading.

##### 3. Order number and numpad
The order number represents either the table that the customer is seated at, or the number on the sign you give the customer when placing an order. Enter the number using the numpad. Once an order contains at least one item and an order number, you can place the order using the send-button which will have turned from gray to green.

##### 4. Order note
In this field you can enter anything that might be good to know about the specific order. Such things might be if the customer is seated outdoors, if they would like their order in a to-go container or perhaps if they would want it at a specific time. Order notes are seen in blue next to every order that has been placed.

##### 5. Menu and modification field
The menu list contains all menu items that can be ordered for the specific occasion. To add an item to your current order, press the respective button. There might be more menu items than can fit on the screen, in which case the list becomes scrollable.

There is also a modification field that you can use to modify a certain menu item, such as ordering a hamburger without onion. To do this, write whichever modification the customer wants in the modification field and press the menu item button. This will add the menu item to the current order with the requested modification next to it within parentheses.

{{% notice warning %}}

Note that modifications must be entered before you press the menu item button, not afterwards! This means the modification should be thought of as *no onion -> hamburger* instead of *hamburger -> no onion*!

{{% /notice %}}

##### 6. Membership checker
If you would like to check a person's UTN membership, you can ask them for their personal number and enter it here and press the "Check membership" button. If the person is a member the button will turn green, otherwise red.

##### 7. Order column
In this column all currently active orders can be seen, together with their customer number, their contents, when they were placed, eventual order notes as well as the order status.

An order can be pressed to bring up its information window.

{{% notice info %}}

The four different statuses that an order can have are:
**Waiting** for orders that haven't been processed yet.
**In progress** for orders that are currently being processed by tap or kitchen staff.
**Done** for orders that are ready to be delivered.
**In transit** for orders that are in the process of being carried out.

{{% /notice %}}


##### 8. The order information window
Pressing an order brings upp the following window:
![order information modal](/images/ordsys/views/bar_modal.png?width=35pc)

Here you can see the order a bit more clearly, as well as access individual order functions. The top-most button will either be "claim" or "delivered" depending on the order's status. Pressing the "claim" button will change the order's status to in transit, and pressing "deliver" (which can only be done on orders with the *in transit* status) will remove the order from view.

Pressing the edit button will open the order up for editing, see section 9.

Pressing the delete button will remove the order from the system entirely, without affecting the statistics.

##### 9. Editing an order

Pressing the edit button in the order information window will open the order in edit mode.
![order edit mode](/images/ordsys/views/bar_edit.png?width=25pc)

Editing an order is very similar to creating an order, and is useful since editing an order does not move it in the priority queue. You can add and remove items, change their modifications, the order note, customer number and more. The key difference is once you're done editing an order, pressing the send button will update the existing order instead of creating a new one.

{{% notice info %}}

An order can only be edited if it has the *waiting* status, since any other status means that the order is being or has already been fulfilled.

{{% /notice %}}

{{% notice warning %}}

Since beverage and food orders are split upon creation and sent to the tap and kitchen, respectively, you can not edit a food order to add a beverage or vice versa. If you need to add a beverage to a food order or vice versa, you must therefore create a new order.

{{% /notice %}}