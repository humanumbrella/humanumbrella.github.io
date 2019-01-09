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

Topology at my place is a little complicated. Have Google fiber and I'm connected via Ethernet directly into that router. I have another mesh router acting as a router on 10.0.0.1/24, and another set of routers acting as access points on the same 192.168.1.1/24. Suffice it to say there are 2 networks (10.* and 192.* ) and the printer is on one (10.* ) and my desktop is on the other (192.* ).

I thought I needed to give access to the 10.0.0.1/255 network via the fiber box - but that's not true (and there's no option to do that on the box). Instead the problem was solved by opening ports on the 10.0.0.1 router through to the Brother printer.

I could have put the printer in the DMZ since it's already inside another NAT but I couldn't find that option on first pass looking through the settings, but I didn't look too hard. After searching, I found some links that showed which ports were needed for this or that to work on a Brother wireless printer through a firewall and found a few ports mentioned. I tried all of these and had mixed results.

* 137
* 161
* 9100
* 54925
* 54926

E.g. when I tried to search for the printer automatically on my desktop (192.* ), it failed. But I could supply the 192 IP of the mesh router directly and Windows would recognize the Brother wireless printer. The rest of the prompts were familiar:  tell me that I already had the driver as if things were working properly, ask if I want to share, ask if I want to print a test page. I got excited because I thought I was done. However, while the printer would add just fine,  nothing would print. Bummer.

I started digging a bit more and found something interesting under Printer Properties > Ports > Standard TCP/IP Port (this is the port that was added via the wizard).

[![Windows 10 Printer Management]({{site.root}}/assets/img/190103-brother-manage.png)]()

If I click Configure Port here I see that there are two options for the print protocol:  Raw and LPR. LPR is selected by default. Below that, I see port number 515 as the one used for LPR.  *BINGO!*

[![Printer Port Settings]({{site.root}}/assets/img/190103-brother.png)]()

I added that port (515) to the 10.0.0.1 router for the printer's IP and then tried to print again and things worked just fine.

* 515

So if that helps anyone else, cool.

Sidenote -- I got excited and thought I'd fixed the problem earlier but it turned out to just be a coincidence. It turns out that the Raw port is 9100, and whatever you send to this port will print. I didn't know that at the time and I tried to hit IP:9100 in the browser and the GET request printed out. I didn't make the connection until I went over and saw what printed out, haha.

[![printed GET request]({{site.root}}/assets/img/190103-lol.jpg)]()

You could have some fun with this... but I'll leave it at that. I removed 9100 from port forwarding.
