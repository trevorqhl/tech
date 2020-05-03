---
layout: post
title:  "How to install Netbeans on Centos"
date:   2020-04-21 19:30:52 -0400
img: java.png
categories: Java
tags: Programming
---

![Linux]({{site.baseurl}}/images/java.png)

# Install Oracle java
{% highlight ruby %}
# You can get Java from Oracle website. If you do not want to register, use the step below
# Login as root
wget https://mirror.its.sfu.ca/mirror/CentOS-Third-Party/RCG/common/x86_64/jdk-8u202-linux-x64.rpm
rpm -ivh jdk-8u202-linux-x64.rpm
{% endhighlight %}

# Ensure you set default Java to Oracle Java if you have more than one Java version installed
{% highlight ruby %}
# Login as root
alternatives --config java
{% endhighlight %}

# Download and install Netbeans
{% highlight ruby %}
# Login as you
wget http://download.netbeans.org/netbeans/8.2/final/bundles/netbeans-8.2-linux.sh
chmod +x netbeans-8.2-linux.sh
./netbeans-8.2-linux.sh
{% endhighlight %}
