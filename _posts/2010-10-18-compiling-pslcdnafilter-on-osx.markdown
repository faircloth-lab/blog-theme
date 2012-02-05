---
title: compiling pslCDNAFilter on osx
layout: post
author: brant
categories:
    - bioinformatics
---

I need to filter some `psl` output from [blat](http://www.ncbi.nlm.nih.gov/pubmed/11932250), and I'd like to do it using
the `pslCDNAFilter` that's provided as part of the [Kent Source tree](http://genome-source.cse.ucsc.edu/gitweb/?p=kent.git;a=summary).
Although the Kent Source typically behaves well after you set your environment
variables appropriately, this little bit was not behaving well.  So, I undertook a horrific hack job to get it to compile (this basically requires altering the `makefile` and physically placing some text into `pslCDNAFilter.c`):

<script src="http://gist.github.com/633694.js"> </script>
