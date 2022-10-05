---
id: 1317
title: 'Our encryption tools must be free software, not just open source'
date: '2014-03-03T00:15:30-08:00'
layout: post
guid: 'https://parkerhiggins.net/?p=1317'
permalink: /2014/03/our-encryption-tools-must-be-free-software-not-just-open-source/
categories:
    - Uncategorized
tags:
    - crypto
    - 'free software'
    - 'freedom of the press foundation'
    - 'open source'
    - 'trevor timm'
---

In order to serve its purpose at all, encryption and secure communications software has to be single-mindedly dedicated to protecting and promoting its user’s interest. In the real world, that dedication can be subverted in a handful of ways. Broadly speaking, these failures can come from with technical problems, or from the developer’s interest being misaligned with the user’s.

The Freedom of the Press Foundation, which is currently raising money for a handful of important secure communications projects, published [a blog post Thursday](https://pressfreedomfoundation.org/blog/2014/02/why-its-vital-public-fund-open-source-encryption-tools) about the need to [give financial support to open-source encryption tools](https://pressfreedomfoundation.org/). It’s a good post, and a vital effort, but it focuses only on the second class of failures.

Part of the issue is that the term “open-source” is doing more work here than it’s able: yes, software has to have the technical robustness and verifiability that comes with access to the source code, but it can’t stop there.

Access to source code is important for any program you’re going to trust, but for a security or encryption program it’s essential, for two related reasons. One: if the program doesn’t adhere to [Kerckhoff’s principle](https://en.wikipedia.org/wiki/Kerckhoffs%27s_principle), it’s vulnerable to bad actors busting through the obscurity on which it depends. Two: in the spirit of [Linus’s Law](https://en.wikipedia.org/wiki/Linus%27s_Law#By_Eric_Raymond), eyeballs on the source code may be the best hope for finding bugs.

But beyond any kind of licensing questions, users need to know they are actually running the software described by that source code. That affects [a whole range of things that aren’t dictated by the license](https://www.eff.org/deeplinks/2014/02/open-letter-to-tech-companies). Software source and binaries both need to be distributed securely—an area in which [we are really horribly failing](http://noncombatant.org/2014/03/03/downloading-software-safely-is-nearly-impossible/). [Builds need to be verifiable](https://blog.torproject.org/blog/deterministic-builds-part-one-cyberwar-and-global-compromise), and currently only a small handful of projects promise that. Source code needs to be documented and tested, not just available to read. These are the kinds of technical guarantees that encryption tools need to make—not just access to source code.

These are reasons enough to reject software for encrypted communications that doesn’t follow these practices. But as is often the case, alongside these technical requirements is a need for software that actually respects the user’s freedom. For that reason, despite the fact that it might raise confusion about funding models, I think we should demand that our security tools are [not just open-source](https://en.wikipedia.org/wiki/The_Free_Software_Definition#Free_Software_Definition_vs_Open_Source_Definition), but are [free software](https://www.gnu.org/philosophy/free-sw.html).

Fundamentally, the Foundation’s blog post talks about how commercial proprietary software has interests that are out of alignment with those of their users. That’s absolutely correct, and the efforts to raise money for better services is a good way to address that problem in the near term. ((A couple of years ago, Jake Appelbaum and Dmytri Kleiner had [a great conversation about this](https://www.youtube.com/watch?v=zOiFgUj9bWI) at Republica in Berlin. I’ve been meaning to snip out the best bits for a while.))

But while “open-source” is a nice proxy to describe that kind of alignment, it doesn’t quite do the trick. Releasing source code doesn’t make software respect its users, and operating for profit doesn’t necessarily mean a software company will [cut corners on security concerns](http://www.nytimes.com/2014/03/03/technology/when-start-ups-dont-lock-the-doors.html) or turn to surveillance as its business model. Really, beyond a threshold of technical competence, the meaningful axis is commitment to user freedoms, and only free software delivers on that.

It’s like the problems with [that old tired phrase](http://epeus.blogspot.com/2012/03/when-youre-merchandise-not-customer.html), “If you’re not paying for it, you’re the product.” Sometimes you’re not paying for something because it’s been released free into the world; sometimes you’re paying for it and they’re still selling you out.

We can and should support open-source encryption tools. [The Freedom of the Press Foundation’s current bundle](https://pressfreedomfoundation.org/) is a great way to do that—and in fact, all of the tools it supports *are* free software and set a high bar for respecting users. (Full disclosure, I donated early on in this cycle.) But most importantly, we should support and promote tools that respect our freedoms.