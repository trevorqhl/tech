---
layout: post
title:  "Understanding HTML basics"
date:   2020-04-25 10:20:52 -0400
img: html.png
categories: html
tags: www
---

![Linux]({{site.baseurl}}/images/html.png)

### Basic form
{% highlight ruby %}
<tag> … </tag>
<standalone-tag>
<!-- comment -->
{% endhighlight %}
## Basic HTML template 
{% highlight ruby %}
<!doctype html>
<html>
<head>
	<title>Website Name</title>
	<style>
		<!-- Your CSS here -->
	</style>
	<!-- meta information, load other files, etc. -->
</head>
<body>
<!-- Your website content -->
</body>
</html>
{% endhighlight %}

## Basic HTML concepts
{% highlight ruby %}
Head - Where the metadata is added
Body - The actual content of your site
Comments - Text ignored by the browser when rendering HTML
Div - A section of HTML tags
{% endhighlight %}

## Basic text tags
{% highlight ruby %}
<h1>text</h1>, <h2>text</h2> - Different levels of headings
<p>text</p> - Paragraph text
<a href=https://google.com>Link Text</a> - Link
<img src=imagelink width=100 height=100> - Images
<b>text</b> - Bold text
<i>text</i> - Italic text
</br> - Line break (go to next line)
{% endhighlight %}

## Div Tags
{% highlight ruby %}
Surround your HTML with <div> </div> tags
Allows for sectioning of HTML
Important for CSS and JavaScript
{% endhighlight %}

The best online sources for HTML is [w3schools.com][w3schools]

[w3schools]: https://www.w3schools.com/html/
