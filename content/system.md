---
title: "System"
date: 2018-12-09T23:10:04+09:00
draft: true
---


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
> file -ib <file name>

change file encoding
> convmv  -r -f <fileenco> -t <dest encoding <file name/or dir with -r>>


