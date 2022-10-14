---
id: 1570
title: 'A Twitter list of somebody else&#8217;s timeline'
date: '2015-12-13T17:00:58-08:00'
layout: post
guid: 'https://parkerhiggins.net/?p=1570'
permalink: /2015/12/a-twitter-list-of-somebody-elses-timeline/
tags:
    - t
    - twitter
---

Sometimes I wish I could use Twitter as a different account, and read all the conversations and references that result from the unique list of accounts a person has chosen to follow (sometimes over the course of years!) There’s no “use Twitter as @x” mode yet, so the next best thing is to create a list of all the accounts somebody follows. The public view of that list is, roughly, that person’s main timeline. This came in handy recently as I was [trying to follow a basketball game](https://twitter.com/xor/status/675514816618885120), because I don’t yet follow the kinds of people who make insightful comments about basketball games.[^1]

Fortunately, this is a one-liner with the super handy command line program `t`. If you don’t have `t` installed, I [strongly recommend downloading and configuring it](https://github.com/sferik/t) even if you don’t want to do the rest of these steps. It’s just a very useful tool to have in your Twitter toolbelt.

Here’s the `t` command:

> `t followings OTHERACCOUNT | xargs t list add LISTNAME`

Where `OTHERACCOUNT` should be replaced with the name of the account you want to use, and the `LISTNAME` should be the name of an existing list. I just made the list through the web interface, which allows me to set it as private.

Important note! If you don’t set it as private, or if you ever make it public, members of the list will get a notification that they’ve been added. People [tend to think that’s very weird](https://twitter.com/theshrillest/status/675515014506156032).

I also like to add the originating account to the list so you can see replies to and from that person.

Finally, some caveats: obviously, you won’t get access to private accounts that user follows. You will see people that user has muted, unless you’ve already muted them. You won’t see notifications that user sees. And of course, if the user has something like Tweetdeck and uses columns other than the “main timeline,” you won’t know. Still, it’s a pretty good way to check out Twitter from somebody else’s point of view.

[^1]: You could argue it’s like a DIY version of Twitter Moments, where you trust the curation done by an individual user is better than the algorithm, but I won’t be the one making that argument.
