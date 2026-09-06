---
layout: post
title: "Splunk Laser Bananas and Edge Hub"
subtitle: ""
date: 2025-09-19
categories:
 - Videos
tags:
 - "Splunk"
 - "Observability"
 - "IoT"
 - "Dashboards"
author: JasonConger
readtime: true
video-id: mOmpzfFM2y8
video-duration: "2:32"
thumbnail-img: https://i.ytimg.com/vi/mOmpzfFM2y8/hqdefault.jpg
share-img: https://i.ytimg.com/vi/mOmpzfFM2y8/hqdefault.jpg
excerpt: "Laser Bananas and the power of Splunk! While at Splunk .conf25, I had the opportunity to chat with Simon Slade about how he brought together physical data with observability to demonstrate the breadth of Splunk solutions. By shooting a laser out of a banana (that is not a typo), receiving the signal, brokering the MQTT…"
featured: false
---
Laser Bananas and the power of Splunk! While at Splunk .conf25, I had the opportunity to chat with Simon Slade about how he brought together physical data with observability to demonstrate the breadth of Splunk solutions. By shooting a laser out of a banana (that is not a typo), receiving the signal, brokering the MQTT data with Splunk Edge Hub, and visualizing the results in a Splunk dashboard, Simon brought gamification to life. While this is a fun use case, think about all the other implicati

{% include youtube.html id="mOmpzfFM2y8" %}

## Transcript

*Auto-generated captions, lightly cleaned. Speakers are not separately labeled.*

Hey everyone, we're out here at do and I ran into Simon here and somehow you have these laser bananas that are shooting at targets and hitting that data into Splunk somehow. Can you tell me how all this works? &gt;&gt; Sure, no problem. Uh so, uh we've been using the edge hub for quite a while and we wanted to build out a kind of technology demonstrator that allows uh customers to see how easy it is to get their operational technology data and how valuable that is to them. So we thought we build build out a kind of representative environment that is gamified that they can work with. So uh behind us we've got a number of targets and bananas uh the fire lasers that act as nodes or sensors that would traditionally be in an operational technology environment. Uh and from those we can use one of the protocols that Edgehub um supports uh MQTT to negotiate uh and orchestrate a game uh between the the lasers being fired by the bananas and being received by the targets and the edge hub orchestrating all that all with a a Docker containerized uh game function that uh all gets sent up into Splunk. And we can then use our traditional dashboarding to to bring out uh the uh the results of the game uh and also the health of the system and and tell a story around the technology but do it in a fun way. &gt;&gt; So some non-traditional data you got the your banana hitting the target and that target data is going into edgehub as a broker into Splunk and you got some dashboards going on there. Is that right? &gt;&gt; That's right. Yeah. So uh not only have you got the uh the kind of the business uh axis of how uh the systems are actually performing in their day-to-day job but you've got the all the underlying metrics that tell you about the health of the system so you can give that insight in terms of the resilience of the whole system in itself. &gt;&gt; That's great. So if I wanted to go do some non-traditional use case similar to this how would I go get started? What types of technologies could I use? &gt;&gt; So uh it's a good question. Uh it very much depends on the kind of underlying technology that you're using. As you know, with Splunk, we've got so many different ways of getting data in. Uh, and they'll typically be one, perhaps even two or three different ways of doing it. So, it's to evaluate what what's being driven and what the benefits are of using that technology. In this case, the edge hub was a perfect fit because we're using some industrial protocols, which are t typically uh a bit more tricky than traditional IT to work with, but there there are so many different ways to do it, and it's really to focus on what what are you working with, what outcomes do you want for working with that data. &gt;&gt; That sounds fantastic. Thanks so much for your time. Appreciate it. &gt;&gt; Thank you very much.
