---
layout: post
title: "Do you misuse the placeholder attribute in HTML5?"
date: "2015-05-07"
disqus: true
categories: webdevelopment
---

Placeholder attributes are nice. They can give the user
a hint on what to enter in any input field. See this
example:

```
<label for="email">E-mail</label>
<input id="email" type="email" placeholder="Example: you@example.org">
```

It will look like this:

<fieldset>
<label for="email">E-mail</label><br>
<input id="email" type="email" placeholder="Example: you@example.org">
</fieldset>

But I've lately seen the placeholder attribute be misused, like this:

```
<input type="email" placeholder="E-mail">
```

Do you see what is missing? The whole `label` tag was replaced with a placeholder.

This is bad for several reasons:

 * Users with older devices and/or screen readers won't get the support they need
 * The placeholder goes away directly when you have entered the text, so a user might forget what the were supposed to enter or have something erroneous be pre-filled by their browser and not notice.
 * The placeholder is usually much harder to read than a label

 If you know anyone misusing this, please refer them to this article or link them directly to the [W3C warning](http://www.w3.org/TR/html51/semantics.html#the-placeholder-attribute). Thanks to [@rogerjohansson](https://twitter.com/rogerjohansson/status/596331844032983040) for pointing out this article.

By the way, I'm not perfect in any way myself. I've found this on several of my own pages, due to lazyness when copying pasting code from other places. I actually had to fix the e-mail list signup link in the bottom of the page. But I'll try to fix this whenever I see it. 



