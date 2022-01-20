---
title: "The Comeback of a Language"
date: "2007-06-22"
tags: 
  - "catalyst"
  - "frameworks"
  - "perl"
---

Not sure what was going on with me this morning, but I think I was trying to pick a fight in [#catalyst](irc://irc.perl.org/catalyst) this morning. I was at work all of about ten minutes before I asked a simple question, amounting to: "Are there any plans to bring Catalyst to a wider audience?" Confusion followed, followed by a decent discussion. The general point I was trying to make is simple. If you ask someone who works near web development if they've ever heard of Ruby on Rails, chances are, they have. If you ask them about Catalyst, you'll usually end up with a shrug. Those who are willing to listen further generally stop listening as soon as you say "framework for perl".  
  
There is a stigma attached to perl for various reasons -- people view perl as unreadable, or slow, or hard to develop in on a large scale. Most people have a perception of perl that dates back to the late 90's, coding against cgi-lib.pl or CGI.pm. Hell, back then, I was rolling my own CGI scripts so they were 'lightweight'. God forbid anyone look at _my_ code from back then. Perl was pushed as a rapid-development, but hacky language, and most people produced a lot of code that looked like line noise or otherwise, and that is what is burned into people's minds. There is an unfortunate percentage of the current perl population that still writes kludgy one script wonders and calls it a web application, and that's also bad for the community, in my opinion. Frankly, a language that holds contests on who can make the most unreadable code, or who can fit the most into one line, generally deserves that stigma.  
  
The other side of the coin is Perl 6, the upcoming complete rewrite of Perl. If you Google for perl 6, you'll find articles talking about its impending release dating back to 2001, yet we still don't have a final revision. The bytecode interpreter is far from complete, and the closest thing there is to a working, usable interpreter is written in Haskell, another higher level language. The whole thing feels kludgy and incomplete to an outsider, and that's probably because compared to other modern object oriented languages like Ruby and Python, Perl 6 is kludgy and incomplete.  
  
So, disillusionment and wankery abounds when it comes to perl, and a lot of it is deserved. It's a perception problem, and one that is almost impossible to solve. But, hell, I'm stubborn, and other people have made far inferior products rise from the ashes.  
  
Those who remember a few years back realize that not many people were aware of or used Ruby before Rails came out, and a lot of old perl hands fell right into Ruby because of its similarities. I find Ruby to go against 'what I mean', so it's a reach when I start pounding out any code. I was hoping to find an alternative when I stumbled upon Catalyst, and I've been hooked since. I think quite a few people would see the same thing, if they only knew what was there.  
  
My plea to #catalyst was simple. Catalyst is a diamond in the rough, a flexible, fast, and powerful web application framework that is very easy to use once you get over the first learning curve. It is an excellent demonstration of modern OO perl development, despite any flaws or issues that still remain in the framework. The problem, however, is there is very little marketing or outreach happening, and without any kind of constant public opinion, the userbase stagnates and eventually shrinks, leaving frameworks like Catalyst to die on the vine. Someone within the Catalyst community, or even tangentally related to the Catalyst community needs to find a way to bring people back into the perl fold by making them aware of the strengths of the framework.  
  
A few things would need to happen, in no particular order. Note that this is only my opinion, and I'd be happy to be told I was wrong.  

  
- They want their wiki moved from Trac to MojoMojo before they do any major wiki work. Fine, I'll give that one.
  
- Get some nice looking skeletons into the default Catalyst project template. Make it look pretty. For some reason, this actually works, and makes people want to do the same.
  
- Catalyst's primary development happens on mailing lists and on IRC. This should be outlined somehow within the wiki so creep doesn't occur.
  
- The primary focus of catalystframework.org should be marketing and outreach -- a bulletproof example of the stability and scalability of an application written in the framework, with easy to deal with tutorials and a complete set of hyperlinked documentation. Links should be given to external sites who use the framework, as well as third party Catalyst tutorial sites.
  
- There needs to be a third party tutorial and development site! You can toot your own horn, but it's hard to convince people that what you have works really well unless they can see other people getting together and doing things really well. The real championing of OS X doesn't happen on apple.com, so the real championing of Catalyst shouldn't be on catalystframework.org. Luckily, it's not, as the site is a bore and makes the project look dead, as it is hardly updated.
  
- Along with the third party site comes some community support. Bring people together. Show people to IRC, bring people to a forum. Get a forum of a couple of hundred and hold CatalystConf or something similar. The key to getting the product into the eyes of many is to show people that there is an active following behind it. Lesser languages and frameworks do it and give people confidence to continue developing. Check out Lasso and REALbasic if you have no idea what I mean.
  
- Tell people you're using Catalyst. If you run a site that is truly great, and starting to get public attention, mention the framework. The Rails apps are doing it. The PHP people just try to hide that it's PHP behind it.
  

  
  
I'm not talking about zealotry, here. I'm not talking about Catalyst being the best or brightest, or that perl is the best or the brightest. I'm not talking about how Ruby, Python, or PHP suck (this time). I'm only talking about bringing a really great language and a fantastic framework into the foreground so people are at least aware of the options before they talk some smack.  
  
Or maybe, just maybe, I'm completely full of it.
