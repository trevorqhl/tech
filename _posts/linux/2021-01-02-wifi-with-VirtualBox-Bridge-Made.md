---
layout: post
title:  "How To Use Wireless Adapter With VirtualBox Bridge Mode"
date:   2021-01-02 08:30:52 -0400
img: linux.png
categories: Linux
tags: OS
---

![Linux]({{site.baseurl}}/images/linux.png)

{% highlight ruby %}
Many people hit a wall when configuring Bridge network for a VirtualBox VM with a Wireless Aadapter on the host machince. Usually it is because the wifi authentication is in fact tied to the MAC address of the network card. An easy walk around is to set the bridge network address to the same mac address of the wireless adapter on the host machince, and configure static IP address on the VM.
{% endhighlight %}

