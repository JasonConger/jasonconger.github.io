---
title: IoT and Flying Ponies at .conf 2015
author: jason
excerpt: One of the coolest demos I witnessed at Splunk .conf 2015 was the one by Nate McKervy. The reasons this demo was so cool is 1) it was live, 2) it involved audience participation, and 3) it involved shooting stuffed ponies out of an air cannon.
layout: post
thumbnail-img: /assets/img/2015/10/15/buttercup_2x_1x.jpg
share-img: /assets/img/2015/10/15/buttercup_2x_1x.jpg
categories:
  - Splunk
  - Splunk Blog
tags:
  - Splunk
---
{: .box-note}
Originally posted on the Splunk official blog: [https://www.splunk.com/en_us/blog/tips-and-tricks/iot-and-flying-ponies-at-conf-2015.html](https://www.splunk.com/en_us/blog/tips-and-tricks/iot-and-flying-ponies-at-conf-2015.html){:target="_blank"}

One of the coolest demos I witnessed at Splunk .conf 2015 was the one by [Nate McKervy](https://www.splunk.com/en_us/blog/author/nmckervey.html){:target="_blank"}. The reasons this demo was so cool is 1) it was live, 2) it involved audience participation, and 3) it involved shooting stuffed ponies out of an air cannon. This article will explain a little more of what was going on under the covers.

Skip to 19:18 for the demo
<iframe class="youtube-player" type="text/html" width="640" height="390" src="//www.youtube.com/embed/hrWpTFYhTtk?version=3&amp;rel=1&amp;fs=1&amp;showsearch=0&amp;showinfo=1&amp;iv_load_policy=1&amp;wmode=transparent" frameborder="0" allowfullscreen="true"></iframe>

## Getting Data from the Audience

To kick off this live demo, some data was needed. What better way to get real data than to get the audience involved? To do this, a mobile website was created that prompted for a couple of questions and then instructed you to shake your mobile device (in case you are wondering, the [ondevicemotion](https://developer.mozilla.org/en-US/docs/Web/API/Window/ondevicemotion){:target="_blank"} event handler was used to measure the shakiness. In fact, you can get the whole [mobile app source code from GitHub](https://github.com/splunk/parallel-piper){:target="_blank"}). This mobile website sent data to Splunk via the new HTTP Event Collector in real time. Boom – live data!

![Shake1](/assets/img/2015/10/15/shake-1.jpg){: width="200"} ![Shake2](/assets/img/2015/10/15/shake-2.jpg){: width="200"}

## Analyzing the Data from the Audience

Ok, now that we have this live data, it is time to start asking questions. You can see in the video some of the analytics Nate pulled off in real time, including:

* Number of users shaking
* Trend – i.e. how much shaking is going on over time
* Who is shaking the most
* The new Choropleth visualization shows what states are shaking
* Devices shaking

## Firing the Air Cannon from Splunk
You'll notice at the beginning of the demonstration that there is a filler gauge visualization. This gauge is wired to an [Octoblu modular alert](https://splunkbase.splunk.com/app/2869/){:target="_blank"} that sends a signal to an Octoblu-powered T-Shirt cannon when the gauge hits 100%. This T-Shirt cannon is filled with stuffed Splunk ponies. It is a little hard to see in the official video, but I was able to capture it with my phone (sorry for the quality as I was pretty far back in the room).

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Ponies fly at <a href="https://twitter.com/hashtag/splunkconf?src=hash&amp;ref_src=twsrc%5Etfw">#splunkconf</a> <a href="https://twitter.com/octoblu?ref_src=twsrc%5Etfw">@octoblu</a> <a href="https://twitter.com/chrismatthieu?ref_src=twsrc%5Etfw">@chrismatthieu</a> <a href="https://twitter.com/chrisfleck?ref_src=twsrc%5Etfw">@chrisfleck</a> <a href="https://twitter.com/pcrampton?ref_src=twsrc%5Etfw">@pcrampton</a> <a href="https://twitter.com/virgilvox?ref_src=twsrc%5Etfw">@virgilvox</a> <a href="http://t.co/HjLpiDdJcz">pic.twitter.com/HjLpiDdJcz</a></p>&mdash; Jason Conger (@JasonConger) <a href="https://twitter.com/JasonConger/status/646372098802237440?ref_src=twsrc%5Etfw">September 22, 2015</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

## Recap

To recap, shaking mobile devices sent real-time data to Splunk via the HTTP event collector. All sorts of new visualizations are available to analyze the data. The new modular alert framework fired off an Octoblu workflow to send those ponies flying. Splunk is fun!

## Resources

* [Mobile app code for the shaking](https://github.com/splunk/parallel-piper){:target="_blank"}
* [Octoblu Alert Action](https://splunkbase.splunk.com/app/2869){:target="_blank"}
* [Build your own T-Shirt cannon](https://www.hackster.io/team-octoblu9/iot-air-cannon-6c83b0#.VgsSk5tW3Pk.twitter){:target="_blank"}
* [Why we chose ponies to fly – a.k.a. The Story of Buttercup](https://blogs.splunk.com/2013/04/23/the-story-of-buttercup-the-splunk-pwny){:target="_blank"}