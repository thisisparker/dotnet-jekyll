---
title: Real-time events with Bluesky and Jetstream for Helping Friendly Bot
layout: post
tags:
    - bluesky
    - phish
    - programming
    - jetstream
    - python
    - twitter
---

This weekend I decided I needed real-time events from a particular Bluesky feed for a bot project. I was nervous that I'd have to consume events from the firehose, which seemed like it would require a lot of complexity and bandwidth, so I was relieved to learn about [Jetstream](https://docs.bsky.app/blog/jetstream), which solved my problem nicely. Here, I've got some notes about what I'm doing and how I'm doing it.

### The background: Helping Friendly Bot

My amorphous ["Helping Friendly Bot" project](https://github.com/thisisparker/helping-friendly-bot) publishes historical context to [Bluesky](https://bsky.app/profile/helpingfriendly.xor.blue) and the [fediverse](https://shakedown.social/@helpingfriendlybot/) about the song that the band Phish is _currently_ playing, while they are playing it, for people attending a concert or watching a stream at home. Naturally, running the bot requires solving two problems:

- analyzing the statistical properties of a given song, which is easy because of the meticulously updated [Phish.net](https://phish.net) database and its [robust API](https://docs.phish.net/)
- discovering what song Phish is playing, which has varied in difficulty over time

When I first wrote the bot, I used the Twitter Streaming API to get real-time events from the [@phish_ftr](https://twitter.com/phish_ftr) account, which was officially operated by the band. I will not recount Twitter's ham-fisted mishandling of its API access in depth here, but the company officially [deprecated that free endpoint](https://devcommunity.x.com/t/announcing-the-deprecation-of-v1-1-statuses-filter-endpoint/182960) shortly after the Elon acquisition and then quietly turned it off a few months later, and replaced it with a [new version](https://docs.x.com/x-api/posts/filtered-stream/introduction) that is available for $5000/month. So, that option was off the table.

In lieu of a streaming approach, I turned to scraping the live and volunteer-compiled setlist data at [live.phish.net](https://live.phish.net). That has worked, but it has been much slower, and prone to different kinds of errors. It's an amazing service that they offer, but it doesn't quite fit my needs, and I felt bad requesting and scraping that page throughout an entire show.

But then last week, timed with the new beginning of a Spring tour, Phish announced they would now be [posting real-time setlist updates to their Bluesky account](https://bsky.app/profile/phish.com/post/3lmzvu3sf5c2h). To my surprise, they have also stopped posting to X (formerly Twitter) — so Bluesky is really where it's at. If I could get those posts as they're happening, that would be a fast and official stream of exactly the information I need.

### Enter the Jetstream

My project is in Python, and to date I've used the excellent [`atproto`](https://atproto.blue) package for interacting with the Bluesky API, so my first stop was its documentation. For streaming, it offers [the firehose](https://atproto.blue/en/latest/atproto_firehose/index.html) — which as I mentioned above, seemed like total overkill for my application. I don't need realtime updates from the entire platform, I just want one account! So [I asked on Bluesky](https://bsky.app/profile/xor.blue/post/3ln6pv7q4b22g), and got the helpful pointer to Jetstream.

In the launch post for the project, the Bluesky team explains the trade-offs: you don't get the cryptographic authentication of the firehose, and it's not officially part of the protocol and so might change over time. But you do get:

> - simple JSON encoding
 - reduced bandwidth, and compression
 - ability to filter by collection (NSID) or repo (DID)

Those are pretty much exactly the three things I needed. Looking at the [the docs in the repo](https://github.com/bluesky-social/jetstream), I determined that I could make a websocket connection to one of the first-party Jetstream instances and use the `wantedDids` filter to narrow it to just the one account.

After reviewing a few options, I decided to use [`websocket-client`](https://github.com/websocket-client/websocket-client) package to connect, mostly because I liked the callback-function structure of its API. Creating a new streaming client was straightforward:

```python
streamer = websocket.WebSocketApp(f"wss://jetstream2.us-east.bsky.network/subscribe?wantedCollections=app.bsky.feed.post&wantedDids={did_to_monitor}", on_message=process_message)
streamer.run_forever()
```

Here, the `did_to_monitor` is just the DID of the @phish.com account. When a new message is posted, the `process_message` function gets called. From there, it's a simple matter of `json.loads`-ing the message, checking to see if it's relevant, and then sending the appropriate alerts.

### Wide open Bluesky

One thing to note: connecting to Jetstream doesn't require any sort of authentication! It is freely available for anyone with a websocket client. That is pretty "radically open," to quote [Gavin Anderegg's blog post about it](https://anderegg.ca/2024/11/25/playing-with-the-bluesky-firehose).

I think the effect is exciting. This weekend I also read [Simon Willison's observations on Jetstream](https://simonwillison.net/2024/Nov/20/bluesky-websocket-firehose/), and I found myself agreeing with this assessment:

> The API scene growing around Bluesky is really exciting right now. Twitter's API is so expensive it may as well not exist, and Mastodon's community have pushed back against many potential uses of the Mastodon API as incompatible with that community's value system.
> 
> Hacking on Bluesky feels reminiscent of the massive diversity of innovation we saw around Twitter back in the late 2000s and early 2010s.
