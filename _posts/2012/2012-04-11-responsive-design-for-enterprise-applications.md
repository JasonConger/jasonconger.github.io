---
id: 881
title: Responsive Design for Enterprise Applications
date: 2012-04-11T07:37:46-05:00
author: JasonConger
excerpt: 'Responsive Design that web developers use can now be applied to Enterprise Applications thanks to the Citrix Mobile SDK.  This post will give you a glimpse of what is possible to get your wheels turning.'
layout: post
image: wp-content/uploads/2012/04/Responsive-Design-Icon.png
categories:
  - Citrix XenApp
tags:
  - mobility
  - Responsive Design
  - XAMP
  - XenApp
---
Have you heard of <a title="Responsive Web Design" href="http://en.wikipedia.org/wiki/Responsive_Web_Design" target="_blank" rel="noopener">Responsive Web Design</a>?  The term was coined by Ethan Marcotte in his <a title="Responsive Design on A List Apart" href="http://www.alistapart.com/articles/responsive-web-design/" target="_blank" rel="noopener">article on A List Apart</a>.  The gist of the idea is that web pages can be designed to adapt or respond to the entity that is viewing it.  The Boston Globe's website is a good example of responsive design.  You can see by the screenshots below, that given enough screen real estate, the website has a 3 column layout.  But, as the screen width starts to shrink, the layout is adjusted to 2 columns and then 1 column.  Also, the navigation changes to better suit the layout and images are adjusted or hidden.

<a href="/wp-content/uploads/2012/04/Boston-Globe-3-column.png" target="_blank"><img src="/wp-content/uploads/2012/04/Boston-Globe-3-column.png" width="400" /></a>

<a href="/wp-content/uploads/2012/04/Boston-Globe-2-column.png" target="_blank"><img src="/wp-content/uploads/2012/04/Boston-Globe-2-column.png" width="400" /></a>

<a href="/wp-content/uploads/2012/04/Boston-Globe-1-column.png" target="_blank"><img src="/wp-content/uploads/2012/04/Boston-Globe-1-column.png" width="400" /></a>

<h2>Applying Responsive Design to Enterprise Applications</h2>
Just like web pages, enterprise applications are starting to get viewed on a myriad of devices.  What if we could take some of the same techniques web designers are using and apply that to enterprise applications?  Well, as it turns out, we can with the help of the [Citrix XenApp 6.5 Mobile Application SDK]({% post_url 2012-02-06-installing-and-using-the-citrix-xenapp-6-5-mobile-application-sdk %}).  By using the Mobile Application SDK, enterprise applications that are hosted on a XenApp 6.5 server can respond to the type of device using the application.
<h3>Responsive Application Example</h3>
As an example, I wrote an application that takes data from EdgeSight about the types of Citrix clients used in an environment.  The application displays this information in a chart as well as a table.  I then published this application from AppCenter on a XenApp 6.5 server and launched it using a fat client.  You will notice that both the chart and the data table are shown as well as a menu strip at the top to select a chart type.

<a href="http://www.jasonconger.com/wp-content/uploads/2012/03/Responsive-Design-Demo-Windows.png" target="_blank"><img class="aligncenter size-medium wp-image-884" title="Responsive Design Demo (Windows)" src="http://www.jasonconger.com/wp-content/uploads/2012/03/Responsive-Design-Demo-Windows.png" alt="" width="400" /></a>

&nbsp;

Now, if you launch the exact same application from the exact same server using a mobile device, some very interesting things happen:

<a href="/wp-content/uploads/2012/04/Responsive-Design-Mobile-1.png" target="_blank"><img src="/wp-content/uploads/2012/04/Responsive-Design-Mobile-1.png" width="200" /></a>
<a href="/wp-content/uploads/2012/04/Responsive-Design-Mobile-2.png" target="_blank"><img src="/wp-content/uploads/2012/04/Responsive-Design-Mobile-2.png" width="200" /></a>
<a href="/wp-content/uploads/2012/04/Responsive-Design-Mobile-4.png" target="_blank"><img src="/wp-content/uploads/2012/04/Responsive-Design-Mobile-4.png" width="200" /></a>
<a href="/wp-content/uploads/2012/04/Responsive-Design-Mobile-3.png" target="_blank"><img src="/wp-content/uploads/2012/04/Responsive-Design-Mobile-3.png" width="200" /></a>

<ol style="list-style-type: decimal;">
 	<li>Only the chart is shown initially.  If you rotate the device, only the data table is shown.</li>
 	<li>The application's window chrome is gone.</li>
 	<li>The width and the height of the application were changed to the width and height of the device.</li>
 	<li>Tapping the chart image brings up the device's native picker.</li>
 	<li>Changing the orientation of the device changes the display.</li>
</ol>

Check out this short video for a demo:

<iframe width="560" height="315" src="https://www.youtube.com/embed/bqEMjvjoi2A" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<h2>Try It Out Yourself</h2>
Want to try it out yourself?  I have made the program and the source available so you can beat it up and come up with some more ideas.  You can <a title="Responsive Design Prototype" href="http://www.jasonconger.com/enterprise-application-responsive-design-prototype">download it here</a>.