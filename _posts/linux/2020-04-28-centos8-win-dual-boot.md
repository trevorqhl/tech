---
layout: post
title:  "How to dual boot Centos 8 and Windows"
date:   2020-04-28 22:30:52 -0400
img: linux.png
categories: Linux
tags: OS
---

![Linux]({{site.baseurl}}/images/linux.png)

### Install Windows 10 first

### Shrink partition if necessary

###  Install Centos 8
After Centos installation, you might see the boot menu only includes Centos 8
### Identify the Windows boot partiton 
```
# fdisk -l /dev/sda

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *         2048   1187839   1185792  579M  7 HPFS/NTFS/exFAT
/dev/sda2         1187840 111558655 110370816 52.6G  7 HPFS/NTFS/exFAT
/dev/sda3       111558656 113655807   2097152    1G 83 Linux
/dev/sda4       113655808 234440703 120784896 57.6G  5 Extended
/dev/sda5       113659904 234440703 120780800 57.6G 8e Linux LVM

```

In the above output /dev/sda3 through to /dev/sda5 are clearly the RHEL 8 partitions. The smaller /dev/sda1 partition is the Windows system partition, leaving /dev/sda2 as the Windows boot partition.

The RHEL 8 boot system works using partition indexes where the first partition is partition 0, the second is partition 1 and so on. As such, the Windows boot partition from the point of view of the boot menu is located on hard disk 0 at partition index location 1 and is defined in the boot configuration as “hd0,1”.

### Add Windows to boot menu (for legacy BIOS boot only)
Add the following into /etc/grub.d/40_custom
```
menuentry "Windows 10" {
         set root=(hd0,1)
         chainloader +1
         }
```

###  Generate the boot menu
```
grub2-mkconfig --output=/boot/grub2/grub.cfg
```

On the next reboot, you will see the Windows menu

### UEFI process coming up next
