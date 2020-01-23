---
layout: post
title: MacOS Extended Encryption Bug
description: lost data because of this
categories: articles
date: 2020-01-22 13:29:22 -0800
tags: [macos, encryption, hfs+, bugs]
---
I've lost data over this and I thought I just forgot the password - definitely did not.

---

## The first bug is that there is no way to see the hint when you incorrectly enter the password.

This has to be a known bug - it's unbelievable though. I did some searching and saw others have the same problem.
It looks like in their hasty fix to the "hint just shows your password" bug - they just stopped showing the hint at all. That sucks.

---
## The second bug is about unknowingly choosing an invalid password.

To recreate:

* Erase your drive and set it up with MacOS Extended (Journaled, Encrypted)

* Choose a password "a   1" with spaces in your password.

* Eject and unplug the drive

* Plug it back in and enter `a   1` to see that this fails.

maybe I'll put some screenshots in here later tonight.

Cheers!
