---
layout: post
title: "AGNTCY and the Internet of Agents at Cisco"
subtitle: ""
date: 2025-09-16
categories:
 - Videos
tags:
 - "Cisco"
 - "AI"
 - "Observability"
author: JasonConger
readtime: true
video-id: RGblNPqVVag
video-duration: "4:17"
thumbnail-img: https://i.ytimg.com/vi/RGblNPqVVag/hqdefault.jpg
share-img: https://i.ytimg.com/vi/RGblNPqVVag/hqdefault.jpg
excerpt: "AGNTCY is an open-source infrastructure project focused on creating the 'Internet of Agents' - a system that enables AI agents from different organizations to discover, connect, and collaborate seamlessly across boundaries."
featured: false
---
AGNTCY is an open-source infrastructure project focused on creating the 'Internet of Agents' - a system that enables AI agents from different organizations to discover, connect, and collaborate seamlessly across boundaries.

{% include youtube.html id="RGblNPqVVag" %}

## Transcript

*Auto-generated captions, lightly cleaned. Speakers are not separately labeled.*

Hey everybody, we're out here at Cisco GSX and I just saw this really incredible presentation by John here about the internet of agents and the agency project. Can you give me some more information about what you just presented? &gt;&gt; Sure. Thanks. So, uh, what we're talking about here is the agency project which is part of the Linux Foundation. Cisco is a formative member of this along with Dell, Google, Oracle, and Red Hat. We started this out with 75 different companies that got together and the formative members took all of the work put in the Linux Foundation and what we're trying to do is to get agents to communicate at scale and there's a lot of things that we need to do to get this from a toy into a full running system in enterprise. We need identity, we need directories, we need protocols, we need semantics, we need observability, please, we need open telemetry all the way from the top all the way down to the network through the LLM. So what we've done is we tried to make a sample reference application. So Aditi who's been working on this is going to go through the reference application. So Aditi, why don't you show off the reference application? &gt;&gt; Absolutely. &gt;&gt; Hi everyone. Yes, we've been working on coffee agency which is a supply chain reference application to show off all of agency's capabilities. You might head to agency's GitHub organization and be a little overwhelmed by all the open source code that we have. But that's why coffee agency exists. The whole point is to go there and see working code showing off the different components of agency as well as other open source projects that have dominated the agent industry these days. So let me show you guys a little bit of a sneak peek of our demo. So in this demo you'll see four different agents and sticking to our supply chain example. You have a buyer agent and you have three different farm agents, coffee farms, and they're all talking to each other over Slim, which is Cisco's agent transport, which has been built specifically for agent to agent and agent to uh tool communication. And we're not only showing a onetoone request response uh use case like you usually see in A2A and MCP, but we're taking it one step further by showing us showing a one to many uh where you can use PubSub to not to publish to a a topic and have your agent subscribe to that topic and then be able to respond. So we have all of our agents built out in a langraph orchestrated A2A and um they are able to handle different inventory and order tasks. So I can show you here uh our supervisor agent can ask how much inventory exists across all the farms. can basically publish out to the pups subtopic saying how much inventory do you have and all of the different farms can go ahead and respond with their inventory and we get a response as we expect from all the different farms. Uh you can also send request responses one to one and we also have integrated agent identity service from agency into this application um where you can go ahead and uh secure your different agents by registering them within agent identity service backed by many different IDPS. The whole point of agency is openness and interoperability. So everything that we're building is meant to work across um all the different options that are out there. So we integrate with a ton of different IDPs. Even coffee agency is built so that you can try out different types of transports. If you don't want to use slim, you can use nats, you can use MQTT and you can play around and and have fun with it. Um we also have an MCP server that one of our farms is talking to. So we demonstrate MCP over Slim. But the whole point of coffee agency is to really see working code with MCP with A2A with agency components. And it's a chance for you to explore it and then try it out for yourself. So I implore you to go ahead and add a farm to Coffee Agency with whatever agent protocol that you're interested in. Try it out for yourself. Head to the agency GitHub repository and take a look at all our code. And if you have feedback on what we're doing, we would love for you to create GitHub issues for you to contribute to the conversation. Um, for more information, you can head to our agency website where we have plenty of docs, um, our GitHub, as I mentioned earlier, you can join our working groups and contribute to the conversation, or you can always reach out to us.
