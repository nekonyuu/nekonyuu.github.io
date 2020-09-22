+++
content_img_path = "/images/20200921-surfacebook2.png"
date = 2020-09-24T22:00:00Z
draft = true
excerpt = ""
layout = "post"
subtitle = ""
thumb_img_path = "/images/20200921-surfacebook2.png"
title = "Developer Life with WSL"

+++
## Why did I leave Linux Desktop

In January 2019 I prepared myself for the big jump as a freelancer and one of the first questions was "Which laptop should I buy for my activity ?", as I'd need one of my own.

My list of requirements was a bit high :

* nice battery life (over 8h under IntelliJ)
* good amount of RAM ;
* have an NVidia GPU for CUDA usage ;
* stylus friendly (to be actually able to draw things and take note on it) ;
* Under 2.5 kilograms ;
* Linux-compatible.

If you do not know, finding a laptop fully working with Linux is hard, especially when most powerful laptops have a discrete NVidia GPU alongside the Intel one (mechanism called Nvidia Optimus). In most cases, the Nvidia GPU isn't supported and stays on, eating your battery.

After searching for weeks, I asked myself if I really wanted to limit myself to Linux. One option was Mac OS X, but there's no stylus-friendly laptop, so that one's out. The other option was Windows, and Microsoft announced WSL years ago as well as Windows Terminal in the works.

All those moves from Microsoft appealed to my curiosity, so I wanted to see for myself what all of this is about : I ended up taking something from the Surface line, the Surface Book 2.

## Windows Subsystem for Linux

Windows Subsystem for Linux (WSL), in its first version, is simply a form of emulation, a bit like Cygwin but smarter and without rebuild needed. This means _any_ ELF64 binary does run in WSL, without any modification !

![](/images/2020-09-22.png)

But "any ELF64 binary" is a bit of an exaggeration : in truth, this does work till you need any system call or kernel feature, like those needed for Docker (cgroups, namespaces, …). This shouldn't scare you, as actually you barely use/need any of those if you're under Linux/MacOS, as we'll see next in my journey to working on Windows with WSL !

In order to satisfy those of you who want to know how it works under, you can check out one of the official blog posts about it [at Microsoft](https://blogs.msdn.microsoft.com/wsl/2016/04/22/windows-subsystem-for-linux-overview/) or [the nice explanation from Jessie Frazzele]( "https://blog.jessfraz.com/post/windows-for-linux-nerds/").

## Installing WSL and a distro

Microsoft done a pretty nice job at packaging distributions : you've got on the store Ubuntu, Kali, Debian, Alpine, OpenSUSE… which are all one click away ! Install them, run them from the start menu then you're greeted with an invite asking the username and password you'd like.