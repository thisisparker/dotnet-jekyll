---
title: Messaging Signal groups based on Puzzmo webhooks (using Tailscale Funnel)
layout: post
categories:
    - Uncategorized
tags:
    - tailscale
    - puzzmo
    - puzzles
    - golang
    - programming
---

I recently found myself in a situation where I wanted to send the payload of a webhook to a Signal group, and I decided to build a solution. It's now deployed and it works great, so I'm sharing it here in case anybody else wants to do exactly the same thing, or wants to use my code as a jumping off point for a similar project. I think this approach is pretty neat, and in particular it uses [the `tsnet` library](https://tailscale.com/kb/1244/tsnet) and [Tailscale Funnel](https://tailscale.com/kb/1223/funnel) in a fun way that people may want to try.

Some context: I'm a daily solver of the [Puzzmo puzzle site](https://puzzmo.com), and one of my favorite features of the site is the Groups functionality. You can join up in groups with friends, which unlocks two new kinds of competition: _within_ the group, to be the top scorer on a particular game, and _between_ the groups, to reach the top of the global leaderboard of combined scores.

Stoking that competition, Puzzmo will send daily updates on the performance of your group and its members to a Slack or Discord channel. To enable that, you provide Puzzmo with a special URL, and it will send those updates to that URL and [Slack](https://tailvector.slack.com/marketplace/A0F7XDUAZ-incoming-webhooks) or [Discord](https://support.discord.com/hc/en-us/articles/228383668-Intro-to-Webhooks) will handle the rest. (Those updates are sent via "webhook," a term that for a long time sort of intimidated me, but it's basically just an inbound HTTP request.)

From experience, that works great if you're in a Slack or Discord with the other group members! But one group of my Puzzmo friends hangs out in a Signal group. Signal doesn't have any support for webhooks at all, so I couldn't even make a feature request to Puzzmo and wait for [Orta](https://orta.io/) to fix it. Instead, I rolled up my sleeves and turned to Go.

### What I built

What I built was [`puzzmo2signal`, a quick little Go program](https://github.com/thisisparker/puzzmo2signal) that listens for inbound webhook requests, cleans up the contents a bit, and forwards them on to a designated Signal group. The message comes in like any other Signal message, and then we can trash talk each other.[^1]

![An inbound Signal message from "Bottie Botterson" with our scores](/assets/images/bot-message-to-signal.png)

From a technical perspective, the middle section of what it's doing is pretty straightforward: it takes a blob of JSON with a `content` key (that's the payload of a Discord-formatted webhook) and strips the Markdown off of it to make it suitable for sending via Signal. That's normal. The front and back of it are both a little weird though.

#### Down the Funnel

On the inbound-side, we start with the problem: in order to receive a webhook, you need to have a URL to point it at. Because I'm processing this one myself, I need to create that URL. That could mean an annoying little chore of setting up DNS and securing a publicly addressable machine to deploy this on, which struck me as a headache.

Fortunately, from my time working at Tailscale, I was familiar with Funnel, which is kind of like a pared down ngrok alternative that can give a device a predictable public internet address. Under the hood, Tailscale-the-company operates an ingress server at that address, and sends traffic (via Tailscale-the-product, so ultimately WireGuard) to your endpoint.

Even better, I was able to start up the Funnel service from inside `puzzmo2signal` itself, using the `tsnet` library. That frees me up from worrying about DNS, certs, reverse proxies, things of that nature. Effectively, `puzzmo2signal` uses Funnel to expose itself at a designated URL that I could then provide to Puzzmo for those webhooks.

Sometimes webhook senders have some kind of authentication or give you IP addresses to allow-list, but Puzzmo does not. Ah, well. In order to prevent randos from reading this blog post, guessing my URL, and sending messages to my Signal group, I generate a long random path that the sender must use to get a hold of the server. This is security through (significant) obscurity, but it works.

#### Up the Signal

Once the webhook has been received and processed, I send it to a Signal group using [signal-cli](https://github.com/AsamK/signal-cli). What I can say about this is: it works.

There are lots of reasons you might not want to do it, though. I get the sense the Signal Foundation is not crazy about third-party clients, for one thing, which has some knock-on consequences.
- There's no concept of "write-only" group permissions, so my bot is a group member that can read every message we send. That certainly breaks some of Signal's security guarantees, as the group is really only as secure as its weakest endpoint, whether that's a community-maintained CLI client or an [inadvertently included journalist](https://www.theguardian.com/us-news/2025/apr/06/signal-group-chat-leak-how-it-happened). That said, my bot doesn't read or store any of those messages.
- There's also no neat API for sending Signal messages, or (as far as I can tell) any clean way to set up an account on a new install declaratively. In practice, that means that I had to install and configure signal-cli independently, and pipe out messages with an `exec.Command` call, limiting the options for deploying it. I could clean this up a little with [this project that Dockerizes signal-cli and adds a REST API](https://github.com/bbernhard/signal-cli-rest-api), but that's a project for another day.

Basically, the `tsnet` stuff makes this program super portable and then the Signal stuff makes it super not. Ah, well. In practice, I was able to configure `signal-cli` without too much trouble and deployed the server as a systemd service, which works just fine.

### A puzzling question

Why did I do this? One reason is that I just started a(nother!) batch at [Recurse Center](https://www.recurse.com/), where I'm spending some time improving my programming skills. This was a good opportunity to practice some Go with a quick project that scratched a real itch for me. Obviously my familiarity with `tsnet` from my recent Tailscale past helped this one come together.

I really like small projects that make the web work for its users. Often I've done that work on the client end, like my [crossword puzzle scraper](https://github.com/thisisparker/xword-dl/). This was a fun opportunity to work on the server side.

As a meta note: Recurse means more blog posts likely coming soon! I will try to keep them pretty accessible and looking forward to sharing.

[^1]: There's currently some kind of bug that is setting Weather Memoku scores to 0 on Puzzmo's side, so that one is not subject to trash talk.
