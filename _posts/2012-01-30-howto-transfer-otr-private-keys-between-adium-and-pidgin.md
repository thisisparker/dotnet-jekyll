---
id: 475
title: 'HOWTO: Transfer OTR private keys between Adium and Pidgin'
date: '2012-01-30T01:44:24-08:00'
layout: post
guid: 'https://parkerhiggins.net/?p=475'
permalink: /2012/01/howto-transfer-otr-private-keys-between-adium-and-pidgin/
categories:
    - Uncategorized
tags:
    - adium
    - encryption
    - howto
    - otr
    - pidgin
    - privacy
    - ubuntu
---

I recently re-installed Ubuntu on my home computer, and wanted to move my office Mac’s Adium OTR key and collected fingerprints over to the new install. I had some trouble, but got it eventually, so I wanted to document the process.

The first step is to make sure you’ve got Pidgin and Pidgin-OTR installed on one computer, and Adium on another.

Adium stores the OTR private key and the fingerprints in

```
~/Library/Application Support/Adium 2.0/Users/Default/otr.private_key
~/Library/Application Support/Adium 2.0/Users/Default/otr.fingerprints

```

Pidgin, on GNU/Linux, stores the OTR private key and fingerprints in

```
~/.purple/otr.private_key
~/.purple/otr.fingerprints

```

It’s worth noting that neither application stores these keys encrypted. The threat model assumes that if an attacker has access to your `Adium 2.0` or `.purple` folder, you’re already compromised. But that means you have to be extra careful about transferring these files from one computer to another: obviously, sending your key in a cleartext e-mail is not a good idea.

Anyway, harmonizing is just a matter of copying both files from one location to another, and then modifying the key slightly to match the format that each program stores it in. I was disappointed at how poorly documented these formats are, but fortunately the always impressive [Guardian Project](https://guardianproject.info/) has gone through and documented each program’s file location and format in order to build [a tool to convert files between different IM client formats](https://github.com/guardianproject/otrfileconverter). The tool’s not done, and so far only converts to their [Gibberbot mobile IM client](https://guardianproject.info/apps/gibber/), but the [README](https://github.com/guardianproject/otrfileconverter/blob/master/README.txt) contains all the information you need.

In the case of Adium to Pidgin key transfer, which both use the standard `libotrname` field, which is an integer in the Adium config file, needs to be changed to the actual account name. The `protocol` field needs to be changed from `libpurple-jabber-gtalk` (in the case of a GTalk account) to `prpl-jabber`.

You may need to turn Pidgin’s OTR plugin off and on again, but it should recognize your key, and all of your verified fingerprints should show up as well.