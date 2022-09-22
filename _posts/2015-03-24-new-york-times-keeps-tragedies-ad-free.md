---
id: 1485
title: 'How the New York Times keeps tragedies ad-free'
date: '2015-03-24T16:48:36-07:00'
author: 'Parker Higgins'
layout: post
guid: 'https://parkerhiggins.net/?p=1485'
permalink: /2015/03/new-york-times-keeps-tragedies-ad-free/
categories:
    - Uncategorized
tags:
    - advertising
    - gmail
    - html
    - 'new york times'
---

I was looking at the HTML source of a recent [New York Times story about a tragic plane accident](http://www.nytimes.com/2015/03/25/world/europe/germanwings-crash.html)—150 people feared dead—and noticed this meta tag in its head:

```
<<span class="start-tag">meta</span> <span class="attribute-name">property</span>="<a class="attribute-value">ad_sensitivity</a>" <span class="attribute-name">content</span>="<a class="attribute-value">noads</a>" />
```

There are no Google results for the tag, so it looks like it hasn’t been documented, but it seems like a pretty low-tech way to keep possibly insensitive ads off a very sensitive story—an admirable effort. It’s interesting in part because it’s almost an acknowledgement that ads are invasive and uncomfortable. They cross over into the intolerable range when we’re emotionally vulnerable from a tragic story. Advertisers know this too, and the New York Times might stipulate in contracts they’ll try to keep ads off sensitive pages.

If I had to guess, I’d say this is probably a manual switch in their CMS. It would be interesting to see what sorts of stories get dubbed unfit for ads, though scraping enough article pages to get that information might raise some eyebrows on that side of the paywall.

(This information, by the way, doesn’t have to be exposed for keeping ads off pages they serve. But it could help with debugging, and definitely could be useful for syndication and maybe even displaying in official apps.)

This isn’t the first example of companies declining to advertise against tragedies. Five years ago a user documented that [Gmail doesn’t show ads on emails that contain words from a certain blacklist](http://boingboing.net/2009/07/31/how-to-avoid-ads-in.html), at a certain density—one sensitive word per 167 “normal” words.

## update, 25 March: The Tragedy Tag

Since I originally posted this yesterday, two interesting things have happened. One is that current and former *Times* employees have confirmed my guess that this is a manual CMS switch (dating back to at least 2003), and people familiar with the CMSes at other publications like *The Guardian* have said there are similar systems in place.

The other thing is that the tragic story that prompted this took a turn for the worse, and the deaths that were once suspected have been confirmed. The HTML tag has been updated from `"noads"` to `"tragedy"`, which employees have confirmed is the third and final position on the switch.