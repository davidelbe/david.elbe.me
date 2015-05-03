---
layout: post
title: "One database per customer, or one database for the whole SaaS-app?"
date: "2015-05-03"
disqus: true
categories: saas
---

For someone coming from the classic client-server model of software
development it can be hard to switch an app from serving a single
customer to distributing it as an SaaS-app. 

## Can I have one database per customer?

Sure. I have seen multiple variants of this. It is an easy way
of transitioning and old app built with client-server model to
a SaaS-version. You just set up a new database for each customer
installation.

I have seen use cases where tens of thousands of customers has 
their own database.

There are some *benefits* to this model.

  * A database can be corrupted and it affects only one customer.
  * You can upgrade a few of your customers to a new version of the app
    and move one customer at a time. If something breaks, the first
    customers will let you know.
  * You can move specially important customers to dedicated servers
    with more bandwidth and better performance.
  * It is easier to implement custom changes for specific clients
  * A database with a smaller number of records is much faster
  * Restoring lost data for a single client is easy - just restore the whole database backup for that client.
  * Wider range of choice when picking a database. With different databases for each customer even SQLite may
    be an option, but you will probably need one of the big players if you are going to share the database.
  * Your code will be simpler since you never have to check for client ownership of a record in the database.

But there are also some *drawbacks*:

 * Updating the database schemas will be a pain, even with a good script.
 * Handling all the database connections will require better
   hardware than an equivalent solution sharing a database.
 * Bugs coming from differences in the databases will be hard to track and test
 * Getting statistics from all your customers will be hard using only the database console
 * Row ID:s could be a source of problems when they are reused across the databases and later exposed via an API.

## What are you suggesting?

For new apps, I tend to go with a shared database. Migrating to newer
versions are relatively easy and scaling is easy in the beginning. If I get to a point where
I feel that multiple databases are the best solution I normally have enough customers on the app
to justify spending a couple of days on the migration.

I also like to spend more time in the code and less time managing databases.

## When would you go with multiple databases?

There are some cases that would make me consider having
one database per customer:

 * If you have an existing app that is built for a single customer and don't want to add `ClientID` to all database columns - and code to handle security.
 * If you will be offering a lot of customizations to the app
 * If you will offer installs on customer hardware.
 * If you will have a HUUUGE user base or they will store huge datasets.
 * If your app handles really sensitive data

