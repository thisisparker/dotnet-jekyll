---
id: 1719
title: 'Making mosh-ups: automated datamoshing from multiple video sources'
date: '2017-07-20T12:19:34-07:00'
author: 'Parker Higgins'
layout: post
guid: 'https://parkerhiggins.net/?p=1719'
permalink: /2017/07/making-mosh-ups-automated-datamoshing-from-multiple-video-sources/
categories:
    - Uncategorized
tags:
    - beyonce
    - programming
    - python
    - video
---

Datamoshing is a glitch art technique applied to videos to intentionally create “pixel bleeding” and other digital motion artifacts. It became popular several years ago when it was used in near-simultaneous music videos by [Chairlift](https://www.youtube.com/watch?v=mvqakws0CeU) and [Kanye West](https://www.youtube.com/watch?v=wMH0e8kIZtE). In those cases, and in the tutorials and techniques documented since then, the glitches are typically introduced to a single edited video, and done manually in a visual editing program.

My goal for [this project](https://github.com/thisisparker/automosh/blob/master/automosh.py) was to use two separate video sources — to make a “mosh-up,” har har — and to completely automate the merger. The holy grail would be to use all the motion from one video over all the stills of another, to make sort of an animated [Magic Eye](https://en.wikipedia.org/wiki/Magic_Eye) effect, but without the eye focus requirement. (Side note: it’s [possible and awesome](https://sploid.gizmodo.com/this-amazing-magic-eye-music-video-hides-fun-secret-mov-1513555083) to actually create animated Magic Eyes, but that’s beside the point.)

As you’ll see, I fell a little short of that stretch goal, but still managed to make something that looks pretty cool.

## Moshed-up vids

[The script I wrote](https://github.com/thisisparker/automosh/blob/master/automosh.py) can create two kinds of datamoshes. The first takes a single video as a source and rearranges some key frames to glitch it out. Here’s an example of one such video, glitching up Beyoncé’s incredible [Countdown video](https://www.youtube.com/watch?v=2XY3AvVgDns) with itself. I’ve muted the audio in this upload, but as output from the script it still sounds pretty good.

<iframe allowfullscreen="allowfullscreen" frameborder="0" height="315" loading="lazy" src="https://www.youtube-nocookie.com/embed/a9iNDj0iaug?rel=0" width="560"></iframe>

The second (and more exciting) kind of data moshes takes a certain kind of key frame from one video and replaces the same kind of frame in another video. All of the motion and some of the “re-drawings” of subsequent frames are pulled out of context, creating an effect that is a little surreal and unsettling. It’s not as precise as the pros do with their manual edits, but it also can automatically combine two sources in a way I’ve never seen before. (Here, I used Countdown again, and moshed it together with [Formation](https://www.youtube.com/watch?v=pZ12_E5R3qc).)

<iframe allowfullscreen="allowfullscreen" frameborder="0" height="315" loading="lazy" src="https://www.youtube-nocookie.com/embed/SARwUp1P7oQ?rel=0" width="560"></iframe>

Again, I’ve muted the audio, but in this case it would normally play back Partition without any noticeable [flaws](https://www.youtube.com/watch?v=56qgO0C82vY).

## How it works

This moshing technique relies on some facts about how the H.264 spec compresses and stores its data. It really is a remarkable standard, and if you’re not familiar it’s absolutely worth reading the tribute that is [“H.264 is Magic”](https://sidbala.com/h-264-is-magic/). The gist is that only a very small portion of frames, dubbed I-Frames, contain all the image data necessary to draw a full screen. The other kinds of frames, P- and B-Frames, have partial screens and “motion” data.

Other popular datamoshing techniques include removing I-Frames altogether or duplicating P-Frames so the same motion is re-applied to an image. In this example, instead, I’m replacing I-Frames with other I-Frames, and I’m doing it simply by copying and pasting the bytes from one into the place of another, truncating or padding out the data so it fits exactly.

The reason I can’t get only the motion from one video and only the “textures” from another is that the P-Frames blend those two types of data together into a single frame. If I could figure out some way to isolate the image data in the frame, or to re-encode a video to consist entirely of I- and B-Frames, I could probably get a wilder effect.

As it stands, the output of this script is a video that *plays*, but is pretty badly mangled. If you try to play it back in a client that shows you errors, you’ll see a lot of complaints. For compatibility’s sake, I’ve manually transcoded these videos into another format and back.