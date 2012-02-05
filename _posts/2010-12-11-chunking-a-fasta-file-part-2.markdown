---
title: chunking a fasta file, part 2
layout: post
date: 2010-12-11 15:45:45
author: brant
categories:
    - python
    - bioinformatics
---

Well, it took me more time than I had planned to get around to wrapping [this](http://b.atcg.us/blog/2010/10/03/chunking-a-fasta-file-part-1.html) up... but, it is what it is.  

I have completed some code that will use single- or multiple-processes to split a fasta or fastq file into a requested number of subunits.  I have yet to test the speed of the code relative to something like `split`, but my guess is that it's rather fast, particularly for large files.

I provide a use case at the bottom of the file.

<script src="https://gist.github.com/737708.js"> </script>

