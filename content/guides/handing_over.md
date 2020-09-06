+++
title = "Handing over the Admin position"
date =  2019-04-03T21:58:52+02:00
weight = 15
toc = true
+++

## Introduciton
**This guide is only for the system administrator.**

There comes a time when the admin must step down from his/her position and allow for a new person to take his/her place.

## Handing Over
When handing over the position, the following things must be done

**The new admin must get access to as well as a tour of the following:**

- Digital Ocean (Must be set as an owner)
- Cloudflare
- Glesys
- Google Account (drive, mail etc.)
- Github (Must be set as an owner)
- Project moore (Must become an admin)
- The UTN facebook app at [developers.facebook.com](https://developers.facebook.com)

**The new admin must get ssh access to the servers aswell as an admin account on every server:**

- The new admin must create a new ssh key which the old admin adds via ansible
- The old admin uses ssh to log in to the servers and creates a new account for the new admin, one server at the time. 
    - `adduser [username]`
    - `usermod -aG sudo [username]`
- Test if the new admin can ssh into the server and become root by using `sudo su`

**The new admin must also setup ansible on his/her computer:**

- Install ansible. Instructions can be found [here](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html). If the new admin uses windows, he/she can use `ubuntu for windows` to install ansible.
- Follow the [installation instructions](/development_tools/ansible/) for the UTN ansible repository

**The new admin should also do the follwing things:**

- Install [Hugo](https://gohugo.io/getting-started/installing)

**The admin should also be aware of the following things:**

- Only those who should have access, shall have access
- There is a mail group called [it-gang@utn.se](mailto:it-gang@utn.se) that reaches out to all IT responsible people in UTN:s committees
