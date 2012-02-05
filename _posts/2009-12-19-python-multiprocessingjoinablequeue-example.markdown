---
title: python multiprocessing.JoinableQueue() example
layout: post
author: brant
categories:
    - python
    - bioinformatics
---

After a lot of pain and suffering trying to debug what was going wrong that appeared to be a stuck process, it simply boiled down to not closing my Queues:

<script src="http://gist.github.com/260331.js?file=gistfile1.py"></script>

Here's the full module's documentation:  http://docs.python.org/library/multiprocessing.html

