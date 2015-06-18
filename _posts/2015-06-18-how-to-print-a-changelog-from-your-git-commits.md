---
layout: post
title: "How to print a changelog from your git commits with changelog_parser"
date: "2015-06-18"
disqus: true
categories: ruby
---

Scenario: You have been coding for a full week and you are ready to do a deploy of version 1.3.7 to the server. Your manager/customer asks: "What is in this release, exactly?"

This used to take me some time. I went through my task lists and pull requests trying to find out exactly what was fixed, added and deleted in this version. Then it hit me: I've already got this in git!

So I put together a small and pretty naive tool to print all the changelog messages from a Git repo. It is called [Changlog Parser](https://github.com/davidelbe/changelogparser) in lack of a better name.

## Installation

`gem install changelog_parser`

## Usage

From the command line: `changelog` or `changelog true` (the last version displays all commit messages, not only the ones containing the word _changelog_)

## Good practices

 *  I use the [Version gem](https://github.com/stouset/version) to separate my versions. It is not necessary, but if you don't use it, just add a commit with message "Version bump to x.x.x" where x is your version numbers.
 *  Sometimes the Git commit log tends to be too technical to display to a customer. We usually solve this by adding an additional comment last in the git commit message, like this: 

```
 "Remove the extra <script> tag added by strange NPM package.

 Changelog: Fix bug where footer was missing from the sidebar"
```

The changelog parser gem can output either _every git message in the version_ or _only messages containing 'Changelog: '_ in your git log. Very handy.

## Changelogging like a pro

So, now all you have to do is write proper git messages and your changelog can be generated for you.

Just run `changelog` or `changelog true` to print a changelog for your project. Your customer will be impressed. Your boss will give you a raise on the spot. Maybe not, but it sounds good in theory.

## Example output

From this blog's git log (written without versioning in mind):

```
> changelog true

   * Ramverk - David Elbe
   * How to install Elixir on Mac OS X - David Elbe
   * Blog post: production settings for jekyll - David Elbe
   * Display environment - David Elbe
   * Display host - David Elbe
   * Display port number - David Elbe
   * How to fix a wordpress hack - David Elbe
   * Agenda for a sales meeting - David Elbe
   * Web developer vs Web designer - David Elbe
   * Should I start a saas app? - David Elbe
   * block referral spam in google analytics - David Elbe
```

Here is [changelog_parser](https://github.com/davidelbe/changelogparser) - contributions are welcome. I wrote it over a year ago and haven't touched it since. It works pretty good for my own use case.



