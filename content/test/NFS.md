---
title: "NFS"
date: 2018-12-25T10:47:36+09:00
draft: true
---

# Network File System

allowing remote access to filesystem across a network

all UNIX can access the system

when Windows is involved Samba is needed

#### NFS Server Installation

	sudo apt install nfs-kernel-server

#### Config File

edit the `/etc/exports`

	/srv/nfs2       192.168.201.0/24(rw,sync,no_subtree_check)                          

#### mount the FS

	mount 192.168.201.12/srv/nfs3 ~/nfs2

#### Configure `/etc/fstab`




