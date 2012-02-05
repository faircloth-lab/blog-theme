---
layout: post
title: py2app hell, the second
author: brant
categories:
    - python
---

I have this funny relationship with py2app.  I like what it produces but it is a real hassle to get working.  Anyway, the basic situation is this:

* i needed an application bundle for [msatcommander](http://msatcommander.googlecode.com)
* you cannot, technically, include the Apple-compiled python in an application bundle
* this means you need to get one from somewhere else (e.g. roll-your-own)
* pyqt4 requires a framework build of python (unless you hack, hack, hack)

Other interesting tidbits:

* you need to keep the architectures of everything produced the same.  i chose to stick with `x86_64` and `i386`.
* the prepackaged Qt is built for 3 architectures. This will cause you problems.

Therefore:

<script src="http://gist.github.com/437957.js"></script>
