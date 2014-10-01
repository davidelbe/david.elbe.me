---
disqus: true
layout: post
title:  'October Side Project: Moderated Instragram feed'
date:   2014-10-01
categories: sideproject
---

So, my sideproject for October 2014 is a thing that we need for our clients
at [Standout](http://standout.se/). I will build a simple moderated Instagram
feed that you can embed directly on any website.

## The problem

We have clients that wants to display all Instagram photos for a specific hashtag,
for example everything that is tagged with #stockholm or #standout, but they
want control over the photos that are displayed on their website.

Most photos on Instagram are okay, but once in a while you will se a bad photo
showing up on unknowing customer's sites, or even competitors trying to get
their photos in.

Instagram can never build this moderation tool within a hashtag feed since
the feed is the same for all users, so they can only remove photos that breaks
their terms and conditions. This is not enough for keeping a competitor out
of "your" hashtag, or removing "ugly" photos that does not match you webpage.


## Features

* Embed a moderated Instagram feed on your website
* Get a daily e-mail with new photos in your selected hash tags
* Remove images from the feed
* Combine multiple hash tags
* Create multiple feeds
* Whitelist accounts - allow all photos from certain Instagram accounts
* Get the moderated feed in JSON format if you want to programmaticaly do something more with it.

## Challenges

The main challenge in this is keeping it simple. I get a ton of ideas on how to
improve this idea, but I will keep it as simple as possible for the first release
and see how we can use it with our real customer's sites.

On the technical side I need to prepare for embedding on high traffic sites.
Most things can be outputted in static files that gets updated regularly. My goal
is to have customers all over the world, so some kind of CDN solution for the
embeds would be nice.

Legally, can I do this? It sounds like fair use of the Instagram service to
me, but I have to pick a name that is okay. Instagram has some strange wording
in their [brand policy](https://help.instagram.com/304689166306603/) where they
seem to claim the ownership of both 'Insta' and 'Gram'. So we'll have to see
about the name. My initial thought was _Gramfilter_ but I see now that it can
not be used. Give me some ideas, folks!

## Money

This will be a paid service, but I haven't decided on pricing yet. I always
  find the pricing the hardest part in web apps, so any advice is welcome.

I am thinking that I could charge $5 per month, or $49 for a full year. I guess
 most programmers would charge a lot more for solving this problem for their
 clients without this app, so it seems reasonable. But I may change my mind
 completely on this.

## Timeplan

As usual, this app will be up and running before the end of the current month:
 October 2014.
