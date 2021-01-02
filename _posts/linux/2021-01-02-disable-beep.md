---
layout: post
title:  "How to disable beep sound on Centos 8"
date:   2021-01-02 08:30:52 -0400
img: linux.png
categories: Linux
tags: OS
---

![Linux]({{site.baseurl}}/images/linux.png)

Disable beep sound for shell
{% highlight ruby %}
echo 'set bell-style none' >> ~/.inputrc
{% endhighlight %}
Disable beep sound for VIM
{% highlight ruby %}
echo "set belloff=all" >> .vimrc
{% endhighlight %}
