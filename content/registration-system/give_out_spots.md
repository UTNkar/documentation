+++
title = "Giving out spots"
date =  2020-11-11T10:04:35+01:00
weight = 30
+++

# Event spots
The site administrator for an event can choose to hand out event participation spots to raffle entries
by setting their status to 'won'. This can be done manually, for example in the case of giving out
spots to sponsors, or automatically and randomly through the admin interface.

## Manually giving out event spots
The site administrator can manually have people win by:
- Loggin in to the admin page (found at `/admin`)
- Enter the raffle entry page
- Select any number of raffle entries by checking the box left of each raffle entry
- Select the 'Set raffle entry to won' action.
- Press 'Go'

## Automatically raffle out spots
The site administrator can randomly raffle spots to raffle entries by:
- Loggin in to the admin page (found at `/admin`)
- Enter the raffle entry page
- Enter the desired percentage of UTN members to retrieve raffle slots
- Press "Raffle the slots!"

In the codebase, most of this logic is found in the `admin.py` file
