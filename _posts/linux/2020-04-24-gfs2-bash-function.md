---
layout: post
title:  "How to use function in bash"
date:   2020-04-24 21:30:52 -0400
img: linux.png
categories: Linux
tags: Shell
---

![Linux]({{site.baseurl}}/images/linux.png)


##  Pass a parameter to bash function  
{% highlight ruby %}
#!/bin/bash
# fresh.sh 
 
fresh(){
   echo "fresh(): \$0 is $0"
   echo "fresh(): \$1 is $1"
   echo "fresh(): total args passed to me $#"
   echo "fresh(): all args (\$@) passed to me -\"$@\""
}
 
fresh Tomato
{% endhighlight %}
Run the script 
{% highlight ruby %}
sh ./fresh.sh 
fresh(): $0 is ./fresh.sh
fresh(): $1 is Tomato
fresh(): total args passed to me 1
fresh(): all args ($@) passed to me -"Tomato"
{% endhighlight %}

##  Pass an array to bash function  
{% highlight ruby %}
#!/bin/bash

checkStatus(){
   nodes=("$@")
   for node in "${nodes[@]}"
   do
     if (! pcs status | grep  $node | grep Online ); then
        return 1
     fi
   done
   return 0
}

if [ $USER != "root" ]; then
        echo "Script must be run as user: root"
        exit 256
fi

if [ -f /etc/redhat-release ]; then
  if ! (grep -q -i "release 7" /etc/redhat-release) ; then
    echo "Error: RHEL version is not supported"
    exit 512
  fi
else
  echo "Error: OS is not supported"
  exit 128
fi

nodes=()
for node in `grep "_priv" /etc/hosts | awk '{ print $2 }'`
do
  nodes+=($node)
done

echo ""

echo "Checking cluster node status..."
if (checkStatus "${nodes[@]}");then
   echo "Cluster nodes are all online..."
else
   echo "Cluster node is not online, exit..."
   exit 1
fi
 
{% endhighlight %}
