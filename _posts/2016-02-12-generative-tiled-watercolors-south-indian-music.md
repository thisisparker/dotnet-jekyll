---
id: 1588
title: 'Generative tiled watercolors and live south Indian music'
date: '2016-02-12T23:43:12-08:00'
author: 'Parker Higgins'
layout: post
guid: 'https://parkerhiggins.net/?p=1588'
permalink: /2016/02/generative-tiled-watercolors-south-indian-music/
categories:
    - Uncategorized
tags:
    - 'gautam ganeshan'
    - 'pomological watercolors'
    - python
    - 'san francisco'
---

A few weeks back, [Gautam Tejas Ganeshan](http://gautamtejasganeshan.com/) invited me to display selections from the [Pomological Watercolor Collection](https://parkerhiggins.net/tag/pomological-watercolors/) behind his performance at [San Francisco’s Artists’ Television Access space](http://www.atasite.org/). I jumped at the opportunity, but stressed a little at how I was going to present them. I didn’t want to do a plain old slideshow, and I didn’t want to do anything that looked cheesy.

A few days later I had the idea to draw a grid of tiles, some of which were blank and some of which had watercolors, and play the Game of Life with them. Pretty immediately I ruled that specific plan out—it’d require a large grid, and the paintings would be too small to show any detail—but I was intrigued by the idea of flipping tiles between blank and fruit images.

The result is a little program I called `<a href="https://github.com/thisisparker/pomtiles">pomtiles</a>`. ((This is the project that I learned how to mat images for, which has [already benefited @pomological](https://parkerhiggins.net/2016/02/new-square-backgrounds-pomological/).)) It generates a series of frames with grids of between 2×1 and 3×3 tiles that each show hand-selected colors or randomly picked images. The frames are suitable for stitching up with a program like `ffmpeg` into a single video. The one [I displayed tonight](http://www.atasite.org/2016/02/carnatic-ata-gautam-tejas-ganeshan-new-directions-2/), embedded below, hangs on each frame for 12 seconds and has no accompanying audio. Suitable for being in the background at a party, perhaps.

<iframe allowfullscreen="" frameborder="0" height="315" loading="lazy" src="https://www.youtube-nocookie.com/embed/GnhwNxZ9hRs" width="560"></iframe>

It worked really well in context. Gautam’s music demands a lot of attention, and the images complement that nicely—something in the periphery that is not too challenging, but a nice spot to focus your eyes. The concert ran for a bit over two hours, so the three-hour video didn’t even have to loop.

![](https://parkerhiggins.net/wp-content/uploads/2016/02/IMG_20160212_201107.jpg)

Of course, there are a few things I’d have done differently if I’d had a little more time and expertise. Most would have given some more consistency to the rules, but then probably nobody cared about that but me. Some aspects feel unfinished—like the fact that individual tiles can be modified multiple times between displays, say, or that changes to the rows and columns always happen on the right and bottom side—but the video worked well.

In any case, the Python I wrote to generate the tiles is now [online and dedicated to the public domain](https://github.com/thisisparker/pomtiles). It’s a little janky in places (written with my objectives in mind), but if you want to run it and need help, just let me know.