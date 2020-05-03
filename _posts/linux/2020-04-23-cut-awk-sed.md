---
layout: post
title:  "How to use cut, awk, sed to manipulate text"
date:   2020-04-23 08:30:52 -0400
img: linux.png
categories: Linux
tags: Shell
---

![Linux]({{site.baseurl}}/images/linux.png)

cut - remove sections from each line of files
{% highlight ruby %}
# Print the username from /etc/passwd
cut -d: -f1 /etc/passwd
{% endhighlight %}

awk - text pattern scanning and processing languange 
{% highlight ruby %}
# Print the username from /etc/passwd
cat /etc/passwd | awk -F':' '{print $1}'
{% endhighlight %}

sed - stream editor for filtering and transforming text
{% highlight ruby %}
# Replace every occurence of input to output, echo to standard output
sed -e 's/input/output/g' my_file 
# Replace every occurence of input to output, edit file 
sed -i -e 's/input/output/g' my_file 
{% endhighlight %}


