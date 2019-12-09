---
layout: post
title: "what is my ip"
date: 2019-12-06
---

# find your local and public ip address
```bash
# find out your LAN IP
alias lanip="ifconfig en0 | grep inet | grep -v inet6 | cut -d ' ' -f2"
# find out your public facing ip address
alias webip="dig +short myip.opendns.com @resolver1.opendns.com"
```
### usage
```bash
$ lanip 4000
192.168.1.16
$ webip
172.217.20.4
```
