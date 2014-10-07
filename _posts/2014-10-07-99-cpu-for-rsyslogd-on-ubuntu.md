---
disqus: true
layout: post
title:  99% CPU for rsyslogd on Ubuntu
date:   2014-10-07
categories: servers
---

Following last week's big security woes with [Shellshock](/security/2014/09/25/bash-security-vulnerability.html)
i was upgrading our servers. One of them got stuck with CPU running on 99% all
the time.

After running `top` on the server i found out it was **rsyslogd** that consumed
most of the CPU, but I could not figure out why.

Diving in deeper, I found a lot of messages in `/var/log/syslog` looking like this:

`apps rsyslogd: imklog: error reading kernel log - shutting down: Bad file descriptor`

I did something wrong during the upgrade that most people did when running
`apt-get update && apt-get upgrade`. I got a question if I wanted to update the
config files or keep my own trusted ones. I should have gone with the update
route here.

Luckily it is an easy fix. Just open up `/etc/rsyslog.conf` in your favorite
editor and add `#` before `$ModLoad imklog` line.

Now, restart the rsyslog service with `service rsyslog restart` and you will
have your CPU back.

Thanks to Albert who gave me a link to [this](http://nikolauspolak.info/en/blog/2014/05/openvzproxmox-container-rsyslog-problems-after-dist-upgrade)
blogpost that had the same issue. I could not find it via a Google search,
hence this blogpost.
