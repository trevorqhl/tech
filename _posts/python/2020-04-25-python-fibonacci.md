---
layout: post
title:  "How to use Python to print Fibonacci sequence"
date:   2020-04-25 20:30:52 -0400
img: python.png
categories: Python
tags: Programming
---

![Linux]({{site.baseurl}}/images/python.png)

A Fibonacci sequence is the integer sequence of 0, 1, 1, 2, 3, 5, 8....

The first two terms are 0 and 1. All other terms are obtained by adding the preceding two terms. 

This means to say the nth term is the sum of (n-1)th and (n-2)th term.

{% highlight ruby %}
terms=int(input("Enter the terms: "))
first=0                                         #first element of series
second=1                                        #second element of series

if terms <= 0:
    print("The requested series is ",first)
else:
    for x in range(0,terms):
        print(first,end=" ")
        next = first + second
        first = second
        second = next
{% endhighlight %}

