---
layout: post
title: "Splunk and Netscout"
subtitle: ""
date: 2025-11-18
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
author: JasonConger
readtime: true
video-id: GundoJqACok
video-duration: "2:47"
thumbnail-img: https://i.ytimg.com/vi/GundoJqACok/hqdefault.jpg
share-img: https://i.ytimg.com/vi/GundoJqACok/hqdefault.jpg
excerpt: "There are numerous integrations with the Splunk platform to get more insight and listen to your data. While at Cisco Partner Summit recently, I got an overview from Subarno Mukherjee about Splunk's integration with NETSCOUT and the added visibility from the products working together - from Deep Packet Inspection (DPI) for security to application implications…"
featured: false
---
There are numerous integrations with the Splunk platform to get more insight and listen to your data. While at Cisco Partner Summit recently, I got an overview from Subarno Mukherjee about Splunk's integration with NETSCOUT and the added visibility from the products working together - from Deep Packet Inspection (DPI) for security to application implications for observability.

{% include youtube.html id="GundoJqACok" %}

## Transcript

*Auto-generated captions, lightly cleaned. Speakers are not separately labeled.*

Hey everybody, we're out here at Cisco Partner Summit and I ran into Sabo and we recently released an integration for Net Scout. Can you give me some more information about what it does? &gt;&gt; That's that's right. So we do have um integration which we have released few months back and it is GA we are currently shipping it. Um so NetScout is one of our top tier strategic partners and what do they do is they offer a sensor and a AI streamer that sits into your network traffic and it does a deep packet inspection or commonly known as DPI. So what is DPI? So every packet that moves through your network layer like layer 1, layer two of OSI, it sniffs everything and collects the raw deep packet data and then they also have a AI streamer that sits on top of their sensors which then contextually enrich all the packet data with the relevant metadata. Now that's a very high quality gold standard data for for us and that's what we are now feeding into Splunk for our customers. So with the DPI data now we are getting into Splunk we can correlate that other network telemetry that is always existing within Splunk or we can also combine that with application data which we can source from app dynamics or oi. So now think about this with stitching DPI with APM and infrastructure you have an end toend view of any application performance right from your browser to your application database server all the way down to your network to give you an example you can look at this demo where there is ITSI service map and you can see these are the impacted application some of them are web server some of them are databases but all of them not impacted because of a faulty &gt;&gt; DSN. So that's the power of this integration. &gt;&gt; So you mentioned this is GA where can I go get some more information or actually get this integration? &gt;&gt; Go to splankbase.com and you will see this application is being listed there. And for Splunk people and for our partners, you guys can go to splunk show.plank.com splunk.com where we do have a demo available on demand for you to learn and share with your customers. &gt;&gt; That's amazing. Thanks so much for your time today. Thank you. Pleasure.
