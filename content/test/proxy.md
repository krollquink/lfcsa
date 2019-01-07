---
title: "Proxy"
date: 2019-01-07T12:21:09+09:00
draft: true
---

## PROXY(SQUID)

### Installation

	sudo apt get update

	sudo apt -y install squid

###  Basic Configuration

#### Setup ACL

Setup acl in `/etc/squid/squid.conf

	acl lfcsa src 192.168.201.222 

#### Enable the acl

	http_access allow lfcsa

### Setup Basic Authentication

#### Install `apache2-utils`

	sudo apt install apche2-utils

#### Create passwd file

	touch /etc/squid/passwd
	chown proxy: /etc/squid/passwd

#### Create Proxy user

	htpasswd /etc/squid/passwd lfcsa

#### Add Configuration

add this line in `/etc/squid/squid.conf`

	auth_param basic program /usr/lib/squid/basic_ncsa_auth /etc/squid/passwd   
	auth_param basic children 5 startup=5 idle=1                                
	auth_param basic realm Squid proxy-caching web server                       
	auth_param basic credentialsttl 2 hours                                     
	acl auth_users proxy_auth REQUIRED                                          
	http_access allow auth_users                                                

### Block specific website

#### create list of website 

create file `/etc/squid/block_website.acl` and make a list of website you want to block

	.abc.com

#### Add Configuration

add this line in `/etc/squid/squid.conf`
	
	acl block_url dstdomain "/etc/squid/block_website.acl
	http_access allow bad_urls


### Add Cache

#### Add Configuration

	cache_dir ufs /var/cache/squid 1000 16 256
	maximum_object_size 100 MB
	refresh_pattern .*\.(mp4|iso) 2880



