---
layout: post
title:  "How to list AD groups that the current user belongs"
date:   2020-04-18 09:10:54 -0400
img: windows.png
categories: Windows
tags: Active_Directory
---
![PowerSheel]({{site.baseurl}}/images/windows.png)

### Check the list of your AD groups
{% highlight ruby %}
whoami /groups > groups.txt
groups.txt
{% endhighlight %}
