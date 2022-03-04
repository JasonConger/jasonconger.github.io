---
id: 1515
title: Mobile Application Development Theorems
date: 2014-10-31T09:00:07-05:00
author: jason
excerpt: 'Mobility is so ubiquitous that it is almost not even a separate thing anymore.  I have had some experience building mobile apps and wanted to ponder some self-proclaimed theorems which are outlined in this article.'
layout: post
guid: http://www.jasonconger.com/?p=1515
image: wp-content/uploads/2014/10/mobile-dev.jpg
categories:
  - Mobility
tags:
  - Citrix
  - Development
  - Intel
  - mobility
  - PhoneGap
---
Mobility is so ubiquitous that it is almost not even a separate thing anymore. This creates a challenge for enterprises that offer BYOD mobile devices and corporate data access. How do you enable the mobile workforce with enterprise applications? One way is to roll your own mobile application to get the necessary data into the mobile user's hands. I have had some experience with this and wanted to ponder some self-proclaimed theorems which are outlined below.
<h1>Theorem #1</h1>
<blockquote style="font-weight: bold;">Mobile applications developed for native devices with native code are superior.</blockquote>
The following is an example of what you might need to build native mobile applications for various mobile devices:
<table class="blue_table">
<thead>
<tr>
<th>Platform</th>
<th>Development Framework</th>
<th>Language</th>
<th>IDE</th>
</tr>
</thead>
<tbody>
<tr>
<td>iOS</td>
<td>iOS SDK</td>
<td>Objective-C</td>
<td>Cocoa, Xcode</td>
</tr>
<tr>
<td>Android</td>
<td>Android SDK, Android NDK</td>
<td>Java, C/C++</td>
<td>Eclipse, NetBeans, IntelliJ IDEA</td>
</tr>
<tr>
<td>Windows Phone</td>
<td>.NET</td>
<td>C# and others</td>
<td>Visual Studio</td>
</tr>
<tr>
<td>Window 8 Metro Style Apps</td>
<td>WinRT</td>
<td>C++ / C# / VB.NET / Javascript</td>
<td>Visual Studio</td>
</tr>
<tr>
<td>Blackberry</td>
<td>Java ME + Optional Packages + API extensions</td>
<td>Java</td>
<td>Eclipse</td>
</tr>
<tr>
<td>ChromeOS</td>
<td>Webkit</td>
<td>HTML / CSS / Javascript</td>
<td>Many</td>
</tr>
</tbody>
</table>
Unfortunately, BYOD makes Theorem #1 hard. If you are going to go the native code route, you have to maintain a separate code base (with separate IDE's) for all possible devices your users will bring in. There are some other frameworks that I'll talk about in another article that help with this, but there is always a tradeoff.
<h1>Theorem #2</h1>
<blockquote style="font-weight: bold;">Apps that Look Better are Perceived to <u>be</u> Better.</blockquote>
Looks matter. Period. If you give an application to a user that has limited functionality but looks sexy, that application will be perceived as better than an application that has more functionality but is ugly. You know it's true.

Therefore, do yourself a favor and use a framework like one of the following:
<ul>
	<li><a href="http://jquerymobile.com/" target="_blank" rel="noopener">jQuery Mobile</a></li>
	<li><a href="http://getbootstrap.com/" target="_blank" rel="noopener">Twitter Bootstrap</a></li>
	<li><a href="http://www.sencha.com/products/touch/" target="_blank" rel="noopener">Sencha Touch</a></li>
	<li><a href="http://topcoat.io/" target="_blank" rel="noopener">TopCoat</a></li>
</ul>
These frameworks make it easy to make it look like you know what you are doing (at lease design-wise)
<h1>Theorem #3</h1>
<blockquote style="font-weight: bold;">Inverse Proportions are Everywhere.</blockquote>
<a href="http://www.jasonconger.com/wp-content/uploads/2014/10/inverse-proportions.png"><img class="aligncenter size-full wp-image-1524" src="http://www.jasonconger.com/wp-content/uploads/2014/10/inverse-proportions.png" alt="inverse proportions" width="640" height="247" /></a>

There is always a tradeoff somewhere. Referencing the picture above, think about painting a room. I can paint a room with a paintbrush and not waste too much paint. However, to speed things up, I use a paint roller and waste more paint. Therefore, the ease/speed in which I paint a room is inversely proportional to how much paint I waste.

The same thing is true for security. If everyone in the world had a public IP address with wide open ports, things would be pretty easy if there were not bad guys/girls out here. In the real world, there are bad guys/girls out there, so we have to attempt to keep them out. The security measures can be a burden on the user. Therefore, security is inversely proportional to usability.

That last picture up there is the icon for <a href="http://phonegap.com/" target="_blank" rel="noopener">PhoneGap</a>. PhoneGap is one of many frameworks that attempt to make Theorem #1 easier. You can read an <a href="http://www.jasonconger.com/post/introduction-to-phonegap/">introduction to PhoneGap here</a>.

There, of course, is a tradeoff. Building mobile apps with abstraction layers like <a href="http://www.jasonconger.com/post/introduction-to-phonegap/">PhoneGap</a> introduce translation. You may not have access to all mobile device features immediately, there can be a performance tax, and apps will tend to be bigger. Not all mobile frameworks are created equal and I will talk about some pros and cons of different frameworks (like Xamarin, Citrix Mobile SDK for Windows Apps, Intel XDK, etc.) in a separate article.

 
<h2>Wrapping Up</h2>
So, there you have it. My self-proclaimed theorems for mobile <a href="http://techwitty.com.au/">app development</a>. Agree? Disagree? Or, have something else to add? Just leave a comment below.

 