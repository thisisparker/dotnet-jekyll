---
id: 602
title: 'Problems around me'
date: '2012-03-31T19:55:56-07:00'
author: 'Parker Higgins'
layout: post
guid: 'https://parkerhiggins.net/?p=602'
permalink: /2012/03/problems-around-me/
categories:
    - Uncategorized
tags:
    - apis
    - facebook
    - firesheep
    - foursquare
    - 'girls around me'
    - privacy
---

There’s no denying the creepy factor in “[Girls Around Me](http://girlsaround.me/)“, the iPhone app that until yesterday [displayed the public Facebook data of women checking in nearby on Foursquare](http://www.cultofmac.com/157641/this-creepy-app-isnt-just-stalking-women-without-their-knowledge-its-a-wake-up-call-about-facebook-privacy/). The creepiness was obvious enough that [Foursquare pulled the app’s API access](http://bits.blogs.nytimes.com/2012/03/30/girls-around-me-ios-app-takes-creepy-to-a-new-level/), rendering the service mostly useless. But in doing so, they’ve addressed a symptom, and not the underlying disease.

A year and a half ago, Eric Butler released a widely-discussed Firefox extension called “[Firesheep](http://codebutler.com/firesheep)“, which exploited a known weakness in many popular websites. The effect was that users could get one-click access to the accounts of other users making unencrypted connections to popular sites like Facebook or Twitter on public networks.

Firesheep worked so spectacularly because [the problem it exploited was well-known among experts](https://www.eff.org/deeplinks/2010/10/message-firesheep-baaaad-websites-implement) but poorly understood among the general public. That is to say, the problem was low-hanging fruit: even though the technology needed to hijack user sessions using cookies transmitted in the clear was universally available to the geeks with the expertise to use it, even popular sites had felt little pressure from their userbase to address the underlying problem. All Firesheep had to do was put a more usable interface on the well-understood tools, and it could catch the attention of people who weren’t previously interested in understanding the issue.

The problem that Girls Around Me has identified has the same combination of near-universal recognition in expert circles and general confusion outside of them. Most users cannot understand the privacy settings on most social networks. Worse, social network operators have a commercial incentive to make their settings deliberately confusing, and [even to induce user “over-sharing”](http://www.antipope.org/charlie/blog-static/2012/03/not-an-april-fool-1.html).

So, then, [Girls Around Me is to privacy settings what Firesheep was to security practices](https://twitter.com/#!/thisisparker/status/186235412061233152): a tool, usable by the general public, that makes an underlying problem understandable. ((Other entries in this field include [Please Rob Me](http://pleaserobme.com/), [You Have Downloaded](http://www.youhavedownloaded.com/), and even EFF’s [Panopticlick](https://panopticlick.eff.org/).))

But once you understand the two problems, the difference between them is clear. The solution to the Firesheep problem — that sites were not using, or not using by default, encrypted connections after initial log-ins — is simple: use established encryption by default. ((In the interim, too, savvy users could install [HTTPS Everywhere](https://www.eff.org/https-everywhere) and protect their own connections with websites that supported encryption.)) Put another way, addressing the issue just required a bit of attention, expertise, and resources.

By contrast, the Girls Around Me problem is part of a fundamental trade-off in the way centralized corporate social networks work today. And the cost of addressing it is correspondingly high. It comes down to users controlling how their data is collected and used, a premise antithetical to the business of advertising companies like Facebook and Google.

But until it happens, and until default settings are protective of user privacy, nothing can prevent creepy situations like Girls Around Me from popping up. As long as these situations look like Girls Around Me — a publicly available application that depends on consistent API access, creeps everybody out, and gets written up in major publications — Facebook, Foursquare, et al, can address it with after-the-fact API cut-offs. But nothing prevents, say, individuals with the know-how from rolling their own stalker apps and flying under the radar.

If you ask me, that’s the creepy part.