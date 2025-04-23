---
title: 'Wednesday music'
date: '2022-11-27T10:00:00-05:00'
layout: post
tags:
    - netflix
    - subtitles
    - music
    - regex
image: /assets/images/wednesday-music.png
---

I watched a few episodes of the new Netflix show [_Wednesday_](https://en.wikipedia.org/wiki/Wednesday_(TV_series)). Show's fine, and the Danny Elfman score is interesting, and I laughed when his theme first started playing and was dutifully described in the subtitles as "jauntily macabre." If you want jauntily macabre you have to go to Danny Elfman, right?  

As the show went on, I noticed that a lot of care went into the musical descriptions, so I pulled them out to look at the whole collection.[^1]

Some very fun ones in here! I like "delicate, cryptic", "whimsically morbid", "quirkily dreary", "twinkling, wondrous", "groovy, kooky". The final cues before the last episode's closing theme are "tender, wondrous", "gentle, quirky", into "grimly grandiose". I haven't seen enough of the show to know whether you could follow any of the plot through these descriptors, but I bet you almost can.

I've put the [full list of 255 music descriptors up on Github](https://gist.github.com/thisisparker/ebb1094335c168c7584d56be97c8d989), but as a sample here's all of the second episode:

<div class="column-list" markdown="1">
- eerie
- quirky
- jauntily macabre theme
- chilling
- chilling
- creepy, ornate
- tense
- tense
- dramatic
- quizzical
- plucky, excited
- whimsically morbid
- intimidating
- despondent
- mournful, dramatic
- suspenseful
- dramatic
- suspicious
- mellow
- cheekily dramatic
- pensive
- foreboding
- suspenseful
- elegant instrumental
- instrumental
- chilling
- jauntily macabre outro 
</div>

<style>
.column-list {
    columns: 12rem auto;
    margin-bottom: 1rem;
}
</style>

Jauntily macabre indeed. I do sort of wonder at what point in the creative process those were selected. (Like: did Danny Elfman get a note that they're looking for a "whimsically morbid" piece for that section, or did he write a piece that somebody downstream clocked as whimsically morbid?)

[^1]: I did this by sort of manually compiling a single file `wednesday.xml` that contained all of the season's subtitles and then running:
      
    ```
    grep -oP '(?<=\[)(\w)(,?\s*\w)+(?= music)' wednesday.xml
    ```
     
    I'm not very good with regex but that should be matching lines that include a `[`, then have a word followed by maybe a comma and more words or not, followed by `music`
