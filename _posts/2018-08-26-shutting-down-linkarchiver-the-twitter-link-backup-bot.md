---
id: 1862
title: 'Shutting down @LinkArchiver, the Twitter link backup bot'
date: '2018-08-26T15:13:52-07:00'
layout: post
guid: 'https://parkerhiggins.net/?p=1862'
permalink: /2018/08/shutting-down-linkarchiver-the-twitter-link-backup-bot/
tags:
    - bots
    - programming
    - twitter
---

After a little over a year of service, @LinkArchiver, the Twitter bot that [automatically made Internet Archive backups](https://parkerhiggins.net/2017/07/linkarchiver-a-new-bot-to-back-up-tweeted-links/) of the links you tweeted, has archived its last link. In that time it archived somewhere around 7.2 million links total from about 9,000 users.[^1] The last link it archived was [this LA Times story about Verizon throttling California firefighters](http://www.latimes.com/local/lanow/la-me-ln-data-throttling-20180822-story.html), [tweeted on Thursday morning](https://twitter.com/elizs/status/1032644299144527872).

LinkArchiver stopped working this week when [Twitter turned off the User Stream API](https://twittercommunity.com/t/details-and-what-to-expect-from-the-api-deprecations-this-week-on-august-16-2018/110746) that it relied on. Under the hood, LinkArchiver was only looking at its timeline, so it could use Twitter’s built-in following features to make its user list. Since that API change, it can’t pull down a “stream” of its timeline, and so would have to be redesigned to continue to work.

Even as this project is shutting down, I consider it a pretty major success. I am very grateful to Jacob Hoffman-Andrews for [pitching me the underlying idea](https://twitter.com/j4cob/status/883054720260087808). Writing [the code](https://github.com/thisisparker/linkarchiver/) (and seeing it get an enthusiastic reception) was a great way to kick off my time at Recurse Center last summer. I’m also grateful to Ben Cotton who gave it a [nice write-up at opensource.com](https://opensource.com/article/17/7/linkarchiver-automatically-submits-links-internet-archive) when it launched.

I’ve had a few people ask me about archiving and backup options now that this is no longer available. I’m considering doing something similar for Mastodon, or for plain RSS feeds, but I also don’t want to downplay the fact that Internet Archive does a very good job of running the Wayback Machine crawler, and so the main value I can add is adding a personal layer. In any future work on things like LinkArchiver, I’d want to keep track of that.

There’s also a way to do a Twitter redesign with existing APIs, probably. Instead of getting a stream from Twitter that pinged on new tweet events, it could request new tweets at regular intervals, using an API that’s still operational. If somebody wants to write that, they’re welcome to, but [given the way Twitter is](https://slate.com/technology/2018/08/twitters-new-developer-guidelines-might-end-fun-bot-accounts.html), I’m not eager to do so.

[^1]: “Quote tweets” are treated like links to tweets, and constituted about a third of the total links. Something like 4.8 million links backed up were at domains other than Twitter.
