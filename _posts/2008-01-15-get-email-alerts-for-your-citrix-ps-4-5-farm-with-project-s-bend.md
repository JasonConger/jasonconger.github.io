---
id: 26
title: Get email alerts for your Citrix PS 4.5 Farm with Project S-Bend
date: 2008-01-15T10:42:00-06:00
author: JasonConger
excerpt: Project S-Bend fills the gap in Citrix Presentation Server 4.5 Configuration Logging by alerting you via email when changes happen in your farm.
layout: post
guid: /post/Get-email-alerts-for-your-Citrix-PS-45-Farm-with-Project-S-Bend.aspx
image: wp-content/uploads/2009/09/Citrix-XenApp.png
categories:
  - Citrix XenApp
tags:
  - Configuration Logging
  - Download
  - XenApp
---
Citrix introduced a new feature in Citrix Presentation Server 4.5 called Configuration Logging. Configuration Logging keeps track of every change to every object in your Citrix Presentation Server Farm. This information is kept in a back end database and you have the ability to run reports on these changes via the Report Center in the Access Management Console. For more details on setting up Configuration Logging and running reports, check out <a href="http://alsolorzano.com/blogs/tips__tricks/archive/2007/04/19/setting-up-configuration-logging-in-presentation-server-4-5.aspx" target="_blank">this article by Al Solorzano</a>.

I think this is a really cool feature that lets you know who did what and when they did it. But, in order to get this information, you have to run a report from the Report Center in the AMC. Granted, you can automate reports, but it would be nice if there was some mechanism to alert you when a change was made. This is where Project S-Bend Phase I comes in to play. Project S-Bend was originally created as an exercise for my session titled "<a href="http://www.briforum.com/europe/2007/session.aspx?id=298">Digging into Citrix Presentation Server 4.5 Configuration Logging</a>" at BriForum Europe 2007.

Project S-Bend Phase I consists of 3 main parts; an "Alerts" table added to the Configuration Logging database, a SQL trigger, and a Windows Service. Project S-Bend uses these parts to send email alerts whenever a change is written to the Configuration Logging back end database.

 <img src="http://www.jasonconger.com/images/zip_small.gif" alt="download" align="absBottom" /> <a href="http://www.jasonconger.com/downloads/s-bend/v1.0/JasonConger.com_SBend.zip">JasonConger.com_SBend.zip</a>

<strong>Alerts Table</strong>
This is a very simple table that is populated by the SQL trigger.

<strong>SQL Trigger</strong>
The SQL trigger is added to you Citrix Configuration Logging database and fires any time a change is written to the database. The trigger writes the ID of the change to the Alerts table.

<span class="postHeading"><strong>Windows Service</strong></span>
The Windows Service reads the Alerts table populated by the SQL trigger. For each row in the table, the Windows Service sends an email to the specified email address with details concerning the object changed.

<span class="postHeading"><strong>How it all works</strong></span>
The process is actually quite simple.
<ol>
	<li>When a change is made in your Citrix Presentation Server 4.5 farm, a log entry is created in the Configuration Logging database.</li>
	<li>When the log entry is created, the SQL Trigger fires and writes an entry to the Alerts table.</li>
	<li>The Windows Services reads the Alerts table on a configurable timed interval. When the Windows Service encounters unprocessed alerts in the Alerts table, it sends and email with details of what was changed.</li>
</ol>
<img src="http://www.jasonconger.com/images/articleImages/SBend/PhaseI/S-Bend_flow.gif" alt="Project S-Bend flow" />

<span class="postHeading">What about Phase II?</span>
I guess it is quite obvious that there is a Phase II in the works since I named this thing Phase I. Actually, Phase II is a provider. "A provider for what?" you may ask. Phase II is a provider for reports. Web Interface for Resource Manager will consume this provider as mentioned in the <a href="http://www.jasonconger.com/Web-Interface-for-Resource-Manager-Roadmap.aspx">Web Interface for Resource Manager Roadmap</a>.