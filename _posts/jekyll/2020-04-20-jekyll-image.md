---
layout: post
title:  "How to insert an image into markdown file"
date:   2020-04-20 20:15:52 -0400
img: jekyll.png
categories: Jekyll
tags: Jekyll
---
![Jekyll]({{site.baseurl}}/images/jekyll.png)

How to insert an image into your markdown file
{% highlight ruby %}
# Create images folder if not there
# Copy your image into the images folder
# Locate to the place where you want to put your image from the markdown file
# Insert the block and remove the backslash 

![](\{\{site.baseurl\}\}/images/your-image.png)


{% endhighlight %}

[Webjeda-cards-demo]: https://webjeda.com/cards/
[Webjeda-cards-home]: https://github.com/sharu725/cards
