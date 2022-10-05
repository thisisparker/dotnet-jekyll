---
id: 1668
title: 'New bot: @i_remember_txt, tweeting Joe Brainard&#8217;s &#8220;I Remember&#8221; (1975)'
date: '2017-01-23T20:31:55-08:00'
layout: post
guid: 'https://parkerhiggins.net/?p=1668'
permalink: /2017/01/new-bot-i-remember-txt-joe-brainard-i-remember/
categories:
    - Uncategorized
tags:
    - 'avery trufeman'
    - bots
    - 'joe brainard'
    - poetry
    - programming
    - python
    - twitter
---

Joe Brainard’s 1975 book “I Remember” is an incredible work of poetry. The New Yorker called it [“his miniaturist memoir-poem,”](http://www.newyorker.com/magazine/2008/11/03/the-nancy-book) and Paul Auster’s blurb for the 2001 edition gives a good sense of it:

> *I Remember* is a masterpiece. One by one, the so-called important books of our time will be forgotten, but Joe Brainard’s modest little gem will endure. In simple, forthright, declarative sentences, he charts the map of the human soul and permanently alters the way we look at the world. *I Remember* is both uproariously funny and deeply moving. It is also one of the few totally original books I have ever read.

Those simple declarative sentences—almost all of which begin with “I remember…”—would have been a shock as a book, but today they have the strange familiarity of status updates from your most nostalgic friend.

So when Avery Trufelman asked [if somebody could make a bot](https://twitter.com/trufelman/status/820687962266402816) that tweeted his “memories,” I jumped at the chance. And the resulting bot, [@i\_remember\_txt](https://twitter.com/i_remember_txt), fits in great in between other tweets.

[![](https://parkerhiggins.net/wp-content/uploads/2017/01/Screenshot_2017-01-23_20-28-35.png)](https://twitter.com/i_remember_txt/status/823404900193181696)

Per usual, [the code is online](https://github.com/thisisparker/i-remember-txt) and comments are welcome. It’s pretty straightforward. One thing I did this time which was pretty cool: in the case of memories that were longer than a single tweet, it does [threaded “tweetstorms”](https://twitter.com/i_remember_txt/status/822229699153645568) of up to 4-5 in a row.