---
id: 27
title: Project S-Bend Setup Instructions
date: 2008-01-14T10:40:00-06:00
author: jason
excerpt: Project S-Bend sends alerts when changes happen on your Citrix Presentation Server 4.5 farm.
layout: post
guid: /post/Project-S-Bend-Setup-Instructions.aspx
permalink: /2008/01/14/project-s-bend-setup-instructions/
categories:
  - Citrix XenApp
tags:
  - Configuration Logging
  - XenApp
---
Note: The setup instructions and screenshots shown below are for use with Microsoft SQL Server 2005. However, the steps are similar for Microsoft SQL Server 2000.

 <img src="http://www.jasonconger.com/images/zip_small.gif" alt="download" align="absBottom" /> <a href="http://www.jasonconger.com/downloads/SBend/v1.0/JasonConger.com_SBend.zip">Download Project S-Bend Phase I</a>

<span class="postHeading">Step 1 – Set up the Database</span>

Open SQL Server Management Studio (or SQL Enterprise Manager for SQL 2000).
Right click on your Citrix Configuration Logging database and select "New Query".

<img style="border: 1px solid #000;" src="http://www.jasonconger.com/images/articleImages/SBend/docs/new_query.jpg" alt="New Query" />

In the Query window paste the following SQL Script:
<textarea onclick="this.select();" cols="75" rows="15"> SET ANSI_NULLS ON GO SET QUOTED_IDENTIFIER ON GO CREATE TRIGGER [trig_ChangeAlert]    ON  [dbo].[CtxLog_AdminTask_LogEntry]    AFTER INSERT AS  BEGIN      SET NOCOUNT ON;      declare @LogEntry_RecordID int      SELECT @LogEntry_RecordID = LogEntry_RecordID FROM INSERTED      INSERT INTO Alerts (LogEntry_RecordID) VALUES (@LogEntry_RecordID) END GO CREATE TABLE [dbo].[Alerts]( 	[LogEntry_RecordID] [int] NOT NULL, 	[Processed] [bit] NOT NULL CONSTRAINT [DF_Alerts_Processed]  DEFAULT ((0)),  CONSTRAINT [PK_Alerts] PRIMARY KEY CLUSTERED  ([LogEntry_RecordID] ASC) ) ON [PRIMARY] GO </textarea>

Press F5 to execute the query.  This will create the Alerts table and the SQL Trigger.

<span class="postHeading">Step 2 – Set up the Windows Service </span>

Copy the following files to your preferred destination directory (something like C:\Program Files\CitrixConfigAlert\):
<ul>
	<li>CtxConfigAlert.exe</li>
	<li>CtxConfigAlert.exe.config</li>
</ul>
Edit CtxConfigAlert.exe.config with the appropriate values for your environment. Set values for the following:
<ul>
	<li><span style="text-decoration: underline;">connectionString</span> - Tip: visit <a href="http://www.connectionstrings.com" target="_blank">www.connectionstrings.com</a> for help with this value.</li>
	<li><span style="text-decoration: underline;">PollInterva</span>l - This is how often (in seconds) the Windows Service will poll the Alerts table.</li>
	<li><span style="text-decoration: underline;">MailToAddress</span> - The destination email address to send the alerts.</li>
	<li><span style="text-decoration: underline;">SMTPServer</span> - The name or IP address of your SMTP server.</li>
	<li><span style="text-decoration: underline;">SMTPPort</span> - The port of your SMTP server (defaults to 25).</li>
	<li><span style="text-decoration: underline;">MailSubject</span> - This will be the subject line of the email sent.</li>
	<li><span style="text-decoration: underline;">MailFromAddress</span> - The email address used to send the alert.</li>
</ul>
<div><span class="postHeading">Step 3 - Install the Windows Service </span></div>
<span class="postHeading"> 

</span>
<ul>
	<li>Open a command prompt and change the directory to C:\Windows\Microsoft.NET\Framework\v2.0.<em>x</em></li>
	<li>Perform the following command:
     <strong>InstallUtil /I <em>path_to_CtxConfigAlert.exe</em></strong></li>
	<li>This will install a new Windows Service called "Citrix Change Alerts (S-Bend)".</li>
	<li>Start the service.</li>
</ul>
Any errors that occur while starting the service, or during the operation of the service, will be logged to the Windows Application event log.

Note: Changes made to CtxConfigAlert.exe.config require a service restart to take effect.