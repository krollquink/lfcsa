---
title: "RAID"
date: 2018-12-17T22:59:03+09:00
draft: true
---

# RAID ( Redundancy Array of Independent Disk )

To secure data from hard disk failure by introducing Redundancy

Data are stored in several physical disks

* Can be done by software or hardware

### RAID levels

#### Linear RAID

No redundancy, just end-to-end on other disk

	  1       2
	-----   -----
	| 1 |   | 4 |
	-----   -----
	| 2 |   | 5 |
	-----   -----
	| 3 |   | 6 |
	-----   -----

#### RAID - 0

Alternatively 1 ,2 is seperated

* no redundancy

* increasing read speed

* can use LVM for this

	  1       2
	-----   -----
	| 1 |   | 2 |
	-----   -----
	| 3 |   | 4 |
	-----   -----
	| 5 |   | 6 |
	-----   -----

#### RAID - 1

Mirroring RAID, make a same copy with the other disk

* kind of expensive

	  1       2
	-----   -----
	| 1 |   | 1 |
	-----   -----
	| 2 |   | 2 |
	-----   -----
	| 3 |   | 3 |
	-----   -----

#### RAID 4

Parity in One disk only

#### RAID 5

Parity for each block , spread amond the disk

	  1       2      3      2
	-----   -----  -----  -----
	|A1 |   |A2 |  |A3 |  |PA |
	-----   -----  -----  -----
	|B1 |   |B2 |  |PB |  |B3 |
	-----   -----  -----  -----
	|C1 |   |PC |  |C2 |  |C3 |
	-----   -----  -----  -----
	|PD |   |D1 |  |D2 |  |D3 |
	-----   -----  -----  -----

#### RAID 6

2 Parity for each block ,spread among the disk

	  1       2      3      2
	-----   -----  -----  -----
	|PA2|   |A1 |  |A2 |  |PA1|
	-----   -----  -----  -----
	|B1 |   |B2 |  |PB1|  |PB2|
	-----   -----  -----  -----
	|C1 |   |PC1|  |PC2|  |C2 |
	-----   -----  -----  -----
	|PD1|   |PD2|  |D1 |  |D2 |
	-----   -----  -----  -----

#### Setting up RAID

use `mdadm` command to set up RAID

	mdadm

#### Creating RAID

RAID 0

	mdadm --create */dev/md0* --level=0 --raid-devices=2 */dev/sdb* */dev/sdc*

RAID 1 

	mdadm --create */dev/md1* --level=1 --raid-devices=2 */dev/sdd* */dev/sde*

#### To check RAID

	mdadm --query */dev/md0*

#### To check the details

	mdadm --details */dev/md0*

#### save the config in `/etc/mdadm/mdadm.conf`


#### insert the ARRAY

	khai@ubuntusv2:~$ sudo mdadm --detail --brief --misc /dev/md0 >> /etc/mdadm/mdadm.conf

#### change the name of RAID

stop the raid

	mdadm --stop /dev/md0

	mdadm -Es

	mdadm --uuid=*8c229b6a:c20a3bfa:2d164f4f:84bee133* --update=super-minor --assemble */dev/md2*	
	ARRAY /dev/md0 metadata=1.2 name=ubuntusv2:0 UUID=8a38c25e:f372783e:5d8b78cb:cf82bec5   

