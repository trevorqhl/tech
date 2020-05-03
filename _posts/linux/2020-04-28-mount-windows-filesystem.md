---
layout: post
title:  "How to mount windows filesystsem on Centos"
date:   2020-04-28 22:30:56 -0400
img: linux.png
categories: Linux
tags: OS
---

![Linux]({{site.baseurl}}/images/linux.png)

###  Ensure epel is [installed][epel-url]

### Install fuse if not yet installed
```
dnf install fuse
modprobe fuse
```

### Install ntfs
```
dnf install fuse-ntfs-3g
```

### Mount Windows filesytem
```
mkdir /mnt/win
mount –t ntfs-3g /dev/sda2 /mnt/win
```

### Automate with fstab
```
/dev/sda2 /mnt/win ntfs defaults 0 0
```
[epel-url]: {{site.baseurl}}/linux/2020/04/21/install-epel.html

