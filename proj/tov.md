---
layout: default
categories: Projects
youtubeId: kAz_E1gjOZM
---

<h4>2012 - Transit of Venus</h4>

I was tasked with getting the local university observatory [The Morehead Observatory](https://skynet.unc.edu/guestnight/). (Side note: I also made that website.) capable of observing the sun. For those of you that don't know - the sun is bright... really bright. You need to eliminate almost all of the light hitting the telescope if you want to observe the sun with it. NOTE: don't try this unless you know what you're doing.

I ended up going with a company called Thousand Oaks Optical to purchase the full aperature filter to put over the 24" telescope's Optical Tube Assembly (OTA). The lightweight filter didn't require rebalancing the telescope.  I don't see the model I ordered on the site for a 24" telescope anymore (RG-15750A) but it looked like:

[![Solar Filter]({{site.root}}/assets/img/tov/solar-filter.png)](http://thousandoaksoptical.com/shop/solar-filters/full-aperture-solarlite/)

I also ended up using an inline H-alpha filter(I believe) to double down on filtering the light.

Finally, the goal was to set up a streaming website and create two python scripts to
1) take exposures with the astronomical camera (Apogee U47)
2) upload any newly saved files in the image directory to a server so the stream would show the latest image.

I tested these scripts extensively and got it working such that I only had to entertain the guests and babysit a little instead of trying to do anything with the imaging process on the day of the transit.  

I wasn't prepared for how many people showed up though, hah. It was a little stressful in the moment, especially when the clouds rolled in and we lost sight of the event. We got a few more images before the sun set below the elevation limit of the telescope. However, I was able to capture many images of the event, and afterward I created a video and uploaded to YouTube.

{% include yt.html id=page.youtubeId %}

* [Transit of Venus Video Link](https://www.youtube.com/watch?v=kAz_E1gjOZM) < This is the same as above.

* [WRAL Newscast](https://www.wral.com/weather/video/11165110/) < This is why so many people showed up.

* [Morehead Observatory News Release](http://moreheadplanetarium.org/news/releases/transit-of-venus) < This is why so many people showed up.

  * [pdf backup](#)

* [Morehead Observatory Blog Post](http://moreheadplanetarium.org/news/releases/rare-but-not-impossible-your-last-chance-to-see-a-transit-of-venus-june-5-2012) < This is why so many people showed up.
  * [pdf backup](#)
