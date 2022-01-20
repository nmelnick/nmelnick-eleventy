---
title: "Lifecycle of an Android Application"
date: "2011-04-20"
categories: 
  - "code"
tags: 
  - "android"
  - "development"
  - "eljay"
  - "livejournal"
---

Every time I get a new gadget, something possesses me to try to write an application for it. It's happened with dang near everything since the Newton, yet only a few gadgets have ever had a finished project. I tried the hardest on Symbian, but never came up with anything useful. I'd like to blame the SDK, but you should never blame your tools, no matter how much they completely sucked.

In October of 2008, a brand new T-Mobile G1 arrived via UPS, one of the first Google Android devices to hit the market. I had always owned smartphones, whether they ran Windows Mobile or Symbian (S60 or S80), but I wanted to get something that was easy to develop for, and would work well on my network. So, Symbian was out (hated the SDK), iPhone was out (Just started supporting apps, plus no one wants to be on AT&T), Blackberry was out (SDK even worse). Android seemed like a really neat, but young option. Being on the bleeding edge never scared me, it just usually screwed over other people.

So, approximately 3 days after receiving that G1, I downloaded the SDK, and started to use my extremely rusty Java skills to bang out a LiveJournal client for Android. It's not as though I still really used LiveJournal, but I felt like it'd help me try out all of the neat APIs in Android. Web services, location tracking, image capture and manipulation, they were all there and usable. A shell of an application started to emerge around a series of mocked up layouts, and I was able to hook up login, posting, preferences, and user pictures in a short amount of time. **ElJay** was born, and I even [wrote about it here](http://www.abstractwankery.com/2008/10/eljay-a-livejournal-client-for-a/75). I'm amused at how proud I was that it was pretty complete after a few days -- because it shows. Since I decided to dive right in instead of going through tutorials and example applications, it was subject to many of the first time Android developer errors. Screen rotation would lose settings, or interrupt a login, or interrupt a post. Web activity would throw exceptions that I never caught. Nothing was in a service, so switching applications or views would interrupt the same interruptables as above. Everything I did was in onCreate, so switching back to the application after Android cleaned house meant that someone would have to log in again. Sometimes, state wasn't kept, so you'd post to no account at all. It was a barrel of laughs. I updated and updated until it was a mess of spaghetti code and generic exception catching. Android 2.0 finally broke it, and I didn't care for a while.

I eventually pulled it from the market.

... until the screams entered my inbox.

A few weeks ago, I recommitted to ElJay, but instead of running through to try to fix it, I made the best and worst choice I could make, and started over. This time, I started it as if I were doing one of my Perl-based web applications, or writing a desktop application -- I started with the back end. My first task was my XML-RPC interface, followed by my LiveJournal model. I created a unit test suite for those external interfaces. I created a suite for all of my display controllers. After a while, I got to the point where I had a decent unit test suite, and a few test accounts that passed the unit test suite. This process took a lot longer than the "few days" it took to bang out the first version, but from a system level, it worked well. It also helped me solve a long-standing bug I ran into in the first version, where the default Java XML library used by Android doesn't handle some output from LJ very well. Hey, I could have saved myself from a rewrite! ... Nah.

Tangent.

Only then did I start working on the user interface. This time, I could actually plan for exception handling, threading, the external service, the sync API, even basic user interaction. It also honors resolution independence properly, since I'm no longer using pixels as measurement. :P It's amazing how much more confidence I feel in this application -- not that I believe it's bug free or foolproof, beta testing will prove that wrong within minutes -- but that I can easily work with it, fix issues, and section pieces out for later. Things are getting really close now, and [the beta](https://spreadsheets.google.com/viewform?formkey=dGQ4a01RU2NOWkFjZkRuMlk1RWkwQUE6MQ) rolls out in less than two weeks.

For those keeping track, the first version allowed posting with user pictures, security options, tracked your location, worked with tags and moods, and allowed you to save entries for later. The new one does all of that -- and well -- but also adds friends list support, attaching photos to your posts, and with any luck, manage your messages. I'm also throwing ads in, but they're optional.

It does live.
