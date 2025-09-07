# Passwordless SSH authentication

## Create a ssh key gen pair
```
ssh-keygen -t rsa -b 4096

Generating public/private rsa key pair.
Enter file in which to save the key (/home/thor/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/thor/.ssh/id_rsa
Your public key has been saved in /home/thor/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:AB5/Oh6pxWmERGBJcgJ8QEI2B6n9ka0alco10FzebgM thor@jumphost.stratos.xfusioncorp.com
The key's randomart image is:
+---[RSA 4096]----+
|XOOB=..          |
|oB=+o* .         |
|....o+E o        |
|. . Bo.O         |
| . = +X S        |
|  + o= + .       |
|   o. .          |
|  .              |
|                 |
+----[SHA256]-----+

```

## Copy Public Key to Each Remote Host
##### ssh-copy-id [remote_username]@[server_ip_address]
```
thor@jumphost ~$ ssh-copy-id tony@stapp01                         
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/thor/.ssh/id_rsa.pub"
The authenticity of host 'stapp01 (172.16.238.10)' can't be established.
ED25519 key fingerprint is SHA256:QiMdsoxRvREm6nKjIikLkuLX6Y2NChz+5Pt3KKBhzLo.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
tony@stapp01's password: 

Number of key(s) added: 1

Now try logging into the machine, with:   "ssh 'tony@stapp01'"
and check to make sure that only the key(s) you wanted were added.
```

## Now we can login to remote server without password.
Repeat the process for all app servers from jump server.
