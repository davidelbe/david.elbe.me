---
layout: post
title: "Gramfilter (beta) is up and running!"
date: "2014-10-30"
disqus: true
---

October is coming to an end, and as per my own rules I must be ready with
my side project by tomorrow. I created an [Instagram Feed Moderator](https://gramfilter.com/)
where you can pick which photos from a hashtag is displayed on your website.

So far it has been great. One of our customers are already using it in production
and others are going to use it within a few months. I have integrated payments
with Stripe, and it seems to work fine.

## Example of an embedded feed

Here is a feed for the hashtag *#elbe* that will be updated every hour. It is
currently non-moderated, but I have the ability to remove ugly photos if I see
them.

<!-- start Instagram embed code -->
<div id="gramfilter11"></div>
<script src="http://gramfilter.com/embed/11.js" type="text/javascript"></script>
<!-- end Instagram embed code -->

The embed code looks like this:

```
<!-- start Instagram embed code -->
<div id="gramfilter11"></div>
<script src="http://gramfilter.com/embed/11.js" type="text/javascript"></script>
<!-- end Instagram embed code -->
```

## Known issues / missing features

* Administration does not work in IE8
* It has only one feed layout so far
* Signup page needs some tweaking to feel professional
* Minor layout issues inside the app
* Links to Instagram version of the photos
* Handle removed photos
* Some parts of the app misses 'blank slate', information on what to do when you are just starting out.
* It is not not visible in the search engines yet. I am aiming for the phrase 'moderated instagram feed', but you maybe have better suggestions for me?

I have tomorrow to fix some of the issues above – and since I really like this
project I guess i will continue do some fixes to it in the future.

Any feedback is highly appreciated!
