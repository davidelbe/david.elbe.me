---
layout: post
title: "Angular JS and Slim templates with Ruby on Rails"
date: "2015-01-04"
disqus: true
categories: development
---

I love using Slim instead of ERB when I get the chance. It looks
a lot cleaner, and makes me focus on the content instead of
the HTML tags.

I like to combine Slim templates with Angular, writing code like this:

```
#user {{ user.full_name }}
```

Where `user` comes from Angular. Slim does not like this since it uses
{ and } to group attributes. I used to fix this by using `attr_delims`.

Since version 2.1 of Slim you can no longer use `attr_delims` without
getting deprecations warnings, but no good indication on what to
replace them with. I did som digging in the Slim code and found a
solution:

Put the following in an initializer:

```
Rails.application.assets.register_engine('.slim', Slim::Template)
Slim::Engine.set_default_options(
  attr_list_delims: {'(' => ')', '[' => ']'},
  code_attr_delims: {'(' => ')', '[' => ']'},
  format: :html5
)
```

Now you can combine Slim and Angular. Don't forget to restart your server.
