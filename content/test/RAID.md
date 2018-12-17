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


