---
layout: post
title:  "How to use Github Restful API"
date:   2020-06-09 20:30:52 -0400
img: python.png
categories: Python
tags: Programming
---

![Linux]({{site.baseurl}}/images/python.png)

Use Python requests http library to call [Github API][Github API] 

* Make a GET request to the user repositories endpoint to get a list of repository 

{% highlight ruby %}

import requests

response = requests.get('https://api.github.com/users/trevorqhl/repos')

assert response.status_code == 200

for repo in response.json():
    print ("[{}] {}".format(repo['language'], repo['name']))

{% endhighlight %}

*  Make an authenticated POST request to the repositories endpoint to add a new repo

{% highlight ruby %}

import json
import requests

response = requests.post('https://api.github.com/user/repos',
    data=json.dumps({'name': 'foo'}), auth=('trevorqhl', 'password'))
    
assert response.status_code == 201

{% endhighlight %}

[Github API]: https://developer.github.com/v3/repos/
