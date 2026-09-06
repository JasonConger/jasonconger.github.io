---
layout: post
title: "Splunk .conf24: exclusive interview with Tenable"
subtitle: ""
date: 2024-07-12
categories:
 - Videos
tags:
 - "Splunk"
 - "Security"
 - "Interview"
author: JasonConger
readtime: true
video-id: HHnZdTXCmxI
video-duration: "3:10"
thumbnail-img: https://i.ytimg.com/vi/HHnZdTXCmxI/hqdefault.jpg
share-img: https://i.ytimg.com/vi/HHnZdTXCmxI/hqdefault.jpg
excerpt: "At Splunk .conf24, I had a great conversation with Nick Keuning about Tenable's Cyber Exposure capabilities and Splunk integrations."
featured: false
---
At Splunk .conf24, I had a great conversation with Nick Keuning about Tenable's Cyber Exposure capabilities and Splunk integrations.

{% include youtube.html id="HHnZdTXCmxI" %}

## Transcript

*Auto-generated captions, lightly cleaned. Speakers are not separately labeled.*

hey everyone we're out here at Doom 24 and I got Nick here from tenable to talk more about the tenable and Splunk integration so tell me a little bit more about uh what you do and how you integrate with Splunk sure so tenable is cyber exposure company um we started out as vulnerability assessment moved into vulnerability management now as exposure management what we're really doing is broadening the asset scope of where we can find misconfigurations vulnerabilities or even just detect your assets for you so we started out on server end points we've now got operational technology active directory technology we have a full cnap solution so all the things in the cloud a little bit of everything and it's really at the end of the day we're still detecting vulnerabilities detecting the assets but we're taking all of that putting into a centralized uh interface in our t one product so you can understand your risk across all of your assets and prioritize what's most important to yeah so fantastic to a lot of OT data and a lot of pre-built uh use cases for that data right out of the box so in Splunk is a great example right so every product that we have integrates to Splunk in some way shape or form generically the Integrations are bringing in assets vulnerabilities or misconfigurations and then the plug-in definitions that power those misconfigurations or the vulnerabilities once that's in Splunk most of our customers are going to use that for kind of two main use cases first they're going to use it to help prioritize or deprioritize different alerts because that risk that we're providing is a solid starting point for understanding should I look into this should I not do I care about this asset do I not care about it is there any risk on the asset so use case one prior prioritizing or deprioritizing um alerts that may come in based on the vulnerabilities the Second Use case is most of our customers that are spunk customers they want all their dashboarding and Reporting right in spunk it's super easy to build I already got the data there why not right so we built a u spunk app that takes all of our data D duplicates it because we're St information we're not really like alert based the state could be it could be 90 days ago is the last time you scann so we we duplicated all that and standardized it into our app so there's a lookup table pre-built for you search is pre-built for you even an example dashboard that you can go in and leverage day one but more importantly you have the base framework you need to build any reporting and dashboarding that you might want right within swun so you don't ever even need to go to our UI to do reporting yeah that's incredible a lot of flexibility that you're giving the user yeah exactly it sounds really good how do I get more information about this whole bunch of different ways uh easiest way you can email support or support Splunk table.com uh we'll get you all the information you want you can go under our website table.com under uh partners and then technology ecosystem um you'll there all our Integrations are listed there a bunch of documentation or docs. table.com if you're looking for user guides and stuff like that and I guess lastly Splunk base all the apps are listed on there links to our docs and everything else it's a bunch of different ways you can get to us fantastic thanks so much for your time today yeah thanks for having me
