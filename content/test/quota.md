---
title: "Quota"
date: 2018-12-14T12:22:54+09:00
draft: true
---

# Disk Quota!

to allow limiting disk space allocatied to a user or group

* To activate quota in filesystem , you have to indicate `usrquota` or `grpquota` in
`/etc/fstab` 

* need to reboot after setting up `/etc/fstab`

#### Change User Quota

for user 

	edquota *user*

for group

	edquota -g *group*


