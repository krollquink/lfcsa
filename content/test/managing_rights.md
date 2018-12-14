---
title: "Managing_rights"
date: 2018-12-13T22:51:56+09:00
draft: true
---

# Managing rights!

## File Permission

* three user categories
	
	1. user

	2. group

	3. others

* three rights

	1. read ,r

	2. write ,w

	3. execute ,x

Three commands control the permissions associated with a file:

#### changes the owner of the file;
    chown *user:group* *file*

#### alters the owner group;
    chgrp *group* *file*

#### changes the permissions for the file. 
    chmod rights *file*

#### for *setuid*

	chmod 4000 *file*

#### for *setgid*

	chmod 2000 *file*

#### for *sticky bits*

	chmod 1000 *file*

### `setuid` and `setgid`

this file is relevant for executable file using the user or the group

### Changing the `umask`

this mask make a default permission for a file or directory when it created

`umask 002` will produce **file with permission 664** and **directory with permission 775**


### Changing File attributes

to change file attr

* immutable = file cannot be change or deleted

		chattr +i *file*

* append only = file only can be append

		chattr +a *file*
