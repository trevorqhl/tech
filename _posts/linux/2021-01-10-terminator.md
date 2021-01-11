---
layout: post
title:  "How to configure terminator"
date:   2021-01-10 08:30:52 -0400
img: linux.png
categories: Linux
tags: OS
---

![Linux]({{site.baseurl}}/images/linux.png)

Here is the example to configure Terminator in Linux have to putty like copy/paste and have the Window size at 900x600
{% highlight ruby %}
[trevorl@fox1 terminator]$ cat ~/.config/terminator/config 
putty_paste_style = True
copy_on_selection = True
[keybindings]

[profiles]
  [[default]]
[layouts]
  [[default]]
    [[[window0]]]
      type = Window
      parent = ""
      size = 900, 600
    [[[child1]]]
      type = Terminal
      parent = window0
[plugins]
{% endhighlight %}
