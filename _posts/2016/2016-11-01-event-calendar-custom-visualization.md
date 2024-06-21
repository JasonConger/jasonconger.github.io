---
title: Calendar Custom Visualization with Splunk Simple XML
author: jason
excerpt: Awhile back, I wrote a blog post about using a custom calendar visualization in Simple XML dashboards.  To accomplish this, I used a technique sometimes referred to as escape hatching JavaScript into Simple XML.  While this works okay for a developer, the technique does not lend itself well to the end user. So, I turned this into a downloadable custom Splunk visualization.  Enjoy!
layout: post
thumbnail-img: /assets/img/2016/11/01/calendar_blog.jpg
share-img: /assets/img/2016/11/01/calendar_blog.jpg
categories:
  - Splunk Blog
tags:
  - Splunk
---
{: .box-note}
Originally posted on the Splunk official blog: [https://www.splunk.com/en_us/blog/tips-and-tricks/event-calendar-custom-visualization.html](https://www.splunk.com/en_us/blog/tips-and-tricks/event-calendar-custom-visualization.html){:target="_blank"}

Awhile back, I wrote a blog post about using a custom [calendar visualization in Simple XML dashboards]({% post_url /2013/2013-10-14-calendar-custom-visualization-with-simple-xml %}).  To accomplish this, I used a technique sometimes referred to as escape hatching JavaScript into Simple XML.    While this works okay for a developer, the technique does not lend itself well to the end user.

## Splunk Custom Visualizations
Splunk 6.4 introduced reusable [custom visualizations](http://docs.splunk.com/Documentation/Splunk/latest/AdvancedDev/CustomVizDevOverview) which allows a developer to package up a visualization and integrate it into Splunk just like the native visualizations.  This also addresses the limitation mentioned above – meaning any end user can use the visualization without mucking around with the Simple XML.

So, revisiting the older escape hatch calendar technique, I thought it would be a good exercise to convert the calendar into a custom visualization.  [The calendar is now available on Splunkbase](https://splunkbase.splunk.com/app/3372), and several new features have been added.

## Using the Calendar in Splunk
The calendar expects a search exposing _time and a count.  The timechart search command does a good job of this.  For example, the following search:

~~~
index=_internal | timechart span=1d dc(sourcetype) AS sourcetypes dc(source) as sources dc(host) as hosts
~~~

produces some nice tabular data like so:

![calendar_tabular](/assets/img/2016/11/01/calendar_tabular.jpg)

The calendar visualization can take this data and visualize it on a calendar like this:

![calendar_blog](/assets/img/2016/11/01/calendar_blog.jpg)

There are some formatting options as well.

![calendar_format](/assets/img/2016/11/01/calendar_format.jpg)

Try it out yourself and go [download it on Splunkbase](https://splunkbase.splunk.com/app/3372/).

Special shout-out to the Summer Interns who helped… Yue Kang, Nic Stone, and Phillip Tow!