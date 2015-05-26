---
layout: post
title: "8 different types of programmers"
date: "2015-05-25"
disqus: true
categories: programming
---

Here are 8 different types of programmers that I have encountered in 
different web development projects during the last decade. 

Which one is you?


## 1. MacGyver

The guy who will understand and fix your problems fast. He does not care
about code quality much, and will never fix any indentation errors in 
other people's code. He will use duct tape if he has to.

Can actually write good code from time to time, and is happy when other
people is refactoring his code for him - as long as it works just as good afterwards.

The whole app will be hard to fix if this person ever goes away. Always delivers faster than anyone expects, and always makes the customer and managers happy.

Does not work well with *The Perfectionist*.

## 2. Mister 90%

The guy who almost fixes the problem, but always misses something that
makes the whole feature unusable or sloppy. Cares more about the code
than how the end results works.

His progress will look great at first, since he ticks off many items
on the to do-list – but you will be greatly disapponted since every
issue has to be opened again.

Does not go well with testers, but is good at keeping deadlines. Combine this guy with *MacGyver* and you have a good team.

## 3. The Rewriter

Can never leave a piece of code untouched if he sees something that can
be refactored. Can spend more time on refactoring a non-relevant part
of the codebase than he spends on solving the actual problem.

Has the best test suite in history, but it is always red because a rewrite is
in progress.

If you give an existing project in PHP and MySQL to this guy, he will start
rewriting it with Go with a NoSQL-database. Then he will ask what the problem was that needed to be fixed.


## 4. The perfectionist

Could be the same as *The Rewriter* but this person needs his own code
to be perfect. Can spend days on a task that takes a couple of minutes for *McGyver*
but the resulting code is impeccable. 

Gets really annoyed when looking at code written by anyone else. You never want this person to do your code reviews.

The Perfectionist can never do time estimates because perfection has no time frame.


## 5. The Copy-and-Paste coder

Does not really know what he is doing, but got his job a long time ago. He thanks higher powers every day for backups and code versioning systems, because when he tries to do something there is a good chance that something is going to break.

Likes to fix things in production environments, because his local development copy never works.
Spends half of his days on Stack Overflow.

## 6. The Experimenter

Always tries out new editors, frameworks, build tools, programming languages and keyboards. He is really keen on trying out the latest shiny new thing for your next project. Will spend weeks on a setup, only to change to something better the next day.

Nobody knows anything about the quality of his code, because he never delivers anything - but he is always experimenting with new stuff.

Goes well with *The Rewriter*. 

## 7. The Spaghetti Coder

Constantly cutting corners to meet deadlines. Is probably one of the most productive in the office since he constantly
ships new features, but leaves a trails of undocumented, untested code that even he won't understand a month later.

In the long run he probably creates more problems than he solves, but is great for keeping deadlines and shipping stuff early. Checks in all your secret API-key in your open source project on Github, because that was the quickest and simplest solution.

Does not comply with *The Perfectionist* but creates a lot of work for *The Rewriter*. 

## 8. The Pseudo-coder

A manager who thinks he can get people to understand things better by writing pseudo-code. 

```
if
  price of beer is less than 10
then
  do order drink
else
  exit foobar

```

In reality he sounds like someone talking to a child. "Oh, how cute! Can you give that red ball to mommy? Good programmer!"

