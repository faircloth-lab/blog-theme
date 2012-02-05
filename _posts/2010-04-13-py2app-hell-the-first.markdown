---
layout: post
title: py2app hell, the first
author: brant
categories:
    - python
---

I ran into a problem with a program that I work on where [wxPython][1] wasn't cutting it any longer, for various reasons (notably their current lack of support for 64-bit archs - see [here][2]).  I wasn't really in love with wxPython, anyway, so I decided to ditch it in favor of [Qt4][3], in combination with [PyQt4][4] (which depends on sip for its C++ bindings).

While the general process of rewriting my GUI interface was pretty straightforward (given the decent tools in the Qt SDK + pyuic from PyQt4), I figured that packaging up the release was going to be painful.  Call me crazy, but the shift to 64-bit in Snow Leopard should cause some issues with [py2app][5] working well for building bundles.  It generally turns out that I was correct (don't get me wrong, I like py2app, it's just touchy).
 
I searched around for specific instructions on how to fix lots of the things that were broken.  These included what I think was an endianness error, a typo in py2app's subversion code, mach-o build mismatches between sip-PyQt4-PyQt, and failure of py2app to add a directory to the bundle you build (i think that's it).  Of most utility in my problem solving, I came across [this][6] thread which details many of the additions made (in the subversion trunk) to get py2app working, so thank you [Marc-Antoine Parent][7].  You are awesome.  This [post][8] by [Piotr Maliński][9] was also helpful.
 
Long story short, for the moment, on Snow Leopard (10.6.2) with the system python, you need to do the following to make things work:

<script src="http://gist.github.com/607966.js"> </script>

[1]: http://www.wxpython.org/
[2]: http://trac.wxwidgets.org/ticket/11160
[3]: http://qt.nokia.com/downloads
[4]: http://www.riverbankcomputing.co.uk/software/pyqt/intro
[5]: http://svn.pythonmac.org/py2app/py2app/trunk/doc/index.html
[6]: http://www.mail-archive.com/pythonmac-sig@python.org/msg09615.html
[7]: http://maparent.ca/
[8]: http://www.rkblog.rk.edu.pl/w/p/building-mac-os-x-applications-py2app/
[9]: http://twitter.com/riklaunim