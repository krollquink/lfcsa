---
title: "System"
date: 2018-12-09T23:10:04+09:00
draft: true
---
## Soft Links and Hard Links
#### to create soft links

> ln -s *target* *link-name*

## Settings Time 

### Timezone

* use **tzdata** package to manage timezone

* to modify it can use 

> dpkg-reconfigure tzdata

* the configuration is stored in `/etc/timezone`

* the file from `/usr/share/zoneinfo` also copied to `/etc/localtime`

* if you want to change it temporarily use `$TZ` enviroment variable

#### Show Clock

> date 


#### Setup Hardware clock

> hwclock

set hardware clock to system clock

> hwclock --set --systohc

### Time Sync

* Use **NTP** to sync time across networks

for Client 

1. install **ntpdate** package

2. change the ntp server in `/etc/default/ntpdate`

for Server

1. local ntp server are provided by **ntp** package

2. edit the `/etc/ntp.conf` 

## Settings system locale
especially the date, monetary,currency

use `locale`

> locale 

list of enabled locale can be found in 

> /etc/locale.gen

this file can be edited by hand, but should use the `locale-gen` after mod

for system-default enviroment use below

> /etc/default/locale

this will inject all locale configuration in PAM

for system-default enviroment that will be loaded when user logged in is 

> /etc/environment


### File Encoding

to check file encoding

> file -ib [file name]

change file encoding

> convmv  -r -f [fileenco] -t [dest encoding [file name/or dir with -r]]

## Shell environment 

`bash` = standard shell  
`/etc/bash.bashrc` for **"interactive shell"** >> shell such as **xterm**  
`/etc/profile` for **"login shell"** >> shell that are use during login or via ssh or when using `bash --login`

## Autocomplete in bash
can be enable by uncommenting file in `/etc/bash.bashrc`

## Environment

global enviroment is stored in `/etc/enviroment`

* to change default editor in debian 

> udapte-alternatives --config editor



