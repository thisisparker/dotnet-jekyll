---
id: 1278
title: 'Scripts for book scanning'
date: '2013-11-28T13:50:54-08:00'
layout: post
guid: 'https://parkerhiggins.net/?p=1278'
permalink: /2013/11/scripts-for-book-scanning/
categories:
    - Uncategorized
tags:
    - books
    - bookscanning
    - e-books
    - noisebridge
    - programming
    - scanning
---

I had the pleasure of using [Noisebridge’s book scanner](https://www.noisebridge.net/wiki/Digital_Archivists) to “rip” a couple of rare or unusual books I had lying around. So far as I could tell, none of these had been digitized yet, so that’s kind of exciting. Here’s a picture of me at work, taken by [Maira](https://twitter.com/maira).

[![jpeg](https://parkerhiggins.net/wp-content/uploads/2013/11/jpeg-300x300.jpg)](http://instagram.com/p/grwrRAxgj3/)

Anyway, the scanner is really great, and a work in progress, so for now all it does is dump the photographs—high res images taken by DSLRs affixed to the machine—as sequentially numbered JPEGs in a directory on an attached computer. For a 600 page book, that’s over a gigabyte of photos, and not terribly useful as a digitized book.

So I used [ScanTailor](http://scantailor.sourceforge.net/), which is a great piece of free software, to take a page that looked like the one on the left and (basically running on autopilot) output one like that on the right.

![comparedscans](https://parkerhiggins.net/wp-content/uploads/2013/11/comparedscans.png)

But then I had a directory full of TIFFs, which looked great but were not as portable as a PDF or OCRed to be treated like text. With a little help from smart people like [Eric](https://twitter.com/konklone) and [Seth](http://loyalty.org/~schoen/), I was able to write a script to loop through that directory and output a big PDF, and another to run the images through [Tesseract](https://code.google.com/p/tesseract-ocr/) and output an OCRed text file.

These are really really simple scripts (which is good because I’ve got no idea what I’m doing), but in case those are useful to anybody I’ve [put them up on GitHub](https://github.com/thisisparker/bookscanning) (and even released those three-line loops into the public domain, ha.)

The next step, I think, is manual proofreading. Unfortunately, I don’t think that can be scripted.