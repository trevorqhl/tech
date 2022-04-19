---
layout: post
title:  "How to Read and Update Google Spreadsheets with Python"
date:   2020-06-09 20:30:52 -0400
img: python.png
categories: Python
tags: Programming
---

![Linux]({{site.baseurl}}/images/python.png)

Login to https://console.developers.google.com/
Create a new project

{% highlight ruby %}
grubby --args="ipv6.disable=1" --update-kernel=DEFAULT
{% endhighlight %}

Verify the updated entries of kernel arguments on the default kernel
{% highlight ruby %}
grubby --info DEFAULT
{% endhighlight %}

Dsable IPv6 to the all kernels
{% highlight ruby %}
grubby --args="ipv6.disable=1" --update-kernel=ALL
{% endhighlight %}

Verify the updated entries of kernel arguments 
{% highlight ruby %}
grubby --info ALL
{% endhighlight %}

Restore IPv6 to the all kernels
{% highlight ruby %}
grubby --remove-args="ipv6.disable=1" --update-kernel=ALL
{% endhighlight %}

Verify the updated entries of kernel arguments 
{% highlight ruby %}
grubby --info ALL
{% endhighlight %}

After kernel boot update, you might need to turn off IPv6 across Linux configuration files
{% highlight ruby %}
* /etc/hosts

# cp -p /etc/hosts /etc/hosts.disableipv6
# sed -i 's/^[[:space:]]*::/#::/' /etc/hosts
 
* /etc/netconfig

udp        tpi_clts      v     inet     udp     -       -
tcp        tpi_cots_ord  v     inet     tcp     -       -
#udp6       tpi_clts      v     inet6    udp     -       -
#tcp6       tpi_cots_ord  v     inet6    tcp     -       -
rawip      tpi_raw       -     inet      -      -       -
local      tpi_cots_ord  -     loopback  -      -       -

* /etc/sysconfig/chronyd

OPTIONS="-4"
{% endhighlight %}

