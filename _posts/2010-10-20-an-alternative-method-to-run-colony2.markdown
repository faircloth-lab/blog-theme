---
title: an alternative method to run colony2
layout: post
author: brant
categories:
     - bioinformatics
---

For parentage/sibship inference, I've started using [Colony2][1] and
[MasterBayes][2] in place of the venerable [Cervus][3].  However, one
(of two\*) things that is annoying about Colony2 are the scripts for
running the program that are available on "alternative" operating
systems (e.g. not Windows).  These scripts are provided as part of the
[rcolony][4] package.

Because the script to run colony through [R][5] (aka `run.colony()`) was 
causing me problems and because I'd rather do pretty much anything than hack on
R code, I wrote some [Python][6] code to accomplish a function similar to 
`run.colony()` but that operates outside of R.  Here goes:

<script src="http://gist.github.com/637381.js"> </script>

\* The second thing that can be a downer when using Colony on alternative 
operating systems is the formatting of the input file.  I've got something in
the works, there, too... it's just not at all on the front burner

[1]:http://www.zsl.org/science/research/software/colony,1154,AR.html
[2]:http://cran.r-project.org/web/packages/MasterBayes/index.html
[3]:http://www.fieldgenetics.com/pages/aboutCervus_Overview.jsp
[4]:http://r-forge.r-project.org/projects/rcolony/
[5]:http://www.r-project.org/
[6]:http://www.python.org
