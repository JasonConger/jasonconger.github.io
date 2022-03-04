---
id: 702
title: Citrix XenApp 6.0 to XenApp 6.5 PowerShell Upgrade Utility Under the Hood
date: 2011-09-28T17:39:16-05:00
author: jason
excerpt: 'Citrix recently released XenApp 6.5.  However, there is not a way to do an in-place upgrade from XenApp 6.0 to XenApp 6.5.  This means that the Citrix administrator will have to uninstall XenApp 6.0 components and install XenApp 6.5 components.  Citrix released a PowerShell utility to help in this process, and in this post I break that utility down into a Visio flowchart to you can understand what is going on behind the scenes.'
layout: post
guid: http://www.jasonconger.com/?p=702
image: wp-content/uploads/2010/08/PowerShell.png
categories:
  - Citrix XenApp
tags:
  - Citrix
  - PowerShell
  - Visio
  - XenApp
---
Ever since I was a kid, I liked taking things apart.  Citrix recently came out with a <a title="Citrix XenApp 6.0 to 6.5 Upgrade Utility" href="http://support.citrix.com/article/CTX130614" target="_blank">PowerShell tool</a> to help administrators turn XenApp 6.0 servers into XenApp 6.5 servers because unfortunately (or fortunately depending on the way you look at it), there is no in-place upgrade option from XenApp 6.0 to XenApp 6.5.

This utility is a PowerShell script that performs the following:
<ul>
	<li>Checks to see if XenApp 6.0 is installed or not, and if the XenApp 6.5 installer is available.</li>
	<li>Prompts for a password to silently run the install process after reboot.</li>
	<li>Uninstalls XenApp 6.0 components. By default these include the Online-Plugin, Management Consoles, and XenApp Application Delivery role. Other components are included in the script and can be enabled for automatic removal.</li>
	<li>Installs XenApp 6.5 and, by default, joins the server to the farm as a worker.</li>
	<li>Verifies the join is successful by checking to see if the IMA service is running.</li>
</ul>
<div>I think this script is really cool so I had to take it apart to see just how the script was doing these things.  I made some notes in the form of a flowchart and have provided the flowchart here for your viewing pleasure.</div>
&nbsp;
<div><a title="Citrix XenApp 6.0 to 6.5 Upgrade Tool Visio Drawing" href="http://www.jasonconger.com/Visio drawings/XenApp Upgrade Tool/XenApp Upgrade Tool.vsd">Download the Visio Document</a></div>
<div>-or-</div>
<div><a title="Citrix XenApp 6.0 to 6.5 Upgrade Tool" href="http://www.jasonconger.com/Visio%20drawings/XenApp%20Upgrade%20Tool/XenApp%20Upgrade%20Tool.htm" target="_blank">Check out the interactive pan  &amp; zoom website (best viewed in Internet Explorer)</a></div>
<div>- or-</div>
<div>Click the picture below for .gif image of the flowchart</div>
<p style="text-align: center;"><a href="http://www.jasonconger.com/wp-content/uploads/2011/09/XenApp-Upgrade-Tool.gif" target="_blank"><img class="size-medium wp-image-703 aligncenter" style="border: 1px solid #000;" title="XenApp Upgrade Tool" src="http://www.jasonconger.com/wp-content/uploads/2011/09/XenApp-Upgrade-Tool-149x300.gif" alt="" width="134" height="270" /></a></p>
You can download the tool from Citrix's website -&gt; <a title="XenApp 6.0 to 6.5 Upgrade Utility" href="http://support.citrix.com/article/CTX130614" target="_blank">http://support.citrix.com/article/CTX130614</a>