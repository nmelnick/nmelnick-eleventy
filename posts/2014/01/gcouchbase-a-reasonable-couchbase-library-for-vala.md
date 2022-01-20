---
title: "GCouchbase - A reasonable Couchbase library for Vala"
date: "2014-01-02"
categories: 
  - "code"
  - "vala"
tags: 
  - "couchbase"
  - "vala"
---

I'm pleased to announce that there is a reasonable [Couchbase](http://www.couchbase.com) library coming along for Vala, and it is semi-functional at this point. Sure, an announcement seems weird at "semi-functional", but considering the absence of a library up to this point, I'm calling it good.

Introducing GCouchbase ([github](http://github.com/nmelnick/gcouchbase)/[web](http://gcouchbase.ambitionframework.org/wiki)).

GCouchbase is a combination of a fully functional vapi wrapper around the C libcouchbase library and a pleasant GObject layer on top of it. The libcouchbase functionality is available to the end user via GCouchbase or on its own, but GCouchbase makes the library work more like how one would expect out of a higher level language. The structure is loosely based off of the .NET library, but does not rely on libmemcached or any other proxy layer.

For those who may not be aware of what Couchbase is, it is (in my humble opinion) NoSQL done right. While similar in functionality to other offerings like MongoDB or CouchDB, Couchbase combines a persistence layer with a memory layer to provide fast, scalable JSON blob storage and retrieval that scales evenly with memory and CPU. In other words, you don't need to have a cache layer, a data layer, and a replication layer, Couchbase handles it for you. The built in view functionality is powerful, but can directly connect to an ElasticSearch instance for advanced queries.

It's very neat, and blends in nicely with the speed of Vala.
