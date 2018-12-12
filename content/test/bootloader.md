---
title: "Bootloader"
date: 2018-12-10T23:27:12+09:00
draft: true
---

# Bootloader

* **MBR** occupies first 512 bytes of disk

* generally **bootloader** are installed in **MBR**

Bootloader need to identify hard disk and its partition using /dev/sd\*

Example: 

> /dev/sda1 --> first disk first partition

> /dev/sdb3 --> second disk third partition


## GRUB 2 Configuration

* doesnt need to be invoke in each kernel upgrade

* GRUB can find the kernel in the file itself

#### Install GRUB in MBR of the disk

> grub-install */deb/sda*

### How GRUB define the hard disk

* GRUB usually naming the first hard disk as (hd0) , second as (hd1)  

* GRUB store the name in `/boot/grub/device.map`
* this file can be createad using `grub-mkdevicemap`

### GRUB configuration

* GRUB configuration is stored in `/boot/etc/grub`

* usually this file is not modify by hand because `update-grub` will overwrite the file

* change are made in `/etc/default/grub.cfg` or `/etc/grub.d/50_custom`

* for more complex configuration just add the script inside `/etc/grub.d`




## Identifying disk `/dev` or /udev

* You can identify the disk named by `udev` in `/dev/disk/by-id/`
```
johntravolta:/dev/disk/by-id# ls -l
total 0
lrwxrwxrwx 1 root root  9 23 jul. 08:58 ata-STM3500418AS_9VM3L3KP -> ../../sda
lrwxrwxrwx 1 root root 10 23 jul. 08:58 ata-STM3500418AS_9VM3L3KP-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 23 jul. 08:58 ata-STM3500418AS_9VM3L3KP-part2 -> ../../sda2
```


