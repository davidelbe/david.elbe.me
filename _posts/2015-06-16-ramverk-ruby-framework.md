---
layout: post
title: "Ramverk - the Ruby microframework"
date: "2015-06-16"
disqus: true
categories: ruby
---

So, I love Ruby and most of the time I love Ruby on Rails. Sometimes it feels a little bit too much for smaller projects. So, you have Sinatra, Cuba and other micro-frameworks – but [the new Ruby Micro-framework Ramverk](http://ramverk.org) (the name simply means 'Framework' in Swedish) has a new take on this.

## Why should I even look at Ramverk?

To sum it up: Speed, lower memory usage (read: cheaper hosting) and simplicity. 

To quote Tobias, the creator of Ramverk:

> Sinatra is just too DSL, overusage of blocks and instance_eval ... which is not the fastest thing to do in Ruby. Also, there's too much boilerplate code for every project.

Okay, so I spent a few hours this weekend to play with the new framework. I liked it a lot, especially for smaller projects. Moving to Rails later on should not be a big deal if your project ever outgrows Ramverk.

What could you use it for? Well, __I would personally prefer to use this kind of framework for a quick API__, but it could very well handle a full-scale app.

One more thing i like about Ramverk. It is very unopiniated. Let's face it, much of Rails' success comes from it being opiniated and picking most things out for you; from jQuery and Turbolinks to default databases. Ramverk expects you to know what you want to use and include it. For a seasoned developer that gives a nice feeling of control.

## How do I get started with Ramverk?

I assume you have Ruby 2.2.0 or later installed, since Ramverk won't work with earlier versions of Ruby. I started by cloning Tobias' Sandbox App, to get a feeling for what a Ramverk App could do.

`git clone git@github.com:ramverk/sandbox.git blog`

Install the bundle and run the app

`bundle install && bundle exec rackup`

If everything works as expected you should now have your app running on `http://localhost:9292/`.

![ramverk started](/assets/images/2015-06-16-ramverk-started.png)

## What about databases? Active Record?

There's a [Sequel Adapter](https://github.com/sandelius/ramverk-sequel), but I'm sure you all are familiar with Active Record, and there's a [Ramverk-adapter for Active Record too](https://github.com/sandelius/ramverk-activerecord).

It works as expected, but in contrast to Rails you have to do a bit of fiddling with some configuration files to get it working. No big deal, and it is all well-documented on either repository's GitHub page.

## Documentation

The documentation is better than most, but it is all over the place. The project would benefit from a 'getting started guide' or a quick video tutorial. I'm sure Tobias has something like that up his sleeve.

The project is still young, but it is promising. I like simple solutions, so this one is a keeper if it gets maintained well.

You can get your own copy of ramverk at [ramverk.org](http://ramverk.org)


