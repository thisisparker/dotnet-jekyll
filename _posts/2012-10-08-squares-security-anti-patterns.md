---
id: 861
title: 'Square&#8217;s security anti-patterns'
date: '2012-10-08T00:38:13-07:00'
layout: post
guid: 'https://parkerhiggins.net/?p=861'
permalink: /2012/10/squares-security-anti-patterns/
categories:
    - Uncategorized
tags:
    - money
    - payment
    - security
    - square
---

[Square](https://squareup.com/) dongles really truly make processing credit cards not just easier, but possible for all sorts of groups that didn’t have access before: I’ve bought from bands selling merchandise, taxi drivers, food cart operators, and more. I’m worried, though, that Square also makes credit card fraud easier by teaching credit card users security [anti-patterns](https://en.wikipedia.org/wiki/Anti-pattern).

[![](https://parkerhiggins.net/wp-content/uploads/2012/10/square-reader.jpg "Square reader on an iPad")](https://parkerhiggins.net/wp-content/uploads/2012/10/square-reader.jpg)

In practice, using a Square reader is pretty similar to using any other credit card reader. At the money part of the transaction, you hand your card to the vendor or swipe it yourself through a little dongle hooked up to the headphone jack of an iOS or Android device. Then you enter your email, if you want a receipt sent to you, and sign with your finger on the screen.

That’s the standard description. But it could also be described as handing your credit card to a stranger with a [skimmer](https://en.wikipedia.org/wiki/Credit_card_fraud#Skimming), and then giving him your signature. That’s what makes it an anti-pattern: it has become commonly used, but is counter-productive to security efforts.

In the overwhelming majority of cases, both parties are honest, and nothing goes wrong. But it’s easy to imagine a few ways it could go wrong. For one thing, if the vendor is dishonest, he could intentionally record the data and use it or sell it later. That’s how a standard skimmer works, and the same problem exists every time you hand your card to the waiter at a restaurant.

Even if both parties are honest though, they are trusting the integrity of the software. I haven’t heard of it yet, but again it’s not too hard to imagine malware that attacks exploits in, say, Android or iOS themselves, and surreptitiously records and sends the card data to the attacker. Such malware could target a wide swath of devices and transactions, and would be more difficult to pinpoint as the source of the data leak.

Unlike the first scenario, this one is exacerbated in the Square era. Previously, [malware targeting point-of-sale devices had to be very specialized](https://www.networkworld.com/news/2011/030311-cybercriminals-targeting-point-of-sale.html?page=1). Now, though, point-of-sale devices are general purpose computers and vulnerable to commonly known exploits. And in many scenarios, they’re used for other purposes, too, exposing them to more attack vectors.

Really, though, the problem here is not with Square, but with the structure of credit card security. Our card numbers are a secret, and the only information required to carry out many transactions, but we also entrust them with every stranger we make a payment to.

We used to address this issue by an ad hoc security-by-point-of-sale system. If somebody had an official point-of-sale system, our intuition said they were trustworthy, and that was pretty robust. But it’s failing the same way that, say, [security-by-letterhead](https://www.schneier.com/blog/archives/2007/10/security_by_let.html) has failed. Technology has made attacks we’ve dismissed as prohibitively difficult much easier, and we need to change our behavior to reflect that.

- - - - - -

photo: [The infamous Square card reader](http://www.flickr.com/photos/cdharrison/4991885743/in/photostream/). used under [CC BY](http://creativecommons.org/licenses/by/2.0/deed.en)