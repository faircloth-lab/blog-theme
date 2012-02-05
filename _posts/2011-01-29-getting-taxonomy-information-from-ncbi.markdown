---
title: Getting Taxonomy Information from NCBI
layout: post
date: 2011-01-29 11:01:51
author: brant
categories:
    - bioinformatics
    - python
---

Sometimes you need to get [taxonomy][1] information from NCBI, assuming that you know a particular species name.  If you only are working with one species, then this is not very hard.  When it comes to working with multiple species, however, attempting such a task using the web-frontend would be painful.  Luckily, you can use the NCBI [eutils][2] to make the process somewhat easier, particularly when combined with [BioPython][3]:

<script src="https://gist.github.com/802094.js"> </script>

Several things to remember here:

 * you must add *your* email address as the `Entrez.email` attribute
 * you should not request info. for more than 100 species during the work-day (see [eutils restrictions][4])
 * you will need to make changes to get this to work with your particular input

[1]:http://www.ncbi.nlm.nih.gov/Taxonomy/
[2]:http://eutils.ncbi.nlm.nih.gov/
[3]:http://biopython.org/wiki/Biopython
[4]:http://eutils.ncbi.nlm.nih.gov/entrez/query/static/eutils_help.html#UserSystemRequirements
