---
disqus: 'true'
layout: post
title:  September sideproject wrap-up
date:   2014-09-30
categories: sideprojects
---

As I told you in an earlier blog post, I usually give my side projects a full
month of attention - put them online for the world to see and then hopefully
return to it to fix bugs, take care of customer requests or shut down the
service if nobody is using it.

I am happy with the development of Devb.io. For you who has not followed it is
an easy CV service aimed at developers who wants to get their resume online
and edit it easily. Developers should update their resumes often since they
often add new skills, but in reality this is not frequently used.

## Technology

I used Ruby on Rails 4, PostgreSQL and AngularJS running on Nginx and Puma.
This works really well, but I haven't received a lot of traffic to the site yet.

The front end is not tested at all. I was planning on using nightwatch.js for
this, but never started. The critical parts of back end is covered with about
120 tests.

## Money

The service is free for now, so I haven't made a single dollar out of it.

Maybe users will pay for features such as resume reviews or better layouts on their
resumes, but my plan is to launch another service in the future as an add-on to
Devb.io that is aimed to employers looking for great developers to hire.

I solved my own problem with this, so I am happy anyway. We really needed a good
way to display our resumes when applying for consultancy gigs and now we got it.

## Marketing

Nah, not much. Most traffic comes from Twitter posts and a Reddit post. I could
certainly do better here. The good thing is that we are linking to our Devb.io
profiles from our [work website](http://standout.se/medarbetare/) and we are
asking all new people looking for a job to add their profile to Devb.io.

I was trying to get a referral step in the tour, but the hard part seems to get
people to sign up at all. I was initially very happy with how many signups I got
during the first weeks (over 200), but looking closer most of them was spam
accounts so I deleted these. Left is 18 accounts. I was hoping for at least 100,
but I will give it some time and we'll se if people keep signing up.

One feature that I did not build yet is to ask people to update their profile
after a certain time, say 6 months. This should help people to find their way
back to the site. If you have a good idea on how to bring more users to the site,
just write a comment below.


## What I have learned/experimented with

* This was the first time I used [Prawn](http://prawnpdf.org/) for PDF generation, and it worked pretty well.
* Puma is a great web servicer if you care about memory consumtion. Compared with Unicorn and Passenger it is really good.
* Solving your own problem is a great way to know that the service will continue to be used, but next time I will aim for a problem that I see more than one person has.
* It takes time to get to the top of the search engines if you compete with an existing term. ("devbio" - Developmental Biology). Google does not know where to place our web site. [My own profile](http://devb.io/david) does not show up in search engines, and I can not figure out why since the front page is there.
* I used Bitbucket for git hosting. Works well for private repos when you are a single developer. The service seems reliable and I will probably continue to use it as an alternative to Github.
* Doing my side project the first thing in the morning works for me, but only if I rise early. 

## What's next?

Tomorrow I will start looking for a new side project. I'll tell you more then.
