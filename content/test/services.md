---
title: "Services"
date: 2018-12-13T20:36:51+09:00
draft: true
---

# Managing `systemd` services

`systemd` manage process as a whole

each component is described as a "unit" files

this unit file is stored in

	/lib/systemd/system

and 

	/etc/systemd/system/

### Services and Target

*Services* described a process managed by `systemd`

Services is same as `init`

*Target* described as a state of the system

same as runlevel

* Service file only can be intepreted by `systemd` 

* need to use utility such as `systemctl`

### `systemctl` utility to manage services

#### list all available services

	systemctl

#### give a better view of a service

	systemctl status *services*

	systemctl status sshd.service <-- can be written as sshd 

#### start a service

	systemctl start *services*

	systemctl start sshd.service

#### stop a service

	systemctl stop *services*

	systemctl stop sshd.service

#### to configure service to started automatically at boot

	systemctl enable * services*

	systemctl enable sshd

#### to disable it

	systemctl disable *services*

	systemctl disable sshd

### `journalctl` logging system in `systemd`

to follow a service use 

	journalctl -f


