---
layout: post
title: "Splunk Federation and Data Lakes"
subtitle: ""
date: 2025-02-26
categories:
 - Videos
tags:
 - "Splunk"
 - "Security"
 - "Partner"
 - "Dashboards"
author: JasonConger
readtime: true
video-id: oHcGXeC7xRM
video-duration: "2:58"
thumbnail-img: https://i.ytimg.com/vi/oHcGXeC7xRM/hqdefault.jpg
share-img: https://i.ytimg.com/vi/oHcGXeC7xRM/hqdefault.jpg
excerpt: "Technical Splunkers from around the globe recently gathered for Splunk Global Tech Summit. While there, I had a chance to chat with Camille Gaspard about Federation and Data Lakes which allows you to use Splunk features you know and love on data wherever it is - even without ingesting it into Splunk."
featured: false
---
Technical Splunkers from around the globe recently gathered for Splunk Global Tech Summit. While there, I had a chance to chat with Camille Gaspard about Federation and Data Lakes which allows you to use Splunk features you know and love on data wherever it is - even without ingesting it into Splunk.

{% include youtube.html id="oHcGXeC7xRM" %}

## Transcript

*Auto-generated captions, lightly cleaned. Speakers are not separately labeled.*

hey everyone we're out here at thean Tech Summit been talking to Camille about Federation and rehydration can you give me more information about what that is and what we're doing with that in Span absolutely hey Jason nice to see you here so basically you know a few years back we thought we wanted to give uh customers the same experience that they have in spun then the same awesome experience they have surge dashboard alerting all that but maybe on data that is not inside spunk and then that's we started the journey Federation we started working on S3 Federation where people can start searching data that lives outside connected with your whatever your data is is residing let's say WS blue and uh that kind of got us uh some good traction and then later on we wanted to take this further and we partnered with Amazon to launch Amazon security Lake ASL soong and Amazon Co launch uh ASL with Spong like a year ago we uh debuted in conf last year and then in that uh integration we want to do something different not just search the data that lives outside which is what we did earlier so now we can do it with ocsf also so it's pretty cool so you can search the that lives outside uh your spun ingested kind of indices but with ocsf u you know semantics which is pretty awesome but then we also wanted to take it further and we said okay what if you wanted to do full-on detections on some part of the data that lives outside your Splunk uh you know inj just the data so what we did we introduced the concept of a data Le index we only launch it for ASL and but it's coming now to all other data sets including S3 and later on to other uh data sources and csps and the goal of that is we go and grab the last few days of data from ASL let's say or S3 and ingested for a few days so we can let you run fullon SPL on that so that's pretty cool you can keep your detections as they are and run that and then after 7 days you can switch back to the Federation part so the goal is to have a transparent experi where you can search data that comes in regardless of where it is and you get the same experience with SPL so it's no longer about necessarily getting data in the block you can use data wherever it is exactly and that kind of comes Under the Umbrella of data management the team has done a lot of great work uh to do data management to shift that mentality basically saying you manage your data with spun it doesn't matter what it is we can just you know run analytics and search and all that cool things that you love about Splunk but regardless of where the data that's really great abely uh where can I go get some more information about these capabilities absolutely so spun.com is a good place to start you can search for Federation there's a bunch of uh videos and bl blog posts you can find there and also talk to the your SP Partners fantastic thanks so much thank you so much thank you [Music]
