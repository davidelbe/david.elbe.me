---
disqus: 'true'
layout: post
title:  Capistrano 3 and Airbrake
date:   2014-09-24
categories: webdevelopment
---

I was integrating the error tracking app [Airbrake](http://airbrake.io/) on
my hobby project [Devb.io](http://devb.io/) (which is running Ruby on Rails 4)
today and ran into a few problems that was a bit hard to google for - so I
put up this blog post in hope of helping someone who has the same problem.

When deploying, i got the following error:

{% highlight ruby %}
NoMethodError: undefined method `instance' for Capistrano::Configuration:Class
{% endhighlight %}

The error lies within the airbrake generator. It assumes that you are using
Capistrano 2 instead of Capistrano 3 and the generator adds code to the wrong
place.

To fix the error, start by going to `deploy.rb` and remove the lines added by
the generator, they should be near the bottom and and look like this

{% highlight ruby %}
require './config/boot'
require 'airbrake/capistrano'
{% endhighlight %}

Now, add the following line to your _Capfile_

{% highlight ruby %}
require 'airbrake/capistrano3'
{% endhighlight %}

Now, it should work again! The bug is reported
[here](https://github.com/airbrake/airbrake/issues/324)
