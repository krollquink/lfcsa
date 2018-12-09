---
title: "Dpkg"
date: 2018-12-04T21:17:58+09:00
draft: true
author: "Khairul"
tags: "dpkg"
---

#Debian Package manager

deb use `ar,tar, or gzip,bzip`
`ar` is old program, we usually use `tar`

## ALl about `dpkg`!!
debian package manager

install package 
> dpkg -i vim.deb

configure package 
> dpkg -configure vim.deb

remove package
> dpkg -r vim.deb
> dpkg -P vim.deb <-- to remove configuration too

list all installed package
> dpkg -l {package-name} 
> dpkg -l vim

list where the package is installed
> dpkg -S {package-name}
> dpkg -S vim

use grep to search
> dpkg -l | grep vim

## ALl about `apt`!!
install package
> apt install {package-name}

remove package
> apt remove { package-name}

search 
> apt search vim

## ALl about `apt-cache`!!
main use is to query about apt-cache
can also be used to search for a package name

> apt-cache search {package-name}
> apt-cache search vim

## ALl about `tar`!!

> -t = test label 
> tar -czvf <file.tar.gz> <directory>

## ALl about `zip`!!

bzip2
> zip **-Z bzip2** tar.bzip2 /tar 
for directory
> zip **-r** -Z bzip2 tar.bzip2 /tar 

### `ar` package manager

## `aprox` debian cache proxy for debian cache package
can be use to proxy debian package downloaded from the internet 
the downloaded file can be get by others by setting up the approx server in `/etc/sources.list`
