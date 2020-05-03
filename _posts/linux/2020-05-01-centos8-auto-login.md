---
layout: post
title:  "How to login to Centos automatically"
date:   2020-05-01 16:30:52 -0400
img: linux.png
categories: Linux
tags: OS
---

![Linux]({{site.baseurl}}/images/linux.png)

### Just need to add the entry below and reboot
```
# cat /etc/gdm/custom.conf 
[daemon]
AutomaticLogin=trevorl
AutomaticLoginEnable=True

```
