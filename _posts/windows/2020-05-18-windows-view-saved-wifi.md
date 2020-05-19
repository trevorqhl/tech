---
layout: post
title:  "How to view saved WiFi password"
date:   2020-05-18 09:10:54 -0400
img: windows.png
categories: Windows
tags: Network
---
![PowerSheel]({{site.baseurl}}/images/windows.png)

### List all the Wi-Fi networks you have connected to 
{% highlight ruby %}
netsh wlan show profiles
{% endhighlight %}

### Show a profile including password
{% highlight ruby %}
netsh wlan show profile name=”Profile-Name” key=clear
{% endhighlight %}
