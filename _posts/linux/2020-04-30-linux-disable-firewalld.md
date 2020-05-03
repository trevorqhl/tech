---
layout: post
title:  "How to disable FirewallD on Centos"
date:   2020-04-30 09:30:52 -0400
img: linux.png
categories: Linux
tags: OS
---

![Linux]({{site.baseurl}}/images/linux.png)

### Check if FirewallD is running
```
firewall-cmd --state
```
### Stop firewalld
```
systemctl stop firewalld
```
### Disable the FirewallD service 
```
systemctl disable firewalld
```
### Mask the FirewallD service which will prevent the firewall from being started by other services:
```
systemctl mask --now firewalld
```

