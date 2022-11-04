---
title: 'Public (sub-)domains'
date: '2022-11-04T16:30:00-08:00'
layout: post
permalink: /2022/11/public-sub-domains
categories:
    - Uncategorized
tags:
    - 'public domain'
    - mastodon
    - python
    - 'social media'
image: /assets/images/sub-domain-output.png
---

The tremendous influx of traffic to Mastodon got me thinking that it might finally be time to set up my own instance, and how-to posts from [Jacob](https://jacobian.org/til/my-mastodon-instance/) and [Simon](https://til.simonwillison.net/mastodon/custom-domain-mastodon) have only increased that interest. But as a little branding excercise, and _especially_ if I want to offer accounts to a few close friends, surely I could do something a little more fun than just my first and last name.

[Many Mastodon instances](https://instances.social/) are on subdomains, and since the early days weirder new-style TLDs have been de rigueur. (The flagship has always been at a `.social`!) So I set out to find three-word phrases where the third word is a 4+-letter top-level domain, using as my first source text Moby Dick.

The results were great! The script I wrote output all possible options, which I then spot-checked to see which were available, but I've since updated the script to do a quick `whois` check to see if the domain is already registered. (`whois` support is a little spotty for some of the weirder domains, so many are inconclusive, but I was surprised at some of the good ones available. As of right now, here are some possible instances available for registration:

- certain.fragmentary.parts
- famous.whaling.house
- moreover.unhesitatingly.expert
- however.temporary.fail
- almost.microscopic.network
- should.nominally.live
- another.whaling.voyage
- surprising.terrible.events

Wouldn't those all be great places to call your home in the fediverse?

Normally I would wonder to myself if this kind of thought experiment is cool but this time I feel like I've got external validation in the form of [the reaction to this thread on Mastodon](https://mastodon.xyz/web/@xor/109281433411212592), which has also been great. Somebody even bought the saddest.city domain on the strength of the strangest.saddest.city find.

People responded with some cool possible instance names from [The Great Gatsby](https://mastodon.social/@MattHodges/109282389881819378), [Frankenstein](https://mastodon.social/@ashur/109282921833199535),[White Noise](https://post.lurk.org/@samplereality/109282791738200388), the [King James Bible](https://code4lib.social/@pbinkley/109282743661309956) and more. Really fun.

The [little Python script that finds these](https://gist.github.com/thisisparker/f091f01852911bd849d03c4e09d89856) uses [NLTK](https://www.nltk.org/) to tokenize big text files first into sentences and then, within sentences, into words. Then it checks to see if there are three long-ish words in a row where the third one is on a list of TLDs. Since posting that script on Mastodon yesterday, I've updated it with the built-in `whois` check as well.

As of now, I'm still tooting from [a boring old (well-run!) general purpose instance](https://mastodon.xyz), though who knows... with almost.microscopic.network available, maybe I will move soon.
