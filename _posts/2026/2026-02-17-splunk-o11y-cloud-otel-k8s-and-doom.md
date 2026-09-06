---
layout: post
title: "Splunk o11y Cloud, OTel, K8s, and Doom"
subtitle: ""
date: 2026-02-17
categories:
 - Videos
tags:
 - "Splunk"
 - "Cisco"
 - "Observability"
 - "Dashboards"
 - "Cisco Live"
author: JasonConger
readtime: true
video-id: YRAgpkPRzT8
video-duration: "2:25"
thumbnail-img: https://i.ytimg.com/vi/YRAgpkPRzT8/hqdefault.jpg
share-img: https://i.ytimg.com/vi/YRAgpkPRzT8/hqdefault.jpg
excerpt: "At Cisco Live EMEA, I saw a really cool demo illustrating application instrumentation with OpenTelemetry, Splunk Observability Cloud, and Kubernetes. The cool factor came in when Heath Johnson showed us how quick Splunk Observability Cloud reacts to things like an unexpected Pod deletion. But, he didn't delete the Pod in any old-fashioned way. Instead, he…"
featured: false
---
At Cisco Live EMEA, I saw a really cool demo illustrating application instrumentation with OpenTelemetry, Splunk Observability Cloud, and Kubernetes. The cool factor came in when Heath Johnson showed us how quick Splunk Observability Cloud reacts to things like an unexpected Pod deletion. But, he didn't delete the Pod in any old-fashioned way. Instead, he wired up an implementation of Doom where taking out an enemy in the game took a Pod down in the E-commerce application. It was a fun way to in

{% include youtube.html id="YRAgpkPRzT8" %}

## Transcript

*Auto-generated captions, lightly cleaned. Speakers are not separately labeled.*

Hey everybody, we're out here at Cisco Live in Amsterdam and I've been chatting with Heath here about a really interesting use case you're doing with Splunk. Now, I don't want to spoil the surprise. Can you show us what you're doing here? &gt;&gt; Yeah, so we set up and developed So, this is Splunk's own video game. We made two different video games. This is our version of Doom, the original classic game Doom. As you play the game and you shoot some of the enemies inside the video game, you're actually deleting Kubernetes pods in a backend live e-commerce web application. That e-commerce web application we are then monitoring with Splunk Observability Cloud and picking up all the deletions and chaos that you're creating inside the video game. &gt;&gt; So you're actually shooting pods here, deleting those, and we're picking up with Ali Cloud. &gt;&gt; Exactly. Exactly. Do we have like a dashboard that's going on here? &gt;&gt; So if we jump over to the live dashboard, this is the default name space and these are all the pods that we are shooting at inside the video game and you can see the deleted pods get ticked up immediately inside the game as we play it. So you see how fast observability cloud picks up all these Kubernetes destruction and chaos that's going inside. As well as memory stress, we're picking up CPU stress. Alarms are starting to go off because the services inside this video game are causing problems for our e-commerce web application. And &gt;&gt; that's a really interesting use case of just bringing Splunk to any kind of data, even a game to illustrate the power. Now you're using OTIL, Kubernetes, Ali Cloud. You're stitching it all together. If I want to go do something myself and experiment, how could I get started? &gt;&gt; Yeah, I've got the fastest way to demo Ali Cloud in your own environment on the smallest device possible. So, I wrote this lantern article. We'll have a link to it for uh deploying Splunk Observ Cloud, an open telemetry e-commerce web application. It's actually the same one we use in the game. And uh we deploy it all on top of a Raspberry Pi 5 inside your home lab. Deploys in five or 10 minutes really, really quickly. It's easy to do. Just follow the instructions on this and it'll get you there on our free Ali cloud trial that lasts 14 days. No credit card needed. &gt;&gt; That is really cool, man. And I really appreciate your time. Thanks for coming out.
