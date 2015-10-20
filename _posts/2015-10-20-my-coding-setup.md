---
title: "My current coding setup (2015)"
author: david_elbe
date: 2015-10-20
layout: post
description: "In which I describe how I work with coding."
---

Since my new focus at work has been mostly in the sales area, my time spent coding is less than it used to be.
Still, I believe that in order to sell something you need to understand it – and what better way is there of understanding
programming than to program yourself?

So, most of my time spent coding is spent with Ruby on Rails, Wordpress-plugins, AngularJS and som
occasional dive into another language like Go or Elixir just for the fun of it.

About two months ago I decided to ditch my local dev setup and only work via a remote, cloud-based, solution. I still have
my Macbook Air 11" with 4GB RAM that works perfectly fine - and at work it is connected to a 27" Apple monitor.

## Cloud computing

So, I bought a [Cloud VPS from Cloud Royale](https://cloudroyale.se/?ref=153613bf0ce0) (Swedish host, this is a referral link that will give you a free month of their service).
The host does not matter much, you just want something with good stability and low latency. A simple ping test will work fine most of the time. Also, make sure they have a good backup system.

The cost is about $10-20 per month depending on usage.

## I can work from anywhere

As long as I have a computer with a SSH-connection and access to my SSH-keys I can start coding from almost any machine, anywhere.

## Mosh, for stable connections

[Mosh](https://mosh.mit.edu/) is a drop-in replacement for SSH that you really want to try if you are doing lots of remote work. It is free and available for most platforms. Unfortunately not for iOS yet, though.
It automatically reconnects to a server and the ssh connection feels much snappier.

## Editor: Switching from Sublime Text to Emacs

I finally did the switch. I have used Sublime Text for a couple of years now, but I have long been looking at Vim for editing, but never fallen in love with it. I liked the concept of working in the terminal with my code, but Vim was not my cup of coffee. Then I tried an old friend from my studying days: Emacs. With a little configuration it is really nice to use, and it can be run from any terminal. This means I can be coding from my iPad, from my parents' old computer, from basically anything.

A few of the extras/plugins I use:

 * web-mode
 * ruby-mode
 * magit (must have for git interaction)
 * multiple-cursors
 * expand-region
 * ido-mode
 * markdown-mode

## Tmux, for session management

I use [tmux](https://tmux.github.io/) to be able to continue where I left. It can handle multiple sessions and switching between windows, panes and sessions becomes second nature after a while.

## And my trusty Macbook Air 11"

I still keep my small laptop as my primary computer, altough I am tempted to replace it with an iMac at the office. The reason for this is that I tend to bring a lot of my work home with me, and if I leave my computer at work there will be less working from home. But I am keeping it for now.
The Macbook Air 11" is powerful enough to even handle most of my photo editing (with Pixelmator and Graphic), and I don't find it slow or the screen too small. As a companion to the MBA I have an iPad Air 2.
