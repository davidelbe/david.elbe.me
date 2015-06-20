---
layout: post
title: "Jekyll – how to link to next/previous post on your blog"
date: "2015-06-20"
disqus: true
categories: jekyll
---

I took a quick look on my Google Analytics page today and saw that I get a lot of visitors from Google and other search engines, but they don't explore more content. The simple reason is that I did not give them a good opportunity to do so.

So, I decided to always link to the next/previous post on my blog posts, but I could not find any good documentation for how to do this. After some digging I found some code to help me, and I document it here for future reference.

Here is a screen shot of what I'm trying to accomplish:

![next previous jekyll](/assets/images/2015-06-20-jekyll.jpg)

Do you see the next/previous links?

First step: open up your post layout file. Add the following code:

```
{% raw %}
<div class="PageNavigation">
  {% if page.previous.url %}
    <a class="prev" href="{{page.previous.url}}">&laquo; {{page.previous.title}}</a>
  {% endif %}
  {% if page.next.url %}
    <a class="next" href="{{page.next.url}}">{{page.next.title}} &raquo;</a>
  {% endif %}
</div>
{% endraw %}
```

Next, add some CSS:

```
.PageNavigation {
  font-size: 14px;
  display: block;
  width: auto;
  overflow: hidden;
}

.PageNavigation a {
  display: block;
  width: 50%;
  float: left;
  margin: 1em 0;
}

.PageNavigation .next {
  text-align: right;
}

```

Of course, the CSS and most of the HTML is completely optional. The main things you are looking for are `page.previous.url` and `page.previous.title`. 

Good luck implementing this on your own blog. If you have any related Jekyll techniques for encouraging users to browse your site, please share it in the comments below.
