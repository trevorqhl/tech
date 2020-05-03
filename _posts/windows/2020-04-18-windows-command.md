---
layout: post
title:  "How to use Windows command line to check AD group"
date:   2020-04-18 09:10:54 -0400
img: windows.png
categories: Windows
tags: Shell
---
![PowerSheel]({{site.baseurl}}/images/windows.png)

### Check the list of your AD groups
{% highlight ruby %}
whoami /groups > groups.txt
groups.txt{% endhighlight %}
