---
title: "Log4Vala - A logging framework for Vala inspired by Log4J"
date: "2014-06-19"
categories: 
  - "code"
tags: 
  - "library"
  - "log4vala"
  - "logging"
  - "vala"
---

It's getting pretty easy to see that I should start finishing some entries for this blog if it's going to be at all relevant or useful, but I'll take a moment to introduce another "thing".

This past weekend, while working on a web project in [Ambition](http://www.ambitionframework.org), I started wishing I could control logging in a better way than what was already provided. Specifically, I wanted to be able to amp up logging in one controller while keeping another one quiet. In a horrific turn of events, I found myself longing for something like log4j/log4perl/log4net so I could use a configuration file to handle that.

A few days go by, and here we are.

Introducing [**Log4Vala**](http://github.com/nmelnick/Log4Vala), available on GitHub. Available as a shared library to integrate into your Vala application or library, Log4Vala provides most of the core concepts available in the other logging frameworks, without a lot of overhead. Yes, there are still a few method calls for each logging pass, but it's quiet a bit tighter than a VM environment. I'm pretty happy with the result.

Patches/documentation/heckling welcome.
