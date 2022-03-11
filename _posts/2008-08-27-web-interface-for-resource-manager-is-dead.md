---
id: 22
title: Web Interface for Resource Manager is Dead
date: 2008-08-27T10:53:00-05:00
author: JasonConger
excerpt: 'I have gotten several comments (online and offline) and emails asking about future developments surrounding Web Interface for Resource Manager.  Well, Web Interface for Resource Manager as you know today is officially dead.  There are actually several reasons for this.  Read on for more information...'
layout: post
guid: /post/Web-Interface-for-Resource-Manager-is-Dead.aspx
image: wp-content/uploads/2008/08/WIRM_RIP.jpg
categories:
  - Resouce Manager
tags:
  - Resource Manager
  - WIRM
---
<img style="float: left; padding-right: 15px;" src="http://www.jasonconger.com/images/articleImages/WIRM/WIRM_RIP.jpg" alt="" /> I have gotten several comments (online and offline) and emails asking about future developments surrounding Web Interface for Resource Manager. Well, Web Interface for Resource Manager as you know today is officially dead. There are actually several reasons for this. Read on for more information...

<span class="heading"><strong>MFCOM</strong></span>
<a href="http://www.jasonconger.com/Web-Interface-for-Resource-Manager-3-0-Architecture-Update.aspx">The last update I gave on Web Interface for Resource Manager</a> indicated that MFCOM (MetaFrame COM – the Citrix XenApp <acronym title="Application Programming Interface">API</acronym>) support would be included in order to get real-time statistics. As it turns out, MFCOM is being re-architected with PowerShell technology. So, there will be some re-writes for this type of integration. This also means no remoting (for the time being).

<span class="heading"><strong>EdgeSight</strong></span>
Going forward, Citrix Resource Manager is being re-architected with EdgeSight technology. This means that the back-end database schema will be drastically different. The EdgeSight schema has a lot of the same information as the Resource Manager schema, but queries required to get that information will be a lot different. That means a lot of code re-writing.

This shift also got me to thinking whether I should focus on writing SQL Server Reporting Services Reports, or stick with the ASP.NET (web application) route. I finally concluded that the ASP.NET route is still the best way to go in order to take advantage of <acronym title="Asynchronous JavaScript and XML">AJAX</acronym>, Silverlight (I am looking at some Silverlight charting to replace the Flash charts), Web Services (although SSRS does support Web Services to an extent), etc. FYI: since EdgeSight is built around Microsoft SQL Server Reporting Services (SSRS), you can say goodbye to Oracle support.

<span class="heading"><strong>What does this mean for the future of this project?</strong></span>
To boil things down to the main point – yes, Web Interface for Resource Manager is dead, but out of the demise of WIRM a new project is underway. This new project is called "Project Raley" for the time being. The components of Project Raley were first displayed at <a href="http://www.briforum.com/BriForum-2008-Chicago/" target="_blank">BriForum 2008</a> in a session I did with Kevin Goodman titled <a href="http://www.briforum.com/BriForum-2008-Chicago/session.asp?id=334" target="_blank">"The Data Puzzle – Putting the Pieces Together"</a>. The "Pieces" in that session were Web Services. Putting those "pieces" together involved writing little to no code (although the Web Services require quite a bit of code). All that being said, Project Raley uses these Web Services to create a composite application. The Web Services developed so far are:
<ul>
	<li>Active Directory</li>
	<li>Configuration Logging</li>
	<li>Event Logging</li>
	<li>MFCOM</li>
	<li>Resource Manager</li>
	<li>RTO PinPoint</li>
</ul>
Web Services currently under development are:
<ul>
	<li>Citrix Licensing (via the Citrix Licensing WMI Provider)</li>
	<li>General System WMI</li>
	<li>EdgeSight</li>
</ul>
 

<span class="heading"><strong>The inevitable question – "When is this going to be released?"</strong></span>
The broad answer is – "this year". Using these <acronym title="Service Oriented Architecture">SOA</acronym> techniques has required quite a bit of ground-up work. But, on a positive note, I am able to knock out two projects at the same time. The Configuration Logging Web Service will be consumed by both Project Raley and <a href="http://www.jasonconger.com/Get-email-alerts-for-your-Citrix-PS-4-5-Farm-with-Project-S-Bend.aspx">Project S-Bend</a>. I will also try to post some videos of alpha code to let you see some of this in action as well.

Please feel free to shoot me an email if you would like to beta test.