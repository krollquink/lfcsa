---
title: "Quota"
date: 2018-12-14T12:22:54+09:00
draft: true
---

# Disk Quota!

to allow limiting disk space allocatied to a user or group

* To activate quota in filesystem , you have to indicate `usrquota` or `grpquota` in

* To activate journaled quota in filesystem , you have to indicate `usrjquota=aquota.user` or `grpjquota=aquota.group` and `jqfmt=vfsv0` in
`/etc/fstab` 

* the options to mount journaled quota are available in `man ext4`

* need to reboot after setting up `/etc/fstab`

Example:

	UUID=26572ab6-f3d7-11e8-9eac-080027b28855 none swap sw 0 0                  
	UUID=26572ab7-f3d7-11e8-9eac-080027b28855 / ext4 defaults 0 0               
	UUID=28d9804a-f3d7-11e8-9eac-080027b28855 /home ext4 defaults,**usrquota** 0 0  

for journeld quota

	UUID=26572ab6-f3d7-11e8-9eac-080027b28855 none swap sw 0 0                  
	UUID=26572ab7-f3d7-11e8-9eac-080027b28855 / ext4 defaults 0 0               
	UUID=28d9804a-f3d7-11e8-9eac-080027b28855 /home ext4 defaults,usrjquota=aquota.user,grpjquota=aquota.group,jqfmt=vfsv0 0 0  


### Check the quota

You can check the quota enabled or not by

	quotacheck

	quotacheck -avugc

### Turn on the quota

Turn on the quota for user or group

	quotaon -vu *user*

	quotaon -vg *group*

> to Turn off the quota for user or group

		quotaoff -vu *user*

		quotaoff -vg *group*

#### Change User Quota

for user 

	edquota *user*

for group

	edquota -g *group*

#### `edquota` file

set soft=500M and hard = 600M

	Disk quotas for user khaianna (uid 1000): 
	  Filesystem                   blocks       soft       hard     inodes     soft     hard
	  /dev/sda4                    512140     512000     614400         35        0        0

#### to check quota 

	quota -u khaianna	

for human readable

	quota -s -u khaianna	

quota a based on block size --> 1024Bytes/block

	for 500M just 1024 * 500

soft = warning will be given after user exceeded the quota

to change grace period which soft limit will be change to hard
	
	edquota -t 

hard = cannot exceed this quota 

