+++
title = "Accounts"
date =  2020-11-11T10:03:15+01:00
weight = 20
+++

## Creating an account
Raffle winners who have accepted their spot will have to register an account,
which automatically forms a team with the user as leader. These accounts are saved
and identified by the event user model, for example the `RiverraftingUser` in the case
of the River Rafting instance of the registration system.

## Properties
Accounts (i.e users) are identified by their person number/SSID. Users also have other
properties depending on each event; as an example, the `RiverraftingUser` has properties
describing if they want to buy lifevests and helmets or not.

To extend and include more properties, each event should edit their own user model,
found in `models/<event>` instead of editing the base user model.
