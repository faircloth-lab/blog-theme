---
title: Sphinx + Github With No Submodules
layout: post
date: 2011-01-22 18:59:50
author: brant
category:
    - git
---

Previously, I detailed how I was [using git submodules][1] and [gh-pages][2] at github to host the html versions of my documentation generated by [sphinx][3].  Basically, the problem is that using git submodules for this is a real pain (for me, at least).  You've always got to remember to sync up the submodule(s) just so, or things go horribly wrong and stop tracking each other.

Because I can never remember the correct order of what needs to be committed when, I searched for other ways.  And searched.  And searched.  Finally, I ginned up something that I think I like.  It basically uses a directory, within your project but ignored by `.gitignore`, to keep track of your gh-pages content.  Because the `.git` directory tracks what you need to track, you can run `make html` for sphinx with impunity, and you can push your changes to gh-pages when you want - no need to remember what goes when and where.

Finally, you can track the raw [rst][4] of your doc files in the regular source tree, just like you should.

<script src="https://gist.github.com/791759.js"> </script>

[1]: ../../../2010/02/10/sphinx-documentation-and-github.html
[2]: http://pages.github.com/
[3]: http://sphinx.pocoo.org/
[4]: http://docutils.sourceforge.net/rst.html