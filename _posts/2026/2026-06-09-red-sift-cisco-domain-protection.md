---
layout: post
title: "Red Sift Cisco Domain Protection"
subtitle: ""
date: 2026-06-09
categories:
 - Videos
tags:
 - "Splunk"
 - "Cisco"
 - "Security"
 - "Observability"
 - "Partner"
 - "Cisco Live"
author: JasonConger
readtime: true
video-id: GYIwF70mr00
video-duration: "2:23"
thumbnail-img: https://i.ytimg.com/vi/GYIwF70mr00/hqdefault.jpg
share-img: https://i.ytimg.com/vi/GYIwF70mr00/hqdefault.jpg
excerpt: "We all use email on a daily basis, and attackers have gotten really clever with techniques including phishing, spear phishing, lookalike domains, etc. While at #CiscoLive, I had a chat with Brian Westnedge about Cisco Domain Protection (CDP) by Red Sift. CDP helps organizations stop phishing and fraud by combining domain authentication with real-time monitoring…"
featured: false
---
We all use email on a daily basis, and attackers have gotten really clever with techniques including phishing, spear phishing, lookalike domains, etc. While at #CiscoLive, I had a chat with Brian Westnedge about Cisco Domain Protection (CDP) by Red Sift. CDP helps organizations stop phishing and fraud by combining domain authentication with real-time monitoring of lookalike threats to:

{% include youtube.html id="GYIwF70mr00" %}

## Transcript

*Auto-generated captions, lightly cleaned. Speakers are not separately labeled.*

Hey everybody, we're out here at Cisco Live and I ran into Brian here from Red Sift and we've been chatting and you have a really unique email solution that integrates with a lot of products including Cisco XDR and Splunk, but we talked about authentication down to the email level. Can you give us some more information about that? &gt;&gt; Sure thing. Yes, so Red Sift is a cybersecurity company. We're Cisco's partner for domain protection and brand protection and what that means is companies can use us to add an additional layer of email security based on email authentication. So we help companies implement email authentication protocols, SPF, DKIM and DMARC. Those stop your own domain from being impersonated either inbound for business email compromise or somebody trying to impersonate you to your customers, partners and your supply chain. So that's a SaaS solution called OnDMARC and then one The idea is once you have your own domains protected with DMARC, what about abuse that targets you on cousin and look-alike domains? So we look for domains that are confusingly similar to you in DNS records, using your logo, potentially executive faces and then help companies take that down from the internet. So that's the brand protection side of things. That's called Red Sift Brand Trust. So &gt;&gt; Yeah, and you mentioned you have a hook into Splunk when you're finding things and what's that look like? &gt;&gt; A lot of times we find that um companies are really siloed with their email functions within the organization. So the infrastructure team will look after the Cisco Cloud Email Security Gateway or email threat defense and then the SOC team maybe gets notifications about email incidents, you know, after the fact, after there's already been a phishing incident or a breach. What we try to do is take data from the telemetry that we have in the email authentication and threats that we see via the DMARC protocol and push them in into either XDR or Splunk via webhook. We have a native integration to XDR and other solutions like Microsoft Sentinel if you use those. So trying to bring some of this data from a DMARC solution into the SOC, which we think is fairly unique in this space. &gt;&gt; That's a really interesting solution and integration as well. So, I want to go get more educated. Where do I go? &gt;&gt; Yeah, sure thing. redsift.com, like s i f t flower, redsift.com/cisco. &gt;&gt; Thank you so much. Appreciate &gt;&gt; Thanks, guys. &gt;&gt; Appreciate it. &gt;&gt; [music]
