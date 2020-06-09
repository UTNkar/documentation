+++
date = "2016-08-25T19:29:58+02:00"
title = "Server Access (SSH keys)"
toc = true
weight = 5

+++

All new UTN servers are accessed using public key authentication. The major
advantage over simple password authentication for UTN is that we won't be using
the same password with a whole group, but individual keys for every person in
the group. This allows us to easily deny access to a specific person and
minimizes the password leaking.

To give you access to the server, the system administrator will need to know
your **public key**; this is a key generated specifically for you. Only you can
read something encrypted using your public key, because you are the only one
that has access to your **private key**.

Their is two ways to get a SSH key pair for UTN. Either you ask the system
administrator, or you generated the keys yourself.

### Generating a SSH key pair

Generating a SSH key pair can be easiest done using the terminal. This means
that if you're on Windows, you'll need something like [Git
Bash](https://git-scm.com/downloads).

Once you open the terminal the process becomes rather easy.

1. Execute the following command `ssh-keygen -o -a 100 -t ed25519 -C "Your Full Name"`
(Using your own full name).

2. When prompted `Enter a file in which to save the key
(/Users/you/.ssh/id_ed25519):`, press enter (or type a location you'll remember).

3. Enter a password when prompted.

4. Congratulations! You have generated a SSH key pair, send your public key to
the [system administrator](mailto:admin@utn.se). (If you used the default
location you can use the following command: `cat ~/.ssh/id_ed25519.pub`)
