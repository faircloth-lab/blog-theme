---
title: a plethora of sequence tags
layout: post
date: 2010-11-20
author: brant
categories:
    - bioinformatics
---

Sequence tags can be attached to DNA reads of interest to let you [track][1] [different][2] [pools][3] of reads following a second generation sequencing run.  The best way to generate tags for these reads is a matter of some debate:

 * you can "just make them"
 * you can generate them with a [program][4]
 * you can use [Hamming][5] [distance][13] tags
 * you can use [Levenshtein][6] [distance][14] tags

The problem with "just making" the tags is that sequencing errors can inadvertently turn one tag into another if there is, say, an erroneous substitution of a base into the tag portion of the sequence read.  Error correcting tags using [Hamming distance][3] attempt to counter this effect, but are only robust to substitution errors, which [can be problematic][8].  Levenshtein distance tags are robust to insertion, deletion, and substitution error, but it is often hard to find available sets of Levenshtein distance sequence tags.

With all of that in mind, I offer several sets of Levenshtein distance sequence tags.  These tags range from 4 to 10 nt and edit distance 3 to 9.  The 10nt tags are somewhat slow to create (70 or 80 hours on a multicore machine), so you might as well just use these rather than generate a set, *de novo*.  If you would like to check the tags, to ensure they are of the appropriate distance, you [can][7].

For those interested in the nitty-gritty details, see the [code][9], which is one program within [edittag][10].  Now, here are the tags:

 * [sequence tag xls file][11]
 * [sequence tag csv file][12]

[1]: http://dx.doi.org/10.1093/nar/gkm566
[2]: http://dx.doi.org/10.1371/journal.pone.0000197
[3]: http://dx.doi.org/10.1038/NMETH.1184
[4]: http://bioinf.eva.mpg.de/multiplex/
[5]: http://en.wikipedia.org/wiki/Hamming_distance
[6]: http://en.wikipedia.org/wiki/Levenshtein_distance
[7]: https://github.com/BadDNA/edittag/blob/master/bin/validate_edit_metric_tags.py
[8]: http://dx.doi.org/10.1109/CIBCB.2009.4925705
[9]: https://github.com/BadDNA/edittag/blob/master/bin/design_edit_metric_tags.py
[10]: https://github.com/baddna/edittag/
[11]: https://github.com/downloads/BadDNA/edittag/edit_metric_tags.xls.zip
[12]: https://github.com/downloads/BadDNA/edittag/edit_metric_tags.txt
[13]: http://www.lee.eng.uerj.br/~gil/redesII/hamming.pdf
[14]: http://sascha.geekheim.de/wp-content/uploads/2006/04/levenshtein.pdf

