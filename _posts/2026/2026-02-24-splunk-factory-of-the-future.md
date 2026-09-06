---
layout: post
title: "Splunk Factory of the Future"
subtitle: ""
date: 2026-02-24
categories:
 - Videos
tags:
 - "Splunk"
 - "Cisco"
 - "AI"
 - "Observability"
 - "Cisco Live"
author: JasonConger
readtime: true
video-id: wuknivZ3KA8
video-duration: "3:13"
thumbnail-img: https://i.ytimg.com/vi/wuknivZ3KA8/hqdefault.jpg
share-img: https://i.ytimg.com/vi/wuknivZ3KA8/hqdefault.jpg
excerpt: "Cisco, Splunk, Rock 'n' Roll, and the Factory of the Future was on display at Cisco Live EMEA in a fun and practical way by showcasing a physical guitar factory line testing for product defects, predictive maintenance, assembly line metrics, and more. Young Cho steps us through the demo and the technology behind the demo…"
featured: false
---
Cisco, Splunk, Rock 'n' Roll, and the Factory of the Future was on display at Cisco Live EMEA in a fun and practical way by showcasing a physical guitar factory line testing for product defects, predictive maintenance, assembly line metrics, and more. Young Cho steps us through the demo and the technology behind the demo to show correlation from networking, compute, observability, AI, and business metrics.

{% include youtube.html id="wuknivZ3KA8" %}

## Transcript

*Auto-generated captions, lightly cleaned. Speakers are not separately labeled.*

Hey everybody, we're out here at Cisco Live in Amsterdam and I ran into Young in front of this guitar demo. There's a lot of stuff going on here. Can you give us some more information about what this is? &gt;&gt; Absolutely, Jason. Yeah, we're demonstrating how Cisco and Splunk could provide factory of the future providing AI infrastructure so that customers could easily adopt AI in their factory operations. &gt;&gt; Yeah. And then what all is going on here? Is it looking for defects? Is it tuning or what what is this actually doing? &gt;&gt; Yeah, there's a few types of uh workload that's running on this infrastructure &gt;&gt; on top of unified ECS infrastructure. This where Splunk is running. &gt;&gt; We have number of AI workloads are running on top of that. One is automation of entire operation here as well as we have computer vision as you see there that's taking the photos of the guitars as it moves around the assembly line as well as we have a predictive maintenance on the other side uh predicting if machines about to fail monitoring for any anomalies related to the operational health of the of the robot that's that's in operation &gt;&gt; so in this rig you have UCS and Splunk is running on UCS Yes. And you have vision over here looking for defects and some predictive maintenance on the other side of the rig. All how does this all get into swamp? &gt;&gt; That's a good great question. So in a single UCS server we have everything running into in in the single unit uh starting with virtual PLC which which controls every all the automation process that's going on here. uh where Splunk is connected to those PLC's to pull real-time data &gt;&gt; right &gt;&gt; and also as those mach uh computer vision applications running also on the UCS we are processing all the results out of that computer vision with the image all together into a single uh single event to process all the real-time dashboard and alerting for any quality related issues from the factory. &gt;&gt; Yeah. And like normally in a a data center we're sending Splunk data with uh I don't know forwarders or HTTP event collectors. How are we getting the data from this rig the actual data into the Splunk platform? &gt;&gt; Yeah, it's through the network. Uh like you said all this infrastructure that's supporting this AI and servers, right? &gt;&gt; Uh they're all coming through Splunk through either HC or uh various industrial protocols. Mhm. &gt;&gt; And we connect to those to pull all this realtime metrics and events and alerts so that the customers could see it and OT in a single pane of glass which is critical for many of the manufacturing operations &gt;&gt; and that's really really awesome use case something really outside the box here for Splunk. &gt;&gt; Absolutely. &gt;&gt; If I want to go learn more about a use case like this or OT and Splunk where would I go learn more? &gt;&gt; Visit splunk.com and reach out to uh sales reps that are supporting various manufacturing events. &gt;&gt; That's awesome. Thank you so much for your time today. &gt;&gt; Great.
