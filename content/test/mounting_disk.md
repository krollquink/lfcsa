---
title: "Mounting_disk"
date: 2018-12-12T12:43:30+09:00
draft: true
---

# Mounting and Unmounting Disk

#### to manually mount a device 

> mount -t *devicetype* *device(/dev)* *target dir*

Example:
to mount `/dev/sdb` ext3 filesystem to `/mnt/tmp`

> mount -t ext3 /dev/sdb /mnt/tmp

#### to manually unmount a device

> umount *target*


### Mount A device automatically

* To mount device both automatically and manually, we need to edit `/etc/fstab` file

* Normal user usually dont have any permission to mount or umount disk. 
This permission need to be write in `/etc/fstab`

Example of `/etc/fstab`
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=c964222e-6af1-4985-be04-19d7c764d0a7 / ext3 errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
UUID=ee880013-0f63-4251-b5c6-b771f53bd90e none swap sw  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto 0       0
/dev/fd0        /media/floppy   auto    rw,user,noauto  0       0
arrakis:/shared /shared         nfs     defaults        0       0
```
#### some of `/etc/fstab` **options**

* defaults = 




