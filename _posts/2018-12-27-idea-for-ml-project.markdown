---
layout: post
title: Idea for newbie ML project
description: Documenting my idea for a test ML project
categories: articles
date: 2018-12-27 07:53:07 -0800
tags: [machine-learning, fungi]
keywords: [ML, mushrooms]
image: shroom.jpg
---
So I have an idea about a nice introductory (as far as I know) machine learning problem to play with. It involves trying to create multiple models for different species for when is the best time to forage for wild mushrooms based on the weather.

I collected weather data in Nashville, TN for about a year while I was searching for mushrooms in the woods. I also have the images I took while I was in the woods. These timestamped images give me a date, and then I can prepend say, two weeks of weather data before the mushroom was found.

The weather data is not from directly where the mushrooms grow, but I think it's close enough to be able to potentially predict (given a similar weather pattern) another blooming of the mushroom. This is because for particular species, once you find a spot - that spot will continue to produce for as long as there is a food source (e.g. the log is large).

Anyway, I think the problem is extremely broad with many species. But, to make this project worthwhile and to try something new, let's pick one species, and one finding to see how this stuff works.

[![Inky Cap Mushrooms]({{site.root}}/assets/img/170420-inky.jpg)]()

Just one day later ...

[![Inky Cap Mushrooms day2]({{site.root}}/assets/img/170421-inky.jpg)]()

[![Inky Cap Mushrooms day2]({{site.root}}/assets/img/170421-inky-2.jpg)]()

Here you can see 1 day old (right) and 2 days old (left)
[![Inky Cap Mushrooms day2]({{site.root}}/assets/img/170421-inky-3.jpg)]()
