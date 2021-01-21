# lxd-ssh-gateway
Forward incoming ssh connections for a single user into containers

Very simple example which demonstrates the concept..

My recomended LXD host configuration for /etc/ssh/sshd_config are:-
  PasswordAuthentication no

Then add a 'sandbox' user on your Linux server...

Then install the ~sandbox/bin/gw and a ~sandbox/ssh/authorised_keys
Limitation with this method is a key can only be used to forward to a single container.
See the authroied_keys.example for the command="$HOME/bin/gw <container name> ssh-rsa <public key> syntax.

Make sure the permissions/ownership are correct..
  #chown -R sandbox:sandbow ~sandbow
  #chmod -R g-rewx,o-rwx ~ssandbox/bin

The containers I've been building are Ubuntu 20.10 they don't need to run ssh to work nor do they need networking.

e.g.
   lxc launch ubuntu:20.10 container-X
