---
disqus: 'true'
layout: post
title:  Keeping Ubuntu server clock in sync
date:   2014-10-01
categories: servers
---

Yesterday we ran into a problem with a server running Ubuntu with a clock that
was not set correctly. It was one minute and 17 seconds wrong. This may or may
not be much depending on your application, but I needed a way to sync it
continously.

## Wait, doesn't the system handle this by itself?

Yes and no. Every reboot the clock syncs. But as you know, servers can (and should)
be running for months without rebooting.

## The simple solutions

Just run `sudo apt-get install ntp` and give it a couple of minutes. It will
automatically sync with the nearest [NTP server](http://en.wikipedia.org/wiki/Network_Time_Protocol).
The bad thing with this is that it adds a small extra load on your server.

Your time will be correct with an error margin of a few milliseconds.

## The 'one sync per day' option

For most people the above solutions is perfecly fine, but if you only need the
time to be approximately correct (within a few seconds) you can use the following
method

* Create a file named `/etc/cron.daily/timesync` with the following contents: `ntpdate ntp.ubuntu.com`
* Make sure the file is executable with `sudo chmod 755 /etc/cron.daily/timesync`

Now your time will be more correct than most people's wrist watches.
