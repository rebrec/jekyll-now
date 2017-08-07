---
layout: post
title: "SHA2017 CTF suspectfile1"
categories: CTF
---

## Description
Suspect File1(100) - 63 solves

## Needed Tools
- _gdb_ 
- _peda_ : gdb plugin available [here](http://github.com/longld/peda) (also check the Blackhat 2012 presentation of [PEDA](http://ropshell.com/peda/Linux_Interactive_Exploit_Development_with_GDB_and_PEDA_Slides.pdf))


## Walkthrough

After getting the challenge archive file available [here]({{ site.url }}/downloads/suspectfile1.tgz), we first uncompress it with `tar zxvf suspectfile1.tgz`, which create a new file named _100_.

Next we check what kind of file we are facing with a `file 100`:

![]({{ site.url }}/images/CTF-SHA2017-suspectfile1-20170808-000239.png)

We then run the binary to see what seems to happend


![]({{ site.url }}/images/CTF-SHA2017-suspectfile1-20170808-000556.png)

It's clearly visible that this binary do not try to read user input after being launched.
There must be some commandline parameter processing.

Let's now try to have a look at it withing gdb : `gdb ./100`

Typing `pdisass main` display the disassembled version of the main function.

We can see that the main is quite long (more than 5000 instructions long)


![]({{ site.url }}/images/CTF-SHA2017-suspectfile1-20170808-003447.png)

At the end of this function, we can observe a function named "Sorry". We can guess it is responsible for displaying the "bad boy" message ("Sorry").

We set a breakpoint at this function start address to see the call stack :

`break sorry`

Then we run the program with some parameter :
`r some_parameter`

The breakpoint is reached as we can see below
![]({{ site.url }}/images/CTF-SHA2017-suspectfile1-20170808-003447.png)


Not much to say, we are lucky enough to see the flag at $esp+4


