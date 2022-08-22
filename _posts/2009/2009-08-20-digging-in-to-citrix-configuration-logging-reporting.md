---
id: 14
title: 'Digging in to Citrix Configuration Logging: Reporting'
date: 2009-08-20T19:54:00-05:00
author: JasonConger
excerpt: 'This is the fourth part in a series on Citrix XenApp Configuration Logging.  This part will foucus on out of the box reporting tool.  In a later article, we will look at custom reporting.'
layout: post
image: wp-content/uploads/2009/09/Citrix-XenApp.png
categories:
  - Citrix XenApp
tags:
  - Citrix
  - Configuration Logging
  - Database
  - XenApp SQL
---
This is the fourth part in the Citrix Configuration Logging Series. In [part 1]({% post_url /2009/2009-07-12-digging-in-to-citrix-configuration-logging-part-1 %}), we discussed what Citrix Configuration Logging was.  In [part 2]({% post_url /2009/2009-07-29-digging-in-to-citrix-configuration-logging-setting-up-the-database %}), we discussed how to prepare the database to log configuration changes. In [part 3]({% post_url /2009/2009-08-10-digging-in-to-citrix-configuration-logging-setting-up-the-citrix-xenapp-farm-for-configuration-logging %}), we discussed how to set up the Citrix XenApp farm for Configuration Logging. In this part, we will look at the out of the box reporting tools (in a later article, we will look at custom reporting).
<h2>Citrix Report Center</h2>
Report Center is part of the Citrix Access Management Console.  Report Center allows you to create, schedule, and distribute various types of canned reports.  One of the types of reports available is the, you guessed it, “Configuration Logging Report”.  There are several other reports available as well including, but not limited to:
<ul>
	<li>Alerts Report</li>
	<li>Application Usage Report</li>
	<li>Client Type Report</li>
	<li>CPU Utilization Management Report</li>
	<li>Policy Report</li>
	<li>Server Availability Report</li>
	<li>Environment Usage Report</li>
</ul>

<h2>Report Specification</h2>
Before you can run any report in the Access Management Console, you have to create a report specification.  A report specification basically tells a report where to get its data and where/how to output the data.  Different reports will have different data sources.  For instance, the Configuration Logging Report’s data source would be the Configuration Logging database, whereas the Application Usage Report’s data source would be the Resource Manager Summary Database.  There is a wizard in the AMC that will step you through setting up a report specification.  To start the wizard, simply right-click the Report Center node in the AMC and select “Generate specification”.  The wizard is pretty self explanatory, but I do want to point out one part.

<a href="http://www.jasonconger.com/images/articleImages/ReportStorage_1.png" target="_blank"><img style="display: block; float: none; margin-left: auto; margin-right: auto; border: 0px;" title="ReportStorage" src="http://www.jasonconger.com/images/articleImages/ReportStorage_thumb_1.png" border="0" alt="ReportStorage" width="400" height="369" /></a>

When you choose to store a report for later viewing, the report is stored in your user profile (actually, all report specification options as well as the report specification itself is stored in the user profile).  The bad thing about this is all this stuff is stored in your <strong>local profile</strong> by default in the following path:

~~~
%USERPROFILE%\Local Settings\Application Data\Citrix\ReportCenter\
~~~

If you are using roaming profiles, these reports/specifications will get wiped out when you log off (since Local Settings do not roam).  However, there is an option to store reports in your roaming profile.  This setting is located in the middle column of the AMC when you select the Report Center node.

<a href="http://www.jasonconger.com/images/articleImages/storageprofile_1.png" target="_blank"><img style="display: block; float: none; margin-left: auto; margin-right: auto; border-width: 0px;" title="storageprofile" src="http://www.jasonconger.com/images/articleImages/storageprofile_thumb_1.png" border="0" alt="storageprofile" width="400" height="215" /></a>
<h2>Scheduling Reports</h2>
One of the interesting things you can do is schedule a report to run on a recurring basis.  Say you wanted to get a summary of configuration changes every morning.  You could create a schedule to run this report and email it to you.  To schedule a report, right-click the report specification and select “Schedule report”.

<a href="http://www.jasonconger.com/images/articleImages/ScheduleReport.png" target="_blank"><img style="display: block; float: none; margin-left: auto; margin-right: auto; border-width: 0px;" title="ScheduleReport" src="http://www.jasonconger.com/images/articleImages/ScheduleReport_thumb.png" border="0" alt="ScheduleReport" width="410" height="289" /></a>

Clicking “Schedule report” brings up a wizard that looks a lot like Windows Task Scheduler.  The reason it looks like Windows Task Scheduler is because you are actually creating an ordinary Windows Scheduled Task.  However, if you try to look for this scheduled task in Windows, you probably will not see it.  That is because Citrix was sneaky and made the scheduled task hidden.  To view the schedule task in Windows, you will have to enable “View Hidden Tasks”.

<a href="http://www.jasonconger.com/images/articleImages/ScheduledTask.png" target="_blank"><img style="display: block; float: none; margin-left: auto; margin-right: auto; border-width: 0px;" title="ScheduledTask" src="http://www.jasonconger.com/images/articleImages/ScheduledTask_thumb.png" border="0" alt="ScheduledTask" width="419" height="200" /></a>
<h2>Viewing Reports</h2>
To view a report, you first need to run a job.  You can run a job by right-clicking on a report specification and selecting “Run report now”.  Scheduled reports create jobs as well.  Once a job completes, you can view the report from the “Jobs” section of Report Center.  Reports can be generated in HTML format or CSV format.  The default format of a report is specified in the report specification; however, you can view any report in either format via the AMC.

<a href="http://www.jasonconger.com/images/articleImages/ReportJob_1.png" target="_blank"><img style="display: block; float: none; margin-left: auto; margin-right: auto; border: 0px;" title="ReportJob" src="http://www.jasonconger.com/images/articleImages/ReportJob_thumb_1.png" border="0" alt="ReportJob" width="402" height="279" /></a>

<h2>Modifying the Report Layout</h2>
There isn’t much to discuss about the CSV format, but I do want to show you a few things about the HTML format.  By default, the HTML format report looks pretty ugly.

<a href="http://www.jasonconger.com/images/articleImages/HTMLReport.png" target="_blank"><img style="display: block; float: none; margin-left: auto; margin-right: auto; border: 0px;" title="HTMLReport" src="http://www.jasonconger.com/images/articleImages/HTMLReport_thumb.png" border="0" alt="HTMLReport" width="400" height="319" /></a>

There are a few things we can do to make this report look better.  To better understand how to modify the report, it is important to understand how the reports are generated.

The raw data behind a report is XML.  A command line utility called <strong>genrep.exe</strong> is responsible for going out to the data source and generating the XML in the form of a dataset.  Once the data has been retrieved, a XML style sheet transformation (XSLT) is applied to produce the resulting HTML.  The XSLT files are stored in:

~~~
%ProgramFiles%\Common Files\Citrix\Access Management Console – Report Center\Reports\ConfigurationLoggingReport
~~~

There are some common and language specific transforms here.  The simplest way to style the report is to modify <strong>ConfigurationLoggingReportHTML.xslt</strong>.  Here is a screen shot of a report generated with a modified transform:

<a href="http://www.jasonconger.com/images/articleImages/HTMLReportStyled.png" target="_blank"><img style="display: block; float: none; margin-left: auto; margin-right: auto; border: 0px;" title="HTMLReportStyled" src="http://www.jasonconger.com/images/articleImages/HTMLReportStyled_thumb.png" border="0" alt="HTMLReportStyled" width="400" height="319" /></a>

This concludes our look at “out of the box” capabilities.  Even though we were talking mainly about Configuration Logging reporting, most of this information also applies to other reports in Report Center.  In the next posts, we will explore the back end database and how to do some custom reporting.