---
layout: post
title: Script for New Post
description: Found and then edited a script to set up a new post builder
categories: articles
date: 2018-12-21 09:25:22 -08:00
tags: [automation, bash script]
keywords: [new-post]
image: bg.png
---
OK cool, that seems to work now.

So, I'm using the basic Terminal in Ubuntu 18.10 as I haven't installed anything extra or fancier. I wanted to add a function to my ~/.bashrc so that I can call it to make a new post instead of copy-pasting the post and changing all of the variables each time, especially the datetime.

I searched for a bit and then found this page:  [How to Implement a Bash Script to Create New Posts in Jekyll](http://joshuasoileau.com/articles/2016/06/08/how-to-implement-a-bash-script-to-create-new-posts-in-jekyll.html)

This has a lot of good info here, except they are using zsh so I needed to tweak it a bit for bash.

The original script was from
