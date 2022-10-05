---
id: 1346
title: 'Supreme Court Clouds (2014)'
date: '2014-04-26T08:52:05-07:00'
layout: post
guid: 'https://parkerhiggins.net/?p=1346'
permalink: /2014/04/supreme-court-clouds/
categories:
    - Uncategorized
tags:
    - art
    - clouds
    - 'cory arcangel'
    - mash-ups
    - 'supreme court'
---

Here’s a supercut of audio from April 22, 2014’s Supreme Court argument in *[ABC v. Aereo](http://www.scotusblog.com/case-files/cases/american-broadcasting-companies-inc-v-aereo-inc/)* featuring every use (in order) of the word “cloud.” The video track is from [Cory Arcangel’s “Super Mario Clouds” (2002)](http://www.coryarcangel.com/things-i-made/supermarioclouds/).

<iframe allowfullscreen="" frameborder="0" height="435" loading="lazy" src="//www.youtube-nocookie.com/embed/nJ_eX7HFTbQ?rel=0" width="580"></iframe>

Here’s a version of the audio only (yes, I put my cloud sound on SoundCloud):

<iframe frameborder="no" height="166" loading="lazy" scrolling="no" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/146518737%3Fsecret_token%3Ds-k3sc9&color=ff5500&auto_play=false&hide_related=true&show_artwork=false" width="100%"></iframe>

## How I made this

![IMG_20140425_202703](https://parkerhiggins.net/wp-content/uploads/2014/04/IMG_20140425_202703-300x300.jpg)The Supreme Court makes [transcripts](http://www.supremecourt.gov/oral_arguments/argument_transcripts.aspx) of its oral arguments available on the day of the argument, and puts up [audio](http://www.supremecourt.gov/oral_arguments/argument_audio.aspx) the Friday after. I edited the audio in Audacity, and the transcript is indexed, so I had a list of all the uses of the word “cloud” that I could check off as I went.

Once I had the audio, I grabbed a copy of Cory Arcangel’s video and used `mencoder` to put them together. The commands I used to add the audio was:

`mencoder -ovc copy -audiofile supremecourtclouds.mp3 -oac copy supermarioclouds.mp4 -o supremecourtclouds-unclipped.mp4`

And to clip the video to the length of the audio, I did:

`mencoder -endpos 00:00:56 -ovc copy -oac copy supremecourtclouds-unclipped.mp4 -o supremecourtclouds.mp4`

Attending oral arguments on Tuesday was a great experience. Glad I’ve got this little memento.