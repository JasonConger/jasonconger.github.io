---
id: 1255
title: 'From WIRM to Splunk &#8211; Translating the Past to the Present'
date: 2013-10-18T08:00:17-05:00
author: jason
layout: post
guid: http://www.jasonconger.com/?p=1255
permalink: /2013/10/18/from-wirm-to-splunk-translating-the-past-to-the-present/
image: wp-content/uploads/2012/01/splunk.jpg
categories:
  - Splunk
tags:
  - Splunk
  - WIRM
---
I get to do a lot of cool things at <a href="http://www.splunk.com" target="_blank">Splunk</a>.  One of the things I have been wanting to do is incorporate the visualizations I built a long time ago for <a href="http://www.jasonconger.com/?s=wirm">Web Interface for Resource Manger</a> in Splunk applications.  All of those past visualizations were built using Microsoft ASP.NET and Flash.  So, I have had to use alternate methods to accomplish what I want.

&nbsp;
<h2>Calendar Visualization</h2>
One of the first things I tackled was the calendar visualization that shows how many users log in each day in a month.  Here is the old calendar from WIRM:
<p style="text-align: center;"><a href="http://www.jasonconger.com/images/articleImages/WIRM/v1.2/usageCalendar_large.gif" target="_blank"><img class=" aligncenter" title="WIRM Calendar" alt="WIRM Calendar" src="http://www.jasonconger.com/images/articleImages/WIRM/v1.2/usageCalendar_large.gif" width="502" height="200" /></a></p>
<p style="text-align: left;">Here is what the calendar looks like in Splunk:</p>
<p style="text-align: center;"><a href="http://jasonconger.com/wp-content/uploads/2013/10/Splunk-Calendar.png" target="_blank"><img class="aligncenter  wp-image-1262" alt="Splunk Calendar" src="http://jasonconger.com/wp-content/uploads/2013/10/Splunk-Calendar-1024x464.png" width="473" height="215" /></a></p>
<p style="text-align: center;"></p>
<p style="text-align: left;"></p>
<p style="text-align: left;">If you want to see how to use this calendar visualization in your own Splunk environment, check out my <a title="Splunk Calendar Visualization" href="http://blogs.splunk.com/2013/10/14/calendar-custom-visualization-with-simple-xml/" target="_blank">Splunk blog post</a>.</p>
<p style="text-align: left;">The cool thing about having this available in Splunk is that it is reusable for various types of data including security, XenDesktop/XenApp, Microsoft Windows, Unix, etc.</p>
<p style="text-align: left;"></p>