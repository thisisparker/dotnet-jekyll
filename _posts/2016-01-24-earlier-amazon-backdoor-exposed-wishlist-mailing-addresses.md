---
id: 1574
title: 'Amazon backdoor exposed wishlist mailing addresses'
date: '2016-01-24T20:15:22-08:00'
layout: post
guid: 'https://parkerhiggins.net/?p=1574'
permalink: /2016/01/earlier-amazon-backdoor-exposed-wishlist-mailing-addresses/
tags:
    - amazon
    - privacy
    - security
---

There’s an article circulating right now about how [Amazon customer service can be exploited to reveal targeted mailing addresses](https://medium.com/@espringe/amazon-s-customer-service-backdoor-be375b3428c4#.hqxfxuajw). I discovered and reported a similar vulnerability in December of 2014, which was reported to me as fixed in May of 2015. I haven’t publicly documented that process until now.

The vulnerability I discovered relates to [Amazon wishlists](http://www.amazon.com/gp/registry/search). Users can associate wishlists with a private address, so that people can buy and ship them gifts without having the recipient’s private information. That address should be kept confidential throughout the entire process, but I found that third party shippers—routinely used for Amazon sites outside of the United States—would sometimes include it in confirmation emails.

In particular: I used Amazon.ca to send a book to a friend, and Canada Post delivered her full address to me in an email. In this exchange, Amazon’s confirmation email properly showed my friend’s address as redacted, but Canada Post revealed it in its entirety.

![Amazon confirmation](https://parkerhiggins.net/wp-content/uploads/2016/01/Screenshot_2016-01-24_19-57-19.png)

![](https://parkerhiggins.net/wp-content/uploads/2016/01/canada-post-confirmation.png)

That would be unacceptable in any circumstance. But it’s all the worse because some of the people who use Amazon wishlists are especially vulnerable to targeted harassment. The service is popular, for instance, [among camgirls and sex workers accepting gifts](http://www.dailydot.com/lifestyle/amazon-sex-worker-wish-lists/). I’ve also seen wishlists from Twitter microcelebrities, who get occasional threats and unwanted creepy overtures, as well as wishlists from women who are trying to get some support after leaving an abusive domestic situation. For many of these people, a revealed address can be devastating.

I contacted [Amazon Security](http://www.amazon.com/gp/help/customer/display.html/ref=hp_left_sib?ie=UTF8&nodeId=201182150) via email,[^1] and got a confirmation number and a response from a human that it had been assigned to somebody. The fix, introduced in May, seems to simply removed the second confirmation email direct from Canada Post.

![My email to Amazon Security](https://parkerhiggins.net/wp-content/uploads/2016/01/Screenshot_2016-01-24_20-05-52.png)

![Amazon Security fix](https://parkerhiggins.net/wp-content/uploads/2016/01/Screenshot_2016-01-24_20-06-23.png)

Although the five month window to fix this situation seemed too long to me, I didn’t want to go public until it had been addressed. An attacker who knew about this vulnerability could easily exploit it for the cost of the cheapest item on a particular wishlist, and the only fix a user could make was removing their address entirely.

Given that particular combination—easy, cheap exploitation, and no alternative path to security—it seemed irresponsible in this case to disclose the problem publicly. Others may disagree.

This isn’t the first time wishlists have inadvertently leaked address data—it happened [at least once before in 2011](http://wishlistexposed.blogspot.com/). Nor do I know for sure that the fix has been applied worldwide, as I only tested in Canada. Unfortunately, [for people who could face threats if their address were revealed](https://ssd.eff.org/en/module/introduction-threat-modeling), Amazon seems like a dangerous service to share it with.

[^1]: They make a PGP key available, but [only distribute it over unauthenticated HTTP](http://www.amazon.com/gp/help/customer/display.html?nodeId=200724850). All the more reason Amazon should switch to entirely HTTPS.
