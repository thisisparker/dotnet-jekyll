---
title: Generating an infinite sea shanty in the browser
layout: post
tags:
    - programming
    - sea shanties
    - javascript
image: /assets/images/pirate-drawings/pirateship.png
image_alt: An old-timey pirate ship drawing. 
---

For a project I'm working on, I wanted to generate an endless looping soundtrack that felt like a sea shanty continuing indefinitely without a fixed melody. This proved to be a fun exercise for both musical and technical reasons, so I thought I'd write up some thoughts on how that came together.

I've had a longstanding interest in sea shanties, which made their sudden spike in popularity in 2021 first exciting and then somewhat annoying. One nice side effect, though, was for a few weeks there everybody who writes or makes videos about music stuff [had to talk about shanties](https://www.youtube.com/watch?v=m1ovAB4vKzw), and it produced a lot of good tutorials and discussions that helped me in this effort.[^1]

With generative music, the success or failure of the "composition" really comes down to the actual rules you put in place. There's a narrow path that's fun and interesting, and danger on both sides. If the rules are too strict, it doesn't *feel* generative. Sometimes this looks like overfitting to a particular creative model, which can make variations feel meaningless, leading to [an oatmeal problem](https://emshort.blog/2016/09/21/bowls-of-oatmeal-and-text-generation/). But if the rules are too lax, it doesn't feel composed. You end up making a wind chime. Great if that's what you're aiming for, but not what I wanted.

Similarly, when composing in a genre you encounter some of the same overfit/underfit dynamic. If you lean too much into the [scène à faire](https://en.wikipedia.org/wiki/Sc%C3%A8nes_%C3%A0_faire) elements, the result feels derivative; but too little and it doesn't successfully evoke the genre at all.

With that in mind, embedded below is a working draft of my infinite shanty, and [here's the code that powers it](https://github.com/thisisparker/sea-minor-embed). You can toggle each component individually if you want to hear a given instrument's part more clearly.

<iframe width="100%" height="120px" frameborder=0 src="https://thisisparker.github.io/sea-minor-embed/"></iframe>

### Musical thoughts

In order to make a thing that sounded like a shanty, I outlined some musical constraints that I could represent in the code.

#### Time considerations

Because of the strong historical connection between shanties and repetitive, rhythmic maritime labor tasks, time plays a major role in creating that distinctive sound. There's a heavy emphasis on the downbeat, usually some "swing" (which means that the emphasized notes have a little longer duration), and often there are grace notes leading in to the start of phrases.

A lot of writing online connects shanties with 6/8 time in particular. (6/8 means that you can count six beats in a measure, usually as 1-2-3 1-2-3.) And there are definitely some notable shanties in 6: [Blow The Man Down](https://en.wikipedia.org/wiki/Blow_the_Man_Down) is a traditional one, or [Fathoms Below](https://www.youtube.com/watch?v=EVKPN5yVyNw) from the Little Mermaid is a modern example. I think it's a bit of an oversimplification because lots and lots of shanties are not in 6, but in any case it is the sound I wanted here, so this one is in 6.

And to get more specific: many shanties have a musical connection to Irish traditional music, and can be described as a "jig" (which is usually in 6/8) or "hornpipe" (which is usually in 4/4). I wanted the jig sound, and in particular I wanted a "double jig," which is characterized by notes on each of the 1-2-3 beats. Maybe the most famous traditional Irish double jig is [The Irish Washerwoman](https://en.wikipedia.org/wiki/The_Irish_Washerwoman), which is not a shanty but  has some melodic properties I wanted to emulate.

To get that effect, the timing of the melody I wrote looks like this in the (pretty intuitive!) notation format of [the library I used, Scribbletune](https://scribbletune.com/):

`[xxx][x-x] [xxx][x-x] [xxx][x-x] [xxx][x__]`

#### Melody and sound

That is the rhythm of the melody, and the note values vary with each loop. The Scribbletune library allows me to specify particular notes for some beats, and to pull randomly from a specified set for others. In order to give it a classic shanty feel, I used some preset phrases and pull the random notes from a scale in [the Dorian mode](https://en.wikipedia.org/wiki/Dorian_mode#Modern_Dorian_mode).

Musical modes are a super interesting way to evoke a particular vibe, and I feel like they're not well understood by non-musicians. A very simple description is that they determine which notes are available to use in relation to the "tonic" note. For example, this piece uses the D Dorian scale, which, like C Major, is composed of the white piano keys: no sharps or flats. To distinguish this melody from one in C Major we have to establish that the D is our home base. Here, I did that with a droning bassline that just sits on a D note, except for a little flourish every 8 bars, and by populating the melody with some phrases that resolve to D.

Aesthetically, I think this piece is more interesting with synthesized instruments instead of sampled ones, so that's what I've used. I'd initially wanted the melody to be on some kind of wind instrument, but I couldn't get it to sound good, so I switched to a synthesized steelpan as a nod to some Caribbean sound. Shanties are typically a cappella or close to it, and they have lyrics, so these decisions were really just me vibing. Beyond the melody, there's the simple bass, and two more percussive instruments that really just keep the rhythm going.

### Technical details

It's possible to do web audio stuff using just vanilla javascript, but it pretty quickly becomes a headache to do anything musical. There's [a framework called Tone.js](https://tonejs.github.io/) that is hugely helpful in giving you abstractions like "notes" and "measures" and "instruments," and my first draft of this used Tone.js directly.

But I found that I was still missing some useful abstractions related to composition, and so I turned to [Scribbletune, a javascript library](https://scribbletune.com/) geared towards musical ideation (that uses Tone.js for its browser support). I think in practice that's mostly for electronic music — it's possible this is the first Scribbletune shanty. Beyond that, I think my usage pattern, where the Scribbletune playback in the browser is the actual end product, is a little unusual.

So I hit some rough edges of the library but I'm glad I persevered. For one thing, it has no configurable time signature, so I've had to sort of fake it by grouping my beats into triplets. This is where I think its roots in electronic music come through: not a lot of EDM uses anything but 4/4.

One thing I love about music theory is that it's very empirical but still requires a lot of judgment calls. The time signature of a given piece, especially a traditional one, can be subject to some debate, and there are usually multiple ways of representing the same underlying information that differ mostly in terms of what mental model is being applied. In that way, it kind of reminds me of [duck typing](https://en.wikipedia.org/wiki/Duck_typing). It is useful to be able to say: okay, the software may not have a concept of "time signature," but the *property* I'm looking for is two groupings of three beats, which I was able to achieve with the triplet function.

Beyond that, the randomness is not very configurable, and [I think I found a bug how it's documented](https://github.com/scribbletune/scribbletune/issues/192). I think it accidentally made the piece more interesting, so I can't be too mad.

My goal when starting this project was to make something interesting enough to give your attention for a bit, but ambient enough to fade into the background as necessary. I think I've done that, and I've learned a good deal about both song composition and javascript along the way.

[^1]: That video in particular, from the great Adam Neely, draws a distinction between the "shanty" and the "folk sea song." Like many people online, I am eliding those two terms throughout this post, but if the difference matters to you, his description of it is a good one.	