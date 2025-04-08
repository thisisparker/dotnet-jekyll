---
id: 1699
title: 'Building Mastodon to be frozen'
date: '2017-04-30T17:21:02-07:00'
layout: post
guid: 'https://parkerhiggins.net/?p=1699'
permalink: /2017/04/building-mastodon-frozen/
categories:
    - Uncategorized
tags:
    - archives
    - mastodon
    - 'social media'
---

As the federated social network Mastodon has surged in popularity over the last month, [more than a thousand instances](https://instances.mastodon.xyz/) — ranging from a single user to tens of thousands — have been started by the community.

![](/assets/images/mastodon-logo.png)

That’s a really great development in terms of decentralization and distribution, which bring a lot of benefits, but it also makes it a near certainty that a currently popular instance will go away. It could happen abruptly, if a sysadmin accidentally drops a database, or gradually, if it becomes to expensive or time-consuming to run, but it will happen.

Mastodon developers can make some choices now that could help preserve those communities — if only in a “frozen” form — after they are no longer active. And if done right, it could open up new possibilities for persistent presentation of ephemeral communities.

Specifically, Mastodon can develop a more robust option to export an entire instance in a format that can be served statically. The Mastodon instance would be frozen, in the sense that nobody could sign up or add new content to it, but its links could be preserved and the interactions could be saved. Serving a static version of the site in a dedicated viewer could be done cheaply, and organizations like the Internet Archive would likely step up to host significant defunct communities.

(Twitter sort of has an option like this on the individual level: users can [export their own archive](https://support.twitter.com/articles/20170160), and get a zip file that *looks* like Twitter but is all local.)

The historical benefits of that kind of feature are obvious to anybody who’s gone through old forums or mailing list posts. But if it were built out as a feature, I think more communities would find new creative ways of using the software. One that immediately comes to mind: Conferences could throw up an instance and create accounts for all the attendees. Once that instance was “frozen,” it’s a record of the backchannel like we haven’t really had before. Or in cases where they’ve gotten clear consent, researchers could parse the data to learn things about how the different ways in which individual communities communicate.

Obviously not every instance would want to get the preservation treatment, and instance admins would likely want to make clear what their long term plans are. And of course, this feature would have to be designed very carefully to respect the privacy preferences of people who participate. But for many networks, the present moment gets all the focus while the real value lies in each of those presents that have now become the past. Most social networks don’t stop to consider that fact. Mastodon, with its community focus, could.

There aren’t that many years of Web (or even Internet) history, but already those years haven’t been kind to online communities. [Archiveteam heroics](https://www.wired.com/2010/11/geocities-lives-on-as-massive-torrent-download/) only go so far — designing for the long-term preservation of our spaces should be a priority.
