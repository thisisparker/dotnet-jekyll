---
id: 282
title: 'Klout scores, inactive followers, and Goodhart&#8217;s law'
date: '2011-02-28T02:37:43-08:00'
layout: post
guid: 'https://parkerhiggins.net/?p=282'
permalink: /2011/02/klout-scores-inactive-followers-and-goodharts-law/
categories:
    - Uncategorized
---

My friend [Arlene Wszalek](http://twitter.com/wzzy) has written [a blog post describing a “conundrum” facing users of Klout](http://sw14group.com/wzzy/2011/02/a-klout-conundrum/), a [service which aims to quantify online influence](http://klout.com/) by evaluating [some 35 metrics related to Twitter and Facebook](http://klout.com/kscore). Arlene lays out the problem: one factor Klout apparently considers is the proportion of your followers who are actively engaging with your profile or stream. But by using another service called [ManageFlitter](http://manageflitter.com/), Arlene determined that 27% of her followers are inactive, having not used Twitter in over a month. So her score may be being skewed downwards by that soft cap of followers that are active and could actually be reasonably expected to engage.

I actually don’t identify that situation as a problem. For one, Arlene’s measured 27% follower attrition rate could very well be standard throughout Twitter,[^1] and because Klout scores are basically numbered arbitrarily, “inflation” or “deflation” in this sense doesn’t matter. Put another way, Klout scores are no less useful for being absolutely lower, as long as the same factors are skewing everybody’s profile in the same direction. Of course, Klout may also identify the “bug” Arlene describes as a feature. After all, if 27% of your followers aren’t likely seeing your updates, shouldn’t that be reflected in a measure of your influence?

As I see it, though, a real problem could arise based on the way Klout weighs the different factors that they measure against each other. Enough experimentation could tell you whether removing those 27% of followers would move the Klout score up or down. If the percentage of active followers is weighed more heavily than the absolute number of followers, then running an automated process to remove inactive followers could bump the score up a bit.

Right now, little rides on a person’s Klout, so there probably aren’t yet widespread efforts to subvert their ratings through tricks like that. But if we were to start seeing jobs, sponsorships, speaking engagements, or book deals offered on the basis of Klout scores, that could change — and when it changes, [Goodhart’s law](https://secure.wikimedia.org/wikipedia/en/wiki/Campbell%27s_Law) starts to kick in.[^2] According to that law, the “statistical regularity” of the behaviors Klout measures “will tend to collapse” under corrupting forces once “pressure is placed on it for control purposes.” In other words, users begin to game the scores and the numbers begin to lose their utility.

If that situation should arise, Klout could be compelled to respond by changing their algorithm to something more arcane, in order to be less readily reverse-engineered. I’m afraid that could be a problem for them. The more abstracted and convoluted the algorithm that produces Klout scores gets, the more likely it is to produce seemingly arbitrary results. Users whose natural influence profiles resemble the artificial ones of Klout-manipulators could see their scores adjusted downward, while other users whose profiles matched an increasingly complicated pattern might experience the opposite effect. If enough of these cases show up, Klout scores cease to be a meaningful proxy for influence.

The statistician [George Box](https://secure.wikimedia.org/wikipedia/en/wiki/George_E._P._Box) is famously quoted as saying “Essentially, all models are wrong, but some are useful.” The Klout conundrum I see is not that any particular factor is incorrectly considered — after all, the algorithm can be adjusted — but that they may be forced into deciding between making their model more wrong through action, or less useful through inaction.

[^1]: A widely discussed [Nielsen article from a few years](http://blog.nielsen.com/nielsenwire/online_mobile/twitter-quitters-post-roadblock-to-long-term-growth/) back pegged sitewide **retention** rate among new users at 40%, but there are lots of reasons to think that number could be higher today and that Arlene’s followers wouldn’t be quite so fickle.
[^2]: I debated for a long time whether it’s Goodhart’s or Campbell’s law that is most appropriate here. I decided Goodhart’s was better, on the presumption that it’s the presumed constants of things like follower attrition rate that break down, and not actual following behavior that changes.
