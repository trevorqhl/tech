---
layout: post
title:  "How to get a list of active IP from a local network"
date:   2020-05-08 08:30:52 -0400
img: linux.png
categories: Linux
tags: Network
---

![Linux]({{site.baseurl}}/images/linux.png)

1. Install nmap
```
yum install -y nmap
```
2. 
```
nmap -sn 192.168.200.0/24
```
