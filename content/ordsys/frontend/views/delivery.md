+++
title = "Delivery view"
date =  2021-06-08T11:44:12+02:00
weight = 6
+++

The delivery view is a view intended to be used by runners carrying tablets or cell phones during events where food is carried out to customers by staff.

![delivery view](/images/ordsys/views/delivery.png)

In this view all currently active orders can be seen, together with their customer number, contents, when they were placed, eventual order notes as well as the order status.

An order can be pressed to bring up its information window.

{{% notice info %}}

The four different statuses that an order can have are:
**Waiting** for orders that haven't been processed yet.
**In progress** for orders that are currently being processed by tap or kitchen staff.
**Done** for orders that are ready to be delivered.
**In transit** for orders that are in the process of being carried out.

{{% /notice %}}


##### The order information window
Pressing an order brings upp the following window:
![order information modal](/images/ordsys/views/delivery_modal.png)

Here you can see the order a bit more clearly, as well as access individual order functions. The top-most button will either be "claim" or "delivered" depending on the order's status. Pressing the "claim" button will change the order's status to claimed, and pressing "deliver" (which can only be done on orders with the *claimed* status) will remove the order from view.

Pressing the delede button will remove the order from the system entirely, without affecting the statistics.

{{% notice tip %}}

When orders are picked up to be carried out, their respective orders should be claimed, so other staff don't attempt to deliver the same order.

{{% /notice %}}