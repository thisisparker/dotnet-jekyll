---
title: 'Tooting from the intersection of art and technology'
date: '2022-11-10T18:00:00-05:00'
layout: post
permalink: /2022/11/tooting-from-intersection-art-technology
categories:
    - Uncategorized
tags:
    - mastodon
    - 'social media'
    - hometown
image: /assets/images/intersection.png
---

<img src="/assets/images/intersection.png">

I've finally taken the plunge at set up my own Mastodon instance at a dedicated domain, as has been foretold by the prophesy of my recent posts. Instead of using one of the [very fun subdomains I surfaced in classic literature](https://parkerhiggins.net/2022/11/public-sub-domains), though, I found one that plays on the goofy meme-y phrase about "the intersection of art and technology." And so, my new Mastodon instance lives at [tech.intersects.art](https://tech.intersects.art). The plan is to offer accounts to a handful of friends—never a big general purpose server, but hopefully developing something adjacent to a group chat.

When I posted about the move, somebody on Twitter [asked about the benefits of a smaller server](https://twitter.com/7im/status/1590792701846638593), and I found myself writing enough that it seemed like a good thing to bring over here. This list is a little loosey-goosey, but maybe it will be useful to somebody considering making the mover.

- My instance is running [Hometown](https://github.com/hometown-fork/hometown), which is a fork of Mastodon by Darius Kazemi that introduces a few useful features that are unlikely to get merged into the main version. One that seems significant is the inclusion of "local only" posts, which I hope can help facilitate the group chat feeling. I had been familiar with Hometown before, and had read Darius' [Run Your Own Social](https://runyourown.social/) guide, but a [post from Christa](https://gist.github.com/hartsick/f057cfb16657b93356e045c48b633f4f) really sold me on it. If you're interested in trying Hometown, there are [a bunch of public servers running it](https://github.com/hometown-fork/hometown/wiki/Hometown-servers).
- There's been a lot of discussion about moderation and defederation recently, and I think the implied Mastodon model mostly works better with smaller instances. That is to say: I like the idea of making defederation decisions by and for a small group of people (me and my friends), and I prefer knowing that my own ability to federate isn't contingent on the moderation decisions of a big server admin. In my timeline right now are discussions about instances defederating with [journa.host](https://journa.host/about), an instance that thousands of journalists have recently signed up for, and [the flagship instance](https://mastodon.social/) as well. I totally respect the ability of instance admins to make those decisions, but I don't want to get caught up on either end of it, and I think I'm less likely to in my little corner of the fediverse.
- Also it's a funny cool domain! I haven't had a vanity email address in a while but I've always respected the move. One of my favorite employee perks at my last two jobs where getting `@eff.org` and `@freedom.press` emails. My hope is that this feels like a little symbol of belonging for a handful of my buddies.
- I know the recent rush of traffic was starting to strain people's servers, and there's been a lot of discussion about making sure that people were chipping in to cover volunteer admin support. I only put together recently that, because of ActivityPub's push model, [posting to many followers is more expensive](https://ar.al/2022/11/09/is-the-fediverse-about-to-get-fryed-or-why-every-toot-is-also-a-potential-denial-of-service-attack/). Hosting my own instance means I can worry less about whether I'm a drain on somebody else's resources.
- Similarly, I can throw money at my own instance if it starts to get backed up! I'm hosting my instance with [fedi.monster](https://fedi.monster), and they make it easy to bump up my installation's resources if I need to. I'm not sure that will always be worth it, but it's nice to have that option available.

Given all these benefits, I'd been casually hoping to migrate servers for a while now, and certainly since [it became possible to transfer existing followers](https://github.com/mastodon/mastodon/pull/11846). I'm excited to be starting this chapter of my Mastodon usage now.
