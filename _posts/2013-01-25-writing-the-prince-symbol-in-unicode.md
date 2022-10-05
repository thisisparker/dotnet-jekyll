---
id: 1012
title: 'Writing the Prince symbol in Unicode'
date: '2013-01-25T08:54:45-08:00'
layout: post
guid: 'https://parkerhiggins.net/?p=1012'
permalink: /2013/01/writing-the-prince-symbol-in-unicode/
categories:
    - Uncategorized
tags:
    - prince
    - typography
    - unicode
---

In the early 90s, the musician Prince dropped his name and started going by an unpronounceable symbol. He called it “The Love Symbol,” and it’s a combination of the traditional male (♂) and female (♀) symbols.

![Prince_logo.svg](https://parkerhiggins.net/wp-content/uploads/2013/01/Prince_logo.svg_.png)

Apparently (at least according to Wikipedia) [Warner Bros had to send out floppy disks with a custom font](https://en.wikipedia.org/wiki/Prince_(musician)#The_New_Power_Generation.2C_Diamonds_and_Pearls_and_name_change:_1991.E2.80.9394) to the music press they hoped would review his record. As a side note, this would be one of my all-time favorite collectibles. A purple (and you know it’d be purple) floppy disk with the Prince font? So great.

Anyway, so the Prince symbol is not eligible for inclusion in Unicode, which “does not encode personal characters, nor does it encode logos.” Still, though, the Unicode geeks on mailing lists have talked about it, charmingly using the shorthand TAFKAP (for The Artist Formerly Known As Prince). [In one 1999 thread](http://www.unicode.org/mail-arch/unicode-ml/Archives-Old/UML019/0611.html), a guy named Marco Cimarosti ([personal homepage, in Italian, last updated 2006](http://web.tiscali.it/marco.cimarosti/)) proposed a canonical encoding of the glyph, using these combining characters:

> 01AC LATIN CAPITAL LETTER T WITH HOOK  
> 030A COMBINING RING ABOVE  
> 0335 COMBINING SHORT STROKE OVERLAY  
> 032C COMBINING CARON BELOW

The end result, which will only work if you’re viewing this page in UTF-8 and have proper font support ((If you don’t have the right font, I can recommend [Symbola](http://users.teilar.gr/~g1951d/))) is Ƭ̵̬̊. Rendered large, that’s:  
<span style="font-size: xx-large; line-height: 150%; font-family: Symbola, Helvetica, Arial, sans-serif;">Ƭ̵̬̊</span>  
It’s not perfect, and it isn’t very simple to type, but it beats writing out The Artist Formerly Known As Prince each time.