---
layout: post
author: brant
date: 2011-04-09 12:58:34
category:
    - bioinformatics
---

We've been running [beast](http://beast.bio.ed.ac.uk/Main_Page) and [mrbayes](http://mrbayes.csit.fsu.edu/) on several data sets lately, generally using [ec2](http://aws.amazon.com/ec2/) to help us run multiple analyses simultaneously.  Along those lines, I was interested in getting beast (using the [beagle-lib](http://code.google.com/p/beagle-lib/)) running on ec2, to take advantage of their [GPU HPC](http://aws.amazon.com/ec2/hpc-applications/) options (what a load of acronyms!).

Anyway, here are steps to get BEAST running on ec2. Also, expect something a little more formal in the (hopefully) near future describing this option, and even easier means of implementation.

<script src="https://gist.github.com/835693.js"> </script>

