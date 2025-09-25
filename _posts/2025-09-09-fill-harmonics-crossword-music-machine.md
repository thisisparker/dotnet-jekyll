---
title: Fill Harmonics, the crossword puzzle music machine
layout: post
tags:
    - programming
    - crossword
image: /assets/images/fill-harmonics/fill-harmonics.png
image_alt: The Fill Harmonics setup, with a grid ready to play.
show_hero: false
---

Today I’m releasing [Fill Harmonics](https://fillharmonics.com/), a music machine that takes its rules and styling from the world of crossword puzzles. The name is a pun: in crossword lingo, “fill” is the stuff that goes into the grid. This project is a collaboration with Natan Last, one of my cruciverbal inspirations and the author of “Across The Universe,” a very fun upcoming book on the history and culture of crosswords ([available for pre-order now!](https://www.penguinrandomhouse.com/books/723796/across-the-universe-by-natan-last/)).

See an example grid creation:

<video controls width="100%">
	<source src="/assets/images/fill-harmonics/simple-creation.mp4" type="video/mp4">
</video>

We got started on Fill Harmonics towards [the end of my batch at Recurse Center](/2025/06/recurse-center-return-statement/). From a tech perspective, it was a fun opportunity to continue building in Javascript, and combine some recent areas of interest: in particular, the CSS grid data structure work I’d done for [Malaika’s personal page](/2025/06/new-website-for-malaika/) and the web audio libraries I’d explored for my [infinite sea shanty](/2025/06/generating-infinite-sea-shanty-in-the-browser/). Similarly, this one is written entirely in vanilla Javascript, though I think at some point it exceeded the complexity where that was a good idea.

Natan and I are both fans of [Max Neely-Cohen’s 10,000 Drum Machines project](https://10kdrummachines.com/), and we wanted to build something that could be a part of it. Our shared interest in crosswords was a natural starting point, and we pretty quickly landed on the overlap between sequencing instruments and crossword aesthetics.

As we continued to build, we took that early concept and pushed it out in some fun directions. I think the combination of synthesis for melody and sampling for the drums works really well and allows for pretty elaborate musical phrases to emerge from simple components.

Perhaps the most fun addition was “word play mode,” which changes the sequencer loop from operating simultaneously across each row to instead looping over every “across entry” in the grid. (It makes a little more sense when you see it in action, but it’s still a little brain-bendy.) That mode emerged out of a conversation with [fellow Recurser Gage Krause](https://www.gagekrause.com/), who is working on some [extremely cool and polished drum machine stuff](https://www.gagekrause.com/projects/sealion) right now.

The musical effect of word mode is called [polymeter, a term that lives in the shadow of its more famous cousin polyrhythm](https://www.ethanhein.com/wp/2023/polymeter-vs-polyrhythm/). Polyrhythm takes a measure and divides it with two or more sets of even subdivisions; polymeter, by contrast, keeps each beat the same size but loops them across measures of different lengths. The neat thing about it is that you can easily create phased patterns that only repeat at their least common multiple number of beats.

Keeping the tempo the same across grid mode and word mode means that you can alternate between the two for a neat musical effect:

<video controls width="100%">
	<source src="/assets/images/fill-harmonics/switch-between-playback-modes.mp4" type="video/mp4">
</video>

One other early musical decision that paid off nicely was making the grid always square and configurable between 8 and 16 units wide. That means that the biggest and smallest grids feel like pretty comfortable 4/4 patterns that are easy to alternate between.

Because the grid is always square, and expanding it adds lower notes to the bottom, you can grab the slider for a cool effect that cuts the loop in half and drops the bass out entirely.

<video controls width="100%">
	<source src="/assets/images/fill-harmonics/switch-between-sizes.mp4" type="video/mp4">
</video>

Please send along any sounds you make with [Fill Harmonics](https://fillharmonics.com)! We’ve had so much fun making this thing and I can’t wait to see it in other people’s hands.
