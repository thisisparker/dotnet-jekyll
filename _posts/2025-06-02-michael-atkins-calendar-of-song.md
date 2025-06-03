---
title: The Calendar of Song, by Michael Atkins
layout: post
tags:
    - programming
    - art
    - michael atkins
image: /assets/images/IMG_5028.jpg
image_alt: "A view from inside James Turrell's C.A.V.U. at Mass MoCA shows a disc of light against a colored field."
---

Over at Michael Atkins' blog, he's released a [lovely artist's statement on Calendar of Song](https://allthingsatkins.com/blog/2025/06/01/calendar-of-song-statement/), a new (and old) project I've helped to get working over the years. Through various tech stacks, the basic premise has stayed the same: Michael picks a song of the day, usually highlighting some lyrical relevance or historical coincidence, and some Parker tech "publishes" it.

I've helped Michael build and maintain his site over the years because I love reading his writing, and the short captions that accompany these songs are no different. And besides, he pulls from such a wide variety of music, the playlist itself is a great tour across genres, styles, and traditions.

Since we deployed the [Calendar of Song](https://allthingsatkins.com/calendar), I've added it to my phone's home screen, and tune in each day when I've got a quiet moment. It's been nice.

His statement really captures the project better than I can, but I want to drill down just a bit on his use of the word "site-specific," which is (both) a great pun and a pithy distillation of the some of the motivation behind my implementation decisions.

The first iteration of the Calendar of Song was (what else?) a Twitter bot, where its atomic unit was an individual post, in a format designed to obliterate context. For the viewer, a Calendar of Song update in that era appeared under a headline, over a shitpost, between selfies and memes and reaction gifs. As the algorithmic timeline gained purchase, it lost even the excuse of simultaneity.

Today's Calendar of Song is a different beast altogether. Like a tear-off desk calendar, the only context is: today. There is no "previous post" or "see more" or "index," just the song Michael has picked, and a few words about it. It was fun to build to that spec, especially within the constraints of his (static) site and the delightfully janky CMS I've set up for him.

You might describe it as eschewing the promise of the massively parallel for a more serial experience. In that way, from a user experience perspective, it's as influenced by Wordle as it is the more erudite art antecedents that Michael highlights.

Anyway, [go give it a listen](https://allthingsatkins.com/calendar). And if you like what you hear, see you again tomorrow.