---
id: 1557
title: 'Mad Generation Loss'
date: '2015-10-31T17:35:00-07:00'
author: 'Parker Higgins'
layout: post
guid: 'https://parkerhiggins.net/?p=1557'
permalink: /2015/10/mad-generation-loss/
categories:
    - Uncategorized
tags:
    - 'allen ginsberg'
    - art
    - audio
    - encoding
    - 'free software'
    - howl
    - mp3
---

> Mad generation! down on the rocks of Time!

Mad Generation Loss is a project exploring media encoding and the ways in which imperfect copies can descend into a kind of digital madness. It takes an audio file—here, a recording of Allen Ginsberg reading an excerpt from [his seminal poem “Howl”](https://en.wikipedia.org/wiki/Howl)—and adds another layer of mp3 encoding to each second of the sound. That is to say, the first second is encoded directly from the original, the next second is re-encoded from that first lossy copy, and the third encoded again.

<iframe frameborder="no" height="166" loading="lazy" scrolling="no" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/230756469&color=000000&auto_play=false&hide_related=true&show_comments=false&show_user=true&show_reposts=false" width="100%"></iframe>

That sort of re-encoding from lossy originals, known as transcoding, is supposed to be avoided. The [generation loss](https://en.wikipedia.org/wiki/Generation_loss) builds on itself, and the quality degrades quickly. That effect is exaggerated here by its second-by-second compounding. By the end of the 3:18 recording, Ginsberg’s voice is nearly impossible to pick out among the background noise.

The last seconds of the recording have been transcoded nearly 200 times. All together, the recording represents nearly 20,000 individual mp3 encodes.

![Ginsberg, glitched](https://parkerhiggins.net/wp-content/uploads/2015/10/ginsberg_glitch19-300x300.jpg)This project takes inspiration from earlier efforts to explore generation loss. [“I Am Sitting In A Room” (1969)](https://en.wikipedia.org/wiki/I_Am_Sitting_in_a_Room) by Alvin Lucier was perhaps the earliest, and featured a 4-sentence narration recorded on taped, and re-recorded over and over to hear the tape loss. As the narration notes, that process “smooths out” the irregularities of speech, reflecting instead the rhythm and resonant frequencies of the room of the recording.

More recently, an artist named Canzona documented the process of [downloading and re-uploading a video to YouTube 1000 times](http://gizmodo.com/5555359/the-weirdness-of-a-youtube-video-re-uploaded-1000-times), and the effect of its compound video encoding. He described that project as a tribute to Alvin Lucier.

Unlike those projects, Mad Generation Loss shows the effect of transcoding and loss on a linear recording, not a repeated phrase. The degredation is apparent not from comparing identical inputs and diminished outputs, but from hearing the creep of the telltale white noise and the regular pulse of the mp3s getting stitched together.

The [code to create the Mad Generation Loss audio is freely available under the GPLv3](https://github.com/thisisparker/mad-generation-loss). It is written in Ruby and depends on free software like `lame`, `mp3splt`, and `mp3wrap`. Thanks are due to Eric Mill and Ben Gleitzman for technical assistance (though please do not attribute my sloppy code on them), and to Caroline Sinders and Ethan Chiel for their encouragement.