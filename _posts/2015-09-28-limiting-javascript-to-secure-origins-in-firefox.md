---
id: 1549
title: 'Limiting Javascript to secure origins in Firefox'
date: '2015-09-28T20:08:39-07:00'
author: 'Parker Higgins'
layout: post
guid: 'https://parkerhiggins.net/?p=1549'
permalink: /2015/09/limiting-javascript-to-secure-origins-in-firefox/
categories:
    - Uncategorized
tags:
    - firefox
    - javascript
    - security
---

I’m a Firefox user, but I was very interested to read Chris Palmer’s [guide to privacy and security settings in Chrome](https://noncombatant.org/2014/03/11/privacy-and-security-settings-in-chrome/). One thing he did that really intrigued me was enabling Javascript only on secure sites. It ends up being a pretty good default not just because it prevents attacks that rely on Javascript injection—like the ads that [Comcast](http://arstechnica.com/tech-policy/2014/09/why-comcasts-javascript-ad-injections-threaten-security-net-neutrality/) and [AT&amp;T](http://webpolicy.org/2015/08/25/att-hotspots-now-with-advertising-injection/) have inserted into pages accessed on their hotspots, or the [massive man-on-the-side attack](https://www.eff.org/deeplinks/2015/04/china-uses-unencrypted-websites-to-hijack-browsers-in-github-attack) the government of China apparently conducted against Github—but also because a site going through the effort to authenticate itself is also a reasonable proxy for the kind of stuff I’d allow anyway.

As far as I can tell, on Firefox that means installing [NoScript, a powerful extension](https://noscript.net/) that I’d previously disabled because manually turning on Javascript where I needed it was too much of a hassle. After a few hours of browsing with these settings, it seems to strike the right balance: not exactly *no* fiddling with permissions, but greatly reduced manual intervention with a lot of unnecessary scripts getting blocked.

The option is in NoScript’s preferences, under `Options > Advanced > HTTPS > Permissions`. As long as the global block is on (which it is by default), I found that setting the drop-down menu, “Forbid active web content unless it comes from a secure HTTPS connection” actually works best when set to “Never”—or if you’re a frequent Tor user, to “When using a proxy”. ((This setting is pretty counter-intuitive to me, but if it is set to “Always” I experienced some funny interactions with manual permission changes.)) Then the checkbox below, “Allow HTTPS scripts globally on HTTPS documents”, should be checked.

![Screenshot_2015-09-28_20-00-40](https://parkerhiggins.net/wp-content/uploads/2015/09/Screenshot_2015-09-28_20-00-40.png)

Of course, this isn’t a perfect guarantee of privacy or security. If you don’t trust the Javascript being served from the authenticated site—because the site operators may be malicious or just incompetent—then this technique won’t help. But it does make browsing much faster across much of the web, and preserve the rich interactivity you’re used to on pages your browser trusts.