---
layout: post
title: "Splunk Detection Studio in Splunk Enterprise Security"
subtitle: ""
date: 2026-03-24
categories:
 - Videos
tags:
 - "Splunk"
 - "Security"
author: JasonConger
readtime: true
video-id: mrxYJoq3APQ
video-duration: "2:39"
thumbnail-img: https://i.ytimg.com/vi/mrxYJoq3APQ/hqdefault.jpg
share-img: https://i.ytimg.com/vi/mrxYJoq3APQ/hqdefault.jpg
excerpt: "One of the new features of Splunk Enterprise Security is Detection Studio. While at RSAC, I had an opportunity to chat with Tyson S. about all the capabilities. Detection Studio brings detection authoring and editing detections to the next level, provides visibility into detection effectiveness, and utilizes Enterprise Security versioning capabilities to iterate on your…"
featured: false
---
One of the new features of Splunk Enterprise Security is Detection Studio. While at RSAC, I had an opportunity to chat with Tyson S. about all the capabilities. Detection Studio brings detection authoring and editing detections to the next level, provides visibility into detection effectiveness, and utilizes Enterprise Security versioning capabilities to iterate on your detections

{% include youtube.html id="mrxYJoq3APQ" %}

## Transcript

*Auto-generated captions, lightly cleaned. Speakers are not separately labeled.*

Everybody, we're out here at RSA conference here and I'm running into Tyson and we've been talking about detection studio and it's something brand new and Splunk Enterprise Security. Can you give us some more information about what it is and what it does? &gt;&gt; Yeah, sure. So, detection studio is now built inside of Enterprise Security and it's going to allow you to within a single pane be able to see not just the detections that we have deployed or pushed down out of the box that you can deploy in your environment, but also detections that you can build yourself. We're going to be able to catalog those and then from a single pane be able to see not just the detections themselves, but also you'll see how they fit within your environment. What's the compatibility? Do you have the data to support those detections? How efficient are they? Can you improve the efficiency of the queries underlying those detections? And then also be able to see the actual code that's underneath, right? So, a lot of cases in the past if you had detections that you were pushing out to Splunk, right? They would have a macro. And if you want to see what's underneath that macro, you'd have to dig back and go through the macros page and really dig through and figure out what's under there. Now within on the right side panel when you click on a detection, you can see the macro, the definition for the macro and any lookups and any lookup fields that are being pulled into the detection as well, all within that same framework so that you can easily make adjustments as you need to without having to go hunt and find the various pieces you need. On top of that, we can map those we can now see and visualize a mapping of those detections back to MITRE ATT&amp;CK framework so that we can see quickly what our level of coverage is across MITRE, but also where our gaps are so that we can start to prioritize what we need to do within the environment to make sure that we are covering a large swath of all of MITRE ATT&amp;CK. Thank you, sir. &gt;&gt; And something that you mentioned earlier about versioning on the detections. How does that work? &gt;&gt; Yeah. Yeah, so Enterprise Security 8 now has built-in version control. Um this is not part of detection studio. It's let's I'll it's part of Enterprise Security 8 to standard, right? So, now when you're building detections, if you want to iterate on the detections, if you see that you need to make some tune fine time fine tune adjustments to the SPL code, we can save a save the original query and then iterate on it. Keep it deployed, right? So you're not losing any having any gaps in coverage while you're iterating. And then once you have it ready for prime time, to go ahead and push out the update. But you still keep a history of all the other previous ones, so you can roll it back if that breaks or doesn't work properly. You can always roll back to the original one. &gt;&gt; That's really incredible. Now, if I want to go get some more information about this new feature in enterprise security, where can I go learn more? &gt;&gt; Yeah, so splunk.com help.splunk.com is all of our documents pages now. So you can always go there too and read up more about in more in-depth about what we have there. But splunk.com is where you're going to be able to find videos, uh blogs, and press [music] releases about everything that we have coming out. &gt;&gt; That's really incredible. Thanks so much for your time. Appreciate it. &gt;&gt; Thank you.
