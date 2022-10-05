---
id: 1737
title: 'New bot: @78_sampler, serving up old records'
date: '2017-08-11T10:36:49-07:00'
layout: post
guid: 'https://parkerhiggins.net/?p=1737'
permalink: /2017/08/new-bot-78_sampler-serving-up-old-records/
categories:
    - Uncategorized
tags:
    - bots
    - 'internet archive'
    - music
    - programming
    - python
    - twitter
---

The Internet Archive hosts an [incredible collection](https://archive.org/details/georgeblood) of over 25,000 [professionally digitized 78rpm records](http://great78.archive.org/). The great thing about a catalog that large is that, if you know what you want, you’re likely to find it. On the other hand, if you just want to browse it can be overwhelming and even intimidating. Each item could possibly be a delight, but it’s difficult to even think about individual records in the face of such a huge archive.

In that sense, would-be browsers face similar challenges with the Great 78 Project as they do with the [Pomological Watercolor Collection](https://usdawatercolors.nal.usda.gov/pom/home.xhtml)—an archive [I’ve worked with a lot](https://parkerhiggins.net/tag/pomological-watercolors/). Sensing that similarity, I decided to build a tool like [@pomological](https://twitter.com/pomological) to help surface individual records.

<span class="citation">[@78\_sampler](https://twitter.com/78_sampler) tweets every two hours with a randomly selected record from the Archive’s collection. It was important to me that the audio fit smoothly and natively into a Twitter timeline, so I decided to render each tune into a video file using the Archive’s still image of the record as the visual. Twitter limits videos to 2:20—exactly 140 seconds, cute—which is shorter than most 78 tunes, so while rendering the video I truncate the clip at that point with a short audio fade at the end.</span>

The [code to do all this](https://github.com/thisisparker/78_sampler) is a short Python script which I’ve posted online. It relies on ffmpeg to do the video encoding. Crafting ffmpeg commands is famously convoluted, and it’s a little frustrating to format those commands to be called from Python. Maybe that’s something I’ll do differently in the future but, for now, this works and I can dip my cup into the deep Archive well with a little more ease than before.