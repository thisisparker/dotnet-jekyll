---
id: 1565
title: 'How many US people are named Isis?'
date: '2015-11-21T15:48:20-08:00'
layout: post
guid: 'https://parkerhiggins.net/?p=1565'
permalink: /2015/11/how-many-us-people-are-named-isis/
categories:
    - Uncategorized
tags:
    - isis
    - names
    - 'new york times'
---

The New York Times has reported that, despite the long-standing traditional meaning of the name, [people named Isis have faced issues](http://www.nytimes.com/2015/11/21/world/europe/when-youre-named-isis-for-the-goddess-not-the-terror-group.html) ranging from inconveniences to major discrimination in the past several years on the basis of their name. This problem disproportionately affects women, and it’s not just a few cases. What is the scale of people who may be affected?

Using data from the Social Security Administration about birth names and death rates, I estimate that there are 10,620 living people designated female at birth named Isis in the US. ((There is no comparable data for people designated male at birth because the name has not been common enough to be reported.

Obviously, not all people designated female at birth are women, and not all women are designated female at birth. Further, not all people with the name Isis will have it at birth, and not all people born with it will have it as a name now. This is a major limitation of the data. I’ve tried to be as precise as possible throughout this post, but please feel free to suggest corrections.)) The [full data is available on Github](https://gist.github.com/thisisparker/5f1e9cc4e7ae5687a6a3).

According to SSA, [the name “Isis” has been in the top 1000 since 1994](https://www.ssa.gov/OACT/babynames/rankchange.html) for people designated female at birth in the US. It peaked in 2005, with 561 new social security card applications in that year.

SSA only makes information on [names outside of the top 1000](https://www.ssa.gov/OACT/babynames/limits.html) available as raw data, not through its “explorer.” I downloaded it and pulled the number of Isis births into one document. That would be sufficient to calculate (roughly) the number of people born with the name Isis, but wouldn’t account for how many of these people may no longer be living.

In order to determine that number, I went to another data set from SSA: the [Actuarial Life Table](https://www.ssa.gov/oact/STATS/table4c6.html). ((Thanks for the link, [Alex](https://twitter.com/WhatsaTararrel/status/668130752270348289)!)) That dataset includes the percentage of living people at each given age, as of 2011. I fudged the numbers forward, and treated is as if it were 2014 data.

That was the most complex component of the estimation, and it turned out to be mostly unnecessary. The name Isis did not appear to be given to even five babies designated male or female at birth in a single year between 1901 and 1960, ((Though: Social Security card applications were much less common before 1937, so some births may be excluded)) so nearly all US-born people named Isis are under 55 years old and are still alive.

Put in concrete terms: of the estimated 10,715 people in the US named Isis at birth, only about 95 are deceased.

There are serious limitations to this estimation. Among them: it doesn’t account for people born outside of the United States or who did not apply for Social Security cards. The survivorship calculation assumes that the name is evenly distributed across demographics, which is probably not true. It depends on SSA’s treatment of gender as an unchanging binary, which is incorrect. Still, it does provide some insight into the number of people affected by heavy-handed efforts by social media platforms and others to filter out [content related to Daesh](http://www.vox.com/2015/11/14/9734894/daesh-isis-isil).