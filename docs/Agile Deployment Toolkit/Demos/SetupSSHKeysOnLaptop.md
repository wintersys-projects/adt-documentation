SSH KEYS

1. Check for existing SSH Keypairs if you are not sure.

>     /bin/ls -l ~/.ssh/id*

If you see a message "No such file or directory" that means that you don't have any existing SSH keypairs.

2. Depending on whether you have existing keypairs or not you can decide to use one of your existing keys or whether to generate a new keypair.
   If you have existing keys and you are geneating new a new keypair be careful not to overwrite your existing keys. If you are using an existing
   keypair that you already had, skip to step 4

4. Geneate a new keypair. You can choose your prefered algorithm from one of the following (you can apply a passphrase to access your keypair by entering it between the quotes for the -N option):

>     /usr/bin/ssh-keygen -t rsa -b 4096 -C "adt-laptop"
>     /usr/bin/ssh-keygen -t ecdsa -b 521 -C "adt-laptop"
>     /usr/bin/ssh-keygen -t ed25519 -b 521 -C "adt-laptop"

You will be now prompted to choose the location for the key pair.
Press Enter to save the key pair in the default location (~/.ssh/id_rsa).
You may be warned if you are about to overwrite any existing SSH keys and if you very sure you are OK with that press Y.
You will also be prompted for a passphrase to access your keys, its advisable to enter one. 




