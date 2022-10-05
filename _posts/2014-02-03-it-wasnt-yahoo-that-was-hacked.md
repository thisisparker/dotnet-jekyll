---
id: 1302
title: 'It wasn&#8217;t Yahoo that was hacked'
date: '2014-02-03T00:52:39-08:00'
layout: post
guid: 'https://parkerhiggins.net/?p=1302'
permalink: /2014/02/it-wasnt-yahoo-that-was-hacked/
categories:
    - Uncategorized
tags:
    - passwords
    - security
    - yahoo
---

I’ve been disappointed to see a lot of journalists get a recent story about security breaches and Yahoo Mail wrong. In particular, I worry that this kind of misleading reporting will contribute to worse security practices for both the companies that users trust with their data, and the users themselves.

First, here’s what happened: Yahoo [reported on its Tumblr](http://yahoo.tumblr.com/post/75083532312/important-security-update-for-yahoo-mail-users) that it had detected “a coordinated effort”—basically, an attack—by somebody trying to gain access to user accounts. Yahoo deserves some credit here for reporting that information, and also for taking the good next steps of resetting passwords of affected users and “implement\[ing\] additional measures to block attacks.”

This is not an attack on Yahoo. It’s the predictable result of a leak of *somebody else’s* database. Let’s call the origin of that database Company X. Company X’s database contains both user email addresses and passwords to log into Company X’s site. But if Company X users had the same password to log in to both their email account and Company X’s site, it’s trivial to take the leaked information and try to log into email accounts with it.

That’s what it sounds like happened in this case. Yahoo detected somebody using this leaked database to try to get into many different user accounts and proactively changed passwords to mitigate the risk for people who reuse password.

But the press reported it instead as if Yahoo had screwed up. Slate’s barely-accurate headline is “[Yahoo Email Usernames and Passwords Stolen in Cyberattack.](http://www.slate.com/blogs/the_slatest/2014/01/30/yahoo_reports_some_email_usernames_and_passwords_stolen_in_cyberattack.html)” LA Times says [Yahoo “fell victim” to an attack](http://www.latimes.com/business/technology/la-fi-tn-yahoo-mail-breach-number-users-not-disclosed-20140130,0,3294421.story); Washington Post’s headline was “[Yahoo mail hacked](http://www.washingtonpost.com/business/technology/yahoo-mail-hacked-what-to-do-if-youve-been-affected/2014/01/31/2857ef8a-8a7d-11e3-833c-33098f9e5267_story.html)” and goes on to give Yahoo-specific security tips.

That’s where the real danger is: misunderstanding this kind of breach as the result of bad security by *Yahoo*, and not bad security by *users*. The right way to mitigate this problem is to never reuse passwords, and certainly never to reuse your email account password. Note that this entire attack fails completely if users’ Company X passwords are different from their Yahoo Mail passwords. The best way to use good and unique passwords is to use a password safe like [KeePass X](https://www.keepassx.org/) or [LastPass](https://lastpass.com/) and have that program generate a new one for each site.

This is good advice everywhere, but absolutely critical stop-reading-this-blog-post-and-do-it-now advice for email accounts. Email addresses are both uniquely vulnerable targets and valuable assets for attackers. A leaked database from some random site won’t include information about your credentials on other websites *except* your email. And compromising an email account can get an attacker master keys into other accounts. They can search for banking info, for example, and have your super-secret bank password reset with a “Forgot my password?” email reset option.

Given those heightened risks, you want your email provider to be especially vigilant. When they detect any kind of attack, you want them to take action. I worry that if the press reports this kind of sensible reaction as if it were a screw-up, it will discourage other companies from following suit.