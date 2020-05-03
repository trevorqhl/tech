---
layout: post
title:  "How to use loop in Python"
date:   2020-04-21 08:30:52 -0400
img: python.png
categories: Python
tags: Programming
---

![Linux]({{site.baseurl}}/images/python.png)

In this example to use loop in python, we write a program to find factorial of number using for and while loop.

Factorial of a number is calculated by multiplying it with all the numbers below it starting from 1.

For example factorial of 4 is 24 (1 x 2 x 3 x 4).

Below program takes a number from user as an input and find its factorial.

# Using For Loop
{% highlight ruby %}
num = int(input("enter a number: "))
 
fac = 1
 
for i in range(1, num + 1):
   fac = fac * i
 
print("factorial of ", num, " is ", fac)
{% endhighlight %}

# Using While Loop
{% highlight ruby %}
num = int(input("enter a number: "))

fac = 1
i = 1

while i <= num:
  fac = fac * i
  i = i + 1

print("factorial of ", num, " is ", fac)
{% endhighlight %}
