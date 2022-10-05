---
id: 1567
title: 'New bot: @pomological'
date: '2015-11-29T12:48:02-08:00'
layout: post
guid: 'https://parkerhiggins.net/?p=1567'
permalink: /2015/11/new-bot-pomological/
categories:
    - Uncategorized
tags:
    - 'pomological watercolors'
    - python
    - twitter
---

I’ve unleashed a new bot onto the Twitter timeline today: [@pomological](https://twitter.com/pomological) tweets an image and description from the Pomological Watercolor Collection in the USDA’s National Agricultural Library. (As all of my friends and anybody unfortunate to stand near me at parties knows, I’ve worked extensively on [bringing these watercolors to the public](https://parkerhiggins.net/tag/pomological-watercolors/).) These are beautiful images with serious historical significance, so it’s fun to slip them in between everything else happening on Twitter. [You should follow](https://twitter.com/pomological)! Here’s the first automated tweet from the account:

> muster apples, painted by royal charles steadman, 1924 [pic.twitter.com/gZ72sqO33j](https://t.co/gZ72sqO33j)
> 
> — old fruit pictures (@pomological) [November 29, 2015](https://twitter.com/pomological/status/671060578681511936)

<script async="" charset="utf-8" src="//platform.twitter.com/widgets.js"></script>

For the nerd stuff: the code (such as it is) is [available on Github](https://github.com/thisisparker/pombot). The actual bot doesn’t do much; the trick was getting all the data together in advance so it just has to wake up every three hours and pick from about 7500 statuses to post. One thing that has been super helpful on a lot of these projects is a scrape that [Dave Riordan](https://twitter.com/riordan) did earlier this year of the Collection’s page on the USDA site.

On the programming side, I continue to be incredibly pleased with the book [*Automate the Boring Stuff With Python*](https://automatetheboringstuff.com/). I feel like I promote it too much, but it really has been so helpful and has gotten me off the ground on a bunch of projects that I was too intimidated to face before. In this project, the manipulation of CSVs and scraping web pages with BeautifulSoup were done with skills straight out of the book.