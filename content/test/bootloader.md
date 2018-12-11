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

## Disk Partition

### MSDOS partition type

* this type of partition consist only 4 "primary" partitions

* ---> need to use "extended" partitions to make secondary partitions and the numbered  from 5

> /dev/sda5 --> first disk secondary partitions

* this partition table only can hold 2Tib size.....

### GPT partition type

* allow up to 128 partitions

* size max up to 8ZiB = around 8TB

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



