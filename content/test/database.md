---
title: "Database"
date: 2019-01-07T22:21:25+09:00
draft: true
---

## Database 

#### Installation

	sudo apt install  mysql-client mysql-server

#### Start mysql services

	systemctl start mysql

#### Create database

	create database lfcsa ;

#### show database
	
	show databases ;

#### change database 

	use lfcsa ;


#### Delete Database

	drop database lfcsa ;


##################################

#### create tables

	create TABLE lfcsa (
	id Int(3),
	first_name Varchar(15),
	email Varchar(15)
	);

#### Show tables

	show tables;

#### show columns

	show columns from lfcsa;

#### Add columns

	ALTER TABLE exam ADD country Varchar (10) AFTER email;
#### show tables

	select * from exam;

#### insert values into table

	INSERT INTO exam VALUES ('1','abc','1111')

#### delete values in table

	DELETE from exam where id = 1;

#### update values in table

	UPDATE exam SET id = 3 WHERE first_name = 'abc';

#### delete column

	ALTER TABLE exam DROP country

#### rename table

	RENAME TABLE exam TO new_exam


##################################

#### Backup database

	mysqldump -u root -p lfcsa > abc.sql

#### Restore database 

	mysql -u root -p lfcsa < abc.sql
