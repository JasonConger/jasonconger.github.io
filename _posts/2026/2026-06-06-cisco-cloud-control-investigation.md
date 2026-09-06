---
layout: post
title: "Cisco Cloud Control Investigation"
subtitle: ""
date: 2026-06-06
categories:
 - Videos
tags:
 - "Splunk"
 - "Cisco"
 - "AI"
 - "Dashboards"
 - "Cisco Live"
author: JasonConger
readtime: true
video-id: tBCUs8jnDQ8
video-duration: "4:50"
thumbnail-img: https://i.ytimg.com/vi/tBCUs8jnDQ8/hqdefault.jpg
share-img: https://i.ytimg.com/vi/tBCUs8jnDQ8/hqdefault.jpg
excerpt: "Cisco Cloud Control brings Cisco platforms together and advances Cisco's AgenticOps vision, allowing customers to build their own apps and agents in natural language, and extending to third-party tools. While at Cisco Live, I had a chance to get an investigation demo from Aqib Kazi that shows us how easy it is to jump from…"
featured: false
---
Cisco Cloud Control brings Cisco platforms together and advances Cisco's AgenticOps vision, allowing customers to build their own apps and agents in natural language, and extending to third-party tools. While at Cisco Live, I had a chance to get an investigation demo from Aqib Kazi that shows us how easy it is to jump from high-level notification to deep-dive analytics while using AI as a guide. This is a great way to get value across all the Cisco products, and it provides a platform for partne

{% include youtube.html id="tBCUs8jnDQ8" %}

## Transcript

*Auto-generated captions, lightly cleaned. Speakers are not separately labeled.*

Hey everybody, we're all here at Cisco Live and then we ran into Akib and we've been talking about the Cisco Cloud Control and how it aids in investigations. Can you give me a little bit more thoughts on that? &gt;&gt; Absolutely. Yeah, we're able to tie in AI Canvas as well into the investigation process and really simplify the whole investigation process to where an admin can just get on and be able to use AI Canvas and simplify the troubleshooting process and be able to get to the root cause much quicker. &gt;&gt; Yeah, so we've got a big screen here. Can you uh can you give us a little demo? &gt;&gt; I'll check it out for sure. Yeah, so kind of starting off at the Cisco Cloud Control Panel. Um here we're already logged into Splunk and Cisco Cloud Control. And then I've got a series of investigations. Um anything interesting Jason that you'd like to take a look at today? &gt;&gt; Hey, let's go with AI Pod. &gt;&gt; Absolutely. Yeah, let's check out the AI Pod. Um so here we kind of first start out. Everything is running really well. This AI Canvas is reporting Cisco AI Pod performance is normal. We don't have any alerts. We look at our Nexus dashboard insights. Everything looks green. Everything looks good. Uh and then we look at our application performance graphs here. Everything is green. So now let's take a closer look at that once things start to change. They can change quickly and we already go red here. We've got an issue. AI Canvas is reporting that this specific LLM, the Meta Llama 3.1, has a 22-second uh delay in rag calls. And we can start to see our network map changes here very quickly. We've got uh red on our NIM run time. Our Splunk IT Service Intelligence is reporting red. The performance graph is still red, but it's interesting when we go over to our APM service map, that's actually red. And we actually see something interesting there. That rag server to Meta Llama latency, which is what AI Canvas actually reported. And then over here we can actually see the rag to NIM latency path. And we can start to see some more details there on that Meta Llama LLM. And it's a web app server to the payment service where we're actually seeing that delay. So, let's go a little bit further now here into AI Canvas and take a look at what we can do now. So, the next thing he does is pull up the Ali Cloud Tag Spotlight. So, if I go into Ali Cloud, I've got my tags already and here I can see I have a 100% latency on that specific AI pod {dot} system {dot} local. Uh and that's at that end point of 100%. Now, if we go a little bit further down here, we see that that issue is at the Ali Cloud Nvidia inference microservice for LLM. And that end-to-end request latency is already at 16 seconds. Now, we can see our GPU utilization is normal AI Canvas is reporting. So, that really kind of minimizes it down to that Nvidia inference microservice. So, if we go over here, we can see that 16 seconds on our chart here, the Nvidia NM for LLMs, it started to peak really quick here for 16 seconds. And that's causing our issue. Start to root cause this further and now we can pivot over to our Ali Cloud Nexus switch view and now we really start to see the issue. We've got these transmit drops Nexus is reporting an advisory alert transmit drops on switch and that's really the issue that is causing our high latency. So, now let's ask AI Canvas how do we solve that if that is our issue. A sample prompt I would ask is, "Why am I experiencing these packet drops across these VLANs?" And AI Canvas responds saying it's a VPC peer link misconfiguration. Now, that's an easy fix. Uh go ahead and fix that and AI Canvas says we should add VLANs to the VPC peer link. And that brings our latency down. We can see here our application performance graph goes green. We're back to normal running status. So, AI canvas helped us walk through that whole process and we went from originally being green, everything's running normal, to red with our Splunk APM. And then going further down that root cause analysis, we found the issue on this specific AI pod, the latency was 16 seconds per minute. And all we had to do was reconfigure our VPC peering. &gt;&gt; And that just showed a lot of technologies right in one interface here across the Cisco portfolio. Now, if I want to go learn some more of the capabilities, where do I go? &gt;&gt; Absolutely. Yeah, go to splunk.com and then go to Cisco cloud control as well. We've got a lot of integrations. But yeah, going across the portfolio here, very powerful. &gt;&gt; Thanks so much for your time. I appreciate it. &gt;&gt; Thanks, Jason. My pleasure.
