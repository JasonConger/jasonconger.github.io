---
id: 10
title: 'MFCOM to PowerShell: How to Make the Transition'
date: 2010-06-08T21:29:00-05:00
author: jason
excerpt: "MFCOM has been the de facto standard for programmatically interfacing with Citrix XenApp. Whether you wanted to write a simple script or develop an application that interfaced with XenApp, MFCOM was the answer. Now, Citrix is committed to building their management architecture on PowerShell--not just for XenApp, but for all Citrix products. That's great news for standardization across platforms and aligning with Microsoft on using PowerShell for management architectures. Now, the question is how do you take what you know about MFCOM and translate that to PowerShell?"
layout: post
guid: /post/MFCOM-to-PowerShell-How-to-Make-the-Transition.aspx
permalink: /2010/06/08/mfcom-to-powershell-how-to-make-the-transition/
image: wp-content/uploads/2010/08/PowerShell.png
categories:
  - Citrix XenApp
  - MFCOM
  - PowerShell
tags:
  - API
  - BriForum
  - Citrix
  - MFCOM
  - PowerShell
  - XenApp
---
As you may of may not already know, Citrix has committed to building their management architecture (and SDK) on PowerShell – not just for XenApp, but for all Citrix products.
<div style="border: 1px solid #000; padding: 5px; background-color: #ececec;">

In XenApp 6.0, MFCOM is not available anymore. The underlying architecture has changed dramatically enough to make backward compatibility with MFCOM impossible. The replacement for MFCOM is PowerShell. MFCOM-based scripts need to be completely re-written in XenApp cmdlets. In most cases, the conversion should be simple and most MFCOM scripts can be replaced with one-liner PowerShell commands.

Source: Citrix XenApp 6 PowerShell SDK reference manual.

</div>
That's great news for standardization across platforms and aligning with Microsoft on using PowerShell for management architectures.  But, that begs the question - what do you do about all those scripts and applications that leverage MFCOM going forward?  I’ll be <a href="http://briforum.com/html/sessions.html#MFCOM" target="_blank">presenting a session</a> at BriForum 2010 with <a href="http://bsonposh.com/" target="_blank">Brandon Shell</a> about this very topic.  The session will cover:
<ul>
	<li>General Object Orientation</li>
	<li>Specific Citrix XenApp objects</li>
	<li>Examples of how scripts and applications were done with MFCOM</li>
	<li>Converting scripts and applications to use PowerShell</li>
	<li>PowerShell remoting</li>
	<li>Availability of PowerShell cmdlets on XenApp 5 and XenApp 6</li>
	<li>C# applications leveraging the PowerShell command wrapper</li>
</ul>
<a href="http://briforum.com/" target="_blank">BriForum</a> takes place from June 15th to June 17th at the Hilton Chicago Hotel.  There is still time to register.