---
layout: post
title:  "How to install Centos 8 from internet"
date:   2020-04-21 08:30:52 -0400
img: linux.png
categories: Linux
tags: OS
---

![Linux]({{site.baseurl}}/images/linux.png)

1. Download the minimal iso from a [Centos Mirror][centos-iso]

2. If using windows, download [Rufus][Rufus] and install it to Windows

3. If using Linux, it just can't be easier
```
dd if=CentOS-8.1.1911-x86_64-boot.iso of=/dev/sdb
```
4. Burn the iso into a USB drive

5. Boot your computer using the USB drive

6. From Installation Source
```
Select On the network and use 
http://
Enter URL 
mirror.centos.org/centos/8/BaseOS/x86_64/os/
```
7. The rest are customized to your preference and kick off installation

[centos-iso]: http://mirror.csclub.uwaterloo.ca/centos/8.1.1911/isos/x86_64/
[Rufus]: https://rufus.ie/
