---
title: Recurse Center return statement, or What I did on my coding vacation
layout: post
tags:
    - programming
image: /assets/images/recurse-lab.jpg
image_alt: A handful of vintage computers displayed on a table in front of a whimsical mural showing a robot operating a keyboard.
---

I've just wrapped a 12-week batch at [Recurse Center](https://www.recurse.com), a self-directed coding retreat that provides an environment for people to become better programmers. I'm a huge fan of RC, and previously did a full batch in the summer of 2017 and a week-long minibatch at the start of 2019. It's common for people finishing some time at Recurse Center to write up some notes afterwards, which are cutely called "return statements," and that's what I'm going to do here.

I had a good conversation with some fellow Recursers at about the halfway point of my batch, where we lamented how easy it is to feel like you're "not getting enough done," especially because the opportunity to focus on your own projects for 6 or 12 weeks is rare and feels precious. That is true, but it's missing some critical context. In my opinion, the main project I've worked on for each of my two full batches was *myself*, as a programmer, cultivating my expertise and preferences and experiences.

It's hard to account for that project, but any reckoning that doesn't include it is incomplete. Sometimes it presents in more straightforward ways—like in my first batch I committed to using a real text editor, which was new to me and slowed things down, but has paid dividends so many times over—but often it's intangible improvements to how I think about technology and problem-solving.

That said, I did ship some projects that I'd like to share!

### Signal bot for Puzzmo leaderboards

I wanted to write some Go during my batch, which helped shape [this first project](https://parkerhiggins.net/2025/04/webhooks-to-signal-groups-tailscale-puzzmo/): a server that processes Puzzmo webhooks containing daily leaderboard updates and sends them to a Signal group. It was fun to dip in to a project that used Tailscale's `tsnet` library, and it was also nice to start immediately getting daily benefits of code in production.

At first I felt a little self-conscious that this was not really packaged for public consumption, but that faded. I came across another Recurser's blog post about ["houseplant programming"](https://hannahilea.com/blog/houseplant-programming/), a concept that I have come to really love. This was a real houseplant programming job for me, and it made my life a little better while improving my understanding of things like webhooks and Go and Tailscale and [Docker and Signal and sysadmin stuff](https://parkerhiggins.net/2025/04/signal-messenger-api-tailnet-docker-compose/). Hopefully it [serves as](https://rygoldstein.com/posts/introducing-mirror-darkly) "an ad to write tiny software just for yourself."

### Surfing the Bluesky Jetstream with Helping Friendly Bot

When I did my first Recurse Center batch in 2017, social media bots—which mostly just meant Twitter bots—were a primary medium for me. In the years since, I've watched Twitter (and its API) get destroyed. It's forced me to think about how to continue to apply the lessons I'd learned and the practices I'd developed in a new context.

So it was especially fun to work on [a Bluesky project that would not have been possible with Twitter](https://parkerhiggins.net/2025/04/realtime-bluesky-events-jetstream-for-helping-friendly-bot/). This project involved expanding my pre-existing Helping Friendly Bot, which posts context data about Phish songs as the band plays them on-stage, to listen for real-time Bluesky events and do a bunch of finicky replying and reposting stuff.

Beyond the Bluesky and [AT Protocol](https://atproto.com/) specific parts, I learned a lot about websockets, shell-scripting, [job scheduling with the `at` utility](https://www.redhat.com/en/blog/linux-at-command), and more sysadmin stuff.

### Personal sites for friends: Calendar of Song and Malaika's crossword chart

I knew about myself that I love websites and I love helping people publish websites that speak to them. These two projects really worked in that vein. For Michael, I [updated a long-running project](https://parkerhiggins.net/2025/06/michael-atkins-calendar-of-song/) to each day [refresh a page](https://allthingsatkins.com/calendar) on the personal site I'd previously built for him. For Malaika, I built her a [brand new portfolio page](https://malaikahanda.com/) that displays her (many, many) publications on [a GitHub-style contributions graph](https://parkerhiggins.net/2025/06/new-website-for-malaika/).

It's fun working to a friend's specifications, and it enforces some discipline about where you won't cut corners. I think I built things a little nicer for my friends than I would have for myself, and I appreciate the opportunity to show some craftsmanship. I also discovered about myself that I like writing Javascript that runs in the browser! That has not always been the case, but I've grown and so has the language and it's gotten me started on a few projects that will ship in the future.

### Maintenance on `xword-dl` and others

I had told myself coming in to this batch that I would not let myself fall back on Python throughout. I've spent much more time writing in Python than in any other language, and it's fast and comfortable for me. But there are definite benefits to embracing a diversity of languages and approaches, and building the skills and confidence to be able to choose the right tool, not just the one closest at hand.

So it was with some trepidation that I undertook some maintenance on my [`xword-dl` crossword scraping utility](https://github.com/thisisparker/xword-dl/)—would I be learning, or just doing chores?

That fear was misplaced. There's so much to learn, and there is a distinct value to continuing to work on a codebase over the course of years. I've now watched this project grow and develop as I have grown and developed, and I learned a lot about newer Python features, development best practices, and packaging stuff.

### Infinite sea shanty in the browser

A corner of a larger project that I'm still working on, this [generative sea shanty](https://parkerhiggins.net/2025/06/generating-infinite-sea-shanty-in-the-browser/) was a fun opportunity to catch up on web audio and dip my toe back into the world of generative composition and music theory. I used to be a musician and I have always loved theory, and to be honest I kind of forget that it is a body of knowledge I have spent thousands of hours working on.

(Do you ever do that? Write off skills you have as trivial to fixate on the skills that you don't?)

So in that way, this was a fun exercise on the first order, and then it was also fun to figure out how to embed it into a (very lightly) interactive blog post, which was new for me. I also found a bug in the library I was using, reported it, and got it fixed! Between the original composition and the post about it, I learned a lot about Javascript, Tone.js, web audio, git and GitHub, and even some music theory. I also got to listen to a lot of shanties.

### You should probably go to Recurse Center

This list of projects isn't complete, because there are a few things I'm still working on and want to keep cooking for a little bit longer. I've come to appreciate that Recurse Center is something of a mindset, and that I can chase down those projects and the curiosity that inspires them even as I re-enter the world.

This has been a really hard year for me, in a lot of ways. That has forced me into introspection, and trying to figure out what parts of myself are load-bearing, and how I want to build around them.

Alongside that project, I have been so grateful to have a space and a community like Recurse Center that encourages the pursuit of self-improvement. Obviously at RC, the focus is becoming a better programmer. Developing the volitional skills and the discipline to learn through building at the edge of your abilities, though, helps across the board.

Hands-down, though, the best thing about Recurse Center is the community of Recursers. People that I've met during batches have been hugely helpful and inspirational to me, and the alumni network is a constant source of wonder. I am grateful to have met so many of these people, and I want to meet more of them, and I want to learn generously and inspire others the way I've been inspired.

I know it is an incredible privilege to be able to focus on that for months at a time. But if you can swing it, I [encourage you to apply](https://www.recurse.com/apply) to do a batch.