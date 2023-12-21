---
title: "Server Access (SSH keys)"
weight: 5
---

UTN servers use public key authentication. This method is advantageous because it allows for individual access control. Each person has a unique key, simplifying the process of revoking access without affecting others and reducing the risk of password leaks.

To gain server access, you must provide your **public key** to the system administrator. Your public key can encrypt information that only you can decrypt with your **private key**.

There are two ways to obtain an SSH key pair for UTN: request one from the system administrator or generate one yourself.

## Generating an SSH keypair

You can generate an SSH key pair using a terminal. Windows users may need [Git Bash](https://git-scm.com/downloads) or another terminal program.

Follow these steps to generate a key pair:

1. Run the command: `ssh-keygen -o -a 100 -t ed25519 -C "Your Full Name"`, substituting "Your Full Name" with your actual name.

2. At the prompt `Enter a file in which to save the key (/Users/you/.ssh/id_ed25519):`, press Enter or specify a memorable location.

3. Create a password when prompted.

4. You have now created an SSH key pair. Send the public key to the [system administrator](mailto:admin@utn.se). If you used the default location, use the command: `cat ~/.ssh/id_ed25519.pub` to display your public key.

5. Once the system administrator grants you access, connect to the servers using `ssh [server name].utn.se`. Note that accessing the server named moore requires additional instructions from the system administrator.
