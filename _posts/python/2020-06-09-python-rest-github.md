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

username = 'trevorqhl'
token = '000000000000000000000000'
url = 'https://api.github.com/users/trevorqhl/repos'

response = requests.get(url, auth=(username,token))

assert response.status_code == 200

for repo in response.json():
    print ("[{}] {}".format(repo['language'], repo['name']))


{% endhighlight %}

*  Make an authenticated POST request to the repositories endpoint to add a new repo

{% highlight ruby %}

import json
import requests

username = 'trevorqhl'
token = '0000000000000000000000000'
repo = 'foo' 
description = 'Created with api'

headers = {'Authorization': 'token ' + token}

payload = {'name': repo, 'description': description, 'auto_init': 'true'}

response = requests.post('https://api.github.com/' + 'user/repos', headers=headers, data=json.dumps(payload))

assert response.status_code == 201

{% endhighlight %}

* Delete a repo
{% highlight ruby %}
import requests

username = 'trevorqhl'
token = '000000000000000000000000000000'
repo = 'foo' 

headers = {'Authorization': 'token ' + token}

response = requests.delete('https://api.github.com/' + 'repos/' + username + '/' + repo, headers=headers)

assert response.status_code == 204

{% endhighlight %}

[Github API]: https://developer.github.com/v3/repos/
