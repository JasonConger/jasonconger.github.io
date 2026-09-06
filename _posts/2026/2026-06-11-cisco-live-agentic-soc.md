---
layout: post
title: "Cisco Live Agentic SOC"
subtitle: ""
date: 2026-06-11
categories:
 - Videos
tags:
 - "Splunk"
 - "Cisco"
 - "Security"
 - "AI"
 - "Observability"
 - "Cisco Live"
 - "Interview"
author: JasonConger
readtime: true
video-id: cFi43yfcI8g
video-duration: "8:42"
thumbnail-img: https://i.ytimg.com/vi/cFi43yfcI8g/hqdefault.jpg
share-img: https://i.ytimg.com/vi/cFi43yfcI8g/hqdefault.jpg
excerpt: "Interview with Dan Christiansen (CISSP) about running a live SOC on the Cisco Live show floor network, using Splunk Enterprise Security, Attack Analyzer, and the Triage Agent to automate tier-1 detection and investigation."
featured: true
---
Interview with Dan Christiansen (CISSP) about running a live SOC on the Cisco Live show floor network, using Splunk Enterprise Security, Attack Analyzer, and the Triage Agent to automate tier-1 detection and investigation.

{% include youtube.html id="cFi43yfcI8g" %}

## Transcript

*Auto-generated captions, lightly cleaned. Speakers are not separately labeled.*

Everybody, we're out here at Cisco Live and I ran into Dan here and now you've been working the sock of the thing. Now across from us is the knock. Right. But making it all secure is the team over here in the sock. And now we're using our own products to make the conference secure. Can you give me a little bit of idea about what all the technology are we using to do that? Absolutely. So, as many of you know that Cisco had acquired Splunk a couple years ago and we've been working diligently to be able to bring the best of both technologies together. You know, now we have the best of network telemetry, the firewall data, we have the ability to be able to bring in Cisco's XDR to be able to help with the Agentic SOC capabilities and then we've been leveraging that with our enterprise security and a lot of the other Splunk security products like Attack Analyzer, a lot of our Agentic AI capabilities that we bring to it, the Triage Agent's been really fundamental for us as well.

Yeah, so you're gathering a lot of information. Kind of what's going into this? Is it wireless data? Is it network data? What are you actually looking at here in the SOC? Yeah, so we have a bunch of different subnets. We have a public Wi-Fi area. We also have the show floor, both wired and wireless as well. And so we've been monitoring everything from the NOC infrastructure throughout the entire Cisco Live event. And so with that data, we're able to see a number of different activities, everything from normal network traffic to be able to work with the SOC to be able to keep things fast and efficient. But we also, on the security operations side, we've been seeing a lot of different types of malware attacks and a lot of other things happening on the client devices for the guest Wi-Fi that we're trying to be able to help them take care of as well.

So what are some of these surprising things that you're actually finding over here? Yeah, you would be surprised. So, as of today, there's been over 600 unique users who have had passwords sent in the clear. A lot of them for email servers, applications, and things like that. So, the good news is that with our Agentic SOC, we automatically detect the clear passwords on the network. Normally, we can grab a username, an email address, something like that that's been sent in the clear as well. We have an Agentic Triage Agent that automatically scrapes all that data, anonymizes it, we send it over to our SOAR playbooks, and we contact those users out of band from the security operations center, letting them know that their email has been potentially compromised, they've been sending their passwords in the clear. So, we're kind of acting as a guardian angel here at the security operations center, having all of our guests who are using the public Wi-Fi know that we're keeping them a little bit safer than they were outside of these four walls.

So you got your cleartext passwords, but you tell me some other interesting things going on with some crypto mining, some BitTorrents. What are you seeing there? So, there's been some interesting things. We've seen hundreds of examples of command and control activity with malware. We've been seeing a lot of crypto mining, a lot of attacks against some infrastructure, things like DNS servers, firewall data, things like that. There's been a lot of compromised devices with active connections to malicious websites, and so we've been trying to work with the SOC hand-in-hand to block those connections so that the users' devices will be safe within our networks, and reduce the chance of spread. So, it's been really interesting to see how that's all come to fruition.

And something interesting we talked about — you pretty much automated all the level one stuff, but things like Triage Agent, SOAR playbooks. What all has gone into that? Yeah, so our Triage Agent and our Splunk SOAR have really taken the lion's share of that automation capability. Day one when we came in here, we tell all of our customers about the capabilities of Cisco and Splunk, the full agentic AI that we have for our SOC, but we're actually leveraging all those technologies — eating our own food, if you will. So, we've been leveraging that to outsource the entire tier one. Literally everyone on day one was promoted to tier two and tier three. All of the low-level investigation is completely automated by the Triage Agent. SOAR playbooks are out contacting users out of band when their devices appear to be compromised, sending passwords in the clear. So, we don't have to do any of those things. We can focus on the higher-level threats and make sure we keep them safe in the process.

Now, you're out there talking about Splunk a lot. And you shared with me this is the first time you worked a show for SOC. Yes. So, what's been your experience getting hands-on and seeing what's going on in the show floor here? Yeah, it's been incredible. So, I've been at Splunk almost 11 years now, from the SE side as well as a security strategist and specialist side. So, I get to see the technology, I get to play with it, use it all the time to help our customers achieve all their mission-critical goals in security. But it's totally different to actually work in the SOC defending against live attacks with live data. And it's just been really eye-opening. I've learned a lot. I can see the magnitude of the amount of attacks that happen regardless of the type of show. If you're at something like a security show like a Def Con or a Black Hat, you expect a lot of shenanigans on the network. But when you're at a legitimate conference that's more IT and security focused, especially with all the AI and things like that, it's amazing to me to see just the amount of activity that there is. It's the most network activity we've had at any Cisco Live to date.

You told me a lot of really cool things earlier — one of them, doing some PCAP captures, Zeek format going into Attack Analyzer. Yes. Tell me more about that. Absolutely. So, we partner with a company called Endace to help us with the PCAP capturing. That way we have the full network telemetry to be able to go in and help with our investigations, replay the attacks, look at the protocol analysis. But what it's doing that's a little different than traditionally is not only is it grabbing all that full PCAP data for us to use, allowing us to export into Wireshark and things effortlessly, but it's actually able to export it into Zeek log formats, and it's automatically stripping out IP addresses from destinations, URLs, and sending them into our Splunk Attack Analyzer to automatically investigate these to see if any of them are malicious. The ones that are malicious get kicked back into Splunk as an alert, and then we can actually see it inside the SOC and go through and take a look at our connection logs from the firewall to see if it's already being blocked or not. And if it's not, we can escalate it up to the NOC to get it taken care of.

And one more thing, to wrap up — this is at Cisco Live, but we're protecting other events like the Olympics as an example. So, give me some more information about how we're taking what we learn here and expanding it to other venues. Yes. So, Cisco and Splunk take all the best-of-breed technologies that we have between the two companies, and we've put it into what's called a "SOC in a box" that travels around the world. We take care of Black Hat, RSA. We have a SOC here at Cisco Live. We're going to be working with the LA Olympics in 2028. So, there's a whole team behind me who will be working the Olympics for the full-fledged SOC. That one's a little unique because not only do we protect the actual Olympic event and the Wi-Fi and the infrastructure there, but even things in the surrounding area like water, sewer, city infrastructure, even things like Uber and Lyft to make sure they're not getting compromised on the public networks. So, we actually have hotlines established with a lot of these organizations, the critical infrastructure, the city management, because a cyber attack could easily disrupt the Olympics. Things like Black Hat in Asia, out of Singapore, the one coming up in London later this year, is another one that we'll be working with full SOC as well.

Very cool. Man, that's just really eye-opening to know what all's going into the NOC, but then securing it over here in the SOC to make sure everybody at Cisco Live is safe. I really appreciate your time. Thank you. Thanks for having me.
