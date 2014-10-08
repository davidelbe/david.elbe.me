---
disqus: true
layout: post
title:  'October 2014 sideproject: Status update after 1 week'
date:   2014-10-08
categories: sideproject
---

I am continuing my morning development time between 7 AM and 8 AM. That works
pretty well, and most of the days I am not disturbed at all during that time.

So far I have created a small web app where you can create an account using
only your e-mail address. You won't need a password, next time you want to
login you just enter your e-mail and you get a special link that automatically
signs you in. Last app I used oauth logins, so I wanted to try something else
and I know people are tired of remembering passwords.

I have also successfully grabbed images from Instagram with thumbnails and links
to the larger versions of said images. You can create new feeds and the images
will import once.

Next step is to automatically update the feed once per day and send out an email
to the user that she has new photos to moderate. After that I am going to implement
the actual moderation and then get started on the embed code.

Since the service can be used world wide I am thinking of using some kind of
CDN for hosting the feed script. It will be mostly static, but updated once
per day - so I need to be able to update it.

Or maybe I am complicating things too much. I can just get started with my
test server and see if that works well enough for most people. :)

Nothing online yet, I need some security checks in place first. I'll tell you
more soon.
