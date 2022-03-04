---
id: 725
title: 'Citrix Acquires ShareFile &#8211; a Citrix Service Provider Perspective'
date: 2011-10-14T22:05:40-05:00
author: jason
excerpt: 'Citrix Systems recently completed the acquisition of a company called ShareFile.  In this post, I take the perspective of a Citrix Service Provider (CSP) and dream up some ways that ShareFile could be used to add value to CSP subscribers.'
layout: post
guid: http://www.jasonconger.com/?p=725
image: wp-content/uploads/2011/02/Citrix.png
categories:
  - Citrix
tags:
  - Citrix
  - Cloud
  - ShareFile
---
<a title="Citrix Systems" href="http://www.citrix.com" target="_blank">Citrix Systems</a> recently completed the acquisition of a company called <a title="ShareFile" href="http://www.sharefile.com" target="_blank">ShareFile</a>.  ShareFile provides several services including file synchronization among many devices and creating custom-branded, password-protected space where you can exchange business files with clients easily and securely.

<a href="http://www.brianmadden.com/blogs/brianmadden/archive/2011/10/14/citrix-buys-dropbox-like-company-quot-sharefile-quot-all-eyes-in-palo-alto-to-see-what-citrix-will-do-next.aspx" target="_blank">Brian Madden wrote an analysis on this acquisition already</a>, but I wanted to share how this service can be used to supplement a Citrix Service Provider's (CSP) architecture.<span style="direction: ltr;"> </span>
<h2>File Transfer to the Cloud</h2>
One challenge that many CSP subscribers face is data upload to the cloud.  Now, Citrix has client drive mapping that can help transfer files from the subscriber's local workstation to the CSP cloud, but explaining the nuances of client drive redirection to subscribers can be a challenge.  Plus, the Citrix virtual channel for client drive mapping is not optimized for file transfers.

Now, image if the subscriber had a special folder on their workstation where they can put a file and it "magically" shows up in the CSP cloud.  That would be cool and ShareFile makes this possible (to be fair, <a title="Dropbox" href="http://dropbox.com" target="_blank">DropBox </a>could be used to do the same thing).

<a href="http://www.jasonconger.com/wp-content/uploads/2011/10/Citrix-ShareFile-Sync.jpg"><img class="aligncenter size-medium wp-image-729" title="Citrix ShareFile Sync" src="http://www.jasonconger.com/wp-content/uploads/2011/10/Citrix-ShareFile-Sync-300x236.jpg" alt="" width="300" height="236" /></a>

&nbsp;
<h2></h2>
<h2>Mobile Device Synchronization and Offline File Access</h2>
People use multiple devices to access CSP cloud resources.  Imagine ShareFile synchronization components being available as a Citrix Receiver plugin.  Then, certain files could be made available on mobile devices.  Picture this, you need to access an Excel spreadsheet you created in the CSP's cloud from your iPad and you do not have WiFi or 3G access available.  Normally, you would be out of luck.  But, if this file was synchronized to your iPad via ShareFile, you would have mobile offline access to the file.<span style="direction: ltr;"> </span>
<h2>Sharing Files with non-CSP Subscribers</h2>
ShareFile allows you to create a custom-branded, password-protected space where you can exchange business files with clients easily and securely.  This is kind of ShareFile's forte.  CSP subscribers oftentimes want to share a file beyond the boundaries of the CSP's firewall.  ShareFile makes this as easy as sending an email.  Since everything is encrypted along the way, could this also be used as a make-shift email encryption mechanism?  <span style="direction: ltr;">The following graphic depicts all the pieces together:</span>

<a href="http://www.jasonconger.com/wp-content/uploads/2011/10/Citrix-ShareFile-Overview.jpg"><img class="aligncenter size-medium wp-image-728" title="Citrix ShareFile Overview" src="http://www.jasonconger.com/wp-content/uploads/2011/10/Citrix-ShareFile-Overview-300x233.jpg" alt="" width="300" height="233" /></a>

&nbsp;

&nbsp;

&nbsp;