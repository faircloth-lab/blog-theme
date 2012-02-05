---
layout: post
title: virtual restriction digests with biopython
author: brant
categories:
    - bioinformatics
    - python
---

The other day, I needed to get an approximate idea of the size of fragments 
returned from a particular restriction digest.  Generally, this sort of
info is available on the intertubes, but I was not finding terribly much.

So, I decided to do a quick, virtual restriction digest using Python, BioPython,
and numpy for some summary stats (in this case I "digested" chr1 of _Arabidopsis thaliana_):

{% highlight python %}

from Bio import SeqIO
seq = SeqIO.read(open('chr1.fas','rU'),'fasta')

len(seq)
30427671

from Bio import Restriction
Restriction.HindIII.search(seq.seq)
sites = Restriction.HindIII.search(seq.seq)

# get the number of fragments produced by cutting
len(sites)
16963

# sort the sites by position (just to be sure)
sites.sort()

# get the distance between sites
dist = [sites[r] - sites[r-1] for r in xrange(1,len(sites))]

# generate some summary stats
import numpy
import math
dist_a = numpy.array(dist)

# mean fragment size
numpy.mean(dist_a)
1793.6787525056006

# 95 % Confidence invterval around mean
1.96 * numpy.std(dist_a, ddof=1)/math.sqrt(len(dist_a))
33.572399955020472

# get number of fragments btw. 100 and 500 bp - this could likely use some #
# cleanup, but I was in a hurry
less_than_five_bool    = dist_a < 500
less_than_five         = dist_a[less_than_five_bool]
greater_than_one_bool  = less_than_five > 100
one_to_five_hundred_bp = less_than_five[greater_than_one_bool]

{% endhighlight %}