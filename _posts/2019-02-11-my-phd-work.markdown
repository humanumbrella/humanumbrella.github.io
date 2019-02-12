---
layout: post
title: My Unfinished Astrophysics PhD
description: Run through of hementation of the work
categories: articles
date: 2019-02-11 13:29:22 -0800
tags: [phd project, polarimeter, arduino, maximDL]
---
So this morning I had an interview and was asked to go over some coding stuff I've worked on before. I chose to go over my PhD project at a high level and thought to myself that I should have a page I can point to for this work. Welcome, you're reading it.

I was busy coaching this weekend so I planned to use a couple hours before the scheduled 10am interview to get everything set up and running again. I was a bit nervous that I'd have enough time to get everything up and running again since it's been so long, but things worked out just fine. I guess I remember enough and things work well enough.

I'm likely going to make a project page that points to this blog post. The stuff I was working on was always interesting, mostly very cool, and sometimes frustrating. Let's begin.

---

## A bit about the motivation

Why do we want to build this instrument in the first place? The tldr version of that is:  theorists predict certain polarization signatures (properties) for early time light that is headed our way coming from Gamma Ray Bursts (GRBs). If we can get imaging data early enough on a GRB (very short delay from event > imaging, something Skynet, the global network of robotic telescopes is very good at...) and also acquire polariation data from that early time - we can help constrain theoretical models by providing the data necessary to confirm, constrain, or negate several hypotheses about the underlying mechanism at the heart of the explosion. E.g. what is actually going on?

There is of course some noise in this because this package of light on its way to us has been through a lot on its journey, some of which could have affected the polarization signature. However, we're simplifying that out of our thinking at this point.

---
## This wasn't the first rodeo

> _In fact, the name of the telescopes ["PROMPT"](https://en.wikipedia.org/wiki/PROMPT_Telescopes) actually includes polarimetry in the acronym._

This was the **second attempt** to build an instrument capable of measuring real time polarization data from an active Gamma Ray Burst (GRB). The first version of the instrument had some limitations we were trying to overcome. First and foremost the limitation was an all-or-nothing usage of the telescope. This means that acquiring non-polarization data required a hands-on (physical) change to accomplish either by replacing the equipment on a maintenance trip or by asking the local workers to remove and replace the instrument. Not ideal to require hands-on changes to get out of polarization mode. There's a much higher demand for imaging than there is for polarization imaging. :+1:

Secondly, the field of view for the image was drastically reduced from the already small 10 arcminutes, and there were regions of the image necessary to discard because of contamination by the optical elements.

{% include image.html
            img="/assets/img/phd/motivation.png"
            title="Polarimeter v1"
            caption="Polarimeter v1" %}

The green highlighted areas were good places to acquire data, and the blue highlighted regions here show matched stars. Finally, the red highlighted areas are to be avoided because of optical distortions.

{% include image.html
            img="/assets/img/phd/prism.png"
            title="Wollaston + Fresnel Prism"
            caption="(NOTE:  V and H components are coming out of the same face of the cube.)" %}

You can see also how the cube splits the light into its polarized components. If the incoming light happens to be aligned to this cube then great - you're done, but it's likely not aligned. So there has to be a rotation of the entire setup such that you fully sample the polarization space.

Now imagine increasing the angle of separation between the two components of the light to 90 degrees and adding a second, orthogonal camera. That's what I was attempting to make.

One huge benefit, unrealized by me until later was RC design allowing focus to be achieved by secondary focuser instead of trying to move your entire instrument package to achieve focus on a fixed backplane distance focal plane.


## A v2.0 design (caveat: fixed backplane distance!)

some images and thoughts here.


## Now we have a hardware design

Definitely glossing over how difficult this was to get everything situated. The biggest problem being that the telescope and imaging equipment was already installed in Chile and was in use every night. I did not have a duplicate of all of the hardware locally which was a terrible idea.

I needed to use SolidWorks and drafting skills to interface with the guys in the machine shop to custom build the aluminmum scaffolding we needed in order to fit all of these components together. Measure twice cut once.

A significant amount of work went into getting the physical hardware connections stabilized and connecting. Custom pieces needed to be manufacturered because of the complications involved with fitting everything into the backplane distance. Getting proper screws and making sure there the light path is unimpinged and finally that the device can move back and forth inside without also interfering was quite a difficult task, and I made many mistakes.

## Moving on to software.

There are levels here. From arduino and motor controllers, to simultaneously imaging with both cameras using commercial software, and finally to computing a polarization measurement for the entire frame using image analysis tools.

### Step 1. Arduino software package

Arduino UNO + Adafruit Motor Driver board, with an added bank of pins for extra grounds for all of the limit switches. 

The code is open sourced, and you can find it on my [GitHub](https://github.com/humanumbrella/ArduinoPolarimeter). The essence of this code is: set up all of the pins and settings in the setup ... and like all of the autonomous, meant-to-be-remote software in the group - it will not work unless it knows where it is, meaning you need to issue a *HOME* command if the device has been rebooted or has lost its state. We do not want to be issuing moving commands if we do not know where things are situated.

## What did I learn
A lot. How to put things together - how to push beyond "that's not possible" to "here's how I'll do it." Ask for help. I did not ask for help, and I got buried under the amount of work involved in this project. I accomplished a great deal but ultimately did not complete the necessary amount of work to graduate. I completed all of the requirements to graduate except perform novel science with the instrument because that required staying on the mountain for an extended period of time waiting for GRB's to occur. I don't have regrets, life moves on. I don't think I was in the right place for this work, and I don't think the incentives lined up properly for my advisor to push me out into the world rather than keep me around. I place no blame on anyone. I was simply ready to move my life in a different direction.

Cheers!