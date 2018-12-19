---
title: "Virtualization"
date: 2018-12-18T23:46:32+09:00
draft: true
---

# KVM ( Kernel Virtual Machine)

* KVM use 'libvirt'

##### Check the CPU for virtualization support 

	cat /proc/cpuinfo | egrep "svm|vmt"

#### install KVM

	sudo apt install qemu-kvm libvirt-bin virtinst virt-viewer virt-manager

#### create image pool at '/srv/kmv'

	virsh pool-create-as srv-kvm dir --target /srv/kvm
	
	or default

	/var/lib/libvirt/images

#### use 'virt-install' to create guest 

	virt-install --connect qemu:///system 
			   --virt-type kvm           
               --name testkvm            
               --ram 1024                
               --disk /srv/kvm/testkvm.qcow,format=qcow3,size=10 
               --cdrom /srv/isos/debian-8.1.0-amd64-netinst.iso  
               --network bridge=br0      
               --vnc                     
               --os-type linux           
               --os-variant debianwheezy

#### 'virsh' command

	virsh -c qemu://system

To start domain

	virsh -c qemu://system start *testkvm*

To stop domain 

	virsh -c qemu://system destroy *testkvm*

other
	
	suspend = suspend domain
	resume = unpause domain
	reboot = reboot domain
	autostart enable /--disable = enable/disable autostart domain
	undefine = remove all traces from libvirtd
	define = define /create VM
	dumpxml = show VM XML file
	help


#### use 'virt-viewer' to open the graphical console

	virt-viewer -c qemu:///system testkvm

### use vnc to open graphical console
	
	virsh -c qemu:///system vncdisplay *testkvm*

#### LXC !




