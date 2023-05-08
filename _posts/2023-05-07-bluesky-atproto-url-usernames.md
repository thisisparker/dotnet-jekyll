---
title: Bluesky, AT Protocol, and the exciting possibilities of URLs as usernames
date: '2023-05-07T18:00:00-04:00'
layout: post
categories:
    - Uncategorized
tags:
    - dns
    - bluesky
    - "social network"
image: /assets/images/bird-bluesky.jpg
---

<img src="/assets/images/bird-bluesky.jpg" alt="A bird perched in a bare tree against a blue sky." />

I've been posting for a few weeks now on [bluesky](https://bsky.app/), a new social network built on new technology called the [AT Protocol](https://atproto.com/). Everything about that stack—the app, the network, the protocol, etc—is under active development and subject to change (and my understanding might not be fully correct), but I am excited about one component in particular that I think is still underappreciated.

Namely, it's the protocol's first-class support for [domain names as handles](https://blueskyweb.xyz/blog/3-6-2023-domain-names-as-handles-in-bluesky). This design decision may not seem as radical as it is, because for now there is only one star in the bluesky constellation. But if the network continues to grow, this role for domain names could have pretty major implications.

### My domain is my passport, verify me

Even today, there are a few big consequences. The first comes as a result of the fact that a domain username requires demonstrating control over the domain itself (through the use of a DNS record). In light of the blue-check verification tire fire happening at Twitter, a lot of focus has been on the way domains-as-usernames delegate out the verification function: bluesky employees don't need to confirm by hand that the accounts purporting to be the Washington Post or Senator Ron Wyden are who they say they are, because in both cases they have verified through DNS records.[^1] Washington Post's username is `@washingtonpost.com`, and Wyden's is `@wyden.senate.gov`.

Situating the question of identity verification at the DNS level makes a lot of sense to me. Much of our security models of the web already rely on the domain name system being sort of an ultimate source of truth; consider how much anti-phishing advice boils down to "manually enter the domain in question to get you back to safe territory." In the case of Senator Wyden, even the top level .gov domain is an indicator of (some level of) trustworthiness.

Here and elsewhere, I think it is useful to compare with the approach that Mastodon[^2] has taken. Some people have rigged up small Mastodon instances at domains they control to allow them to effectively confirm their identity through their username, but for the most part verification happens by demonstrating control not of the DNS responses for a URL, but instead over the content served from that address. [My Mastodon profile](https://tech.intersects.art/@xor) has a verified link to [parkerhiggins.net](https://parkerhiggins.net) because of the [`rel="me"` link](https://indieweb.org/rel-me) at the top of this page.

There are pros and cons to each of these approaches. I think the Mastodon approach is most reasonable in a world where people run servers that serve blogs or personal home pages or project portfolios where they control what gets served. I'm one of those people, clearly! In a post about more than just verification, Ben Werdmuller categorizes the difference as [one between European and American mindsets](https://werd.io/2023/the-fediverse-and-the-at-protocol), and that seems like a good insight.

I think also it reflects a "web vs. net" difference. Mastodon and ActivityPub strike me as an evolution of the vision of the web that reigned in the height of the RSS and blogging era—a vision that I have a lot of affinity for. By contrast, bluesky doesn't even really have a neat way of linking to posts. Verification by HTML reflects a web-first mindset, verification by DNS reflects a net-first mindset.

### Name that space!

Beside top-level verification, there's another cool thing that DNS usernames give you: a namespace. It's just as easy to verify subdomains with DNS records, and that demonstrates a connection between all of the "children" of a given domain name.

So far I haven't seen many uses of this. But when I set up two of my bots on the service—ports of the [old roadside](https://twitter.com/oldroadside) and [pomological](https://twitter.com/pomological) bots—I decided to make them subdomains of my own handle: `@roadside.xor.blue` and `@pomological.xor.blue`, respectively. For me that's just a neat thing, but for organizations it may prove to be an elegant way of doing delegated verification.[^3] Contrast that to the dozens of official New York Times Twitter accounts that share some branding and an "@nytimes" account prefix.

One neat quirk about the bluesky implementation is that the mapping from an @-username to the canonical user identifier[^4] happens right when a post is created and doesn't break later even if the DNS records change. So if an organization verifies you as an employee—say, `@sullivan.washingtonpost.com`—and then you leave for a different job, _old_ uses of your handle will still point to the correct user profile, even if you no longer use that username.

A second neat quirk is that you can have multiple DNS entries pointing to a particular user. For example, I've got a DNS record at parkerhiggins.net pointing to my user page, even though I'm not using `@parkerhiggins.net` as my username.

I think that means that you could create intentionally ephemeral DNS usernames as identifiers, and count on posts made with those DNS usernames to point to the right user. For example, you could have `@editor.washingtonpost.com` or `@potus.whitehouse.gov` point to the current occupant of that role, and preserve the meaning of references made in posts. (Twitter's username system handles this somewhat inelegantly: all `@POTUS` tags point to the current president, for example.[^5])

It's definitely worth noting here that this combination enables fun possibilities and also some more sinister ones. The namespace identification goes one way, but I'd guess many users assume some bidirectionality. If I own evilexample.com, I could imply that Alice has some affiliation with it by pointing `@alice.evilexample.com` right to her profile. Or I could set up `@todaysenemy.evilexample.com` to coordinate bad actors to a particular target.[^6]

### Portable in a storm

The last thing I want to focus on is the "portable" nature of domain-based usernames. That's mostly true only in theory today, but again there are already some pretty cool knock-on effects.

The plan for bluesky and AT Protocol is eventual federation. They've released [more information about that this weekend](https://blueskyweb.xyz/blog/5-5-2023-federation-architecture); the upshot is that eventually many different "blueskies" will exist, and users will be able to choose between them. A design goal is that users hopefully won't have to think about this too much, unless they want to.

According to the plan, users will eventually be able to switch their affiliation and take their data with them. And if they've used their own domain as an identifier, they wouldn't even change usernames.

That particular benefit depends on the direction the bluesky ecosystem takes. Portability matters less if there's nowhere else to go. Notwithstanding that, though, domains-as-usernames mean good things for user portability right now.

The list of stable platform-agnostic unique identifiers for a person is pretty short. Your email address, your phone number, your social security number or similar government-issued ID. It's worth noting that these are each pretty sensitive! But you get asked for each of them pretty frequently, because identification is important and hard to do.

Even outside of the technical promises of portability, I like the idea of allowing users to connect their identity to a less sensitive stable identifier under their control, like a domain name. This is sort of the promise of Signal's (controversial) decision to use phone numbers as identifiers for users: when its developers were explaining their choice not to build towards federation, they argued that the ["address book is now the social network."](https://signal.org/blog/the-ecosystem-is-moving/) In other words, the power of portability comes not from your ability to use another Signal server, but from you to quickly reassemble your network on a different platform altogether.

It's a small example, but already [Jesse J. Anderson's](https://adhdjesse.com/) [SkyLink browser extension](https://addons.mozilla.org/en-US/firefox/addon/skylink-bluesky-did-detector/), which lights up when you're visiting a domain that has a pointer to a bluesky account, feels like a step in the right direction as a tool for users that works directly through DNS.

If bluesky is one domino in the sequence that leads to my being able to use domain names as stable long-term identifiers outside of any platform's control, I think that would be a great thing for users.

[^1]: There is also a non-DNS mechanism to demonstrate domain ownership, but I'm ignoring it for right now because I think it's likely to change in light of [a funny exploit](https://chaos.social/@jonty/110307532009155432).
[^2]: slash ActivityPub slash the fediverse. Lots of nuance in those distinctions, but that is secondary to the main point here.
[^3]: This is kind of like what Twitter is [calling "affiliation badges" and charging $1000/month for](https://www.theverge.com/2023/2/4/23585612/twitter-gold-checkmark-business-subscription).
[^4]: A [DID](https://www.w3.org/TR/did-core/), outside of this post's scope.
[^5]: Sort of. Linked usernames in replies to a @POTUS tweet will probably correctly resolve.
[^6]: Neither of these are bluesky-specific. I could also redirect alice.evilexample.com to her web site, for example. But it could possibly become a problem on that network in a way it hasn't before.
