---
id: 1610
title: Trigger an Octoblu IoT Flow from Splunk
date: 2015-06-17T09:42:34-05:00
author: jason
excerpt: Octoblu does some incredible stuff with physical things driven by software. Steve Greenberg and I did a demo during Geek Speak Tonight at Citrix Synergy triggering physical devices via a Splunk search. This article goes into some of the Splunk details.
layout: post
guid: http://www.jasonconger.com/?p=1610
permalink: /2015/06/17/trigger-an-octoblu-iot-flow-from-splunk/
image: /wp-content/uploads/2015/06/octoblu.png
categories:
  - Splunk
tags:
  - Citrix
  - IoT
  - Octoblu
  - Splunk
---
An alternate title to this article might be "How Steve Greenberg and I Pulled off the Robo-Kitty Monitor Alerts at Citrix Synergy Geek Speak Tonight".

In case you missed it, here it is below:

[embed]https://www.youtube.com/watch?v=-9jTeWQbVYE&amp;t=54m21s[/embed]

<h2>The Demo Scenario</h2>

Anyway, <a href="http://www.octoblu.com" target="_blank" rel="noopener">Octoblu</a> does some incredible stuff with physical things driven by software. In the demo that Steve and I did, Steve set up an actual desk with various IoT devices on it.  We will call this the "IoT Workspace".  The IoT Workspace had a digital picture frame, lights that can change color, a mini file cabinet (that held business cards), a <a href="https://en.wikipedia.org/wiki/Maneki-neko" target="_blank" rel="noopener">maneki-neko</a> (a.k.a. lucky cat) with several hacked features, a smoke machine, and more.  We started the IoT Workspace using proximity (look for another article about how we did that soon). Then, I had a Splunk instance monitoring a Citrix stack including network, XenApp, hypervisors (XenServer, Hyper-V, and VMware), physical hardware (in this case Cisco UCS), shared storage, NetScaler, etc. At the beginning of the demonstration, the environment was all-good so everything glowed green, the Robo-Kitty was happy, and the picture frame on the desk showed an array of our favorite pictures (see below):

[caption id="attachment_1641" align="aligncenter" width="300"]<a href="http://www.jasonconger.com/wp-content/uploads/2015/06/IoT-Workspace.png" target="_blank" rel="noopener"><img class="wp-image-1641 size-medium" src="http://www.jasonconger.com/wp-content/uploads/2015/06/IoT-Workspace-300x164.png" alt="IoT Workspace" width="300" height="164" /></a> IoT Workspace[/caption]

[caption id="attachment_1628" align="aligncenter" width="300"]<a href="http://www.jasonconger.com/wp-content/uploads/2015/06/Splunk-Octoblu-Green.png" target="_blank" rel="noopener"><img class="wp-image-1628 size-medium" src="http://www.jasonconger.com/wp-content/uploads/2015/06/Splunk-Octoblu-Green-300x196.png" alt="Splunk Octoblu Green" width="300" height="196" /></a> Splunk Dashboard (All Good)[/caption]

Then, the ICA Round Trip Time started to go up. Nothing terrible, but we used that as an indicator that our users might start seeing some lag in their sessions. This is where Splunk fired the first Octoblu trigger to go to a "yellow" state. The picture frame showed a worried Minion, lights turned yellow, and Robo-Kitty’s eyes turned yellow and started to swivel.

Next, Splunk showed problems with the XenApp servers and hypervisors in addition to the ICA Round Trip Time. So, Splunk triggered a "red" state. The Minion in the picture frame looked more worried, lights turned red, and Robo-Kitty’s eyes turned red and around faster.

Finally, the entire stack went to pot. The write latency on the storage array went through the roof, the hypervisors were not happy, the XenApp server resources were scarce, the ICA Round Trip Time was off the chart. Splunk triggered the "defcon red" state. Robo-Kitty shot lasers out of its chest, the storage cabinet on the IoT Workspace started to rattle, smoke was coming out of the desk. The culprit ended up being a write controller issue on the shared storage.  Once everything was fixed, Splunk triggered the "green" state again.

<h2>How it Works</h2>

Steve did all the physical work building the IoT Workspace by hooking up Raspberry Pi, Gateblu, servos, lights, etc. Check out his article for more info -&gt; <a href="http://www.thinclient.net/blog/?p=473">http://www.thinclient.net/blog/?p=473</a>. Steve also built the Octoblu flows to make all that stuff work.

I hooked up the Octoblu triggers in Splunk to kick off all these connected devices. A trigger generally initiates Octoblu flows. These triggers have HTTP POST URLs that can be used to remotely initiate the flows (see screen shot). This is how I had Splunk act upon the data seen in the Citrix stack.

<a href="http://www.jasonconger.com/wp-content/uploads/2015/06/Octoblu-Trigger.png" target="_blank" rel="noopener"><img class="aligncenter wp-image-1631 size-medium" src="http://www.jasonconger.com/wp-content/uploads/2015/06/Octoblu-Trigger-291x300.png" alt="Octoblu Trigger" width="291" height="300" /></a>

I ran a Splunk real-time search and triggered a Python script that initiated the HTTP POST with data from the Splunk search to Octoblu when certain conditions happened. For example, if the ICA Round Trip Time exceeds 30ms and is less than 60ms, trigger a yellow alert condition. Here is the Splunk search:

<code>sourcetype=ICA:RTT ICARTT &gt; 30 ICARTT &lt; 60 | eval url="&lt;HTTP POST URL for the Octoblu trigger&gt;" | eval alert_level="Yellow"</code>

If you are interested, I have the entire Splunk/Octoblu example I used <a href="https://github.com/JasonConger/SplunkOctoblu" target="_blank" rel="noopener">uploaded to GitHub</a>. You can also <a href="http://www.splunk.com/download" target="_blank" rel="noopener">download and use Splunk for free</a>.  There is a data generator built in there as well that will let you trigger different conditions like I did in the demo.

The magic happens in the <a href="https://github.com/JasonConger/SplunkOctoblu/blob/master/octoblu/default/savedsearches.conf" target="_blank" rel="noopener">saved search</a> and a python scripted named <a href="https://github.com/JasonConger/SplunkOctoblu/blob/master/octoblu/bin/scripts/octoblu_trigger.py" target="_blank" rel="noopener">octoblu_trigger.py</a>.  The saved search contains the HTTP POST url and the condition.  The python script takes those parameters from the search and sends it over to Octoblu.  If you want to play around with this on your own system, be sure to edit the saved search by opening the Octoblu app in Splunk and clicking Settings -&gt; Searches, reports, and alerts:

<a href="http://www.jasonconger.com/wp-content/uploads/2015/06/Splunk-Octoblu-Search-Settings.png"><img class="aligncenter size-full wp-image-1637" src="http://www.jasonconger.com/wp-content/uploads/2015/06/Splunk-Octoblu-Search-Settings.png" alt="Splunk Octoblu Search Settings" width="628" height="409" /></a>Click on the example alert and change the URL to your Octoblu trigger URL.

<h2>Conclusion</h2>

Anyway, there you go. It may look kind of complicated at first, but really it is quite easy to trigger any Octoblu workflow given a variety of trigger situations.