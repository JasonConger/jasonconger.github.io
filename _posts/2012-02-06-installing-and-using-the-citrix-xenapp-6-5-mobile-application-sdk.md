---
id: 817
title: Installing and Using the Citrix XenApp 6.5 Mobile Application SDK
date: 2012-02-06T14:00:22-06:00
author: JasonConger
excerpt: In this post, we will go over the installation steps of the Citrix XenApp 6.5 Mobile Application SDK, explorer what is added to the XenApp 6.5 server during installation, and compile one of the samples given in the SDK.
layout: post
guid: http://www.jasonconger.com/?p=817
image: wp-content/uploads/2011/02/Citrix.png
categories:
  - Citrix XenApp
tags:
  - android
  - Citrix
  - iphone
  - mobility
  - SDK
  - XenApp
---
Now that we have <a title="Setting up an Android Emulator for use with Citrix XenApp 6.5 Mobile Application SDK" href="http://www.jasonconger.com/post/setting-up-an-android-emulator-for-use-with-citrix-xenapp-mobile-application-sdk/">setting up an Android emulator</a> out of the way, let's take a look at installing the Citrix XenApp 6.5 Mobile Application SDK and what the install does to a XenApp 6.5 server.

There are 2 parts that you need in order to develop applications that utilize mobile capabilities on a XenApp 6.5 server:
<ol>
	<li>The <a title="Citrix XenApp 6.5 Mobility Pack" href="http://citrix.com/English/ss/downloads/details.asp?downloadId=2317077&amp;productId=186" target="_blank">XenApp 6.5 Mobility Pack</a> - this is the part that goes on the XenApp 6.5 server.</li>
	<li>The <a title="Citrix XenApp 6.5 Mobile Application SDK" href="http://citrix.com/English/ss/downloads/details.asp?downloadId=2317078&amp;productId=186" target="_blank">Citrix XenApp 6.5 Mobile Application SDK</a> - this is the part you use to develop mobile applications.</li>
</ol>
&nbsp;
<h2>XenApp 6.5 Mobility Pack</h2>
When you install the Mobility Pack, 2 new services are added to your XenApp server:
<ol>
	<li>Citrix Location and Sensor Virtual Channel Service - this service enables a server side application to leverage Location and Sensor capabilities.</li>
	<li>Citrix Mobile Receiver Virtual Channel Service - this service enables a server side application to use mobile device capabilities.</li>
</ol>
These 2 virtual channels are kept separate for security reasons.  Maybe you want to have mobile device capabilities available, but you cannot enable GPS features due to security compliance.  Location services are disabled on the Citrix Receiver by default. The way to enable the location capabilities is via Citrix policies.  In order to use these policies, you will need to install the Citrix Group Policy Client-Side Extensions.  These extensions are part of the XenApp Mobility Pack .zip file.

This policy is located under ICA\Client Sensors\Location. Notice that by default, location is disabled.

<a href="http://www.jasonconger.com/wp-content/uploads/2012/02/CitrixMobilePolicy1.png"><img class="aligncenter  wp-image-824" title="Citrix Mobile Policy ICA\Client Sensors\Location" src="http://www.jasonconger.com/wp-content/uploads/2012/02/CitrixMobilePolicy1.png" alt="" width="480" height="244" /></a>

&nbsp;
<h2>Citrix XenApp 6.5 Mobile Application SDK</h2>
So, the <a title="Citrix XenApp 6.5 Mobile Application SDK Requirements" href="http://community.citrix.com/display/xa/XenApp+6.5+Mobile+Application+SDK+-+Requirements" target="_blank">requirements for the Citrix XenApp 6.5 Mobile Application SDK</a> state that you need Windows 7 64 bit (and the MSI is even named XenApp65MobileApplicationSdk64), but it installs to ..\Program Files (x86)\Citrix\MobilitySDK\.  I tried installing the SDK on a Windows 7 32 bit system as well and it worked, so I'm not sure if something absolutely will not work on 32 bit.

I'm using Visual Studio for the examples.  It appears that Visual Studio Express (free) will work as well, but I haven't tested that myself.

Anyway, the documentation that comes with the SDK is pretty comprehensive so I'm not going to rehash it here.  Since I will be showing you some of the examples using .Net, I do want to point out that you will need to run one of the following commands on your development machine in order for things to work:

```
Regsvr32 cmpcom.dll
```

```
Regsvr32 cmpcom64.dll
```

Notice that there is a 32 bit or a 64 bit DLL register. So again, not sure why Windows 7 64bit is a requirement for development. Anyway, make sure you run the appropriate command above as administrator, otherwise you may receive an error stating "<span style="color: #ff0000;">The module was loaded but the call to DllRegisterServer failed with error code 0x80070005</span>" (which is a permissions error).
<h2>Compiling Examples</h2>
The final part of this article will focus on compiling and using the examples that come with the SDK.  The one I'm going to point out here is the picker example.  This example uses the native device's UI to display a list of options.  The example is actually a console application that has no graphics, so it is actually using the local device's display mechanisms rather than trying to do some trickery on the XenApp server side.  So, here we go...
<ol>
	<li>Browse to \Program Files (x86)\Citrix\MobilitySDK\samples\native\showpicker</li>
	<li>Double click on showpicker.sln to open the solution in Visual Studio</li>
	<li>Build the solution by pressing F6</li>
	<li>This will create an executable in \Program Files (x86)\Citrix\MobilitySDK\samples\native\Win32\Debug\showpicker.exe</li>
	<li>Copy this showpicker.exe to your XenApp 6.5 server (I copied mine to \Program Files (x86)\Mobility\picker\showpicker.exe)</li>
	<li>Publish the application via Citrix AppCenter</li>
	<li>Launch the published application using an Android device (or <a title="Setting up an Android Emulator for use with Citrix XenApp 6.5 Mobile Application SDK" href="http://www.jasonconger.com/post/setting-up-an-android-emulator-for-use-with-citrix-xenapp-mobile-application-sdk/">emulator</a>) with the latest Citrix Receiver installed.</li>
</ol>
NOTE: You may receive an error message that states "<span style="color: #ff0000;">The program can't start because MSVCR100D.dll is missing from your computer...</span>"  Here's why - the solution was built in debug mode.  Thus, debug DLL's (notice the "D" in the DLL name) need to be on the XenApp 6.5 server.  Here is what you can do:

Copy:
<ul>
	<li>From:<strong> \Program Files (x86)\Microsoft Visual Studio 10.0\VC\redist\Debug_NonRedist\x86\Microsoft.VC100.DebugCRT\msvcr100d.dll</strong> on your development machine</li>
	<li>To:<strong> \Windows\SysWOW64\msvcr100d.dll</strong> on your XenApp 6.5 server</li>
</ul>
<div>You could technically build the solution in Release mode instead of Debug mode and be okay, but to perform remote debugging, you will want to have the debug DLL on your remote machine.  Speaking of debugging, here are 2 great write-ups on how to debug the mobile applications:</div>
<ul>
	<li>Jeff Muir - <a title="Debugging XAMA SDK Applications" href="http://citrixblogger.org/2011/12/19/debugging-xama-sdk-applications/" target="_blank">Debugging XAMA SDK Applications</a></li>
	<li>Andrew Borzycki - <a title="Debugging applications remotely with Visual Studio" href="http://forums.citrix.com/thread.jspa?threadID=300244&amp;tstart=0" target="_blank">Debugging applications remotely with Visual Studio</a></li>
</ul>
&nbsp;
<h2>The Result</h2>
Here is what the end result looks like.
<p style="text-align: center;"><a href="http://www.jasonconger.com/wp-content/uploads/2012/02/showpicker.png"><img class="aligncenter  wp-image-861" title="Citrix XenApp 6.5 Mobile Application SDK - Picker" src="http://www.jasonconger.com/wp-content/uploads/2012/02/showpicker.png" alt="" width="420" height="392" /></a></p>
Once you pick one of the colors, the console application will give you feedback on the chosen item.  When the appropriate receiver is available for iOS, then the native iOS selector would be shown with no code changes on the developer's part.  That is pretty cool!
<p style="text-align: left;">In the next article on this topic, I will show you how to use mobile device orientation to change what is displayed to an end user.  The example will include data and graphics.  Stay tuned...</p>