---
layout: post
title: restriction batches and biopython
author: brant
categories:
    - bioinformatics
    - python
---

Sometimes, you need to get an idea of the sizes of fragments you are likely to get from a sequence cut with a *batch* of restriction enzymes.  Here's how you would do that virtually.  

This might be useful when you have no idea of the likely size of resulting fragments, but you'd like to have some idea - before you order a lot of enzymes.

{% highlight python %}

# subset record #

test=seq[0:10000]

# take a look at the common restriction enzymes
Restriction.CommOnly

# do a restriction batch analysis on our test sequence with ALL common
# enzymes
Ana = Restriction.Analysis(Restriction.CommOnly, test.seq, linear=True)

# look that the enzymes that cut (BLUNT) the test sequence in more than #
# 10 spots
results = []
for r in Ana.blunt():
    if len(Ana.blunt()[r]) > 10:
        results.append([r, len(Ana.blunt()[r])])

# sort by the 2nd element of the list
for r in sorted(results, key=lambda record: record[1]):
    print r[0], r[1]
    
# or you can do this:
from operator import itemgetter
for r in sorted(results, key=itemgetter(1)):
    print r[0], r[1]
    
{% endhighlight %}
