---
layout: post
title:  "How to do factorization in Python"
date:   2020-04-28 13:30:52 -0400
img: python.png
categories: Python
tags: Programming
---

![Linux]({{site.baseurl}}/images/python.png)

Fuction factorization lists all the factors of a given integer  
Fuction prime_factorization lists the prime factors of a given integer  

{% highlight ruby %}
import math

def factorization(n):

    """returns all the factors of a number"""
    factors = []
    t = 1

    while t < math.ceil((n / 2) + 1):
        if n % t == 0:
           factors.append(t)
        t = t + 1

    factors.append(n)

    return factors


def prime_factorization(n):

    '''returns the prime factorization of a number'''
    factors=[]
    i = 2
    while n >= i:
        if n % i == 0:
           factors.append(i)
           n = n/i
           i = 2
        else:
           i = i + 1

    return factors

print(factorization(250))
print(prime_factorization(250))

{% endhighlight %}

