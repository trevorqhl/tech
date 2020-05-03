---
layout: post
title:  "How to setup httpd"
date:   2020-04-25 08:30:52 -0400
img: linux.png
categories: Linux
tags: www
---


![Linux]({{site.baseurl}}/images/apache.png)

### Install Apache httpd on Centos 8
{% highlight ruby %}
yum install -y httpd
{% endhighlight %}

### Enable and start  httpd service
{% highlight ruby %}
systemctl enable httpd
systemctl start  httpd
systemctl status httpd
{% endhighlight %}

### Create the index.html
{% highlight ruby %}
cd /var/www/html
ls -l
echo "Hello World" > index.html
{% endhighlight %}

### Access your website
{% highlight ruby %}
# Get your IP address of your host 
ifconfig 
# and access it by httpd
# or access by localhost if you are running locally 
http://127.0.0.1/
{% endhighlight %}

