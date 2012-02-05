---
title: extending the nextera indexing set
layout: post
author: brant
categories:
    - bioinformatics
---

**UPDATE**: For those of you unwilling to just jump at these, we have validated all of these extended indices and have not found problems with any of the full set of 24, across 6 lanes of multiplexed Illumina sequencing.  You may also be interested in [edittag](http://b.atcg.us/blog/2010/11/20/a-plethora-of-sequence-tags.html), which provides a more generic solution to the barcode generation problem.

The [Epicentre Nextera](http://www.epibio.com/item.asp?ID=566) kit comes with aliquots of barcodes that are compatible with the Illumina multiplex system.  However, they only send you adapters with 12 different indices:

    #Index	Name
    ATCACG	IDX_1
    CGATGT	IDX_2
    TTAGGC	IDX_3
    TGACCA	IDX_4
    ACAGTG	IDX_5
    GCCAAT	IDX_6
    CAGATC	IDX_7
    ACTTGA	IDX_8
    GATCAG	IDX_9
    TAGCTT	IDX_10
    GGCTAC	IDX_11
    CTTGTA	IDX_12

For whatever reason (HiSeq, anyone?), we may want to run a number of indexed sequences in a single sequencing run larger than 12.  Thus, we want to extend the set of 12 adapters to support a larger number of samples.  Skip to the results, here are the indices/barcodes that extend the set of 12:

* [Extended Nextera Tags (6nt, edit distance = 2)](/media/txt/extended_nextera_tags_6nt_ed2_barcodes.txt)

Now, as you'll see below, the default set of barcode IDX adapters are edit distance 2 apart from one another.  I don't typically feel comfortable until barcode adapters are edit distance ≥ 3 from one another - so, if we want to extend the Nextera set (using *most* of the adapters provided), we can **DROP IDX 1 and IDX 8 from the set of adapters that came with the kit**, and then design additional adapters from the barcode sequences int the following (see below for slightly more detail):

* [Extended Nextera Tags (6nt, edit distance = 3)](/media/txt/extended_nextera_tags_6nt_ed3_barcodes.txt)

I didn't have tons of time to spend on this, so what you can see over at [github](https://github.com/) is slightly ugly.  But, it is what it is.  Also, I put the Methods posted over on github to catch any changes, but the `<script>` formatting that you get (notice below) is not quite WYSIWYG.

<script src="https://gist.github.com/670033.js"> </script>