---
id: 6
title: How to Install the Citrix XenApp 6 PowerShell Cmdlets
date: 2010-08-02T19:43:22-05:00
author: JasonConger
excerpt: PowerShell is the new API for Citrix XenApp starting with version 6. Whether you want to write interactive applications or work with your XenApp farm via command line, you first need to set up the XenApp 6 PowerShell SDK. This post will step you through setting up the Citrix XenApp 6 PowerShell SDK in your environment.
layout: post
guid: /post/How-to-Install-the-Citrix-XenApp-6-PowerShell-Cmdlets.aspx
image: wp-content/uploads/2010/08/PowerShell.png
categories:
  - Citrix XenApp
  - PowerShell
tags:
  - PowerShell
  - XenApp
---
PowerShell is the new API for Citrix XenApp starting with version 6.&nbsp; Whether you want to write interactive applications or work with your XenApp farm via command line, you first need to set up the XenApp 6 PowerShell SDK.&nbsp; This post will step you through setting up the Citrix XenApp 6 PowerShell SDK in your environment.
<h2>Installing the Citrix XenApp 6 PowerShell cmdlets</h2>
Before we get started, you first need to download and install the Citrix XenApp PowerShell SDK (which includes the XenApp cmdlets). You can download the SDK here: <a title="http://community.citrix.com/display/xa/XenApp+6+PowerShell+SDK" href="http://community.citrix.com/display/xa/XenApp+6+PowerShell+SDK.">http://community.citrix.com/display/xa/XenApp+6+PowerShell+SDK.</a>

I recommend installing this on one of your XenApp 6 servers.&nbsp; Technically, you can install this on a workstation and use remoting to remote all the commands to a XenApp 6 server, but it is very messy and doesn’t always work from my experience.&nbsp; Anyway, during the setup of the SDK, you will be asked to set the PowerShell execution policy to AllSigned.&nbsp; It is a good idea to leave this box checked to prevent malicious PowerShell scripts from ruining your day.

<a href="http://www.jasonconger.com/images/articleImages/XA6%20SDK%20Execution%20Policy.png" target="_blank"><img style="display: block; float: none; margin-left: auto; margin-right: auto; border-width: 0px;" title="XA6 SDK Execution Policy" src="http://www.jasonconger.com/images/articleImages/XA6%20SDK%20Execution%20Policy_thumb.png" border="0" alt="XA6 SDK Execution Policy" width="400" height="339" /></a>
<h2>Adding the Snapins to your Runspace</h2>
After installation is complete, the assemblies will be loaded into the GAC (Global Assembly Cache).&nbsp; Every time you want to use the Citrix XenApp cmdlets, you will need to add the snapins to your PowerShell runspace.&nbsp; This can be done by launching PowerShell and using the Add-PSSnapin command as seen below:

<a href="http://www.jasonconger.com/images/articleImages/Citrix%20PSSnapin.png" target="_blank"><img style="display: block; float: none; margin-left: auto; margin-right: auto; border-width: 0px;" title="Citrix PSSnapin" src="http://www.jasonconger.com/images/articleImages/Citrix%20PSSnapin_thumb.png" border="0" alt="Citrix PSSnapin" width="400" height="341" /></a>

Adding the snapins will allow you to execute all the XenApp cmdlets.&nbsp; Alternatively,&nbsp; you can launch PowerShell from the Citrix/XenApp Server SDK folder in the&nbsp; start menu as seen below.&nbsp; This will launch a PowerShell runspace with all the Citrix snapins loaded and ready to go.&nbsp;

<a href="http://www.jasonconger.com/images/articleImages/XenApp%20PoSH.png" target="_blank"><img style="display: block; float: none; margin-left: auto; margin-right: auto; border-width: 0px;" title="XenApp PoSH" src="http://www.jasonconger.com/images/articleImages/XenApp%20PoSH_thumb.png" border="0" alt="XenApp PoSH" width="406" height="437" /></a>

You are now ready to start PowerShelling your Citrix environment.