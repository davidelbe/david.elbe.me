---
layout: post
title: "How to block referral spam in Google Analytics"
date: "2015-06-01"
disqus: true
categories: development
---

If you have a somewhat popular website or web app and uses Google Analytics you will most probably at some point see referral spam in your Google Analytics stats.

## What is referral spam?

Spammers know that you check your referral links in Google Analytics from time to time. It is interesting to see where the visitors to your site are coming from. And you click the link ... and find nothing at all about your site. 

That is most probably because it is a *ghost referral* – which means that they never visited your site at all. They probably wrote some JavaScript to trigger visits to your site, hoping that you would click on the link in your Google Analytics account and go to their site.

## How can I stop it?

Some people suggest modifying your `.htaccess` file, but that doesn't work if you have ghost referrals.

I've found two steps that works. Keep in mind that this will only work on future traffic, so the spam 
referrals already in your Google Analytics won't go away, but you will not be bothered by them in the future. 

### 1. Make sure Bot Filtering is ON

You'll find this setting in Admin -> View settings. The box saying _"Exclude all hits from known bots and spiders"_ should be checked.

### 2. Filter out everything that is not your site

 * Click on *Admin -> Filters -> New filter*. 

 * Since naming is hard for developers, just call it 'Ghost Referral Filter'.

 * Select Filter type: Predefined

 *  Select Include only -> Traffic to the Hostname -> That contain

 * Now add your domain name in the hostname. Without http and www.

 * Click 'verify filter' to see that the filter is working. If you have a local development version that will probably show up here, which is good. 


It is _important_ that you add all your hostnames that you want to track here. If you are using the same Google Analytics code on multiple sites, separate them with a pipe character `|` to make sure you include all valid traffic.

Spammers can still get into your Google Analytics, but it won't be as likely. For most of my sites it has reduced referral spam to 0-10 visits per month, which is a nice improvement.

