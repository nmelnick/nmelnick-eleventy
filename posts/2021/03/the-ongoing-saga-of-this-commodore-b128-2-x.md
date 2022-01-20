---
title: "The Ongoing Saga of this Commodore B128 (2/x)"
date: "2021-03-02"
categories: 
  - "vintage"
tags: 
  - "b128"
  - "commodore"
  - "repair"
  - "vintage"
coverImage: "/static/img/20210222_103343-scaled.jpg"
---

In the [last post](https://www.nmelnick.com/2021/02/the-ongoing-saga-of-this-commodore-b128-1-x/), I introduced my US-market Commodore B128 that wasn't feeling like being a computer. A lot of the diagnostics looked okay, and I was just about to start desoldering components out of a combination of hope and despair.

## Some Soldering Required

Each desoldered component was replaced with a same-size socket, and continuity tested from the pin receiver to the bottom of the board.

Step one was desoldering the 74LS275 at U12. I wasn't sure if there was an internal short that was bringing down D1 at pin 12, and I couldn't test it in circuit effectively. Once out, I put it in my TL866-II to test, and it tested good. For fun, I replaced it with another 74LS275, with the same results. Drat.

Second was the RAM connected to D1, at U65 and U73. That is, theoretically, the only other thing on D1. I don't have a DRAM tester, but I do have some 3764s which should be 1:1 compatible. Popped those in, no appreciable change. Drat.

Third was the 74S138 at U40, to figure out if there's an issue with chip select, since what I was seeing in the oscilloscope didn't really match what I thought the truth table said. It also tested good in the TL866-II. I tried a replacement SN74AS138N1 but that didn't change any of the chip selects, so maybe I'm reading that truth table wrong.

## Hands in the Air

It was this point that I started to wonder if I was going to desolder every TTL chip on this board. Due to my lack of experience, I don't know what these address and data lines are supposed to look like on an oscilloscope, but something about them bother me. It shouldn't be power ripple, but I just have this nagging feeling that something is affecting the data bus on this board, and that's why things are getting weird. Furthermore, there's a huge difference in how the bus looks when the BASIC ROMs are installed versus when they are empty. While I've already successfully read them in my EPROM programmer, something is bugging me.

With that, I'm taking up the offer of another member of the B128 community. He's going to burn me a new 82S100 PLA, and while doing that, he's taking all of my socketed chips and testing them in a working B128 board. I still have a feeling everything's going to check okay, but at least it'll eliminate those chips, particularly the 6509. [Next entry](https://www.nmelnick.com/2021/03/the-ongoing-saga-of-this-commodore-b128-3-x/) will be after those chips are tested and back in the board.

* * *

1. It's incredibly difficult finding a 74S138 nearby, though fairly available as used stock on eBay. I went the instant gratification route after reading up on legacy vs modern versions of these TTL chips. The S is a faster max propagation delay (8ns), high power component. The LS was a low power, but somewhat slower (21ns) variant. The AS has a typical delay of 9ns, whereas the ALS is 12ns. Figured the AS was the closest match to the component.
