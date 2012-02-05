---
layout: post
title: removing a file/directory permanently from git
author: brant
categories:
    - git
---

I'm not entirely sure how many times I've needed this or how many times I've dug it up only to forget it later, but here is how to permanently remove a file or directory from a git repository.  This comes by way of [Dalibor Nasevic's site](http://dalibornasevic.com/posts/2-permanently-remove-files-and-folders-from-a-git-repository).

{% highlight bash %}
# blackhole the content
git filter-branch --tree-filter 'rm -rf my/folder' HEAD

# force the update
git push origin master --force

{% endhighlight %}


If you like to read up on these things, you can find more information in [Chapter 6](http://progit.org/book/ch6-4.html) of the [ProGit](http://progit.org/) book.