---
layout: post
title: bulk sequence renaming with biopython
author: brant
categories:
    - bioinformatics
    - python
---

Sometimes large, genome-size files are not named like you want them to be.  Most of
them are large and it's easier to rename them programmatically.  Here is one
way to do that, using BioPython.

{% highlight python %}

from Bio import SeqIO

# create a dict to hold our new GI:names mapping, which looks like so, in 
# this case (from sheep)
#
# gi|289623201|gb|CM000885.1|	299839927	chr1
# gi|289623190|gb|CM000894.1|	94216033	 chr10
# gi|289623189|gb|CM000895.1|	67137890	 chr11
# gi|289623188|gb|CM000896.1|	86457535	 chr12
data = {}

# read in this file, split it into a dict
for line in open('oviAri1 copy.info','rU').readlines():
    line_split = line.strip('\n').split('\t')
    data[line_split[0]] = line_split[2]

# open a file for the output
output_file = open('new_oviAri1_seq.fa','w')

# create an iterable to hold the new data
new_seq = []

# iterate over seq, updating the name.  This is going to give us something like:
#
# >chr1
# 
for record in SeqIO.parse(open('oviAri1.fa','rU'),'fasta'):
    new_record_name = data[record.id]
    record.id = new_record_name
    record.name = ''
    record.description = ''
    new_seq.append(record)

# write the whole thing out
SeqIO.write(new_seq, output_file, 'fasta')
    
{% endhighlight %}
