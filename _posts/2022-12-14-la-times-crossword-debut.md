---
title: 'My LA Times crossword debut'
date: '2022-12-14T07:00:00-05:00'
layout: post
tags:
    - crosswords
    - los angeles
    - los angeles times
    - brooke husic
    - ryan fitzgerald
    - ingrid
image: /assets/images/lat-blank-grid.png
---

I constructed today's _Los Angeles Times_ crossword puzzle — my first for a paper that my family has subscribed to for my entire life. The puzzle will be available for a week or two on the [_LA Times_ crossword page](https://www.latimes.com/games/daily-crossword), maybe a bit longer in the archives for [Puzzle Society members](https://www.puzzlesociety.com/crossword-puzzles/la-times-crossword), and should be downloadable with a quick [`xword-dl lat -d 12/14/22`](https://github.com/thisisparker/xword-dl) for a good long time. Some spoiler-y notes below!

This puzzle was in the works for a while, and the version of the grid published today is way different from what I originally submitted. That version featured a punny revealer, mostly different themers, and more traditional rotational symmetry. I'm proud of that grid, pictured here, but it didn't quite line up with the editorial vision at the _LA Times_, and they asked for some revisions that required architectural changes.

<style>
#lat-fig {
  max-width: 50%;
  float: right;
  margin: 1rem;
}
.blurred {
  filter: blur(5px);
}
@media (max-width: 650px) {
  #lat-fig {
  max-width: 100%;
  }
}
</style>

<script>
function toggleBlur() {
  const el = document.getElementById('lat-crossword');
  el.classList.toggle('blurred');
}
</script>

<figure id="lat-fig"><img id="lat-crossword" class="blurred" onclick="toggleBlur()" alt="Crossword puzzle grid, filled in with highlighted themeres." src="/assets/images/lat-crossword-original.png"><figcaption>An earlier draft of the puzzle. Click to reveal or blur.</figcaption></figure>

With crossword themes, you're usually shooting for "tightness"[^1] and "consistency."[^2] But as with [Set rules](https://en.wikipedia.org/wiki/Set_(card_game)), you can get credit for "consistent inconsistency." One thing I liked about my earlier theme set is that each of the paired nos worked a little differently.

[^1]: Roughly, how much of the possible theme the entries in the grid represent.
[^2]: Again, roughly, in how many ways your themers are similar to each other.

I wasn't sure there would be a way to rework the puzzle and save the concept, but after a bunch of tinkering and staring at the grid, the idea of using diagonal symmetry (a hip and edgy option employed lately to great effect by [Brooke Husic](https://xwordsbyaladee.blogspot.com/) and others) occurred to me. In my opinion it's a perfect match for the content.

Throughout, I was lucky to be using some new beta construction software called Ingrid by [Ryan Fitzgerald](https://rynftz.gr/). Ingrid does a few things that were huge on this puzzle: it supports diagonal symmetry out-of-the-box, it has a built-in mechanism for "versioning" a puzzle through different revisions, and allows constructors to easily exclude word options for a given slot and see what remain for the rest of the fill.

That last one is big for avoiding heart-breaking dupe situations. For example, I didn't want NO to appear anywhere in the grid outside of the theme. Ingrid helped me steer clear of that without having to futz with my actual wordlist or filling most of a corner only to realize I was approaching a dead end.

Anyway, I hope you enjoyed the puzzle! I had a great time making it.
