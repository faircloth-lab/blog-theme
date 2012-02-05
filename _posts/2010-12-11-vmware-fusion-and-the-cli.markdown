---
title: vmware fusion and the cli
layout: post
date: 2010-12-11
author: brant
categories:
    - osx
    - virtualization
---

Today, I needed to shutdown an instance running on [VMware Fusion](http://www.vmware.com/products/fusion/) so i could free up some resources.  Normally, this is an easy task because I'm sitting at the machine in question.  But, I ran out of my office the other day and forgot to shutdown the instance.  So, i needed to quit it remotely.  Digging into things a bit, I found `vmrun`, which is the CLI to VMware Fusion.  Running `vmrun` without any options show how to make it work, and shutting down a VM is as simple as:

{% highlight bash %}
/Library/Application\ Support/VMware\ Fusion/vmrun stop \
"/Volumes/Data2/VM/Fedora 64-bit.vmwarevm/Fedora 64-bit.vmx" soft
{% endhighlight %}