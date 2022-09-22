---
id: 1755
title: 'Pulling free and open weather data'
date: '2017-09-22T13:41:19-07:00'
author: 'Parker Higgins'
layout: post
guid: 'https://parkerhiggins.net/?p=1755'
permalink: /2017/09/pulling-free-and-open-weather-data-in-python/
categories:
    - Uncategorized
tags:
    - bots
    - howto
    - programming
    - python
    - twitter
    - weather
---

When I decided to add realtime weather effects to [@choochoobot](https://www.twitter.com/choochoobot), I knew there were a few qualities I wanted to find in a data source. Ideally I would find something free and reliable that didn’t require me to agree to many developer terms or sign up for an API token. Google [shuttered its undocumented Weather API](https://www.programmableweb.com/news/google-weather-api/2012/08/28) in 2012, and Yahoo’s offering, which has changed a few times over the years, now requires an account and a consumer key and secret.

It took some poking around but I was eventually successful, and now @choochoobot should correctly show clouds, rain, snow, or thunderstorms, depending on whether observations in New York at the moment it’s tweeting.

![](https://parkerhiggins.net/wp-content/uploads/2017/09/Screenshot_2017-09-22_15-46-34.png)

Current observed weather conditions seems to me like something that should be provided by the government as open data. Fortunately, that intuition was correct: free realtime weather data is openly available, if you know where to look.

The National Weather Service, an agency within NOAA, provides weather observations from stations all over the US in RSS and parseable XML formats. And while parsing XML in Python isn’t exactly pleasant, it’s straightforward enough and I am now able to get qualitative descriptions of the current weather that I can translate into emoji. Here’s [the relevant code](https://github.com/thisisparker/choochoobot/blob/master/choochoogen.py#L62-L86), and here’s how it works:

- Each time @choochoobot tweets, it checks to see whether it’s daytime or nighttime. If it’s nighttime, I skip the weather check and instead calculate the phase and placement of the moon in the sky.
- If it’s during the day, I make download the [XML file provided by the KNYC weather station](http://w1.weather.gov/xml/current_obs/KNYC.xml) in Central Park. You can load the same file in your browser at any point, but you probably have to view-source to see it in a reasonable human-readable format. That’s one of about [1,800 locations in US states and territories](http://w1.weather.gov/xml/current_obs/) that the NWS provides information for.
- <span class="citation">@choochoobot</span> then parses the XML file using Python’s built-in [ElementTree XML API](https://docs.python.org/3.5/library/xml.etree.elementtree.html). The relevant field for my purposes is labeled "weather", which contains a text description of the observed conditions.
- At least in theory, that phrase will always be one of the 250 or so pre-set descriptions [provided by the the NWS](http://w1.weather.gov/xml/current_obs/weather.php). These are sort of grouped into categories—there’s a pretty clear thunderstorm grouping, and one for hail—but it seems a bit ad hoc. My use requires classifying the observed weather into just four or five buckets with matching emoji; I just made a big list of terms that I’d take to mean "cloudy," for example, and checked to see whether the observed weather phrase was on that list.
- Then I pick emoji for the sky, and put the whole tweet together. If the weather is cloudy, I replace the sun emoji with a sun-behind-clouds emoji. Real scientific stuff.

In case it’s useful, I’ve converted the NWS list of [weather conditions to JSON](https://github.com/dariusk/corpora/pull/278) and submitted it to Darius Kazemi’s corpora project. Once that gets merged in, those weather conditions will all be available that way.