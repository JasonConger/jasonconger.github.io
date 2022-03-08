---
id: 1648
title: Using Proximity to Start an Octoblu Workflow
date: 2015-06-29T11:00:33-05:00
author: jason
excerpt: 'This is the second part of the IoT workspace demo.  This time, we will use proximity to kick off an Octoblu workflow without an iBeacon - mainly because this was a last minute add to the demo ;-)'
layout: post
guid: http://www.jasonconger.com/?p=1648
image: wp-content/uploads/2015/06/octoblu.png
categories:
  - IoT
tags:
  - Citrix
  - IoT
  - Octoblu
---
<h1>A Poor Man's iBeacon</h1>
<h2>a.k.a. I needed a quick solution for proximity without an iBeacon</h2>
During the Citrix Geek Speak demo <a href="http://www.jasonconger.com/post/trigger-an-octoblu-iot-flow-from-splunk/">I previously blogged about</a>, we needed a way to kick off everything.  Steve and I discussed a few different ways of doing this, but we landed on using proximity - meaning when Steve walked over to the IoT workspace with a particular device, everything would light up and we would be off to the races.  The correct way to do this would be an <a href="https://en.wikipedia.org/wiki/IBeacon" target="_blank">iBeacon</a>, but this was a last minute decision and we didn't have one.  So, we used bluetooth paring on a laptop.  The rest of this article explains that part in detail.
<h1>Proximity with a Laptop</h1>
My first thought was to write some code to accomplish starting an Octoblu workflow using bluetooth proximity.  There are some examples out there for the pieces I needed for this (bluetooth pairing, bluetooth signal strength, curl, etc.).  But then I thought that there might be something already written.  Sure enough, I found 2 solutions (for Mac) - <a href="http://mousedown.net/mouseware/EventScripts.html" target="_blank">EventScripts</a> and <a href="https://itunes.apple.com/us/app/bluetooth-proximity-tasker/id525925062?mt=12" target="_blank">Bluetooth Proximity Tasker</a>.  EventScripts was more robust and felt more polished, but I ended up using Bluetooth Proximity Tasker for the simple fact that I could control exactly how strong of a bluetooth signal I needed to start/stop an action.  This was important as I didn't know ahead of time what the signal strength would be like on stage at Geek Speak Tonight (especially once the room filled up with fellow Geeks).

<a href="http://www.jasonconger.com/wp-content/uploads/2015/06/Bluetooth-Proximity-Tasker.png"><img class="aligncenter wp-image-1679 size-full" src="http://www.jasonconger.com/wp-content/uploads/2015/06/Bluetooth-Proximity-Tasker.png" alt="Bluetooth Proximity Tasker" width="592" height="475" /></a>

As you can see in the screenshot above, there is a slider that lets me choose the signal strength.  The green bar you see above the slider is my actual signal strength.  So, I would walk around to see what my actual strength was and set the slider appropriately.
<h1>AppleScript Kicks off the Flow</h1>
So now that we have have the bluetooth strength thing worked out, all we need is a script to kick off the Octoblu flow.  Recall from my <a href="http://www.jasonconger.com/post/trigger-an-octoblu-iot-flow-from-splunk/">previous post</a> that all triggers in Octoblu have a HTTP POST URL.  I just used this URL and curl to work the magic.  Here is the script:

~~~
say "eye oh tee, work space. activated"
set theURL to "[your trigger URL]"
do shell script "curl -X POST " &amp; quoted form of theURL
~~~

The first line is a quasi-phonetic pronunciation for "IoT Workspace Activated".  That is about as close as I could get using AppleScript.  The next two lines actually kick off the Octoblu IoT workspace in a green state.
<h1>Conclusion</h1>
So, there you have it.  That is pretty much the complete IoT Workspace demo from my side of the desk.  Octoblu is a lot of fun and I'm experimenting with other ways of using this software for business, home automation, and just plain fun (like Legos).  Go experiment yourself and have fun!