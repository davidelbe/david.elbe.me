---
layout: post
title: "Tutorial – Buy and install SSL certificates on Ubuntu and NginX"
date: "2014-10-21"
disqus: true
---

I install SSL certificates 10-15 times per year, but now when Google has told
us it will have an impact on SEO i expect more customers to order SSL. Every
time I am assigned this task I have to look it up, so here is a short tutorial
on how to buy and install SSL certificates on Nginx. Written by and for myself.

## Buy the certificate

There are multiple options for buying a SSL certificate, and it gets more and
more expensive depending on how good you want it to be. For regular websites
the cheaper options will do just fine, they are often called *domain validation
ssl certificates*.

I used to buy my certificates directly from [Rapid SSL](https://www.rapidssl.com/buy-ssl/index.html)
but they don't have the cheapest option available from their site. You can
actually [buy Rapid SSL certificates via Namecheap for less](https://www.namecheap.com/?aff=75685).

[Here is the cert](https://www.namecheap.com/security/ssl-certificates/rapidssl/rapidssl.aspx?aff=75685)
i used yesterday. It is available for about $10 per year, which is incredibly
cheap compared to most other SSL certs that are used on websites today.

_Disclaimer: I am earning affiliate provision if you use the links above. Thanks for supporting this blog._

### Difference between Domain Validation and Extended Validation

The most visible difference you will see with the cheaper option is that the lock
displayed next to your URL is grey and does not display a specific name.
It is just an SSL cert. (This is for Safari – Chrome displays green locks anyway).

If you go with the more expensive option the lock comes in green and displays
the name of your company to ensure your users that it is not just a secure
domain – it is also owned by the correct company.

For my use case it does not matter much, so I go with the cheaper option. The
certificates are issued by the same company anyway.

### Browser acceptance

One thing you can be looking for if you
are comparing certificates is browser acceptance. That means that the browser
will know about the certificate and don't get any warnings that this certificate
is untrusted. Most vendors have 98-99 percentage of browsers, which will likely
cover 100% of your visitors.

## Generate the CSR

During the buy process you will be asked to provide a CSR (certificate signing
request). This is easy to generate. Just log in to your server via ssh and run
the following command:

`openssl req -new -newkey rsa:2048 -nodes -keyout server.key -out server.csr`

This will ask you a bunch of questions that you should already know the answer
to (like your name, e-mail and other things). The one you have to look out for
is **common name** which is a wierd way of asking for the domain of your site.

Make sure to enter `www.example.com` instead of just `example.com` because
certificates issued for www-subdomain will be valid for both with and without www,
but using only `example.com` will not give you a valid certificate for `www.example.com`

You will now have two files on your server. Save them in a good place. The file
called `server.key` will be used by nginx later and `server.csr` is the file you
copy and paste into the checkout form over at Namecheap.

## Validate your e-mail

Next step is to validate your e-mail address. You will get a list of common
e-mail addresses on your server and be asked to pick one of them. That address
will be sent a message with a verification link that you have to click on.
Simple enough.

## Install in Nginx

After a while (usually within 15 minutes of confirming your e-mail) you get the
SSL certificates via e-mail. Copy and paste them into a regular text file.
It should look something like this when you are ready:

```
-----BEGIN CERTIFICATE-----
aBcdEf124329...[loads of gibberish on multiple lines]
-----END CERTIFICATE-----
-----BEGIN CERTIFICATE-----
aBcdEf124329...[more gibberish]
-----END CERTIFICATE-----

```
I usually put a new line at the end of the file, since I've had problems in the
past with some web servers if I forget it.

Save the file as `example.com.cer` (or any other name, I like to name it the
  same as the domain name) and put it on your web server, preferrably in the
  same folder as `server.key`.

I like to put certificate files under version control (Git, SVN etc) for my own
personal projects – but if you are working in a large team or with an open source
application that is not an option – just keep the files safe.

### Example nginx configuration

Here is an example config that I am using for [Filter](https://gramfilter.com/).


```
# This is the main site, https://gramfilter.com/
server {
  listen 443;
  ssl    on;
  ssl_certificate /path/to/gramfilter.crt;
  ssl_certificate_key /path/to/gramfilter.key;

  server_name gramfilter.com;

  root /var/www/gramfilter/current/public;

  # ... redacted for brevity
}

# This takes care of redirecting visitors from
# https://www.gramfilter.com/ to https://gramfilter.com/
server {
  listen 443;
  ssl on;
  ssl_certificate /path/to/gramfilter.crt;
  ssl_certificate_key /path/to/gramfilter.key;

  server_name www.gramfilter.com;

  return 301 https://gramfilter.com$request_uri;
}

# This takes care of redirecting non https-request to https
server {
  listen 80;
  server_name gramfilter.com www.gramfilter.com;
  return 301 https://gramfilter.com$request_uri;
}
```

### Restart the server

Restarting the nginx process after adding ssl is usually a good idea.
`sudo service nginx restart`

## Troubleshooting

If you have any problems with your nginx config you can often get some help
by running `sudo nginx -t` from your command line, and it will give you a hint
of what is wrong.

It is important to define the paths to ssl certificates before you define the
server name in your config file. If you switch the order you will not get a
valid certificate.
