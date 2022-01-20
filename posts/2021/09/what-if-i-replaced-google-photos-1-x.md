---
title: "What if I replaced Google Photos? (1/x)"
date: "2021-09-10"
categories: 
  - "off-topic"
---

Years and years ago, as I started using operating systems besides Mac OS X full time, I decided to let go of iPhoto and start doing my photo management elsewhere. I ended up on Google Photos for a few big reasons. One, the launch photo editing was pretty amazing. Two, since the primary interface was web-based, it was easy to use pretty much anywhere. Three, since most of my photos were coming from my phone by that time, having it auto-upload from my phone was pretty amazing.

Some time has passed, and I'm starting to get that itch again. I still use Android as my primary mobile OS, but I'm less trusting of Google both from a privacy standpoint and a feature standpoint. They absolutely have the ability to mine through my data, even if I am paying for the storage. They also have a terrible track record of removing features and functionality that they feel doesn't get a lot of traction.

So, I have a home file server, I have outside cloud backup, maybe the landscape is better now for multi-device photo management than it once was. I'm going to explore.

## What do I want?

There are some hard points that I like about Google Photos that I'd like out of any solution, and then there's other functionality that I'd really like to have but wouldn't stop me from migrating. I'm open to both open source and proprietary solutions, provided the proprietary solution doesn't limit me to the consuming platform.

### Must have

- Photos should sync to the destination without me performing the action manually
- Photos could be viewed, added, or removed from a web interface
- Albums could be created, viewed, or removed -- and photos could be moved in and out from a web interface
- I should be able to download images locally from that interface
- Basic categorization should exist automatically...
- ... and in particular, automatic facial recognition should exist and be navigable

### Nice to have

- Open source
- Does not require a separate cloud service
- A server side agent that works on FreeBSD
- A native application for Android and/or iOS for faster, fluent navigation
- Google Photos is pretty good at determining other objects, words, and locations from photos, and I'd like to see something similar. For instance, searching for "green", or searching for "car"
- Location categorization for determining where photos were taken
- Video organization along with photo organization
- Automatic file organization, similar to iPhoto, to make it easier to export, back up, and avoid collision
- Duplicate detection, in case two photo sources get mixed up
- Public sharing of photos or albums, to allow those with a certain link to view certain photos without giving away everything

## Where to from here

At the time of this post, without veering off to other solutions, these are the ones I'm going to be looking at, in alphabetical order:

- Adobe Lightroom (proprietary, requires subscription)
- LibrePhotos (open source)
- Mylio (proprietary, requires subscription, potentially allows for self hosting images)
- Photonix (open source)
- PhotoPrism (open source)
- Piwigo (open source)

## Auto syncing from my phone

While some of the solutions I'll be looking at have some capacity for auto sync from my phone, I wanted to at least have a solution to get photos from my phone to my file server without having to mess around with it.

### Enter [Syncthing](https://syncthing.net/)

Syncthing provides bidirectional or unidirectional sync between folders on two different devices. In some cases, this could be a documents folder on your laptop and your desktop, or maybe important files between work and home. They have agents for Windows, Linux, macOS, the various BSDs, and even Solaris. Even better, they have a first party client for Android. A third party is currently working on an iOS client that will likely cost some money to use.

I was able to set up my file server and my Pixel 4 very easily, and was able to point the Pixel at the QR code from the file server's web interface to link up the two devices. By default, the Android client is set up to send pictures one way from the camera folder to another device, so it was a matter of flipping the switch to enable it, and authorizing the connection from the file server and setting the destination folder. All of the NAT traversal was automatic, and within a few minutes, all of the photos from my phone were safely on my file server.

That seems like a good starting point to me, I'll worry about a Google Photos export once I find a decent solution.

More to come.
