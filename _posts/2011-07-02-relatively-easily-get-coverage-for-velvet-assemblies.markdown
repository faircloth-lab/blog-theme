---
title: (Relatively) Easily Get Coverage for Velvet Assemblies
layout: post
author: brant
date: 2011-07-02 11:15:59
category:
    - bioinformatics
---

You can get kmer coverage from contigs assembled by velvet by [parsing the kmer value from the output fasta header][1], but sometimes I want "actual" coverage for contigs or coverage across a specific subset of contigs.

Here is a way to do this relatively painlessly (requires that you first download and build the amos tools).

<script src="https://gist.github.com/1061484.js"> </script>

[1]:http://seqanswers.com/forums/showthread.php?t=6887
