---
layout: post
title: matplotlib hell, too
author: brant
categories:
    - python
---

For another thing I'm working on, I needed matplotlib to compile (this is on a slightly difference machine than that of the previous post).  Bottom line is this:  I needed matplotlib built for `x86_64` and `i386` and without too much other mumbo-jumbo.  I wanted to build this in a virtualenv, because that is how i like things.

Needless to say, matplotlib building is pretty awful (see [previous post](http://ambiguousbase.com/post/444830454/matplotlib-is-a-compilation-nightmare-but)).  It sort of reminds me of py2app. 

Of course, all of that being said, part of the problem is due to Apple switching architectures while maintaining backwards compatible support (at least up to OSX 10.5).  Anyway, I was finally able to get a working matplot lib (with help from the stackoverflow post [here](http://stackoverflow.com/questions/1477144/compile-matplotlib-for-python-on-snow-leopard), using the following OSX-specific makefile (note: i installed freetype and libpng from source into `/usr/local/`)

<script src="http://gist.github.com/437978.js"></script>

And the following edits to the `./Makefile` that comes with matplotlib (not making these edits builds some shared objects for `ppc` and `i386`, which causes problems):

<script src="http://gist.github.com/437975.js"></script>

Finally, I built matplotlib with:

    make -f osx.make mpl_build
    make -f osx.make mpl_install
