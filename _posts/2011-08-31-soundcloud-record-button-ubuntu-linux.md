---
id: 371
title: 'Getting the SoundCloud Record button to work in Ubuntu'
date: '2011-08-31T21:08:02-07:00'
layout: post
guid: 'https://parkerhiggins.net/?p=371'
permalink: /2011/08/soundcloud-record-button-ubuntu-linux/
categories:
    - Uncategorized
tags:
    - flash
    - howto
    - soundcloud
    - ubuntu
---

Since it was introduced, the SoundCloud Record button has been hard to get to work in Ubuntu and other GNU/Linux distributions. Fortunately, my buddy [Omid](http://twitter.com/omidaladini), who is a SoundCloud developer, has found a solution.

It turns out the problem is caused by a “Linux-specific security feature” (read: [bug](https://bugs.adobe.com/jira/browse/FP-1211) \[login required\]) that prevents a Flash settings dialogue from appearing when wmode=opaque is used. In any case, there are a few easy workarounds.

If you’ve got the flash-player-properties package installed (which, at least on Ubuntu, ships separately from the flash-plugin, but is available in the standard repositories), you can add “a1.sndcdn.com” to the allowed sites under the “Camera &amp; Mic” tab of that program.

Otherwise, if you’ve unsuccessfully attempted to record at least once on [the SoundCloud upload page](http://soundcloud.com/upload), you can add a1.sndcdn.com from the Flash player’s [web settings panel](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html). While you’re there, check your security settings!

Hope this is helpful to other SoundCloud users on Linux who haven’t quite been able to get recording working.