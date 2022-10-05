---
id: 1542
title: 'HOWTO: One big file from a YouTube playlist'
date: '2015-08-25T19:39:33-07:00'
layout: post
guid: 'https://parkerhiggins.net/?p=1542'
permalink: /2015/08/howto-one-big-file-from-a-youtube-playlist/
categories:
    - Uncategorized
tags:
    - 'command line'
    - 'cory arcangel'
    - howto
    - video
---

In celebration of the 40th anniversary of the release of [Born To Run](https://en.wikipedia.org/wiki/Born_to_run), I decided to watch Cory Arcangel perform [his classic Glockenspiel Addendum](http://www.coryarcangel.com/things-i-made/2006-008-the-bruce-springsteen-born-to-run-glockenspiel-addendum). He’s posted videos from a 2008 concert to YouTube, so it should be no problem, right?

Well, the version he posted is in eight parts. Fine for YouTube, but I don’t want to have to click play between each segment, and I don’t want to be interrupted if my Internet goes down. I solved the first problem by [creating a YouTube playlist of the whole concert](https://www.youtube.com/playlist?list=PL5V1zfjBPBJkSJ2tV0Cu31HAfNTJ3fhAZ), but in order to solve the second problem I’d need a local copy.

The [excellent (and public domain!) program `youtube-dl`](https://rg3.github.io/youtube-dl/) can fetch a copy of each of the videos separately, and will even take a playlist link as input. I made myself a `glockenspiel` directory, and filled it with eight mp4s.

That’s probably enough for most situations! `mplayer` (or your media player of choice) can take a list of files. But I wanted one big mp4, and I wanted to do that without transcoding.

In some cases, the `ffmpeg concat demuxer` would probably work. It’s one of three *different* concat features [documented on the `ffmpeg` wiki](https://trac.ffmpeg.org/wiki/Concatenate), and designed for merging file formats that cannot be simply concatenated but that shouldn’t be transcoded. It takes a list of files in the following format:

```
file 'path/to/file1.mp4'
file 'path/to/file2.mp4'
```

etc. You can generate that list with a little bash loop:

```
for f in ./*.mp4; do echo "file '$f'" >> list.txt; done
```

And then feed it into the concat demuxer with the following command:

```
ffmpeg -f concat -i list.txt -c copy output.mp4
```

If that works for you, great, you’re set. Unfortunately, I ran into a problem: the resulting mp4 file had some weird reference frame issues, resulting in some (but not all) of the video parts to be garbled flashing green frames. ((It’s outside the scope of this post, but the next thing I tried, mkvmerge, created a file with the exact same problem.)) `mplayer` kept spitting errors like: `number of reference frames (0+5) exceeds max (3; probably corrupt input), discarding one.`

I wasn’t going to be able to use the `concat demuxer`, but as I mentioned above `ffmpeg` has three different concat options. This [Q&amp;A describes a way to place the mp4 files in a new transport stream container](http://superuser.com/questions/43588/how-can-i-merge-two-mp4-files-without-losing-quality/522658#522658), which is one of the kinds of files that can be concatenated with the concat *protocol*, at the file level. One by one, I made temporary mpeg transport stream files like this:

```
ffmpeg -i input1.mp4 -c copy -bsf:v h264_mp4toannexb -f mpegts temp1.ts
```

And then I merged all those files, temp1.ts through temp8.ts, with the following unwieldy command:

`ffmpeg -i "concat:temp1.ts|temp2.ts|temp3.ts|temp4.ts|temp5.ts|temp6.ts|temp7.ts|temp8.ts" -c copy -bsf:a aac_adtstoasc output.mp4`

Which works like a charm. Not a totally painless process, but now I’ve got a pretty well merged and not transcoded local version and can watch me some glockenspiel.