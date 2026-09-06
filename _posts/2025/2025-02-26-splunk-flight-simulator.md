---
layout: post
title: "Splunk Flight Simulator"
subtitle: ""
date: 2025-02-26
categories:
 - Videos
tags:
 - "Splunk"
 - "Microsoft"
author: JasonConger
readtime: true
video-id: AtjSwubK-GA
video-duration: "1:43"
thumbnail-img: https://i.ytimg.com/vi/AtjSwubK-GA/hqdefault.jpg
share-img: https://i.ytimg.com/vi/AtjSwubK-GA/hqdefault.jpg
excerpt: "With Splunk, you can pretty much ask any question of any data and take any action. To put this to the test Kendrick Tugwell and Paul Bannister were able to send Microsoft Flight Simulator data to Splunk via Splunk's HTTP Event Collector. They challenged fellow Splunkers to 'fly' planes in the Top Gun challenge where…"
featured: false
---
With Splunk, you can pretty much ask any question of any data and take any action. To put this to the test Kendrick Tugwell and Paul Bannister were able to send Microsoft Flight Simulator data to Splunk via Splunk's HTTP Event Collector. They challenged fellow Splunkers to 'fly' planes in the Top Gun challenge where they received telemetry data to score the pilots. I had a chat with them to get the scoop on how they did it.

{% include youtube.html id="AtjSwubK-GA" %}

## Transcript

*Auto-generated captions, lightly cleaned. Speakers are not separately labeled.*

hey everyone we're out here at Splunk Tech Summit and I've been chatting with Paul and Kendrick about this flight simulator and you've hooked up a flight simulator to give to limit your display how'd you do that so what we did was we integrated with the Microsoft flight simulator 2020 SDK which generates CSV files we use the program to convert that to Jason it cues it up and then sends that data straight to the Splunk HTTP event collector so all you need is the game the small appp that we create and Splunk and you can get the live Telemetry data straight from Microsoft light simulator cool now if I wanted to go do this myself how would I go about learning more that I'd go ahead and sort of reach out to your sort SP count manager or even to the community events just to chat to your local SE to see what weird and one for you'll find that there's quite a lot of us doing some weird stuff we long to pulling in data from all sorts of sources and I would just think if you've got an idea just head to Google figure it out the data is in there you and swy getting it from anywhere yeah also curiosity right so you don't even need us to help you do it if you've got flight simulator at home get yourself a free troll license of Splunk from splunk.com uh get yourself onto something called FS Telemetry from GitHub uh and you can install it without any help from us at all and get this data going straight into Splunk and you can do all challenges we're using Top Gun here for example but there's multiple Landing challenges there's flying through the Arctic there's so many challenges where you can get so much data from amazing thank you no worries thanks very much [Music]
