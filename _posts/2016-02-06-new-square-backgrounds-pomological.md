---
id: 1586
title: 'New square backgrounds for @pomological'
date: '2016-02-06T08:01:41-08:00'
author: 'Parker Higgins'
layout: post
guid: 'https://parkerhiggins.net/?p=1586'
permalink: /2016/02/new-square-backgrounds-pomological/
categories:
    - Uncategorized
tags:
    - 'pomological watercolors'
    - python
    - twitter
---

I’m happy to say I’ve fixed the most frequent complaint I’ve gotten about [@pomological](https://twitter.com/pomological): the images, while great, are overwhelmingly in the portrait orientation, making the preview images on many Twitter clients—and especially Twitter.com—kind of lousy.

No more! Beautiful squares on a color hand-picked to match most of the painting backdrops.

> panariti grapes, painted by amanda almira newton, 1908 [pic.twitter.com/ve1CHqUhbY](https://t.co/ve1CHqUhbY)
> 
> — old fruit pictures (@pomological) [February 6, 2016](https://twitter.com/pomological/status/695884141154291712)

<script async="" charset="utf-8" src="//platform.twitter.com/widgets.js"></script>

To address this, I had to learn a little about `pillow`, the leading Python image library. Now, when the bot downloads a random image from the watercolors, it draws a new neutral-colored box that’s a little longer than the painting’s longest side, and pastes the thing in the center of that.

The hardest part was ensuring the resulting image was in a format that Twitter can understand—especially because this is one of the handful of things that changed in between Python 2 and 3. But I persevered, and read a lot of documentation, and now it’s live.