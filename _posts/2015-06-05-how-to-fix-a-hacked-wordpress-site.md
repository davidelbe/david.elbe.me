---
layout: post
title: "How to fix a hacked WordPress site with code injected on top of every PHP file"
date: "2015-06-05"
disqus: true
categories: wordpress
---

I got a call from a customer today. They are running a Wordpress site that they manage themselves and it was acting wierd. I logged in to the server and found that each PHP file had some garbish in the beginning of the file.

```<?php if(!isset($GLOBALS["\x61\156\x75\156\x61"])) { $ua=strtolower($_ ... ```

They were using an old plugin that was the source of an automated hack. So I needed a quick way of removing this code in all .php files on the server. Luckily it was always the first line that looked like this. 

The solution was to run this from the command line:

```find . -name '*.php' | sed -i -e '1s/.*/<\?php/' *.php```

It basically finds all files with a PHP file extension, and then replacing everything on the first line with `<?php `

Both `find` and `sed` are standard commands that are available on Linux distributions, including Mac OS X. 

Don't forget to update to latest Wordpress version and also update your plugins when you're at it. You don't want that hacker coming back. I would also advice you to change all admin passwords and FTP passwords. 

So, the website is online and running, and now I can go back to writing Ruby code again. :)
