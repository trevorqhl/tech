---
layout: post
title:  "How to connect Windows machine with RDP from CentOS"
date:   2020-06-24 16:30:52 -0400
img: linux.png
categories: Linux
tags: OS
---

![Linux]({{site.baseurl}}/images/linux.png)

###  Install freerdp
```
yum install freerdp -y
```
### Connect to Windows via RDP
```
xfreerdp /v:ec2-88-88-88-88.us-east-2.compute.amazonaws.com /u:Administrator /p:password /size:1366x768
```
