---
id: 1241
title: 'Ripping CDs like a nerd in Mac OS X'
date: '2013-10-09T23:10:07-07:00'
author: 'Parker Higgins'
layout: post
guid: 'https://parkerhiggins.net/?p=1241'
permalink: /2013/10/ripping-cds-like-a-nerd-in-mac-os-x/
categories:
    - Uncategorized
tags:
    - apple
    - audio
    - cds
---

I haven’t ripped a CD in a long time, so tonight when I had occasion to, I was at a loss for the right method. I used to rip CDs mostly on a computer that runs Ubuntu, but I no longer have an external optical drive, so I was stuck using my Mac. Here are my (loose) requirements:

- No iTunes. I’m sure they’ve improved the ripping and encoding process a lot since I last checked, but I just can’t stand using the software.
- The rip has to be pretty secure. Truthfully, I don’t really have a way of verifying this paranoia, but I want to at least see a log that shows possible errors.
- Output must be lossless, or at least output the lossless step. I want to rip, and then I want to optionally encode, but I don’t want to have the encoder determined by the ripper. FLAC is acceptable, and a mountable disc image is even better.
- Finally, I’d prefer a command line interface. And obviously free software.

I looked at a number of options. I used to use [rubyripper](https://code.google.com/p/rubyripper/), which is super paranoid about ripping and checking, but I had a vague recollection that last time I had some compilation issues. Since it’s not in very active development, I decided to keep looking around.

I tried using [abcde](https://code.google.com/p/abcde/), which I’ve used before on Ubuntu, and it worked fine but got inconsistent track names. I’m sure this is something I could debug, but I was eager to try other options.

Finally, I settled on [XLD](http://tmkk.undo.jp/xld/index_e.html). It’s got its own error-checking system, but can also use cdparanoia. It’s built to be easily extensible on the encoder side, so it can output in most any format now and in the future. It’s got a command-line interface and a very subdued GUI. Most importantly, it handled everything I threw at it, including one fairly scratched disc, with no problems.