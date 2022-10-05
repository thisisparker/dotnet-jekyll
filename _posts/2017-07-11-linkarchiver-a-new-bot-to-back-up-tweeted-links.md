---
id: 1715
title: 'LinkArchiver, a new bot to back up tweeted links'
date: '2017-07-11T13:10:04-07:00'
layout: post
guid: 'https://parkerhiggins.net/?p=1715'
permalink: /2017/07/linkarchiver-a-new-bot-to-back-up-tweeted-links/
categories:
    - Uncategorized
tags:
    - archives
    - bots
    - 'internet archive'
    - programming
    - python
    - twitter
---

Twitter users who want to ensure that the Wayback Machine has stored a copy of the pages they link to can now sign up with [<span class="citation">@LinkArchiver</span>](https://twitter.com/linkarchiver) to make it happen automatically. <span class="citation">@LinkArchiver</span> is the first project I’ve worked on in my 12-week stay at [Recurse Center](https://www.recurse.com/), where I’m learning to be a better programmer.

The idea for <span class="citation">@LinkArchiver</span> was [suggested by my friend Jacob](https://twitter.com/j4cob/status/883054720260087808). I liked it because it was useful, relatively simple, and combined things I knew (Python wrappers for the Twitter API) with things I didn’t (event-based programming, making a process run constantly in the background, and more). I did not expect it to get as enthusiastic a reaction as it has, but that’s also nice.

The entire bot is [one short Python script](https://github.com/thisisparker/linkarchiver/) that uses the Twython library to listen to the [Twitter User stream API](https://dev.twitter.com/streaming/userstreams). This is the first of my Twitter bots that is at all “interactive”—every previous bot used the REST APIs to post, but can not engage with things in their timeline or tweeted at them.

That change meant I had to use a slightly different architecture than I’ve used before. Each of my previous bots were small and self-contained scripts that produced a tweet or two each time they run. That design means I can trigger them with a cron job that runs at regular intervals. By contrast, <span class="citation">@LinkArchiver</span> runs all the time, listening to its timeline and acting when it needs to. It doesn’t have much interactive behavior—when you tweet at it directly, it can reply with a Wayback link, but that’s it—but learning this kind of structure will enable me to do much more interactive bots in the future.

It also required that I figure out how to “daemonize” the script, so that it could run in the background when I wasn’t connected and restart in case it crashed (or when I restart the computer). I found this aspect surprisingly difficult; it seems like a really basic need, but the documentation for how to do this was not especially easy to find. I host my bots on a Digital Ocean box running Ubuntu, so this script is running as a systemd service. The [Digital Ocean documentation](https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units) and this [Reddit tutorial](https://www.reddit.com/r/raspberry_pi/comments/4vhofs/creating_a_systemd_daemon_so_you_can_run_a_python/) were both very helpful for my figuring it out.

Since launching the bot, I’ve gotten in touch with the folks at the Wayback Machine, and at their request added a custom user-agent. I was worried that the bot would get on their nerves, but they seem to really appreciate it—what a relief. After its first four days online, it’s tracking some 3,400 users and has sent about 25,000 links to the Internet Archive.