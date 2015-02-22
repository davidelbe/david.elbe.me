---
layout: post
title: "Bitbucket vs Github for code collaboration in a small team with lots of projects"
date: "2015-01-03"
disqus: true
categories: development
---

We are experimenting with Bitbucket for code hosting. I have had personal projects there
for most of the year, but almost all of our code at [Standout](http://standout.se/) is hosted
at Github. During december we tested Bitbucket's collaboration features, mostly because we
thought that Github was becoming ridiculously expensive for us.

We are maintaining many projects for our clients. We normally don't charge for code hosting (maybe we should, though).

# Github

 * The community is much stronger. Noone has ever asked me about my Bitbucket profile, but everyone wants to look at a Github profile when hiring new staff.
 * It is generally easier to find integrations if you use Github. For example, Travis CI is Bitbucket only right now.
 * It gets expensive fast if you maintain many private repos. For a team with a few repos or mostly open source pricing won't be an issue though.
 * I like the UI of Github better, most of the time.
 * Deploy keys can not be reused on multiple repos, which is irritating.

# Bitbucket

  * Pricing is much more reasonable for a small team with many repositories.
  * It is harder to find good integrations. For example, we had to use [Codeship](https://codeship.com/) (great service btw) instead of Travis CI, since the latter was Bitbucket only.
  * The Bitbucket UI feels a bit old and it can be hard to find the right buttons since they are not always position in the most natural places.
  * Collaborator approval on pull requests are a great feature. I wish you could auto-merge a PR when everyone has approved, though, but the feature is great.
  * It looks like Atlassian who develops Bitbucket is ignoring feature-requests/bug reports. That is not a good sign.
  * Deploy keys can be reused on multiple repos

I'll keep this blog post updated when I find something I like/don't like.
