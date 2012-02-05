---
layout: post
author: brant
date: 2011-11-05 10:58:59
categories:
    - bioinformatics
    - programming
---

I'm working on [some
code](http://www.github.com/faircloth-lab/demuxipy/) that I initially
wrote to write results to a [mysql](http://www.mysql.com/) database.  I
chose mysql because it supports concurrent writes, and this program
processess data in parallel having each process write it's results to
the database when a given task is complete.  This was a lazy way of
getting the data stored relatively quickly and easily (let's forget
about the overhead of any given process for a moment).  That said,
having mysql as a dependency of your code is a bummer, particularly for
folks with one-off tasks who don't have the time or patience to install
and configure mysqld.  Additionally, portability of mysql data, while
relatively easy using dumpfiles, is not as useful as several other
options.

Because I'm working in [Python](http://www.python.org/), I can also use
the exceptional [sqlite3](http://docs.python.org/library/sqlite3.html)
module.  It offers most of the database functions that i want/need, it's
generally available on any platform, it is open source, and databases
are portable between machines.

However, sqlite3 does not support concurrent writes - meaning that I
need a general way to process my data in parallel while writing my
results to a database using a single process.  This basically translates
to needing a multiprocessing model having multiple producers and a
single consumer - something with few examples available on the
interwebs.

So, after a bit of playing around, here's some test code that does just
that:

<script src="https://gist.github.com/1255715.js"> </script>
