---
title: "User_group"
date: 2018-12-10T00:08:39+09:00
draft: true
---
# User and Group Manipulation

## User n Group Database
user database is stored in `/etc/passwd`
for encrypted password is stored in `/etc/shadow`

#### /etc/passwd file
```
john:x:1001:1002:john,,,:/home/john:/bin/bash 
```
put `/bin/false` to prevent the user from login 

### passwd

change expire date to make user need to change the pass

> passwd -e *user*

#### /etc/shadow file
the file where encrypted password is stored
```
micheal:$6$f0bfO.Db$G.vj5ehlXiaSEp7L8Pp1MNfyBk3oluzica9CoJngiUIw
52YEBG0hRbvBaezvum7AHzv./It14jVbFNn3IYl860:17875:0:99999:7:::   
```

#### /etc/group file
contain the group databese
```
micheal:x:1003: 
```

## Modifying USER Command

#### create User

> adduser *user*

template for new user can be edited in `/etc/adduser.conf`


#### change pass

> passwd *user*

#### change full name and to comment other

> chfn *user*

after using `chfn` the use `/etc/passwd` will change to below
```
john:x:1002:1002:John Academian,123,080-1111-1111,080-2222-2222,coworker:/home/john:/bin/bash               
```

#### list of available shell

> /etc/shells <--edit this file to enable/disable shell

#### change default shell

> chsh /bin/bash

#### change expire date of account

> chage 

#### show current user settings

> change -l *user*

#### disabling an account(locking an account)

> passwd -l *user*

#### enabling an account(unlock)

> passwd -u *user*


## Modifying GROUP Command
user will create a group which is their "main group"
this group is created during user creation

#### to  change main group

> newgrp

**setgid** can be set on directory which cause the file created in that directory
to automatically belong to the group

#### adding group

> addgroup *group*

#### delete a group

> delgroup *group*

#### modify group

> groupmod *group*

#### change group passwd

> gpasswd *group*

> passwd -g *group*

#### delete group passwd

> passwd -r -g *group*

#### Check database of user using `getent`

> getent passwd *user*



## Sharing Administrator Rights

change the `/etc/sudoers` to edit admin rights

#### use below command to edit `/etc/sudoers` 

> visudo 

#### To make a user to use `sudo` without pasword add this to `visuo`

>  john ALL= NOPASSWD: ALL

**dont forget to put this command on the last line !!!**

for more complex configuration please refer `man sudoers`

