---
id: 572
title: 'A modest defense of QR codes'
date: '2012-03-19T01:32:59-07:00'
layout: post
guid: 'https://parkerhiggins.net/?p=572'
permalink: /2012/03/a-modest-defense-of-qr-codes/
categories:
    - Uncategorized
tags:
    - encryption
    - 'qr codes'
---

I’m sort of a QR code anti-hipster: I was into them [before they were uncool](http://ramisayar.com/enough-with-the-qr-codes/). I actually think they’re a really nifty encoding that’s easy to read and write with the right tools, and useful for a handful of situations. But they’re [so widely misused](http://wtfqrcodes.com/) in marketing that most people never get to see one used properly.

But there is a way to use them properly! It’s just not the way marketers have been doing it. When is a QR code the right tool for the job? Well, it’s helpful to think about the limitations of the codes in the first place, instead of just wedging it in to every ad and package design.

#### The limitations

- **They look like [robot barf](http://robotbarf.com/).** It’s true. So don’t count on it being a positive addition to packaging or ad design. If it’s useful that’s great, but it’s not a design element.
- **They’re almost impossible to memorize.** It seems to me like a pretty bad idea to put a company or personal URL in a form that human beings can’t read. If people are already taking out their phones to scan, it’s a missed opportunity for them to write out the domain.
- **They are only scannable in limited circumstances.** Like when people have a scanner app installed, data signal, are stationary relative to the code, and have time to take out and futz with their phone.
- **Almost nobody uses them.** Even I know this.

#### Other properties

- **They use robust error correction.** So there won’t be any typos or misread messages.
- **They add an extra requirement to decoding text.** For marketing purposes, this is terrible. But in some circumstances, it can be useful to know that the decoder can choose not to read the message.
- **They’re easy to generate and scan.** It doesn’t require much processing to encode or decode QR, and they can be made and read locally, without server access.
- **It’s easy to scan a lot of codes in a row.** Scanning the first code involves taking the phone out of your pocket, selecting the app, and focusing the camera. But from there, the marginal cost is very low on additional codes.

Now, if the people using these codes thought about these qualities and picked them only when appropriate, there’d be no problem and no backlash. But alas. When might these be a good tool?

#### Nice uses

- **Cryptographic fingerprint checking.** I use a great open source Android app called [TextSecure](https://play.google.com/store/apps/details?id=org.thoughtcrime.securesms), which allows you to exchange encrypted SMS with other users. But because it’s public key encryption, you have to verify the other person’s fingerprint. Fortunately, you can each just generate and scan QR codes to do so: in this case the alternative isn’t typing in a URL, but manually verifying 64 or so characters.
- **Sending links directly to your phone.** [Chrome to Phone](https://code.google.com/p/chrometophone/) has provided a nice alternative to this usage, but it doesn’t always do the job. Sometimes a QR code is the best way to get a URL, usually a long one, right over to the phone.
- **Selecting some items from a list of many.** In South Korea, Tesco allows shoppers to [scan codes on items in a subway ad in order to purchase them](http://www.geek.com/articles/mobile/koreas-tesco-reinvents-grocery-shopping-with-qr-code-stores-20110628/). Here the low marginal cost of code scanning comes in handy. Once the phone’s out, it makes sense to quickly scan each of them.
- **When “voluntary security” is an element.** Weakly protecting secrets like the answers to quiz questions or hints/spoilers for a game calls for encoding that is easy to decode when wanted, and difficult until then. As long as the user isn’t accessing the content from her smartphone itself, a QR code could useful.
- **Accessing data which requires many dynamic URL parameters.** Because it’s easy to generate QR codes for any length of URL, it could be really nifty to generate them on the spot for URLs that wouldn’t be easy to type in but that wouldn’t make sense to shorten in advance, as with URLs with many parameters. That could happen if, say, a person has selected and scanned a bunch of objects and she wants to see them in a virtual cart, or has filled out a form at an offline kiosk and needs to send the data up through their phone.

The point is, as maligned as QR codes have been recently, there are some jobs for which they’re just right. But as Jaron Lanier is quoted on the back of [The Information Diet](http://www.amazon.com/The-Information-Diet-Conscious-Consumption/dp/1449304680/), “There is no such thing as a tool that is good even if used without conscious consideration.” The marketing guys have spoken, and they’re not ready to provide a counter-example.