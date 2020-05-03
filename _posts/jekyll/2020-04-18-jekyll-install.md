---
layout: post
title:  "How to build a website with Jekyll and GibHub"
date:   2020-04-18 08:15:52 -0400
img: jekyll.png
categories: Jekyll
tags: Jekyll
---

![Jekyll]({{site.baseurl}}/images/jekyll.png)

Install packages including ruby 
{% highlight ruby %}
# Login as root
yum install -y ruby ruby-devel make gcc gcc-c++ zlib-devel redhat-rpm-config
{% endhighlight %}

Install install jekyll and bundler
{% highlight ruby %}
# Login as yourself
gem install jekyll bundler
bundle install
{% endhighlight %}


Use jekyll to create a site called blog
{% highlight ruby %}
# Login as yourself
jekyll new blog
{% endhighlight %}


Run website locally to test
{% highlight ruby %}
cd blog
bundle exec jekyll serve

You can only jekyll serve next time
jekyll serve
{% endhighlight %}

Acess the site on link below
{% highlight ruby %}
http://127.0.0.1:4000/
{% endhighlight %}

Create a repo from [github.com]
{% highlight ruby %}
# It is easy to just set the repo name to your-github-account.github.io
# If you use a different name for repo, like blog, you would need to go
# to Settigs of the repo and choose a branch to enable your GitGub Pages 
{% endhighlight %}

Initialize and push blog to github repo from Linux
{% highlight ruby %}

# If you have not yet set up git enviornment
git config --global user.name "Trevor Li"
git config --global user.email "trevorl@example.com"
git config -l

# cd into where the jekyll site located, it is blog in this case 
git init
git remote add origin https://github.com/trevorqhl/blog.git
git add .
git commit -m "first commit"
git push -u origin master
{% endhighlight %}

Update the site and push to github 
{% highlight ruby %}
# Once the update is done run website locally to test
jekyll serve

# Once you are satisfied, check git status
git status

# If there are new files to add
git add .

# commit to local repo
git commit -a -m "update blog"

# push to master
git push 
{% endhighlight %}


Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
[github.com]: https://github.com/trevorqhl/blog
