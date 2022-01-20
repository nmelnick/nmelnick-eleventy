---
title: "The Ongoing Saga of this Commodore B128 (3/x)"
date: "2021-03-15"
categories: 
  - "vintage"
tags: 
  - "b128"
  - "commodore"
  - "repair"
  - "vintage"
coverImage: "/static/img/20200926_110300.jpg"
---

In the [last post](https://www.nmelnick.com/2021/03/the-ongoing-saga-of-this-commodore-b128-2-x/), I ended up desoldering some components that I thought could be a problem, only to find that they appear to be _just fine_. I moved on to second guess my assumptions due to my experience level, specifically wondering about whether these address and data lines are correct. I then sent off all of my socketed chips to another member of the Commodore CBM-II community to see what he thinks.

Oh, ho, ho.

My new Commodore friend popped my 6509 CPU, 6526A CIA, PLA, and 3 ROMs into one of his test boards to verify functionality. My ROMs and PLA successfully ran for an hour of diagnostics. My CIA checked out okay (but looked quite different than the CIAs he had). My 6509... was toast. In two different machines, it hung up before it could even hit diagnostics. I don't know for sure if what he saw was similar to what I see on my board, but it certainly was not computing, and that looked a lot like what I was running into.

![Camera image of the Commodore B128 displaying diagnostic results](/static/img/diagscreen.jpg)

Now, nothing else using the 6509 was released by Commodore, so finding these chips in the wild is rare to impossible. Luckily, back in December, I ordered a [Nu6509](http://store.go4retro.com/commodore/nu6509-6502-65c02-65c816-to-6509-adapter/) from [RETRO Innovations](http://store.go4retro.com/), and with any luck, that will arrive soon. The Nu6509 allows one to use a 6502, 65C02, or 65C816S CPU, and adds the memory banking logic of the 6509 to provide a fully compatible CPU for these machines. I ordered it as a "just in case", and now it looks like we have a winner.

That said, I'm fully aware that this could be one element of potentially multiple failures in this board, so I am not getting my hopes up.

In the meantime, I am awestruck by the work of Michal Pleban [creating a replacement 8088 card for the CBM-II](https://www.facebook.com/708927025/videos/10157878724537026/). Commodore originally created an 8088 board to allow CBM-II owners to use MS-DOS 1.25, however, since none of the I/O ports matched up with the IBM PC, it was DOS-compatible, but not PC-compatible, so of limited usefulness. Michal took the original card design, and created a quasi-virtualization layer to proxy those requests to Commodore hardware. Furthermore, he managed to get FreeDOS running on it from an SD card, making it a fairly usable XT-style machine that can work in high profile and low profile CBM-IIs. [Now he has a schematic available, and is building boards to sell this fall.](http://www.cbm-ii.com/) If I get this machine working, that may end up being my next step -- unless I can convince him to send me a card. :)

Next update when I receive my parts and my Nu6509.
