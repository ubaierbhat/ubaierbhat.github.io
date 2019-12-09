---
layout: post
title: "who is using port"
date: 2019-12-09
---

# find out which applicaiton is using a particular port 
```bash
whoisusing() { lsof -i tcp:$1; }
```
### usage
```bash
$ whoisusing 4000
COMMAND  PID       USER   FD   TYPE            DEVICE SIZE/OFF NODE NAME
ruby    5425 macbookuser   12u  IPv4 0x748cf89b35036d9      0t0  TCP localhost:terabase (LISTEN)
```
