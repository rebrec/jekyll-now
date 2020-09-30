---
layout: post
title: Presentation of Hurry (The IT admin's companion)
categories: Tool
published: true
---

## Release of Hurry
Hurry is an Opensource tool designed for IT professionals for doing repetitive tasks such as remote support tasks.

To find download links, just go at [the end of this article](#download).


## Why Hurry ?
Before talking about Hurry, let me explains why I have created it.

I have done Linux and Windows administration over the last 20 years. During this time, I often needed to create custom scripts to fix things for the helpdesk team. I also sometimes created one-liners to ease doing some repetitive task on many computers or servers.

After coding, I always had to teach my collaborators how to use my scripts, how to run that specific script on this specific computer.

All this has never been the fun part, as doing repetitive tasks is always boring, a source of mistakes, and time-consuming.

I was looking for an opensource tool that allows me to **offer an easy way to use my scripts** and one-liners to *support users* through some **user interface** with **menu** and so on.
 
I found a few basic solutions but was also facing another problem: have the ability to run scripts against devices referenced from different part of the Information System:

- a server list from a Cloud Provider,
- a help desk ticketing system ([GLPI](https://glpi-project.org/)),
- a simple host file storing a list of servers for an old application,
- a list of VM from vCenter,
- etc.

I ending creating my own tool and today I share it with you and hope it will ease your daily IT life.


## Hurry to the rescue

Hurry was designed to do graphically what experts do from the command line.

To accomplish this, Hurry **spawns shells** in the background (*bash*, *cmd*, and *Powershell* are currently supported but other interactive shells can be added quite easily).

It simply "type" commands for you, into the shell:

- When you search a user or a computer from a specific data source, Hurry simply type powershell commands. If you know how to search for some data in Powershell, then letting Hurry do it graphically is as easy as writing a small plugin of a few lines of code.
- When you run a command against a specific search result, Hurry simply run a predefined command in the desired shell. It just does string interpolation so that the command you run can use your search result's properties (e.g: Hostname, Username, IP Address, Asset Tag, Hypervisor, etc.)

Shell's output can be viewed from a dedicated pane to either debug, or see how Hurry does it's stuff.

Hurry was designed with a few concepts in mind:

- _Being cross-platform_: I love use both Windows and Linux. I would love one day to be able to manage all my Windows systems from a Linux workstation. Having a cross-platform tool for this task is one step in the direction of this goal (and who knows, maybe in the future, support teams will use Hurry on Linux workstations to do remote tasks on Windows systems).

- _Being extensible_: I have created a plugin system that quickly allows me to add new data sources on which I can apply commands. So when I need to interact with devices from a new Cloud Provider, I can add to my existing data source list very quickly. This plugin system has a final goal: be shareable so that what I do for my needs can be used as-is for other Hurry users.

## How does it looks

Here it is !

![](https://raw.githubusercontent.com/rebrec/hurry/master/docs/hurry_vSphere_result_ping.png)

On this screenshot you can see the search box at the top with the *vSphere* **Datasource** selected. After clicking the **search button**, you get **results** (green are the one who answer ping requests).

By click on one of the **results**, you have access to a **contextual menu** where you can find **actions** to performs against this **search result**.

The UI is quite basic and would need a real relooking but I am not a web designer. I hope that some folks will be glad to give it a nice looking if the project gets popular.

At least, it does what it is designed to: let others use my work from a GUI. I also use it sometimes since it can be faster to use it than type some stuff in a command line.

Check out [the GUI Overview](https://github.com/rebrec/hurry/blob/master/docs/GUI_Overview.md) for **more screenshots**. 

## How to use it

### Simple use case

Let's imagine that Peter has a problem with its workstation. He need remote support. 

#### The traditional way

I run my favorite **remote support** tool (*VNC Viewer*) against it's hostname but peter doesn't know it... so, I first need to find it: I connect to my IT Asset Management application (mine is [GLPI](https://glpi-project.org/)). I search for peter's computer, copy its hostname and paste it into VNC Viewer so I can start doing remote assist.

#### The Hurry's way

Now, let's try to do the same thing with Hurry: 

There is a search box in the middle of Hurry's area. I type the same **search keyword** I did previously and hit Enter. This time, Hurry will create an API call to my IT Asset Management application and will display the results below.

I select the proper result (the one with Peter's hostname): a **menu** is displayed where I can **select the action I need**: *VNC Connect*. Hurry will start VNC Viewer and give the proper hostname parameter from the selected result. That's it.

An interesting addition is the **History** feature of Hurry:

Each time a run a command against a specific device, Hurry stores it within an history tab.

From this tab I can, for each command:

- Run again the same command on the same host
- Run the same command on another host
- Display the same host again so I can perform another action on it.

From time to time, if you often use the same actions or the same devices, you will be able to do them even faster from the **History Pane**

## What's next

Hurry is still under active development. I am looking for help on the UI design part and also on feature addition. A lot of bug fixes need also to be done and the initial configuration process needs improvements.

If you have ideas, troubles using it or any questions about it, feel free to :

- Open an [Issue](https://github.com/rebrec/hurry/issues/new/choose)
- Get in touch using [discord](https://discord.gg/7cEWVvC) and be part of the community

{: #download }

More details can be found on [the project's page](https://github.com/rebrec/hurry/).

**Download The Latest release** from [here](https://github.com/rebrec/hurry/releases/latest).
