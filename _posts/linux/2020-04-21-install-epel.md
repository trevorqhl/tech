---
layout: post
title:  "How to install EPEL"
date:   2020-04-21 08:30:52 -0400
img: linux.png
categories: Linux
tags: OS
---

![Linux]({{site.baseurl}}/images/linux.png)

Extra Packages for Enterprise Linux (or EPEL) is a Fedora Special Interest Group that creates, maintains, and manages a high quality set of additional packages for Enterprise Linux, including, but not limited to, Red Hat Enterprise Linux (RHEL), CentOS and Scientific Linux (SL), Oracle Linux (OL).

EPEL packages are usually based on their Fedora counterparts and will never conflict with or replace packages in the base Enterprise Linux distributions. EPEL uses much of the same infrastructure as Fedora, including buildsystem, bugzilla instance, updates manager, mirror manager and more.

For more information please visit [EPEL][EPEL]

1. Install EPEL that includes Fedora Extra Packages for Enterprise Linux
```
yum install epel-release
```
2. Enable the PowerTools repository since some EPEL packages may depend on it
```
yum config-manager --set-enabled PowerTools
```

[EPEL]: https://fedoraproject.org/wiki/EPEL
