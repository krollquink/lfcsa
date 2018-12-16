---
title: "DNS"
date: 2018-12-15T15:23:20+09:00
draft: true
---


# DNS (Domain Name Server)

map IP to hostname

* DNS are managed in zones and each zone are matches either domain(or subdomain) or IP address range.



#### Installation

to install dns

	sudo apt install bind9

to install for testing and troubleshoot

	sudo apt install dnsutils


#### to setup cache nameserver

1. Set the file in `/etc/bind/name.conf.options`

2. change the `fowarders`


>	you can add the zone directory in `/etc/bind/name/named.conf.options` too

#### first setup a zone 

setup zone in  `named.conf.local` or make new file

	zone "khaianna.test" {
        type master;
        file "/etc/bind/db.khaianna.test";
	};

#### Setup a zone file
	
	$TTL    86400
	@       IN      SOA     khaianna.test. root.khaianna.test. (
								  9         ; Serial
							 604800         ; Refresh
							  86400         ; Retry
							2419200         ; Expire
							  86400 )       ; Negative Cache TTL
					NS      ns.khaianna.test.
	;
	ns      IN      A       192.168.10.10
	gw      IN      A       192.168.1.1

>	DONT FORGOT TO CHANGE SERIAL EVERY TIME YOU CHANGE THIS FILE

#### test the DNS

	[khaianna@khaianna-pc ~]$ dig @192.168.56.101 gw.khaianna.test A

	; <<>> DiG 9.13.4 <<>> @192.168.56.101 gw.khaianna.test A
	; (1 server found)
	;; global options: +cmd
	;; Got answer:
	;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 22010
	;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 2

	;; OPT PSEUDOSECTION:
	; EDNS: version: 0, flags:; udp: 4096
	; COOKIE: 598441d7bd0c8008874073625c15c0eb9ed7ded01c123f22 (good)
	;; QUESTION SECTION:
	;gw.khaianna.test.		IN	A

	;; ANSWER SECTION:
	gw.khaianna.test.	86400	IN	A	192.168.1.1

	;; AUTHORITY SECTION:
	khaianna.test.		86400	IN	NS	ns.khaianna.test.

	;; ADDITIONAL SECTION:
	ns.khaianna.test.	86400	IN	A	192.168.10.10

	;; Query time: 0 msec
	;; SERVER: 192.168.56.101#53(192.168.56.101)
	;; WHEN: 日 12月 16 12:06:56 JST 2018
	;; MSG SIZE  rcvd: 122


## Reverse DNS

From IP to hostname!

##### Set the zone

	zone "1.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/db.192.168.1";
	};


#### set up the DB

	$TTL    86400
	@       IN      SOA     ns.khaianna.test. root.khaianna.test. (
								  5         ; Serial
							 604800         ; Refresh
							  86400         ; Retry
							2419200         ; Expire
							  86400 )       ; Negative Cache TTL
	;
					NS      ns.khaianna.test.
	1       IN      PTR     gw.khaianna.test.

#### test the reverse DNS

	[khaianna@khaianna-pc ~]$ dig -x 192.168.1.1 @192.168.56.101

	; <<>> DiG 9.13.4 <<>> -x 192.168.1.1 @192.168.56.101
	;; global options: +cmd
	;; Got answer:
	;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 53590
	;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 2

	;; OPT PSEUDOSECTION:
	; EDNS: version: 0, flags:; udp: 4096
	; COOKIE: 1072ae876ab92430b2cf4b2f5c15c615a3799c8ba6868f19 (good)
	;; QUESTION SECTION:
	;1.1.168.192.in-addr.arpa.	IN	PTR

	;; ANSWER SECTION:
	1.1.168.192.in-addr.arpa. 86400	IN	PTR	gw.khaianna.test.

	;; AUTHORITY SECTION:
	1.168.192.in-addr.arpa.	86400	IN	NS	ns.khaianna.test.

	;; ADDITIONAL SECTION:
	ns.khaianna.test.	86400	IN	A	192.168.10.10

	;; Query time: 0 msec
	;; SERVER: 192.168.56.101#53(192.168.56.101)
	;; WHEN: 日 12月 16 12:28:58 JST 2018
	;; MSG SIZE  rcvd: 144

-----

## DSS Zone Transfer (SLAVE)

#### Enable transfer from master

Set the `allow-transfer` options

		zone "khaianna.test" {
        type master;
        file "/etc/bind/db.khaianna.test";
		allow-transfer { 192.168.56.254; }; <-- set secondary DNS here
	};


Set the `allow-notify` options for notify when there are changes

		zone "example.com" {
		type master;
		file "/etc/bind/db.example.com";
		allow-transfer { 192.168.1.11; };
		also-notify { 192.168.1.11; }; <-- add this to notify
	};

#### Setup secondary DNS

Set the `master`,`type`,`file` options

		zone "khaianna.test" {
        type slave;
        file "db.khaianna.test";
		master { 192.168.56.101; }; <-- set master DNS here
	};




	
