---
title: "MooseX::Declare, TextMate, and TmCodeBrowser"
date: "2010-02-18"
categories: 
  - "hax"
tags: 
  - "ctags"
  - "moose"
  - "moosexdeclare"
  - "textmate"
  - "tmcodebrowser"
---

Do you use [TextMate](http://www.macromates.com)?  
Do you use [TmCodeBrowser](http://www.cocoabits.com/TmCodeBrowser/)?  
Do you use [MooseX::Declare](http://search.cpan.org/dist/MooseX-Declare/lib/MooseX/Declare.pm)?

Must be a pain that nothing shows up the side pane when you start using it. It was for me.

Open _'~/Library/Application Support/TextMate/PlugIns/TmCodeBrowser.tmplugin/Contents/Resources/.ctags.tmcodebrowser'_ in a text editor. Add the following:

```
--regex-perl=/^[ t]*(class)[ t]+([^ t;]+)s*[ t]*[{;]/2/c,class,classes/--regex-perl=/^[ t]*has[ t]+'([^ t;(]+)'/1/p,property,properties/--regex-perl=/^[ t]*method[ t]+([^ t;(]+)/1/m,method,methods/
```

Reload TextMate.

Bask in the awesome.
