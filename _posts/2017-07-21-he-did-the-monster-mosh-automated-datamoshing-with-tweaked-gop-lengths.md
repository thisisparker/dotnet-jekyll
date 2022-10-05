---
id: 1723
title: 'He did the monster mosh: automated datamoshing with tweaked GOP lengths'
date: '2017-07-21T14:52:32-07:00'
layout: post
guid: 'https://parkerhiggins.net/?p=1723'
permalink: /2017/07/he-did-the-monster-mosh-automated-datamoshing-with-tweaked-gop-lengths/
categories:
    - Uncategorized
tags:
    - beyonce
    - mash-ups
    - programming
    - python
    - video
---

After I posted yesterday about my [automated datamoshing experiment](https://parkerhiggins.net/2017/07/making-mosh-ups-automated-datamoshing-from-multiple-video-sources/), I got a [nice message on Twitter from developer and botmaker Ryan Bauman](https://twitter.com/ryanfb/status/888159099413811202) who was able to run my script on his own videos. We talked for a bit about how it could be improved, and I had a major realization that I had to test immediately.

In yesterday’s post I mentioned that the relative prevalence of P-Frames precluded my preferred effect of stills from one video and movement from another. Too much image data was being drawn by the P-Frames for it to really get unrecognizable. I didn’t and still don’t know how to reduce the number of P-Frames per se, but the big realization was I could change the ratio of I-Frames to P-Frames by ratcheting the [“Group Of Pictures” size](https://en.wikipedia.org/wiki/Group_of_pictures) way down. That variable determines how often a video includes an I-Frame, and I could set it easily in ffmpeg while re-encoding the source videos.

A normal default GOP size might be 250 frames — which is to say, no more than 10 seconds of video go by without a full I-Frame render. Poking around, I tried changing that number to a few different values to see what works best. Experimentally, a GOP size maximum of 48 frames (once every two seconds) seems to do the trick for two video sources. An excerpt of that video looks like this:

<iframe allowfullscreen="allowfullscreen" frameborder="0" height="315" loading="lazy" src="https://www.youtube-nocookie.com/embed/TLsT1H7HOs0?rel=0" width="560">  
</iframe>

What are the constraints on the GOP size? Here, as in many other moments of this project, my considerations are very different from most people’s. In most cases, you want I-Frames to happen frequently enough that cutting and seeking through the video can be relatively precise, but rare enough that the filesize can stay low. Since every I-Frame has to contain a full frame of image data, they can be large.

Because I’m swapping I-Frames at the byte level, and truncating or padding each frame to fit, every I-Frame insertion is a potential source of trouble. You can see in the video above, my encoder struggles in certain places. And given that I’m doing substitution, the closer my GOP gets to 1, the more my mosh-up starts to just look like a slideshow.

For single source videos, where I-Frames are likely to be more similar to each other, I was able to use an even shorter GOP length. Here’s a datamoshed version of the Countdown video with a GOP length of 25 frames.

<iframe allowfullscreen="allowfullscreen" frameborder="0" height="315" loading="lazy" src="https://www.youtube-nocookie.com/embed/u4YJU4mV-7M?rel=0" width="560"></iframe>

So, in conclusion: messing with GOP sizes means a different number of I-Frames which means more opportunities for hijinks in mangling the videos.