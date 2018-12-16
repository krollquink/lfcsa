---
title: "Web"
date: 2018-12-16T12:46:57+09:00
draft: true
---

# Web Server!

this section will tell about various web server!

for http proxy or static pages  = maybe can consider `nginx` or `lighttpd`

## Apache Web server

### Installing Apache

install `apache2` package


#### Apache2 configuration layout directory structure

	/etc/apache2/
	|-- apache2.conf
	|       `--  ports.conf
	|-- mods-enabled
	|       |-- *.load
	|       `-- *.conf
	|-- conf-enabled
	|       `-- *.conf
	|-- sites-enabled
	|       `-- *.conf

#### Configuring virtual host

default conf for virtual host is `/etc/apache2/sites-available/000-default.conf`

cp the file from `/etc/apache2/sites-available/khaianna.com.conf`


Example:



	Listen 2000    <-- apache listen port 2000
	<VirtualHost *:2000>      <-- this virtual host listen in 2000
			ServerName www.khaianna.com       <- -server name                       
			ServerAlias *.khaianna.com         <-- server alias
			ServerAdmin webmaster@localhost                          
			DocumentRoot /var/www/html/khaianna.com           <-- server root dir       
																	 
			#LogLevel info ssl:warn                                 <--log level 
			ErrorLog ${APACHE_LOG_DIR}/error.log                    <-log 
			CustomLog ${APACHE_LOG_DIR}/access.log combined         <-- log 
	</VirtualHost>                                                   
																	 
																	 
	<Directory /var/www/html/khaianna.com >                       <-- directory options   
			DirectoryIndex index.abc                                 
			AllowOverride ALL                                        
																	 
	</Directory>                                                     

#### enable the HTTP server

	ap2ensite www.khaianna.com

	sudo systemctl start apache2	

#### disable the HTTP server

	ap2dissite www.khaianna.com

	sudo systemctl start apache2	

#### Enable/disable module in for Apache

Enable a module

this command actually only create/delete symbolic link in `/etc/apache2/mod-enabled` stored in `/etc/apache2/mod-availabe`

	a2enmod *module

	a2dismod *module

#### Enable SSL for web

enable SSL module 

	a2enmod ssl

#### enable group to edit file

	sudo chgrp -R webmasters /var/www/html
	sudo find /var/www/html -type d -exec chmod g=rwxs "{}" \;
	sudo find /var/www/html -type f -exec chmod g=rw  "{}" \;
