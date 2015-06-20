---
layout: post
title: "Jekyll – how to use different settings for production and development"
date: "2015-06-08"
disqus: true
categories: jekyll
---

Right now I use Jekyll for publishing this blog. 

Sometimes I need to display different things in production settings (in my case Github Pages) and in development. For example, I don't want to include the Disqus Comments or load the Google Analytics script when I'm in development mode.

You could use two different config files, but I've found a quicker solution.

So, here's my way to use one setting for production and one for development when running your Jekyll site:

```
{% raw %}
{% if jekyll.environment == 'production' %}
  I'm in production!
{% else %} 
  I'm in development!
{% endif %}
{% endraw %}

```

So this easily lets me hide Disqus and Google Analytics from development mode and only include it when running jekyll in production on Github Pages.

This works fine if you let Github Pages generate the site, they are always set to production. 
If you compile it locally before production you only need to set the `JEKYLL_ENV` variable when doing a production compile, like this: `JEKYLL_ENV=production jekyll build`
