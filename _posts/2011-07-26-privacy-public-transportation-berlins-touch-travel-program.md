---
id: 347
title: 'Privacy, public transportation, and Berlin&#8217;s Touch&#038;Travel program'
date: '2011-07-26T01:44:57-07:00'
author: 'Parker Higgins'
layout: post
guid: 'https://parkerhiggins.net/?p=347'
permalink: /2011/07/privacy-public-transportation-berlins-touch-travel-program/
categories:
    - Uncategorized
tags:
    - berlin
    - germany
    - location
    - privacy
    - 'public transit'
---

[NPR Berlin reported today](http://www.npr.org/blogs/nprberlinblog/2011/07/25/138673758/bvgs-commuter-touch-travel-app-raises-privacy-concerns) that Berlin’s public transportation authority, [the BVG](http://www.bvg.de/index.php/en/index.html), launched the [Touch&amp;Travel program \[de\]](http://www.bvg.de/index.php/de/3200/name/Tickets%2B/article/12252.html) earlier this month, which allows Vodafone and Telekom customers to use an Android phone or an iPhone to pay for their transport tickets. Participants “check in” while boarding, and confirm their location either through continuous GPS data directly from their phones, or by scanning a QR code at the end points of their trip.

From a privacy perspective, this system stands in stark contrast to the current standard procedure in Berlin. As with nearly all German municipal rail, Berlin subways and buses operate on a [proof-of-payment system](https://secure.wikimedia.org/wikipedia/en/wiki/Proof-of-payment): tickets are required while on board, but are only very occasionally checked.

Apparently, such proof-of-payment systems rose to popularity because of German labor shortages in the 1960s, but they also happen to be extremely respectful of rider privacy ((You can imagine that the labor shortages, and the subsequent manpower restrictions might have served as a constraint that influenced the design of public transportation systems in the same way that Jonathan Zittrain says a lack of financial resources influenced the early design of the Internet ([See him explain that at Harvard](http://www.youtube.com/watch?v=gKmtmhrfMps&feature=player_detailpage#t=817s)) )). Because travel and location data is never even collected, there’s no chance of it being cross-referenced against other data sets, given to the government, or sold to corporations. Though tickets may be traced to a buyer’s credit card, their actual use is not tracked, and riders may also pay cash with no penalty, preserving anonymity.

Berlin’s recently launched pilot program has none of these advantages. First, there’s the issue of anonymity: even taking the BVG and Deutsche Bahn at face value that the user data will be “scrubbed” and saved anonymously for only six months — a dubious proposition given the tempting law enforcement and ridership research opportunities of slipping from that stance — there is a huge and growing body of scholarship covering the possibilities of de-anonymizing large data sets. [AOL search queries](http://query.nytimes.com/gst/fullpage.html?res=9E0CE3DD1F3FF93AA3575BC0A9609C8B63), [Netflix movie ratings](http://www.cs.utexas.edu/~shmat/netflix-faq.html), even [US Census data](http://crypto.stanford.edu/~pgolle/papers/census.html) have effectively received the de-anonymization treatment.

There’s also the general question of locational privacy: individuals should have the [“ability to move in public space with the expectation that … their location will not be systematically” recorded](https://www.eff.org/wp/locational-privacy). That definition is at odds with the premise of the Touch&amp;Travel program, which is basically consent to systematic tracking in exchange for a more convenient ticket purchase process.

Obviously that convenience is nice, and you only need to experience once the feeling of seeing your train pull away while you’re waiting for your ticket to print to understand the temptation of such a trade. And it’s true that there are occasionally positive outcomes of large-scale surveillance programs — New York City’s MetroCard data has been used in both [legitimate alibis and criminal convictions](http://www.nytimes.com/2008/11/19/nyregion/19metrocard.html?pagewanted=all), and even critics acknowledge that there are [a small number of crimes that London’s CCTV system has helped solve](http://www.independent.co.uk/news/uk/crime/the-big-question-are-cctv-cameras-a-waste-of-money-in-the-fight-against-crime-822079.html). I won’t argue that there are no advantages to such a system, but that they’re outweighed by more subtle and incremental disadvantages. The loss of privacy and anonymity carries a real cost, even if it’s not one that’s immediately tangible.

Berlin’s public transportation system is currently one of the best imaginable in terms of privacy, and implementing a system that strips those benefits away is irresponsible and short-sighted. Further, privacy is a hard thing to introduce into a developed system; Berlin should reject any new solution that doesn’t make adequate consideration of privacy in its basic design, even if it’s a promised eventual addition.

Being mindful of privacy doesn’t require foregoing an update to ticket-buying infrastructure, either. There are [cryptographic techniques for validating credentials anonymously](https://secure.wikimedia.org/wikipedia/en/wiki/Digital_credential#Anonymous_digital_credentials_and_pseudonyms) that, while complex and occasionally difficult to understand, can be used to address the current pain points while still preserving privacy and anonymity. A system built with those techniques might not be as straightforward to develop and deploy, but would be invaluable to the people living in and visiting Berlin, and as a model to transportation agencies all over the world.