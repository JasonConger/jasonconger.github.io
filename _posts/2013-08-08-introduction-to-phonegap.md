---
id: 1207
title: Introduction to PhoneGap
date: 2013-08-08T08:00:54-05:00
author: jason
excerpt: 'Your end users expect mobile access to enterprise resources now.  Unfortunately, our traditional remote access methods do not lend themselves easily to mobile form factors.  So, we are left with the choice to use 3rd party apps, "mobilize" existing apps, or build our own.  This article will address one of the players aimed at helping you build your own mobile apps with less effort.'
layout: post
guid: http://www.jasonconger.com/?p=1207
permalink: /2013/08/08/introduction-to-phonegap/
image: wp-content/uploads/2013/08/phonegap-1.png
categories:
  - Mobility
tags:
  - android
  - iOS
  - mobility
  - PhoneGap
---
<h1>Mobile Enterprise Apps - Virtualize, Buy, or Build?</h1>
When it comes to mobile enterprise applications, you basically have 3 choices:
<ol>
	<li>Virtualize what you have (via Citrix HDX, RDP, VMware PCoIP, etc.)</li>
	<li>Buy something from a 3rd party</li>
	<li>Build something yourself</li>
</ol>
There are use cases for each of these, but I'm going to focus on one way to build something yourself.  In this case, I'm going to cover <a title="PhoneGap" href="http://phonegap.com/" target="_blank">PhoneGap</a>.

&nbsp;
<h1>What is PhoneGap?</h1>
PhoneGap is a framework for building mobile applications using only HTML, CSS, and Javascript.  This removes the complexity of using multiple programming languages for the various mobile platforms out there.  The PhoneGap framework gives developers access to almost all of the device's features such as GPS, Camera, Accelerometer, Notifications, etc. via the included Javascript library.

The easiest way I think of it is like this - PhoneGap is a specialized web browser without a user interface.  There is a specialized web browser for each native platform - iOS, Android, Windows Phone, Blackberrry, etc.  This allows you to reuse your code across platforms; however, this does not allow you to use one IDE for all platforms.  Each PhoneGap app you build gets complied into this chrome-less browser and delivered just like any other native application.  The end result is an individual .ipa (for iOS), .apk (for Android), .xap (for Windows Phone), etc..  Therefore, you still have the ability to use all your EMM and MAM tools you may already have to manage these apps. Each time you build a new PhoneGap app, you get a new .ipa, .apk, .xap, etc. that includes the chrome-less browser and your HTML, CSS, JavaScript, etc.
<p style="text-align: center;"><a href="http://www.jasonconger.com/wp-content/uploads/2013/08/PhoneGap.png"><img class="aligncenter size-medium wp-image-1216" alt="PhoneGap" src="http://www.jasonconger.com/wp-content/uploads/2013/08/PhoneGap-300x274.png" width="300" height="274" /></a></p>

<h1>What's needed to develop with PhoneGap?</h1>
You still need to use the various platform IDE's to develop an app with PhoneGap.  For instance, I developed a simple app for iPhone and Android.  For iPhone, I used Xcode to create and compile the PhoneGap application.  For Android, I used Eclipse to create and compile the application.  I had to set up each IDE to use the PhoneGap framework, but that is all documented pretty well.

I started with Xcode and got things working liked I wanted for iPhone.  Then, I literally just copied and pasted my HTML, CSS, and images over to Eclipse and the Android app just worked.  My app is very simple, but here are the results:

[gallery ids="1218, 1229" size="medium"]

[gallery ids="1222, 1221" size="medium"]
<h1></h1>
<h1>What is the catch?</h1>
PhoneGap is free.  Even though <a href="http://www.businesswire.com/news/home/20111003006347/en/Adobe-Announces-Agreement-Acquire-Nitobi-Creator-PhoneGap" target="_blank">Adobe acquired PhoneGap in 2011</a>, the PhoneGap code was contributed to the Apache Software Foundation (ASF) under the name <a href="http://cordova.io/">Apache Cordova</a> and graduated to top-level project status in October 2012.

I have noticed that some PhoneGap apps seem to run a little sluggish when dealing with animations as compared to traditional apps.  I'm assuming this is due to the chrome-less browser nature of PhoneGap applications.  However, when dealing with enterprise applications, I do not see this as being a big issue.

The other issue I see for enterprises (and this is not unique to PhoneGap) is data access.  <a title="Virtual Desktops and Applications are not as important as you think" href="http://www.jasonconger.com/post/virtual-desktops-and-applications-are-not-as-important-as-you-think/" target="_blank">Your application is really just another front end for data</a>.  You have to provide enterprise data access somehow.  This can be done via VPN, or using local device storage and sync strategies.  Like I said, this isn't unique to PhoneGap, but it is something to think about.
<h1>Conclusion</h1>
PhoneGap lowers the bar of entry into "native" device applications because there are a lot of HTML, CSS, JavaScript developers out there.  Oftentimes, enterprises may already employ people with expertise in these areas.  If not, it is more budget-friendly to hire a Web developer as opposed to developers that specialize in Objective-C and/or Java and/or .Net languages.  You get the benefits of maintaining one code base across multiple devices.  All of your EMM/MAM products should work with PhoneGap applications.

On the contrast, you are not developing "real native" code and devices may come out with features faster than the PhoneGap framework can accommodate.  You still have a data problem.  If your app requires a lot of fancy animated graphics, then PhoneGap may or may not suit your needs.

So, there you go.  If you have experience with PhoneGap or just something to add, feel free to leave a comment below.

&nbsp;