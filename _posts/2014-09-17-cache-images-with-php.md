---
disqus: true
excerpt: How to store images locally with a fast caching script in PHP.
layout: post
title:  Caching remote images locally with mod rewrite and PHP
date:   2014-09-17
categories: code php
---

Sometimes you need to load images from a remote server. In my case it was a
customer site that used an external image service. The only problem was that
the image service was a bit unreliable and slow - which made the customer's
site look slow.

We decided to make a local cached copy of the images, and the solution was
simple enough to share here. The website was running on Apache and we took
advantage of the *mod_rewrite* module by placing the following in our .htaccess
file.

{% highlight php %}
RewriteEngine On

# Images
RewriteCond %{REQUEST_URI} ^/images/
RewriteCond %{DOCUMENT_ROOT}%{REQUEST_URI} !-f
RewriteRule (.*) /images/cache.php?querystring=$1 [L]
{% endhighlight %}

This means that all requests to /images/ that does not match a real file
hits our images/cache.php with the image request path as the querystring.

{% highlight php %}

<?php

# Ok, the file does not exist on our server. Get it from the remote server
# http://example.com/pictures/$image_path

$image_path = $_GET['querystring'];

# You may want to do some sanity checking here, depending on which file names
# you are allowing.
$url = "http://example.com/pictures/$image_path";


# Check to see if we can load the URL at all.
$data = @file_get_contents($url);

if($data)
{
  # Permission to write to server is required.
  file_put_contents("$image_path", $data);

  # Redirect the user to the remote server this time.
  # Next time she will get the cached image.
  header("Location: $url");

} else {

  # Did not find the image on remote server. Send user to our missing image.
  header("Location: http://example.com/images/missing.png");
}

?>
{% endhighlight %}

In our production code we have some more security measures to see that the
filename is a valid path, matches some given filenames and does not contain
strange characters. But this will give you a nod in the right direction if you
need to build something similar.
