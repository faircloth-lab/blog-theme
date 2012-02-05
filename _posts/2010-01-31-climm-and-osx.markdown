---
layout: post
categories:
    - random
---

I've been looking for a CLI chat program that works pretty well.  After digging around for some time, I came across [climm][1].  climm has a lot of dependencies, including:

* tcl
* iksemel
* libgcrypt
* openssl
* pkgconfig
* gloox
* gnutls
* libotr
* autoconf
* automake
* libtool

You can get most of these from [macports][2] (if you install libgcrypt, you should pull down pretty much everything).  You will still need to `port install libotr` and you will also need to download the source for gloox (1.0) as the version at macports fails to build.

Once all of that is done, get the source for climm, patch the source of configure.ac with the patch referenced below ([climm-r2826.patch](http://gist.github.com/331172)) and `rm configure`.  

You also need to patch  `climm-0.7/src/io/io_dns.c` replacing 

    #include <arpa/nameser.h> 

with 

    #include <arpa/nameser_compat.h>

See [climm-nameser_compat.patch](http://gist.github.com/331171).  Now, you want to 

    make clean
    ./configure
    make
    sudo make install

Follow the instructions from the wizard.  climm initially segfaulted after finishing the wizard, but appears to be "fine" on a restart.
 
Update:  I should have mentioned that these changes were made to the 0.7.0 source distribution.

[1]: http://www.climm.org/
[2]: http://www.macports.org/