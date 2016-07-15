---
disqus: true
layout: post
title: "Using Slack to mimic Basecamp's Heartbeats feature"
---

![Slack](/assets/images/slack-heart.jpg)

I have followed David, Jason and the other nice people at Basecamp for nearly a decade now. They seem to have found a way that works for working remotely, which is not always easy. A while back [they shared how they are working with Heartbeats](https://m.signalvnoise.com/the-tool-we-built-to-keep-everyone-in-the-loop-at-basecamp-69bc58312014), a small tool they built to keep everyone in the loop.

We are not using Basecamp, but I liked the idea of asking people to share what they have done today. It is a practice that we have used internally at [Standout](http://standout.se/) for a long time, but it never worked well with people working remotely.

I did not realize how bad it was for our remote workers until I started going on business trips more often and had to leave the office for days. I was not in the loop anymore. It did not take long until I felt like I wasn't a part of the team anymore.

So I needed a way to encourage the team to share what they did and learned for the day, just like they do at Basecamp, but without using Basecamp. What I did was using a feature in a tool that we already used.

## Reminders in Slack

I set up two recurring reminders in our Slack #general channel.

 * One reminder every weekday (monday to friday) that asks "What did you do or learn today?"
 * One reminder every monday that asks "What are you going to do this week?"

 Slack has [a help article](https://get.slack.help/hc/en-us/articles/208423427-Setting-reminders) explaining how to use reminders, but I'm going to make it easy for you and show how I set up the two reminders above.

## Step by step

  1. Open up Slack and place the cursor in the box where you normally write messages.
  2. Write `/remind #general every weekday at 4pm to What did you do or learn today?`
  3. Hit enter
  4. Write `/remind #general every monday at 8am to What are you going to do this week?`
  5. Hit enter

Feel free to change the Slack channel name (#general) to what you're using in your own team.

If you ever want to remove a reminder, just write `/remind list` in the message box and you will get a list of current reminders, with the option to remove them.

## Results so far

I have only had this running for a couple of days, and the results so for are better than expected. Most reply almost directly when the reminder pops up, and some people are asking follow-up questions if they want to know more about a certain project or tool that another team member shared.

Since we're already using Slack it was nice to not introduce a second tool just for this small feature. I think it is a big win. Of course, the Basecamp solution looks nice and can present the status in a way that Slack can not do - but simplicity wins over beauty.
