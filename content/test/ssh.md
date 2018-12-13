---
title: "Ssh"
date: 2018-12-13T22:17:18+09:00
draft: true
---

# All about `SSH`

`ssh` is the client

`sshd` is the server

### Key based authentication

1. Create a public/private keys

		ssh-keygen -t rsa 

2. send the key to the server

		ssh-copy-id *server*

3. now you can log in without passworf

### Encrypted tunnel for Port Forward

Reverse SSH!!

this is use to reverse the port of the remote to local

ssh -R 22:192.168.2.1:3000 john@192.168.2.1

this is use to forward the port of the remote to local

ssh -L 80:192.168.2.1:3000 john@192.168.2.1


### SSHD services!
