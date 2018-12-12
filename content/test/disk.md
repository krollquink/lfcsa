---
title: "Disk"
date: 2018-12-12T16:05:18+09:00
draft: true
---


## Disk Partition

### MSDOS partition type

* this type of partition consist only 4 "primary" partitions

* ---> need to use "extended" partitions to make secondary partitions and the numbered  from 5

> /dev/sda5 --> first disk secondary partitions

* this partition table only can hold 2Tib size.....

### GPT partition type

* allow up to 128 partitions

* size max up to 8ZiB = around 8TB

### Modifiying Partition

we can partition a disk using `fdisk` or `parted`

* `fdisk` for partition in MBR table

* `parted` is for partition in GPT


## Mounting and Unmounting Disk

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


### From New Disk to Mount to mountpoints 

1. Setup a disk

2. Check the disk kernel name using `fdisk` or `parted`
```
$ fdisk -l
khai@ubuntusv1:~/new_mount$ sudo fdisk -l                                     
Disk /dev/sda: 16 GiB, 17179869184 bytes, 33554432 sectors                    
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes                         
I/O size (minimum/optimal): 512 bytes / 512 bytes                             
Disklabel type: dos
Disk identifier: 0x63f1cd60

Device     Boot    Start      End  Sectors  Size Id Type                      
/dev/sda1  *        2048 15624191 15622144  7.5G 83 Linux                     
/dev/sda5       32507904 33552383  1044480  510M 82 Linux swap / Solaris      
Partition table entries are not in disk order.                                

Disk /dev/sdb: 2 GiB, 2147483648 bytes, 4194304 sectors                       
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes                         
I/O size (minimum/optimal): 512 bytes / 512 bytes                             

```
3. Start partitioning

> fdisk */dev/sdb*

> parted */dev/sdb*




