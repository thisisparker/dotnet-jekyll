---
id: 802
title: 'Stanford Cryptography and #CryptoParty'
date: '2012-08-23T22:30:00-07:00'
layout: post
guid: 'https://parkerhiggins.net/?p=802'
permalink: /2012/08/stanford-cryptography-and-cryptoparty/
categories:
    - Uncategorized
tags:
    - crypto
    - cryptoparty
    - 'dan boneh'
    - encryption
    - stanford
---

I recently finished the free online [Stanford cryptography course](https://class.coursera.org/crypto) offered through Coursera and taught by Dan Boneh. It’s a challenging class, with at least four hours of lectures a week, and it actually took me two attempts to get all the way through it. I’m really glad I did though: cryptography is a tremendously empowering subject, and learning the theoretical foundation can be not just educational but inspirational. In one early lecture, Boneh lays out a basic tenet that really spoke to me:

> There’s a very central theorem in crypto, and it really is quite a surprising fact, that says that any computation you’d like to do, any function F you’d like to compute, that you can compute with a trusted authority, you can also do without a trusted authority. …
> 
>  Instead, what the parties are gonna do, is they’re gonna talk to one another using some protocol, such that at the end of the protocol all of the sudden the value of the function becomes known to everybody.

Boneh is talking, in this example, about elections and private auctions, but the broader message is striking. Any function that’s possible with an authority is possible without one. Any group can devise a method for communicating internally and producing results without a requirement to put trust in a party on the outside.

This central theorem gave me new perspective on the connection between anarchy and cypherpunks. I knew that the government classified crypto technology as a munition during the “crypto wars” of the ’80s and ’90s, but I’d always assumed that the government feared its use to assist in acts of violence. I realize now how much more subversive it can be.

I had looked in the wrong place of Weber’s model of governmental authority as a [monopoly on the legitimate use of physical force](https://en.wikipedia.org/wiki/Monopoly_on_violence); while the government could claim to be concerned about crypto’s use in creating violence, it may have really been worried about its undermining the government’s monopoly on legitimacy. Any function that’s possible with an authority is possible without one.

The rest of the class was interesting as well, and the math involved feels clever but simple, complex but not complicated. I recommend it to anybody who’s given some thought to cryptography but wants to know more.

Of course, for some purposes a full class on cryptography is total overkill. It’s useful to gain a more complete understanding of the theoretical background, but for most it suffices simply to be literate. For everybody, but especially for people in high-risk situations — people who face threats from sophisticated, even state-level attackers — it’s important to know how to use the sophisticated tools that are available.

That, so far as I understand it, is the genesis of [\#CryptoParty](https://twitter.com/Asher_Wolf/status/238389782634459136). It’s a set of global get-togethers where more experienced users can teach beginners how to use the commonly available tools that tap into the incredibly powerful technology of cryptography. I hope that a beginner walks away from a #CryptoParty with an understanding of not just PGP, OTR, and the like, but with an idea of why threat models are important, what attack vectors she ought to consider, and — most importantly — a network of people and resources she can contact for even more knowledge.

As far as I know, #CryptoParty is still less than 48 hours old, but it’s popping up with events all over the world. I’m planning to get together the SF chapter, if you can help with that, please drop me a line!