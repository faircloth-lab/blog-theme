---
title: casting a numpy array of strings to int
layout: post
date: 2010-12-13 09:27:59
author: brant
categories:
    - python
    - bioinformatics
---

Sometimes you need to create an array from a string, and then you need to cast the array (which is of string type) into something more useful like `int` - for example when reading PHRED quality scores from a file.  You can do this several ways, often using a list comprehension, perhaps like so:

{% highlight python %}

import numpy

s = '40 40 40 40 40'
sl = s.rstrip().split(' ')
si = [int(elem) for elem in sl]
sa = numpy.array(si)

{% endhighlight %}

But, this is kludgy and there is a more efficient way:

{% highlight python %}

import numpy

s = '40 40 40 40 40'
sa = numpy.array(s.rstrip().split(' ')).astype(int)

{% endhighlight %}
