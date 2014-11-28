---
layout: post
title: "Upgrading Rbenv on Ubuntu 14.04"
date: "2014-11-08"
disqus: true
categories: development
---

It has been a busy week. I have not had time to work on my side projects,
not even to decide a side project for November - so I will keep this short.

It was a week of system upgrades. I upgraded my dev machine (a Macbook Air 11")
to Mac OS X Yosemite and it works really well. I did a clean install of the OS
and it runs perfectly so far. I also wanted to upgrade the Devb.io server to
the latest version of Ruby (2.1.4). 

Last time I had to find parts of the solution on how to upgrade the system
on different sites, so I compiled this checklist for myself and if anyone
else is helped by it – perfect.

## What I am running

 * Nginx
 * Ubuntu 14.04 LTS
 * Ruby via Rbenv (2.1.2)
 * Puma
 * Ruby on Rails (4.1.7)
 * PostgreSQL
 * Capistrano for deploys

## System upgrade

A updated system is a good start. 

 `apt-get update && apt-get upgrade`
 
I usually restart the database server after a system upgrade, since
I have found that postgres can behave strange if it is not restarted.

`sudo /etc/init.d/postgresql restart`

## Install the new Ruby version

`rbenv update && rbenv install 2.1.4`

## Project settings

In your Rails app you need to modify the `Gemfile` (just change the Ruby number)
and your `config/deploy.rb` (:rbenv_ruby-type setting) and your local `.ruby-version`
file (done via `rbenv local 2.1.4`). Commit, run your tests and push to Github/Bitbucket.

## Install bundler on the server

Most people use bundler on the server, but it does not come preinstalled with a new 
Ruby version, so we need to add that. `rbenv local 2.1.4 && gem install bundler`.

On some setups I needed to install the Ruby web server too, not sure about why
since I think this should be handled by bundler. `gem install puma` in my case.

## Stop the web server

Now is the time to put a maintainance page up, or just shut the webapp off
for a moment. Capistrano can handle this. On your local machine:
`bundle exec cap production deploy:stop`

You can leave it running, but Capistrano will send a phased restart that will
try to use the old Ruby version by default. Stopping it makes sure we use the
new ruby version on next start.

## Do a deploy

On your local machine: `bundle exec cap production deploy`

Now, your web app should be running the latest and greatest version of Ruby. 

