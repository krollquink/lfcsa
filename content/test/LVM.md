---
title: "LVM"
date: 2018-12-17T22:59:16+09:00
draft: true
---

# LVM ( Logical Volume Manager)

Make volume management more flexible

#### Installation

	sudo apt install lvm2

### Phsyical Volume(PV)

#### Create PV

	pvrcreate */dev/sdd*

#### To check created PV

	pvdisplay -C

	pvdisplay */dev/sdd*

### Volume Group(VG)

#### Create VG

	vgcreate */dev/sdd*

#### To check created VG

	vgdisplay -C

	vgdisplay */dev/sdd*

### Logical Volume(LV)

#### create LV

	lvcreate -n *lv_critical* -L 1G *vg_critical*

#### Check LV

	lvdisplay -C

	fdisk -l
	
	ls -la /dev/mapper
	
	ls -la /dev/dm-*

#### Resize LV

	lvresize -L 7G vg_critical/lv_files	

#### resize th filesystem

	resize2fs /dev/mapper/vg_critical-lv_critical 



