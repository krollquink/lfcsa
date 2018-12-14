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

this is use to reverse the 192.168.2.3:3000 port of the remote to local port 22 while tunnel is local and 192.168.2.1

	ssh -R 22:192.168.2.3:3000 john@192.168.2.1

this is use to forward the local port 80 to remote  port 8000

	ssh -L 8000:localhost:80 john@192.168.2.1


### SSHD services!
