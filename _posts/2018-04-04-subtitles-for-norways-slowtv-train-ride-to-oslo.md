---
id: 1816
title: 'Subtitles for Norway&#8217;s SlowTV train ride to Oslo'
date: '2018-04-04T19:24:12-07:00'
layout: post
guid: 'https://parkerhiggins.net/?p=1816'
permalink: /2018/04/subtitles-for-norways-slowtv-train-ride-to-oslo/
categories:
    - Uncategorized
tags:
    - slowtv
    - subtitles
    - trains
image: /wp-content/uploads/2018/04/Screenshot_2018-03-23_22-34-01.png
image_alt: A photographer stands by snowy railroad tracks, poised to snap a picture of the train on which our view is mounted.
---


One thing I enjoy is Norway’s public service broadcaster’s production of a train ride from Bergen to Oslo, which was first broadcast in real time, over seven or so hours, in 2009. It’s predictably pretty quiet stuff, but—at least now that it’s on Netflix—there are in fact subtitles of what little dialog there is.

Netflix makes it pretty straightforward to extract the subtitles from a given program, and it stores them according to a very fun standard called [the Timed Text Markup Language, or TTML](https://en.wikipedia.org/wiki/Timed_Text_Markup_Language), which just missed adoption by the WHATWG in favor of a lighter-weight, less-XML spec called [WebVTT](https://en.wikipedia.org/wiki/WebVTT).

Anyway, I pulled out the (very spare) subtitles in that format and wanted to convert them to something a little more usable. So first I converted them to JSON, and produced an array with [an object for every subtitle](https://gist.github.com/thisisparker/c9d42d1e10d7dd1420915ac090a41dd4), and then processed it a little further and created a version where [“adjacent” subtitles are combined into single objects](https://gist.github.com/thisisparker/b03d94c7900415da2b616e1fac5d673d).

The result is nearly as hypnotic as the original video:

```

    {
        "begin": "00:17:21",
        "end": "00:17:23",
        "text": [
            "[metallic clang]"
        ]
    },
    {
        "begin": "00:19:40",
        "end": "00:19:44",
        "text": [
            "[indistinct conversation / woman laughs]"
        ]
    },
    {
        "begin": "00:19:52",
        "end": "00:19:54",
        "text": [
            "[woman laughs]"
        ]
    },
    {
        "begin": "00:19:57",
        "end": "00:20:01",
        "text": [
            "[indistinct conversation]"
        ]
    },
    {
        "begin": "00:21:47",
        "end": "00:21:48",
        "text": [
            "[metallic clang]"
        ]
    },
    {
        "begin": "00:22:10",
        "end": "00:22:12",
        "text": [
            "[metallic clang]"
        ]
}
```
