+++
content_img_path = "/images/20200921-surfacebook2.jpg"
date = 2020-09-24T22:00:00Z
draft = true
excerpt = "In January 2019 I prepared myself for the big jump as a freelancer and one of the first questions was \"Which laptop should I buy for my activity ?\", as I'd need one of my own.\n\nI wouldn't have thought I'd go to Windows, at that time."
layout = "post"
subtitle = ""
thumb_img_path = "/images/20200921-surfacebook2.jpg"
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

If you do not know, finding a laptop fully working with Linux is hard, especially when most powerful laptops have a discrete NVidia GPU alongside the Intel one (hybrid graphics called Optimus). In most cases, under Linux, Optimus isn't supported and either keeps the discrete GPU on, eating your battery, or makes it complicated to use it because of having to reload X server to switch to it.

After searching for weeks, I asked myself if I really wanted to limit myself to Linux. One option was Mac OS X, but there's no stylus-friendly laptop and I've got kind of a bad feeling with it UX wise, so that one's out. The other option was Windows, and Microsoft announced WSL years ago as well as Windows Terminal in the works.

All those moves from Microsoft appealed to my curiosity, so I wanted to see for myself what all of this is about : I ended up taking something from the Surface line, the Surface Book 2.

## Windows Subsystem for Linux

### The genesis

Windows Subsystem for Linux (WSL), in its first version, is simply a form of emulation, a bit like Cygwin but smarter and without binary re-linkage needed. This means that, in theory, _any_ native ELF64 binary does run in WSL, without any modification !

![](/images/20200921-winshellwsl.png)

In truth, though, it does not emulate advanced system call or kernel feature, like those needed for Docker (cgroups, namespaces, …). This didn't hamper me much, but being an emulation layer, although CPU performance was good, I/O were slow, like, _really slow_. This made WSL1 not that usable with Python, Scala or JavaScript projects in the end, being pretty heavy on I/Os.

_If you're curious about how WSL1 works under the hood, you can check out one of the official blog posts about it_ [_at Microsoft_](https://blogs.msdn.microsoft.com/wsl/2016/04/22/windows-subsystem-for-linux-overview/) _or_ [_the nice explanation from Jessie Frazzele_]( "https://blog.jessfraz.com/post/windows-for-linux-nerds/")_._

### WSL2, 100% better

After that, on May 2019, Microsoft announced they were working on a 2nd iteration of WSL, which would use a lightweight VM tightly integrated with Windows and would be soon available to Insiders community. 

I've switched to it as soon as it got on the Insiders channels, as I/O performance was announced to be way better, which it was, and made it actually possible to use it for development purpose, or, well, use it like any native Linux !

Now, since May 2020, it's available natively in the May 2020 Update of Windows 10.

## Installing WSL and a distro

Microsoft done a pretty nice job at packaging distributions : you've got on the store Ubuntu, Kali, Debian, Alpine, OpenSUSE… which are all one click away ! Install them, run them from the start menu then you're greeted with an invite asking the username and password you'd like.