---
title: "Vim"
date: 2018-12-10T09:40:16+09:00
draft: true
---

# vim tip and tricks

## scroll simultenously

to scroll windows simultenously use

> :set scrollbind

> :set scb [!] # for boolean on/off


## use mark to jump around
set mark a at current cursor location
```
ma	#set a mark 

'a 	#jump to line of mark a (first non-blank character in line)

`a 	#jump to position (line and column) of mark a

d'a 	#delete from current line to line of mark a

d`a 	#delete from current cursor position to position of mark a

c'a 	#change text from current line to line of mark a

y`a 	#yank text to unnamed buffer from cursor to position of mark a

:marks 	#list all the current marks

:marks aB 	list marks a, B
```
