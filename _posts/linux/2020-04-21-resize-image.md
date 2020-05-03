---
layout: post
title:  "How to reszie, convert images from Linux"
date:   2020-04-21 08:30:52 -0400
img: linux.png
categories: Linux
tags: Tools
---

![Linux]({{site.baseurl}}/images/linux.png)

1. Ensure epel is [installed][epel-url]

2. Install ImageMagick
{% highlight ruby %}
yum install ImageMagick
{% endhighlight %}

3. Resize image
{% highlight ruby %}

# Check original size
file apache.png 
# Convert by width
convert apache.png -resize 820 apache.png
# CHeck new size
file apache.png 

# Convert by height, keep original name but save into a new file
convert apache.png -resize x100 apache2.png

# ImageMagick will preserve the aspect ratio
{% endhighlight %}

3. Convert Between Formats
 
{% highlight ruby %}
convert example.png example.jpg
{% endhighlight %}

6. The rest are customized to your preference and kick off installation

[epel-url]: {{site.baseurl}}/linux/2020/04/21/install-epel.html
