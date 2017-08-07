---
layout: post
title: "SHA2017 CTF suspectfile1"
categories: CTF
---

## Description
Suspect File1(100) - 63 solves

## Needed Tools
- _gdb_ 
- _peda_ gdb plugin available [here](http://github.com/longld/peda)


## Walkthrough

After getting the challenge archive file available [here]({{ site.url }}/downloads/suspectfile1.tgz), we first uncompress it with `tar zxvf suspectfile1.tgz`, which create a new file named _100_.

Next we check what kind of file we are facing with a `file 100`:

![]({{ site.url }}/images/CTF-SHA2017-suspectfile1-20170808-000239.png)

We then run the binary to see what seems to happend


![]({{ site.url }}/images/CTF-SHA2016-suspectfile1-20170808-000239.png)

It's clearly visible that this binary do not try to read user input after being launched.
There must be some commandline parameter processing.

Let's now try to have a look at it withing gdb :


![]({{ site.url }}/images/CTF-SHA2017-suspectfile1-20170808-000239.png)



![]({{ site.url }}/images/)
![]({{ site.url }}/images/)
![]({{ site.url }}/images/)
![]({{ site.url }}/images/)
![]({{ site.url }}/images/)
![]({{ site.url }}/images/)
![]({{ site.url }}/images/)
![]({{ site.url }}/images/)
![]({{ site.url }}/images/)
![]({{ site.url }}/images/)
![]({{ site.url }}/images/)
![]({{ site.url }}/images/)
![]({{ site.url }}/images/)
![]({{ site.url }}/images/)
![]({{ site.url }}/images/)
![]({{ site.url }}/images/)
![]({{ site.url }}/images/)
![]({{ site.url }}/images/)
![]({{ site.url }}/images/)


