---
title: "Scheduling_task"
date: 2018-12-14T10:39:47+09:00
draft: true
---

## Scheduling task with　`cron`

responsible for executing  scheduled command and tasks


### How to use `cron`

* Each user have their own `crontab`

#### editing `cron`

	crontab -e

#### `crontab` formatting

* minute (0-59)

* hour (0-24)

* day (1-31)

* month (1-12)

* value of day of the week (0-7, 0 and 7 as SUNDAY, 1= MONDAY)

* command to write

#### put program in `/etc/cron.daily`,`/etc/cron.monthly`,`/etc/cron.weekly`, `/etc/cron.hourly`

#### to deny or allow user in  `crontab`

just write a user name file in `/etc/cron.allow` to alllow or `/etc/cron.deny` to deny


## Scheduling with `at`

`atd` = specific one line command to execute in single time in the future

example :

to execute at 12.50 Jan 30 2018 

	at 12.10 30.1.2018 -f *job*

to execute the command 1 minute from now

	at now + 1 minute -f *job*

the `jobs` must be a file that contain command to be executed

## Scheduling with `anacron`

complete `cron` for computer that not on all the times

the `cron` task usually execute after boot by `anacron`

