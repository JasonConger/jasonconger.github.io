---
title: Animate a Splunk SimpleXML Dashboard Elements with a Carousel
author: jason
excerpt: Many years ago, as a learning exercise, I created a Citrix web interface that took some boring static icons and made them spin around like a carousel. This interface was never meant to be particularly useful, but it worked and looked nice. Thinking back on that carousel, I wondered if I could create something similar in Splunk. Spoiler alert - the answer is "yes".
layout: post
thumbnail-img: /assets/img/2017/04/25/SimpleXMLAnimation.gif
share-img: /assets/img/2017/04/25/SimpleXMLAnimation.gif
categories:
  - Splunk Blog
tags:
  - Splunk, Citrix
---
{: .box-note}
Originally posted on the Splunk official blog: [https://www.splunk.com/en_us/blog/tips-and-tricks/animate-simplexml-dashboard-elements-with-a-carousel.html](https://www.splunk.com/en_us/blog/tips-and-tricks/animate-simplexml-dashboard-elements-with-a-carousel.html){:target="_blank"}

Many years ago, as a learning exercise, I created a Citrix web interface that took some boring static icons and made them spin around like a carousel.  Check out a video here:

<iframe width="864" height="696" src="https://www.youtube.com/embed/C3pxtRmPOiI" title="Citrix Web Interface with Microsoft Silverlight and AJAX" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

This interface was never meant to be particularly useful, but it worked and looked nice.

Fast forward to today.  Thinking back on that carousel, I wondered if I could create something similar in Splunk.  After all, SimpleXML renders to HTML and JavaScript in the end.  My thought was, "what if we can make Single Value visualizations spin around?  That could actually be useful in a NOC."  So, I set out to find a JavaScript library that could do this ([which I did find](https://github.com/specious/cloud9carousel){:target="_blank"}), and wired it up to the dashboard.  It was shockingly easy to do.  Here is the end result:

![Carousel](/assets/img/2017/04/25/SimpleXMLAnimation.gif)

# The SimpleXML Dashboard
First, create a dashboard that has a row of Single Value visualizations.  I borrowed some visualizations from the Dashboard Examples app.  The important part of the dashboard XML is adding the JavaScript and adding an ID to the row as seen below:

~~~
<dashboard stylesheet="carousel.css" script="carousel.js">
    <label>Single Value Carousel</label>
        <row id="showcase">
~~~

The full text of the dashboard can be found here -> [https://github.com/JasonConger/mte_visualizations/blob/master/app/mte_visualizations/default/data/ui/views/carousel2.xml](https://github.com/JasonConger/mte_visualizations/blob/master/app/mte_visualizations/default/data/ui/views/carousel2.xml){:target="_blank"}

# The JavaScript for the Dashboards
The next step is to create a JavaScript "shim" between the dashboard and the carousel code.  Here is how it is done:

Excerpt from `carousel.js`:

~~~
require([
    'underscore',
    'jquery',
    'splunkjs/mvc',
    'splunkjs/mvc/simplexml/ready!',
            '/static/app/mte_visualizations/js/lib/jquery.cloud9carousel.js'
], function(_, $, mvc, Carousel) {
    var showcase = $("#showcase");
            showcase.Cloud9Carousel( {
            ...options...
~~~

Notice the `$("#showcase")` part which finds the element with an ID of "showcase" – that finds the row of Single Value visualizations.

Next, we just let the Cloud9Carousel JavaScript library do its thing.  There are several options you can set.  Check out the source of carousel.js to see all the options I used.  [https://github.com/JasonConger/mte_visualizations/blob/master/app/mte_visualizations/appserver/static/carousel.js](https://github.com/JasonConger/mte_visualizations/blob/master/app/mte_visualizations/appserver/static/carousel.js){:target="_blank"}

# Conclusion
Like I said, this was much easier than I thought and somewhat of a learning exercise.  But, the technique used here to blend 3rd party JavaScript libraries with existing Splunk dashboards really isn't that hard and can be quite useful.