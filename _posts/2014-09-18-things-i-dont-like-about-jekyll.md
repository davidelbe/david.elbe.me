---
disqus: true
layout: post
title:  Things I don't like about Jekyll and why I chose it anyway
date:   2014-09-18
categories: jekyll blogging
---

I recently switched over our [company website](http://standout.se/) to use the
static page generator [Jekyll](http://jekyllrb.com) and I am using Jekyll for
this blog too. So it can't be too bad, right? Well, let's talk about some things
that I really miss from other blogging/website tools.

I have used multiple different blogging engines before; Wordpress, Tumblr,
Blogger and a handful of more obscure solutions like our own
[dated-and-badly-in-need-of-a-rewrite-and-documentation CMS](http://github.com/standout/standoutcms).
I have also written several internal blogging solutions for intranets, so I
should know what I am talking about. What is Jekyll missing, then?

## It is too static

I know it is a bit stupid to complain about the staticness of a static page
generator, but I miss the small dynamic things that can be used on regular
PHP/Ruby/Python-pages. If I want to print today's date or a random blog post I
have to resort to using JavaScript.

If I want to publish a page on a certain date I have to wait until that date
to actually publish it, It can not be done in advance since the whole site is
static.

If I want to add a webshop it simply can not be done. Jekyll has no idea who
the visitor is.

## It is too hard for non-programmers

I have seen [Prose.io](http://prose.io) and [Jekyll Admin](https://github.com/zkarpinski/Jekyll-Admin)
and similar solutions, but they all feel like they are
written for other developers, or at least someone with basic CSS/HTML-skills.
I can not put a new customer in front of a Jekyll site and ask them to add
a blog post. To them it feels like we're back to 1997 again.

I am missing a light weight, simple and aimed-to-the-end-user CMS for Jekyll
sites. I might write one myself if I can not find it.


## Deploys

Quick deploys for non-programmers is not clear. FTP:ing your updates to a web
server? Doing git commits to update a blog post if you're hosted on Github
pages. How on earth should I convince my marketing division that this is a
good idea?

## Why should you choose it anyway?

First: it is fast. Static pages are fast, of course - but that is something most
Wordpress sites are not.

I am a developer. I want control over my code and I don't like using wysiwyg-editors
that tries to do too much (and randomly inserts strange tags in my text).
If you are a developer too you should really check it out. If you are a bit
familiar with Markdown and Github it should fit you perfectly. And hosting is
free with Github pages – you can even use your own custom domain just like I
do on this blog. The [source code](https://github.com/davidelbe/david.elbe.me) for this entire blog is available if you'd like
to see.

## Conclusion

I love Jekyll and the simplicity it offers. I know it is targeted towards
developers, and that I should be judging it based on that. But I feel that
Jekyll blogs could really compete with the big ugly solution called Wordpress
that is taking over the web. I really don't like Wordpress - but I miss
a good open source competitor that attacks the same market, and I think Jekyll
could be that competitor – in a slightly modified form.

It would not be too hard to mix the simplicity of Jekyll with the power of
scripting languages such as PHP and Ruby for creating really nice pages that
renders super-fast. But maybe it is not Jekyll then?

I checked the stats on [Devb.io](http://devb.io), and Jekyll is almost never mentioned as a skill
by the developers there. Wordpress on the other hand is mentioned by about 25 %
of the programmers who has registered on the site. I guess the Jekyll people
still have some marketing to do.
