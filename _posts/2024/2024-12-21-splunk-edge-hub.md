---
layout: post
title: "Splunk Edge Hub"
subtitle: ""
date: 2024-12-21
categories:
 - Videos
tags:
 - "Splunk"
 - "Cisco"
 - "IoT"
 - "Partner"
author: JasonConger
readtime: true
video-id: mwTVnEXNTYM
video-duration: "5:50"
thumbnail-img: https://i.ytimg.com/vi/mwTVnEXNTYM/hqdefault.jpg
share-img: https://i.ytimg.com/vi/mwTVnEXNTYM/hqdefault.jpg
excerpt: "The Splunk Edge Hub has a myriad of built-in sensors. It can run containers. It has an NPU built in. It talks common industrial protocols such as MQTT, Modbus, SNMP, and Modbus. And, the list goes on. I recently discussed the device, use cases, and capabilities with Tony Vincent."
featured: false
---
The Splunk Edge Hub has a myriad of built-in sensors. It can run containers. It has an NPU built in. It talks common industrial protocols such as MQTT, Modbus, SNMP, and Modbus. And, the list goes on. I recently discussed the device, use cases, and capabilities with Tony Vincent.

{% include youtube.html id="mwTVnEXNTYM" %}

## Transcript

*Auto-generated captions, lightly cleaned. Speakers are not separately labeled.*

hey everybody we're out here at Cisco partner Summit and I've been talking to Tony about EDG Hub which is a hardware device you actually got one to show on the show floor here can you give us a little bit more information sure absolutely so as you said right one of the cool things with EDG Hub is that it is a physical device first time that splunk's ever built Hardware um do note that because Splunk doesn't want to onboard the hardware it's sold exclusively through Partners that's a good thing right because those partners are also building the solutions wrapped around it whether it's for an auto plant or for uh back of the house at a McDonald's right and we can talk more about use cases as we go the device itself has a whole host of built-in sensors air quality temperature um uh vibration and so forth It's got great connectivity through uh ethernet both Poe and power for USBC also has Wi-Fi both 2.4 and 5 gig and also has a built-in lte1 modem that can be optionally enabled so we got great connectivity for it now all that said like the big win with EDG Hub is that it is a hub so it knows how to talk out of the box to the four biggest industrial protocols mqtt SNMP opcu UA and modbus that allows us to go out and talk to both the gateways and the sensors that exist already out in the Brownfield environment so we can also talk of course through through the Cisco moroi gear which talks mqtt to us so that's pretty cool right um uh EDG Hub uh also has the ability to run containers locally so that means that if you have a protocol that's not in that of four that I gave you like profinet or backnet or SN or S7 maybe as examples then we can do that through node red or through lipus running in a container that's pretty cool because that means that almost anything else you do we can get to it one other thing that I think i' I'd really notice right is that because it has both a quadcore arm and an npu you can take a $30 Amazon special webcam plug it into the USB port and it'll automatically start counting people now you probably don't need to count people let's admit that but the fact that we've got the npu to do those vision and sound models is pretty cool now that's vision and sound and other kinds of non-s spunky things but we can also get to the Splunk type data mltk running in Splunk can build test validate and operationalize a model model we know that we're all used to it but the beauty in this is that I can take that model and it's part of the operationalization I can push it to one or more of the fleet and I can run that model locally now you see that here where automatically I see a little red box that says that this is an anomalous value that shows up in the default dashboards and I can get to it through standard spunk searches lastly most of the data all the mqt data and built-in sensor data in particular shows up as metric data and Splunk so you can build dashboards that are near instantaneous in their responsiveness yeah and so you have a dashboard here it looks like this is for building cars you can you do any dashboard or overlay how are all these metrics overlaid on top of this dashboard here sure I the backdrop of this is uh uh standard dashboard Studio example hub bit image um my guy Simon out of out of Amsterdam did this Rockstar right shout out to to Simon on that uh we have the ability with with this right to be able to just pick up the EDG Hub and give it a good old shake and you'll start to see the vibration sensors on the robots will turn red as it notices that that it's abnormal now again what would that look like in real life well in real life you'd probably have commercial vibration sensors on the robot arms and you'd be looking for vibrations that would come in Via mqtt to EDG Hub and from there up into Splunk that's a really Incredible use case there for manufacturing I imagine there's lots more different use cases let's take an example maybe you've got a contract with the people renting this rack that says they're going to get x amount of power and x amount of cooling and so forth how do you get that information today that contract data lives in core Splunk and while it's completely possible that you get you know uh uh power usage or Etc pulled into I don't know Schneider Electric or something in the back end Maring that requires that we free it from that data Silo and get it back into something that has broader visibility like Splunk and that's really incredible information Tony where can I go get some more information about all this EDG Hub experience sure so for partners and and customers they can go to EDG hubc central.com we've got web pages all set up all ready for them in the expected places Etc y thanks so much Tony appreciate the overview you got it [Music]
