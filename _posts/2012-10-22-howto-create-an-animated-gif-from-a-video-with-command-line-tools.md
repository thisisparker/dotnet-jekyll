---
id: 884
title: 'HOWTO: Create an animated gif from a video with command line tools'
date: '2012-10-22T03:29:13-07:00'
layout: post
guid: 'https://parkerhiggins.net/?p=884'
permalink: /2012/10/howto-create-an-animated-gif-from-a-video-with-command-line-tools/
categories:
    - Uncategorized
tags:
    - anigif
    - 'command line'
    - gifsicle
    - howto
    - mplayer
---

Sometimes I see a few seconds of a video I’m watching and I think that it’d make a great animated gif. But because I don’t always have access to a bunch of graphics software, and because I might be using my Ubuntu or OS X box, it’s nice to have a process that works with widely- and freely-available free software command line tools. So I’ve worked out a process that uses the command line and requires only the programs `mplayer`, `imagemagick`, and `gifsicle`. Here’s how it goes:

1. Make sure you have the programs installed. On Ubuntu (or most anything Debian-based with large enough repositories — these are common programs) it should just be a matter of
    
    > `sudo apt-get install mplayer imagemagick gifsicle`
    
    On Mac OS X, first install the [Homebrew package manager](http://mxcl.github.com/homebrew/), and then install these programs with
    
    > `brew install mplayer imagemagick gifsicle`
2. Isolate the segment of video you want to clip out. You’re just looking for a timestamp, so you can do this in any video player. Once you’ve got a rough clip selected, use `mplayer` to export that to image files. You can use the following line to do that (there are some example values in there that I’ll explain afterward):
    
    > `mplayer -ao null -ss 0:02:06 -endpos 5 -vo gif89a:outdir=gif videofile.mp4`
    
    Here’s what each flag means.
    
    
    - `-ao` means audio output. It’s set to null, because there’s no sound.
    - `-ss` is the start position. What follows is the H:MM:SS timestamp of the beginning of the clip you want.
    - `-endpos` is the end position of the clip, in seconds. So here I’ve taken out a 5 second clip.
    - `-vo` is the video output. The next bit says to output gifs (that’s `gif89a` into the directory called “gif”. You can put them into whatever directory you want of course.
        
        For some reason the I don’t have the gif89a video output driver installed on my OS X computer, so I instead use `png` or `jpeg` in the place of `gif89a` up there. Your mileage may vary.
3. You now should have a directory full of stills. In case you used any other format to output them, I use one line of imagemagick’s `mogrify` to convert them:
    
    > `mogrify -format gif *.png`
4. Then go through and remove the images at the start and the end that you don’t want in the final gif. Sometimes I cheat on the command line here, and just look at all the pictures with Preview or Image Viewer and delete the ones I don’t need.
5. Finally, use `gifsicle` to wrap it all up into an animated gif. I usually start with the line
    
    > `gifsicle --colors=256 --delay=4 --loopcount=0 --dither -O3 *.gif > animation.gif`
    
    and then tweak the parameters from there. Different source material calls for different settings, and I try to keep the final output as small as possible.

If you make a lot of gifs and like to mess with a lot of values, it might make sense for you to do it graphically. But this flow works pretty well for me.