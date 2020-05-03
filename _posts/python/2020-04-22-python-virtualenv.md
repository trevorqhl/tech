---
layout: post
title:  "How to Set Up A Python Virtual Environment" 
date:   2020-04-22 08:30:52 -0400
img: python.png
categories: Python
tags: Programming
---

![Linux]({{site.baseurl}}/images/python.png)

Python virtual environment makes it possible to install Python packages into a discreet Python ecosystem that is entirely separate from your system’s default Python framework. You can use it to manage Python packages for different projects which allows you to avoid installing Python packages globally which could break system tools or other projects. 

Since Python 3.3 or newer, the venv module (included) is the preferred way to create and manage virtual environments. If you use Python 2, you need to install virtualenv using pip.

* For Python3
{% highlight ruby %}
# Check current what are installed to system's pyhton
pip3 freeze

# Create virtual env myenv
python3 -m venv myenv

# activate virtual env
source myenv/bin/activate

# Check current python 
which python3

# Install some packages 
pip3 install pysphere

# Check what are installed in current virtual env 
pip3 freeze

# Exit virtual env
deactivate

{% endhighlight %}

* For Python2
{% highlight ruby %}
# Install virtualenv and activate it
pip install virtualenv
python -m virtualenv myenv
# The rest is the same as python3
{% endhighlight %}
