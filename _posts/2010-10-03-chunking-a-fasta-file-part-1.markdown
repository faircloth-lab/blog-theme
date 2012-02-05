---
title: chunking a fasta file, part 1
layout: post
author: brant
categories:
    - python
    - bioinformatics
---

I've been thinking for a little while about how best to chunk up a gigantic fasta file for distribution across several machines (more on that later).  There are obviously several ways to do this - one of which would just be to sequentially read `x` number of fasta entries (say, 10,000 with some [fasta][1] [parser][2]) and split them off into a file.  Then, rinse and repeat.

However, when we're talking about larger files (let's assume something in the GB range), we may actually want to generate a tuple of start and stop positions within a file (such that each block contains ~ 1 MB of data), and then use this tuple of positions to spread file splitting duties among more than one thread/processor - by having each process grab a set of coordinates, extract a particular part of a file, and write that piece to an outfile.  Let's assume we're splitting something like the following:

    1. this is my first line\n
    2. this is my second line\n
    3. this is my third line\n

For this sort of data, we can take the approach discussed in the [widefinder][3] benchmarks.  Namely, we can write some code to seek through the file in 1 MB chunks, make sure the line we're on is actually a line, and record the start and end positions that split the file into 1 MB chunks/blocks.

However, fasta (and similar files like fastq) present an annoying challenge, by their very design... fasta files look like this:

    >fasta-sequence-number-one
    ATTTACCCTTTATTTGTCCAGTTGACGTTTTACTTTTATAGATAAATGTTTTTAAGAAGT
    TATTGGGCGTTGCTACGAGTGATTGGTAAATACCTTATTGTTTTACTATGTCATGAAGTG
    TGACGTACGTGTCATCCTATTTAAAACTTGTCAGTTGAATGTATCTGCATTCTTGGAGTT
    >fasta-sequence-number-two
    TGACGTACGTGTCATCCTATTTAAAACTTGTCAGTTGAATGTATCTGCATTCTTGGAGTT
    ATTTACCCTTTATTTGTCCAGTTGACGTTTTACTTTTATAGATAAATGTTTTTAAGAAGT
    TATTGGGCGTTGCTACGAGTGATTGGTAAATACCTTATTGTTTTACTATGTCATGAAGTG

What should be apparent, now, is the crux of the problem... the header line of a fasta file is followed by one, two, or many additional lines of sequence data - meaning that the header line (which begins with '>') and the trailing lines (which are not prepended with a symbol) are a *unit* that goes together.  IN other words, this fasta unit could be 2 lines long (1 header line; 1 sequence line) or 20,000 lines long (1 header line and 19,999 sequence lines).  Compounding the formatting nightmare is the additional fact that various fasta-formatting schemes will split the sequence portion of the read across an arbitrary length of characters, to make everything _pretty_.

Thus, the technique used in the widefinder benchmarks - assuming lines of a file are independent while splitting files into chunks of arbitrary size can cause grave problems when applied to DNA sequence data in fasta format:   using this method, we could inadvertently separate (1) the header from it's sequence, (2) the header and line one from lines 2...n, (3) the header and lines 2-3 from lines 4...n, etc., etc.

So, what we need is a method to chunk fasta files that is fast (e.g. ideally faster than sequential read-write operations); efficient (e.g. chunking the file into smaller pieces); and accurate (e.g. not splitting a fasta mid-record).

With that in mind, I offer up fasta_chunker.py, the first of a series of steps that will read a fasta file, returning a iterator of start and offset positions of a chunk that is _n_ (where default = 1) megabytes in size:

<script src="http://gist.github.com/609035.js"> </script>

[1]: http://www.biopython.org/wiki/SeqIO
[2]: http://pypi.python.org/pypi/pyfasta/
[3]: http://effbot.org/zone/wide-finder.htm
