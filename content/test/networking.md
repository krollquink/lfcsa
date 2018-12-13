---
title: "Networking"
date: 2018-12-09T23:48:57+09:00
draft: true
---
# Networking

### File to edit for networking

> /etc/network/interfaces

#### For Ubuntu 18 you need to use `netplan`

> /etc/netplan/config.yaml


### Basic debian networking
if **auto** is written the interface will be automatically configured during the boot

## ETHERNET inter

#### set up DHCP

```
auto enp0s3
iface enp0s3 inet dhcp
	hostname ubuntu16
```

#### static configuraiton
```
auto enp0s8
iface enp0s8 inet static
	address 192.168.1.10  # if 192.168.1.10/24 no need `netmask`
	netmask 255.255.255.0 
	gateway 192.168.1.1
	network 192.168.1.0
	broadcast 192.168.1.255
	dns-nameservers 1.1.1.1 8.8.8.8 # this is optional can be done using /etc/resolv.conf
```

for `netplan`

```
network:                                                            
    ethernets:                                                      
        ens160:                                                     
            addresses: []                                           
            dhcp4: true                                             
        ens192:                                                     
            addresses:                                              
                - 192.168.33.10/24                                  
            dhcp4: no                                               
            routes:                                                 
                - to: 192.168.31.0/24                               
                  via: 192.168.33.1                                 
            nameservers:                                            
                addresses: [8.8.8.8, 1.1.1.1]                       
                                                                    
                                                                    
    version: 2                                                      
```

#### configuring DNS server 

dns server can be configured in `/etc/resolv.conf`

```
nameserver 8.8.8.8
nameserver 1.1.1.1
```

for `netplan`

```
network:                                                            
    ethernets:                                                      
        ens192:                                                     
            nameservers:                                            
                addresses: [8.8.8.8, 1.1.1.1]                       
```

#### configurint static route

for `netplan`

```
network:                                                            
    ethernets:                                                      
        ens192:                                                     
            routes:                                                 
                - to: 192.168.31.0/24                               
                  via: 192.168.33.1                                 
```
#### Configuring hostname
PC hostname is stored in `/etc/hostname`

#### to configure name resolution for local
change the `/etc/hosts` file

#### the default way the machine will choose to resolve a name
the file to change this default is  `/etc/nsswitch.conf`


