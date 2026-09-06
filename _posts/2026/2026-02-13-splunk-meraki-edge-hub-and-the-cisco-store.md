---
layout: post
title: "Splunk, Meraki, Edge Hub and the Cisco Store"
subtitle: ""
date: 2026-02-13
categories:
 - Videos
tags:
 - "Splunk"
 - "Cisco"
 - "Security"
 - "AI"
 - "Observability"
 - "IoT"
 - "Partner"
 - "Cisco Live"
author: JasonConger
readtime: true
video-id: HCTNAHcZ2ME
video-duration: "2:34"
thumbnail-img: https://i.ytimg.com/vi/HCTNAHcZ2ME/hqdefault.jpg
share-img: https://i.ytimg.com/vi/HCTNAHcZ2ME/hqdefault.jpg
excerpt: "At Cisco Live EMEA, we used Splunk, Meraki, Edge Hubs, partner technologies, and more to bring real-time insights to the on-site Cisco Store. Kyle Prins shared with us the underlying technology used in the store as well as the use cases being brought to life. It is a fascinating example of how Splunk can be…"
featured: false
---
At Cisco Live EMEA, we used Splunk, Meraki, Edge Hubs, partner technologies, and more to bring real-time insights to the on-site Cisco Store.  Kyle Prins shared with us the underlying technology used in the store as well as the use cases being brought to life. It is a fascinating example of how Splunk can be used to ask questions, get answers, and take action on any type of machine data.

{% include youtube.html id="HCTNAHcZ2ME" %}

## Transcript

*Auto-generated captions, lightly cleaned. Speakers are not separately labeled.*

Hey everybody, we're out here at Cisco Live in Amsterdam and I've been talking to Kyle here about the Cisco store. Yeah, there's a a lot of technology going on here. Can you give us a rundown of what it is? &gt;&gt; Yeah, we've got a lot of technology both Cisco family and Cisco partner world uh technology integrations here. Uh our latest one that we've been really excited about is actually using Moroi camera data uh and feeding that into Splunk. Now you probably go, "Wait, video data? What are we? That doesn't work for Splunk, right? No, what we're able to do is actually generate uh machine data off of the cameras and then feed that in via MQTT to a Splunk edge hub and then get that into our Splunk cloud environment. We're also able to work with some Cisco partners called Every Angle and they're actually applying machine learning models running on the Maro cameras themselves, generating machine data for us, sending that to our edgehub again over MQTT, pushing that up to Splunk. And where this gets really cool is when you start to think of like remote office, branch office, retail stores, that tends to be a pretty small uplink that you don't really want to flood with a lot of video data. And we can bypass that issue completely using machine data, Splunk, Every Angle, and Moroi. &gt;&gt; Now, we're capturing all this video data and Splunk. What kind of use cases are we doing with that? &gt;&gt; Oh, so we're seeing quite a few use cases. And it's it's fun because Splunk we typically talk security and observability, but now we're able to look at physical security as well. So we're able to run demographic information on who's in the store, where their dwell time is, what items are they looking at, and we can also then run anomaly detection or set alerts up based upon the number of people in a store at the time of day. So like, hey, if the store closes at 9 and at 10 we've got 30 people in the store, something's wrong. Uh so those are use cases we're looking at. Again, it would be demographic and business style information on targeted advertising maybe, but then also physical security around there as well. &gt;&gt; That's awesome. So, all this camera data getting that into Splunk. If I want to go do something like this myself, how would I get started? &gt;&gt; Yeah, absolutely. So, uh I think the first step is talking with either your Splunk partner team or uh Splunk yourself. Uh then getting on Splunk base, obviously you can grab a Splunk Enterprise trial for free. Uh you can download uh the Maro TA for free uh and get those connected and then uh an edgehub from either partner or Splunk World and uh connect it all together and see it in action or uh give us a shout on LinkedIn. We're [music] happy to show it off. That's awesome. Thanks so much, K. Appreciate it. &gt;&gt; Absolutely. Thanks.
