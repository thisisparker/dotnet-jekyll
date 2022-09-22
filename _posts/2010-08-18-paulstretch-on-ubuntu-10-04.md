---
id: 66
title: 'Paulstretch on Ubuntu 10.04'
date: '2010-08-18T16:33:05-07:00'
author: 'Parker Higgins'
layout: post
guid: 'https://parkerhiggins.net/?p=66'
permalink: /2010/08/paulstretch-on-ubuntu-10-04/
categories:
    - Uncategorized
---

There’s been a lot of slowed-down action on the web in the past few days after [a particularly hilarious slowed-down version of Justin Bieber’s “U Smile”](http://soundcloud.com/shamantis/j-biebz-u-smile-800-slower) generated over half a million plays on SoundCloud yesterday. Shamantis, the artist behind the recording, pulled off the hitherto considered impossible feat of making Bieber sound like Sigur Rós. The program Shamantis used is called [Paul’s Extreme Sound Stretch](http://hypermammut.sourceforge.net/paulstretch/)–it’s a powerful (if not particularly multi-faceted) program that is capable of real-time playback of songs stretched to one million times their original length without affecting the pitch, effectively making an audio texture out of any track, clip, or sound.

Paulstretch, as the program is usually referred to, is written by a guy named Nasca Octavian Paul, and it’s free and released under the GPL. Naturally [the source code is available](http://sourceforge.net/projects/hypermammut/files/), but Paul doesn’t compile GNU/Linux binaries, and compiling it on my Ubuntu 10.04 system was not totally trivial.

I was able to compile by installing all Fluid and all the libraries specified in the README, and by adding the line  
`#include <string.h> `after the line  
`#include <string> `  
to the MP3InputS.h file, as was [suggested in a help forum](http://sourceforge.net/projects/hypermammut/forums/forum/561037/topic/3246904).

If you want to hear some of my efforts on it, I’ve uploaded a 800% slower version of the Sigur Rós song “Saeglopur” to SoundCloud.

<object height="18" width="100%"><param name="movie" value="http://player.soundcloud.com/player.swf?url=http%3A%2F%2Fapi.soundcloud.com%2Ftracks%2F4666871&auto_play=false&player_type=tiny&font=Arial&color=b60f0a"></param><param name="allowscriptaccess" value="always"></param><param name="wmode" value="transparent"></param></object>