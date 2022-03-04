---
id: 29
title: Web Interface for Resource Manager Roadmap
date: 2007-12-10T10:37:00-06:00
author: jason
excerpt: 'Web Interface for Citrix Resource Manager has been steadily growing since it was first released back in April 2006.  Find out where this project is heading in this roadmap and what it will take to get there.'
layout: post
guid: /post/Web-Interface-for-Resource-Manager-Roadmap.aspx
categories:
  - Resouce Manager
tags:
  - Resource Manager
  - WIRM
---
Web Interface for Resource Manager has been steadily growing since it was first released back in April 2006. The purpose of this post is to serve as a roadmap for the direction of where Web Interface for Resource Manager is heading. Version 1.0 of Web Interface for Resource Manager included a few basic usage reports and user reports. Since then, many new features have been added including:
<ul style="list-style-type: square;">
	<li>Report Filtering</li>
	<li>User Level Reporting</li>
	<li>Client Level Reporting</li>
	<li>Concurrent Usage Reporting (for both applications and users)</li>
	<li>Server Metric Reporting</li>
	<li>Support for exporting reports to Microsoft Excel</li>
	<li>Configuration GUI</li>
	<li>Support for Microsoft SQL and Oracle</li>
	<li>Multiple Language Support including:    <img src="http://www.jasonconger.com/images/articleImages/flags/us.gif" alt="English" /> English
    <img src="http://www.jasonconger.com/images/articleImages/flags/nl.gif" alt="Dutch" /> Dutch – provided by <a href="http://www.thincomputing.net/" target="_blank">Michel Roth</a>
    <img src="http://www.jasonconger.com/images/articleImages/flags/fr.gif" alt="French" /> French – provided by <a href="http://www.laurentfalguiere.fr/" target="_blank">Laurent FALGUIERE</a>
    <img src="http://www.jasonconger.com/images/articleImages/flags/de.gif" alt="German" /> German – provided by Josef Zeiler
    <img src="http://www.jasonconger.com/images/articleImages/flags/it.gif" alt="Italian" /> Italian – provided by <a href="http://www.dpmworld.net/" target="_blank">Francesco Dipietromaria</a>
    <img src="http://www.jasonconger.com/images/articleImages/flags/ar.gif" alt="Spanish" /> Spanish – provided by <a href="http://www.grupoitpro.com.ar/" target="_blank">Gustavo Gurmandi</a></li>
	<li>Configuration Encryption</li>
	<li>Etc.</li>
</ul>
<span class="heading">That is where we have been, so where are we going?</span>
As I stated earlier, this is a roadmap of what is to come. So, here is a list of a few of the new features slated for future releases:

<a href="http://www.asp.net/ajax/" target="_blank">AJAX</a> Enhancements – this will improve the user experience.
MFCOM Integration – this integration will allow real-time reporting.
Farm Level Reports – these reports will aggregate information to give more of a "bird's eye view" of your Citrix farm. These reports will include drill down capabilities in to some of the more granular existing reports.
Citrix Presentation Server 4.5 Configuration Logging Integration – this will allow reporting on historical changes.

<span class="heading">How do we get there from here?</span>
Since Web Interface for Resource Manager is moving beyond the bounds of the <a href="http://www.jasonconger.com/Visio-Diagram-of-the-Citrix-Resource-Manager-Summary-Database.aspx">Resource Manager Summary Database</a>, a major architectural shift will occur. This shift will implement SOA (Service Oriented Architecture) principles. This will allow a loosely coupled layer approach. Why is this important? This will facilitate implementing a provider model where each provider is something you can turn on or off. Depending on what you have turned on, you will get more information in the reports. The providers currently in development are:

» Summary Database Provider
» MFCOM Provider
» Configuration Logging Provider
» Third party providers (stay tuned for more on this in the future).

<span class="heading">That's great – when do we get this stuff?</span>
In order to get to the next (provider model) release, I first need to complete the architectural shift I talked about earlier. The good thing about this re-architecture is that it will allow more flexibility. The bad news is that it will not add any new features for end users. So, the next release of Web Interface for Resource Manager will include this new architecture and the AJAX enhancements. This will be a 3.0 release. Each new piece I add after that will be an incremental 3.x release. So, stay tuned, there is more on the way.