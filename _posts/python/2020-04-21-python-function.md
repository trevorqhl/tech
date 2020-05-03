---
layout: post
title:  "How to use function in Python"
date:   2020-04-21 08:30:52 -0400
img: python.png
categories: Python
tags: Programming
---

![Linux]({{site.baseurl}}/images/python.png)

A function is a block of code which only runs when it is called.

You can pass data, known as parameters, into a function.

A function can return data as a result.

In this example to use function in python, we write a function to take a number as input and return factorial of the number

Factorial of a number is calculated by multiplying it with all the numbers below it starting from 1.

For example factorial of 4 is 24 (1 x 2 x 3 x 4).

{% highlight ruby %}
 
def factorial(num):
  fac = 1
 
  for i in range(1, num + 1):
     fac = fac * i

  return fac
 
n = int(input("enter a number: "))
f = factorial(n)

print("factorial of ", n, " is ", f)
{% endhighlight %}

