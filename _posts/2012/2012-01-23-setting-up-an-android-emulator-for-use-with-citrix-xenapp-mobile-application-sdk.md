---
id: 800
title: Setting up an Android Emulator for use with Citrix XenApp 6.5 Mobile Application SDK
date: 2012-01-23T10:00:57-06:00
author: JasonConger
excerpt: 'One of the coolest SDKs I’ve seen come out in quite a while is the Citrix XenApp 6.5 Mobile Application SDK.  As of this writing, only the Android version of the Citrix Receiver is supported so I will show you how to set up an Android emulator with the Citrix Receiver for testing purposes.'
layout: post
guid: http://www.jasonconger.com/?p=800
image: wp-content/uploads/2012/01/Android.png
categories:
  - Citrix
tags:
  - android
  - Citrix
  - mobility
  - SDK
  - XenApp
---
One of the coolest SDKs I’ve seen come out in quite a while is the <a title="Citrix XenApp 6.5 Mobile Appliation SDK" href="http://community.citrix.com/display/xa/XenApp+6.5+Mobile+Application+SDK" target="_blank">Citrix XenApp 6.5 Mobile Application SDK</a>. Citrix defines the XenApp 6.5 Mobile Application SDK as "... a rich tool kit for developers to write touch-friendly, mobilized applications that are hosted on Citrix XenApp and delivered to any device with Citrix Receiver. These mobilized applications are able to leverage a wide set of mobile device functionality including GPS, sensors, cameras, and device buttons in the same way that locally running, native applications do."

As of this writing, only the Android version of the Citrix Receiver is supported (iOS is on the way).  Since I do not own any Android devices and I was anxious to get started, I had to set up an emulator and install the Citrix Receiver to get going with the SDK.  Here is how I did it.

<h2>Install the Android SDK</h2>
Go to the Android SDK download page (<a title="Android SDK" href="http://developer.android.com/sdk/index.html" target="_blank">http://developer.android.com/sdk/index.html</a>) and pick the correct installer for your platform. I’m using Windows, so I chose the .exe installer file.  After you run this .exe, you still do not have the emulator.  The reason for this is the Android SDK archive initially contains only the basic SDK tools. It does not contain an Android platform or any third-party libraries. You must install the Platform-tools and at least one version of the Android platform using the SDK Manager.

<a href="http://www.jasonconger.com/wp-content/uploads/2012/01/8.png"><img class="aligncenter size-medium wp-image-801" title="Android SDK Manager" src="http://www.jasonconger.com/wp-content/uploads/2012/01/8-300x214.png" alt="Android SDK Manager" width="300" height="214" /></a>

I installed the Android SDK Platform-tools and all options for Android 4.0.3.

After the install completes, be sure to add <strong>%ProgramFiles%\Android\android-sdk\platform-tools</strong> to your PATH environment variable.  This will be handy later for installing the Citrix Receiver.

<h2>Create an Android Virtual Device</h2>
After the installs complete, you can launch Android Virtual Device Manager (AVD Manager). This can be found in the Windows start menu under Android SDK Tools \ AVD Manager. AVD Manager is used to create various virtual devices running the Android OS.

<a href="http://www.jasonconger.com/wp-content/uploads/2012/01/2.png"><img class="aligncenter size-medium wp-image-803" title="Android Virtual Device for XenApp 6.5 Mobile Appliction SDK" src="http://www.jasonconger.com/wp-content/uploads/2012/01/2-190x300.png" alt="Android Virtual Device for XenApp 6.5 Mobile Appliction SDK" width="189" height="300" /></a>

As you can see, I created an Android 4.0.3 device with 100 MiB of local storage. The more storage you add to your AVD, the longer it will take to boot. Since this AVD is only being used for XenApp 6.5 testing, I only allocated 100 MiB. The first boot of your AVD will take a little longer than subsequent boots.

<h2>Download the Citrix Receiver for Android</h2>
Now that we have a functioning Android emulator, we need to get the Citrix Receiver installed. The first thing we need to do is download the .apk (Android Package) file. Normally, I would just go to <a title="Download Citrix Receiver" href="http://www.citrix.com/receiver" target="_blank">http://www.citrix.com/receiver</a> and choose “Android”. But, as of this writing, when you do that, you are redirected to the Android Marketplace. Unfortunately, Android Marketplace does not work on the Android Emulator. So, here is what you can do instead:
Go to <a href="http://www.citrix.com/downloads" target="_blank">http://www.citrix.com/downloads</a> and choose “Receiver for Android” from the drop down list. From there, you can select the Android client and download the .apk.

<h2>Install the Citrix Receiver for Android</h2>
Ok, so now we have a functioning Android emulator and the Citrix Receiver downloaded. The final step is to install the Citrix Receiver onto the emulator. Here’s how:
<ol>
	<li>Copy the .apk file to %ProgramFiles%\Android\android-sdk\tools</li>
	<li>Open a command prompt and change the directory to %ProgramFiles%\Android\android-sdk\tools</li>
	<li>With the AVD you created running, execute the following command:</li>
</ol>
```
adb install <name of Citrix Receiver>.apk
```

<a href="http://www.jasonconger.com/wp-content/uploads/2012/01/21.png"><img class="aligncenter size-medium wp-image-805" title="Citrix Receiver for Android" src="http://www.jasonconger.com/wp-content/uploads/2012/01/21-300x276.png" alt="Citrix Receiver for Android" width="300" height="275" /></a>

You now have a fully functional Citrix Receiver running on an Android emulator.  My next post shows you <a title="Installing and Using the Citrix XenApp 6.5 Mobile Application SDK" href="http://www.jasonconger.com/post/installing-and-using-the-citrix-xenapp-6-5-mobile-application-sdk/">how to set up a development environment to utilize the Mobile Application SDK and compile some of the examples</a>.