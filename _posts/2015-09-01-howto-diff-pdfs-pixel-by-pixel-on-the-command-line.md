---
id: 1545
title: 'HOWTO: Diff PDFs pixel-by-pixel on the command line'
date: '2015-09-01T19:20:34-07:00'
layout: post
guid: 'https://parkerhiggins.net/?p=1545'
permalink: /2015/09/howto-diff-pdfs-pixel-by-pixel-on-the-command-line/
categories:
    - Uncategorized
tags:
    - howto
    - pdf
---

There was a major order in the Uber class action case today: the class was certified, which means that [the suit can be on behalf of 160,000 drivers](http://motherboard.vice.com/read/judge-rules-160000-uber-drivers-can-sue-in-a-class-action), instead of just the handful putting their names on the documents. Big deal!

Then a few minutes later, the court issued an amended version of the order, but didn’t release a changelog. How is a reader to know which parts are worth looking at?

There are a lot of ways to solve this problem, but I wanted one that would work on the command line, that wouldn’t require much in the way of unusual software (or Adobe), and that wouldn’t depend on having the text embedded in the PDF. Court PDFs usually do have text, but it’s a little unreliable, and in this case the documents were so close that I could compare the pixels of one to the other.

I googled around a bit, and here’s the workflow I decided to follow, adapted from [this Stack Overflow question’s answers](https://stackoverflow.com/questions/6469157/pdf-compare-on-linux-command-line). It assumes you have `pdftk` and `imagemagick` installed.

- Put both PDFs, file1 and file2, in one directory by themselves, and make a subdirectory called `/out` for temporary output.
- Split, or “burst”, each PDF into its component pages with `pdftk`, and put those pages in the `/out` directory.
- Use a bash loop to run `imagemagick`‘s compare feature over each pair of pages from file1 and file2, creating a new page for each that just contains the differences highlighted in red.
- Again using `pdftk`, merge all of those diff pages back into one document that uses the original as the background.

In code, that looks like this:

> `pdftk file1.pdf burst out/file1---page%03d.pdf<br></br>pdftk file2.pdf burst out/file2---page%03d.pdf<br></br>for i in {001..###}; do compare out/file1---page$i.pdf out/file2---page$i.pdf -compose src out/file1--file2--diff---page$i.pdf; done<br></br>pdftk out/file1--file2--diff*.pdf cat output diff.pdf<br></br>pdftk diff.pdf multibackground file1.pdf output compositediff.pdf`

The parts that need to be customized each time are the names of file1 and file2 for the first two lines and the very last line, and the `###` needs to be replaced by the number of pages in each document. Other than that, you can let this one rip and end up with a visual diff in just a few seconds!

![diffed pdf page](https://parkerhiggins.net/wp-content/uploads/2015/09/diffedpdfpage.png)

You can see how it looks above. This is the only page that changed, and it’s just one footnote.