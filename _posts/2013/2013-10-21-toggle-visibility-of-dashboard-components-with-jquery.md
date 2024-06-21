---
title: Toggle Visibility of Dashboard Components with jQuery
date: 2013-10-21
author: jason
excerpt: Sometimes a Splunk dashboard can become too busy to focus. This is especially true when you have both summary and detailed data on a Key Performance Indicator (KPI) dashboard. This blog will show you how to toggle the visibility of Splunk dashboard components
layout: post
thumbnail-img: /assets/img/2013/10/21/User-Experience-Dashboard.png
share-img: /assets/img/2013/10/21/User-Experience-Dashboard.png
categories:
  - Splunk Blog
tags:
  - Splunk, Citrix, XenApp
---

{: .box-note}
Originally posted on the Splunk official blog: [https://www.splunk.com/en_us/blog/tips-and-tricks/toggle-visibility-of-dashboard-components-with-jquery.html](https://www.splunk.com/en_us/blog/tips-and-tricks/toggle-visibility-of-dashboard-components-with-jquery.html){:target="_blank"}

Sometimes a dashboard can become too busy to focus. This is especially true when you have both summary and detailed data on a Key Performance Indicator (KPI) dashboard. An example of this would be the [Citrix XenApp app](https://apps.splunk.com/app/1752/) User Experience dashboard as seen below:

![XenApp Dashboard](/assets/img/2013/10/21/User-Experience-Dashboard.png)

This dashboard scores the various components that impact a user’s experience – things like network latency, server performance, hypervisor performance, shared storage latency, Netscaler throughput, etc.  There is just too much information to show all at once, so we hide parts of the dashboard and allow the user to view the detailed information of only what they want to see.

## Toggle with Simple XML
Adding toggle buttons to hid/show parts of your dashboard isn’t all that hard. To start out with Simple XML, we add a stylesheet and script to the dashboard.

~~~
<dashboard stylesheet="toggle.css" script="toggle.js">
~~~

The stylesheet initially hides the second row by:
1. Setting visibility: none.  Note: using display: none will make charts not render.
2. Setting the height of the row to 0px.  This is done because visibility: none will still leave a gap in the HTML where the element would have rendered.

The javascript sets up the toggle function by:
1. Using jQuery to add a toggle button to the element we want
2. Setting up a click handler on the toggle button created above

Here is the end result:
![Toggle](/assets/img/2013/10/21/SimpleXMLToggle.gif)

## Toggle with a HTML Dashboard
The concept is the same as the Simple XML example.  By using HTML, we get a little more control of when our toggle button is rendered as well as the position of the chart.

This function will asynchronously render the toggle button when the chart has finished its search:
~~~
postSourceTime.on('search:done', function(properties) {
// Set up toggle drop down for Host Performance
$("#imgToggle").show();
$("#imgToggle").click(function(){
toggle($(this), $("#chartSourceCount"));
});
});
~~~

Here is the end result:
![HTML Toggle](/assets/img/2013/10/21/HTMLToggle.gif)

You can download the example source here (note: Splunk 6 is required for these to work): https://github.com/JasonConger/SplunkToggleExample