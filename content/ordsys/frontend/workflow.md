+++
title = "Example workflows"
date =  2021-07-08
LastModifierDisplayName = "Albin Antti"
LastModifierEmail = "albin_antti@hotmail.com"
weight = 100
+++

Below is an example of how OrdSys can be used in two different scenarios, a Thursday's pub during normal circumstances, and in a pub tent during Covid-19 restrictions.

## Normal workflow
During a normal pub night, OrdSys would only be used to manage *food* orders, since beverage orders can be fulfilled immediately. Therefore, only the *bar view* and *kitchen view* will be in use.

#### 1. Placing an order
A customer approaches the bar and orders a beer and a hamburger. The bar staff hands the customer a table number sign and the beer, and proceeds to place an order for a hamburger to the given table number and send it through the system. The customer pays for the order before leaving the bar.

#### 2. Receiving and handling an order
The kitchen staff sees the newly placed hamburger order on a laptop in the kitchen set to the kitchen view. Once the kitchen staff is ready to prepare the burger, they press the rightward-facing arrow on the order, moving it to the *in progress* column to inform the bar staff and to make sure no-one else in the kitchen starts working on the same order.

Should orders start to pile up, the kitchen staff can get an overview of how many items are waiting in the lower right portion of the screen. This is to ensure that they can tell the bar staff if they run out of a certain menu item.

#### 3. Fulfilling the order
Once the hamburger is ready, they press the rightward-facing arrow on the order again to move it into the *done* column. Someone from either the bar or kitchen staff then picks up the burger order and carries it to whichever customer has the provided table number. Once the hamburger has been given out, the staff take the table number sign back to the bar staff, who upon receiving the sign marks the order as *delivered* in the bar view, removing it from view.


## Covid-19 workflow
During the Covid-19 pandemic, a lot of changes were made. One of the biggest changes this made to how pub events worked was that customers were no longer allowed to go to the bar and order food and drinks. Instead, the staff had to wait tables like at a normal restaurant, which required several new views to be added, as well as adding the option of ordering beverages as these could no longer be immediately fulfilled.

The below example is taken from how the TD reception had their pub nights in the TD reception tent every evening during the reception.

#### 1. Placing an order
A waiter using a tablet in the waiter view walks to a table with a customer seated. The customer orders a hamburger and a beer, which the waiter enters into the tablet together with the customer's table number. This order is then split into two orders - one containing the beer and the other containing the burger (since they'll be handled by different staff). The customer does not yet pay.

#### 2. Receiving and handling an order
The kitchen tent and the bar each have their own laptop, displaying the kitchen and tap view respectively (note that the bar view is for ordering, **not** fulfilling). Both the kitchen and the bar staff then start preparing the hamburger or beer in the same manner as the normal workflow example above. Since the tap can fulfil Once the items are ready, they move the respective order card into the *done* column.

#### 3. Fulfilling the order
During the event, another category of staff, *runners*, are monitoring the delivery view, where they can see all orders that are currently waiting, in progress or ready for pickup. When someone in the kitchen or tap view moves an order to the *done* column, it changes color and rises to the top of the delivery view. Once this happens, the runner walks to either the kitchen or the bar and picks up the respective order and mark it as *claimed* in the delivery view, to prevent other runners from trying to pick up the same order.

They then make their way to the table number provided by the order and hand it to the customer who proceeds to make the payment. This means that for an order of one beverage and one food items, two separate payments are made, but it ensures orders can't be given to the wrong customers. If the order is a group order, payment is either taken from one individual or the whole table at the runners discretion. Once the payment is completed, the runner marks the order as *delivered* in the delivery view, which removes the order from all views.
