---
title: "Iptables"
date: 2018-12-20T22:04:27+09:00
draft: true
---

# `netfilter` firewall

this firewall use `iptables`/`ip6tables` as a controller

## `netfilter` table

1. **filter** = filtering rules(accepting,refusing or ignoring packets)

2. **nat** = translate source and dest address

3. **mangle** = changes to the IP packet ( TOS field and options) 

4. **raw** = allow other modification of packet before they reach connection


## table chain

Each table got their own chains

1. **filter**
	
	INPUT

	OUTPUT

	FORWARD

2. **nat**

	PREROUTING

	POSTROUTING

	OUTPUT

### `iptables` command

	-t tables

default is **filter** table


#### Create new chain

	-N *new_chain*

#### Delete empty and unused chain

	-X *chain*

#### Insert Chain 

	-I *chain* rule_num rule

#### Delete chain

	-D chain rule_num

#### Flushes a chain

	-F *chain*

#### List all rules in chain

	-L *chain*

#### define default action/policy

	-P *chain*

### `netfilter` RULES

	*condition* -j *action* *action-options*

#### Conditions

matches protocol field

	-p [tcp|udp|icmp|icmmpv6]

use ! to negate 

matches source/destination address

	-s *address*

	-s *address/mask*

	-d *address*

	-d *address/mask*

matches interface

	-i *interface* <-- incoming

	-o *interface* <-- outgoing

Specific condition 

exp: `-p tcp`

	--source-port *port*

	--dest-port *port*

match state of the packet

	--state **state**

> Require `ipt_conntrack` kernel module

	NEW, ESTABLISHED,RELATED

#### `netfilter` ACTIONS

	ALLOW

	REJECT - reject with ICMP error packet

	DROP - ignore the packet

	LOG - send to `syslogd`

	ULOG - send to `ulog`

	*chain_name* - send to chain

	RETURN - 

	SNAT - apply source NAT
	
	DNAT - apply dest NAT

	MASQUERADE - apply masquerading

	REDIRECT - redirect to a given port
		--to-ports *ports*



