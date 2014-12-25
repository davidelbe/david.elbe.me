---
layout: post
title: "Puma, Nginx, Rails and Capistrano"
date: "2014-12-03"
disqus: true
categories: development
---

I just set up another app for the umteenth time. Since we all do it a bit differently
and it usually takes a couple of weeks or months between new deploys I thought I should
document how I usually set up the servers with Ruby on Rails, Puma and Nginx.

## Why Puma?

Puma uses very little memory compared to Unicorn and Passenger in the apps I have
developed. My second choice would probably be passenger for stability and ease of
configuration, but I when Passenger goes wrong it is hard to find the errors.

NginX is faster than Apache in most of my experiments, so I'll go with that.

## My setup

 * Ubuntu (latest LTS)
 * Ruby (with rbenv for easy version switching)
 * Capistrano (for speedy deploys)

## Configuration

### Capfile

To make Puma play nice with Nginx I use the following config in my Capfile

```
...
require 'capistrano/rbenv'
require 'capistrano/bundler'
require 'capistrano/rails/assets'
require 'capistrano/rails/migrations'

# Puma/nginx config
require 'capistrano/puma'
require 'capistrano/puma/workers'
require 'capistrano/puma/nginx'
...
```
Full Gist [here](https://gist.github.com/davidelbe/3c49cb2b4dadf7ad5972)


### Gems

```
gem 'capistrano', require: false
gem 'capistrano-rails', require: false
gem 'capistrano-bundler', require: false
gem 'capistrano-rbenv', require: false
gem 'capistrano3-puma', github: "seuros/capistrano-puma"
gem 'puma'
```

### Capistrano stages

My staging and production config looks like this:

```
# Common (deploy.rb)
set :rbenv_ruby, "#{File.read('.ruby-version').chomp}"
set :rbenv_type, :user
set :rbenv_map_bins, %w{rake gem bundle ruby rails}
set :puma_worker_timeout, 60
set :puma_init_active_record, true
set :puma_preload_app, true

# Stage specific (stagename.rb)
set :rails_env, 'staging'
set :puma_env, 'staging'

# Configure depending on server load
set :puma_threads, [0, 5]
set :puma_workers, 1

set :nginx_server_name, 'staging.example.com'
```

### Generate server config

First, generate the templates locally `rails g capistrano:nginx_puma:config`

Then run this:
`bundle exec cap staging puma:config puma:nginx_config`

This should generate two configuration files on your server.
Now you should start up the puma instances with
`bundle exec cap staging deploy`

And then reload nginx on the server with `sudo service nginx reload`.




