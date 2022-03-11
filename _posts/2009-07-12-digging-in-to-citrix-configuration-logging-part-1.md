---
id: 17
title: 'Digging in to Citrix Configuration Logging &#8211; Part 1'
date: 2009-07-12T23:58:00-05:00
author: JasonConger
excerpt: 'This is the first part in a series on Citrix XenApp Configuration Logging.  Citrix XenApp Configuration Logging helps keep track of changes made to your server farm.  This feature can tell you what changes were made to your server farm, when they were made, and who made them. Part 1 in this series will further define where changes are logged and how the changes are logged.'
layout: post
guid: /post/Digging-in-to-Citrix-Configuration-Logging-Part-1.aspx
image: wp-content/uploads/2009/09/Citrix-XenApp.png
categories:
  - Citrix XenApp
tags:
  - Citrix
  - Configuration Logging
  - Database
  - SQL
  - XenApp
---
I have presented on this topic in the past at <a href="http://briforum.com/" target="_blank">BriForum</a> and I wanted to share more about Citrix XenApp Configuration Logging here.  This will be a multi-part series that inspects each aspect of Citrix Configuration Logging and some creative ways of extending Citrix Configuration Logging.  So, let’s get started…
<h2>What is Citrix Configuration Logging?</h2>
According to the <a href="http://support.citrix.com/servlet/KbServlet/download/14596-102-19092/Presentation_Server_Administrator_Guide.pdf" target="_blank">Citrix XenApp Administrator’s guide</a>, “the Configuration Logging feature allows you to <strong>keep track of administrative changes</strong> made to your server farm environment. By generating the reports that this feature makes available, you can determine <strong>what changes were made</strong> to your server farm, <strong>when they were made</strong>, and <strong>which administrators made them</strong>. This is especially useful when multiple administrators are modifying the configuration of your server farm. It also facilitates the identification and, if necessary, reversion of administrative changes that may be causing problems for the server farm.” (emphasis added)

When I worked for Citrix, we had a load evaluator that had no available login times.  If a server was acting up, we could apply this “unavailable” load evaluator to it and figure out what was going on.  Oftentimes, we would discover that the “unavailable” load evaluator was applied to a new server and not know who did it or why they did it. So, we would have to resort to sending out an email asking why this server was assigned to the load evaluator.  Now, Citrix XenApp Configuration Logging tells you who did what and when.  That should be enough information to find out why.
<h2>Where are Changes Logged?</h2>
Changes that you make to the Citrix XenApp farm are logged to a database.  The back end database can be:
<ul>
	<li>Microsoft SQL 2000 or Microsoft SQL 2005 (Microsoft SQL Express works too)</li>
	<li>Oracle 9.2 or 10.2 </li>
</ul>
We will explore the details of the database schema in depth later on.
<h2>How are Changes Logged?</h2>
There are several ways to make changes to a Citrix XenApp Farm:
<ul>
	<li>Management Consoles</li>
	<li>Command Line Utilities</li>
	<li><a href="http://community.citrix.com/display/xa/XenApp+Management+SDK" target="_blank">MFCOM</a></li>
	<li><a href="http://www.microsoft.com/powershell" target="_blank">PowerShell</a></li>
	<li>Etc.</li>
</ul>
In order to facilitate logging changes made by any of these methods, Citrix introduced an IMA hook called CitrixLogServer.dll.  As you know, any change made to the data store has to go through IMA first. So, introducing an IMA hook makes sense.

Here are the facts about CitrixLogServer.dll:
<ul>
	<li>Located in %ProgramFiles%\Citrix\System32</li>
	<li>it is a Microsoft .Net assembly</li>
	<li>it uses ADO.NET to write changes to the database.  Once a connection is made to the database, it will automatically disconnect after 5 minutes of inactivity.</li>
	<li>Uses a XSD schema that is optimized for writes</li>
</ul>
 
<h2>Citrix XenApp Configuration Logging Architecture</h2>
When a change is submitted to IMA, the change is written via a transaction to the configuration logging database and data store.  It is possible to require all changes be written to the configuration logging database before they are allowed to be written to the data store.  This ensures all changes are logged.  Since the change is written via a transaction, a failure writing to the logging database or data store rolls back the transaction and no change is made or logged.

<a href="http://www.jasonconger.com/images/articleImages/ctx-cnfglog-overview.png"><img style="display: inline; border-width: 0px;" title="Citrix XenApp Configuration Logging Architecture" src="http://www.jasonconger.com/images/articleImages/ctx-cnfglog-overview_thumb.png" border="0" alt="Citrix XenApp Configuration Logging Architecture" width="580" height="377" /></a>

<strong>Bonus tip</strong>: if you clone servers in your Citrix XenApp farm and cannot join the cloned server to the farm, you may have to disable configuration logging.  Once the server joins the farm, you can re-enable configuration logging.