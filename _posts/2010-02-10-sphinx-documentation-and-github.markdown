---
layout: post
title: sphinx documentation and github
author: brant
categories:
    - python
---

So, there's tools out there to get your documentation up on github ([github-tools][1], [sphinx-to-github][2]), but neither totally jive with how I want to do things.  So, I went searching long and hard for a way to:

* keep the document-generating source in `master`
* place the generated html in `gh-pages`, so it's served as static html
* have everything just "work"
 
Luckily, I came across this post which gets you most of the way there (but assumes you're using jekyll, which isn't the case for me/us).  

So…

<script src="http://gist.github.com/301301.js?file=gistfile1.sh"></script>

[1]: http://github.com/dinoboff/github-tools
[2]: http://github.com/michaeljones/sphinx-to-github