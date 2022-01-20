---
title: "Adventures in Vala: Ambition Framework"
date: "2012-07-18"
categories: 
  - "code"
  - "vala"
tags: 
  - "ambition"
  - "framework"
  - "perl"
  - "vala"
---

Quite some time ago, I posted about my [Adventures in Objective-C](http://www.abstractwankery.com/2010/02/Adventures%20in%20Objective-C/91), postulating that people would be willing to rapidly develop in a static-typed language if the language was easy to deal with. I created the foundation of a web framework that didn't do _too_ much, but was functional enough to prove that it was possible. I also gave up shortly after, as I found development on Windows and Linux to be a gigantic pain -- too few libraries, not much support.

Some of the same ideals I was going for in that previous post still hold true. Java still clicks in a weird way for me, even if it's too verbose and runs in a VM and 90% of the web frameworks for it annoy me to death. Objective-C was cute, but mostly useless for me. I don't mind the idea of C#, except for the fact that it's Windows-centric, and I'm still uncomfortable putting my eggs in the Mono basket.

In the meantime, I stumbled across a language called [Vala](https://live.gnome.org/Vala/). Vala's roots are in the GNOME community, where they have a couple of great C libraries: GLib, and included in that, GObject. Using this standard library, C-based GNOME applications have had a lot of the great benefits of object oriented programming while maintaining the speed and support of the C language. Unfortunately, you got everything else that C provides: no memory management, no namespaces, and difficulty in reading it later.

I'm going to get flamed for that.

Nevertheless, other people saw some of those same things. They also saw some Mono applications creeping into the GNOME core, and felt that all the pieces were there to do something better. Vala was born as a true object oriented programming language, with a very similar design to C#. The difference is, it relies on GLib and GObject to accomplish the OO goals, and therefore, compiles into C, which is then compiled by gcc. As a result, you get significantly smaller and faster binaries than VM-hosted languages, with very minimal pain. Furthermore, you don't need to use GTK or anything like that, it's still a general purpose language that can be hosted on any platform that can compile GLib. That means I can code on OS X and Linux, and, while I haven't done it in a while, Windows can join the party as well.

You see where this is going.

In the end, I took my ideas for a reasonable web framework, and started porting them to Vala. Months ago, I had a proof of concept similar to the ObjC example in my previous post. But, I kept working on it. Routing, templates, plugins, configuration, build systems, all managed to find their way in. Then, the nice things. Session, Authorization, and Form frameworks are a part of it. I've started on a fairly simple ORM, as well, Almanna. The result is, well, this.

This blog is the first production test of the framework. I ported the blog software from Catalyst to Ambition, launched it here on the existing database, and I'm going to see all the places it fails. It will likely do a lot of failing, but it's a decent first effort. After a little stress testing, I'll open this up on GitHub, and see where else it can go.
