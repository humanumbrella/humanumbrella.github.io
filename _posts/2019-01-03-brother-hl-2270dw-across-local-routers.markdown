---
layout: post
title: Brother HL-2270DW across local routers
description: Been meaning to set this up for a while, thought I needed access to the fiber box.
categories: articles
date: 2019-01-03 14:51:27 -0800
tags: [wireless printer, troubleshooting]
keywords: [networking, printer]
image: bro.jpg
---

Topology at my place is a little complicated. Have fiber and I'm piped into it directly. Have another mesh router acting as a router, and another set of routers acting as access points. Suffice it to say there are 2 networks and the printer is on one and my desktop is on another.

I thought I needed to give access to the 10.0.0.1/255 network via the fiber box - but that's not true (and there's no option to do that on the box). Instead the problem was solved by opening ports on the 10.0.0.1 router through to the Brother printer.

I could have made it DMZ since it's already inside another NAT but I couldn't find that option on first pass, didn't look too hard. I found some links that showed which ports were needed for this or that on a Brother wireless printer and it showed a few. I tried all of these and had strange results.

* 137
* 161
* 9100
* 54925
* 54926

E.g. when I tried to search for the printer automatically on my desktop (192.*), it failed. But I could supply the IP of the 192 addy of the mesh router directly, Windows would recognize the Brother wireless printer and say that I already had the driver as if things were working properly. I got excited but then frustrated because the printer would add just fine, but nothing would print.

I started digging a bit more and found under Printer Properties > Ports > Standard TCP/IP Port (that was added via the wizard). 

[![Windows 10 Printer Management]({{site.root}}/assets/img/190103-brother-manage.png)]()

If I click Configure Port here I see that there are two options for the print protocol:  Raw and LPR.  Below that, I see port number 515 as the one used for LPR (which is selected by default).  *BINGO!*

[![Printer Port Settings]({{site.root}}/assets/img/190103-brother.png)]()

I added that port to the router (515) and then tried to print again and things worked great. So if that helps anyone else, cool.

* 515

Sidenote -- I got excited and thought I'd fixed the problem earlier but it turned out to just be a coincidence. It turns out that the Raw port is 9100, and whatever you send to this port will print. I didn't know that at the time and I tried to hit IP:9100 in the browser and the GET request printed out. I didn't make the connection until I went over and saw what printed out, haha.

You could have some fun with this... but I'll leave it at that. I removed 9100 from port forwarding.