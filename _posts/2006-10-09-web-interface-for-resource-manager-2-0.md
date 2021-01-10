---
id: 38
title: Web Interface for Resource Manager 2.0
date: 2006-10-09T09:48:00-05:00
author: jason
excerpt: 'Got Citrix Resource Manager?  Try out Web Interface for Resource Manager! Web Interface for Resource Manager is an ASP.NET 2.0 web application that contains several SQL queries to display useful information contained in the Citrix Resource Manager Summary Database.'
layout: post
guid: /post/Web-Interface-for-Resource-Manager-20.aspx
permalink: /2006/10/09/web-interface-for-resource-manager-2-0/
categories:
  - Resouce Manager
tags:
  - Database
  - Download
  - Resource Manager
  - WIRM
---
<p><img style="float: right; padding-left: 15px" src="http://www.jasonconger.com/images/articleImages/WIRM/software_box.gif" alt="" /> version 2.0 <br /><br />Got Citrix Resource Manager? &nbsp;Try out Web Interface for Resource Manager!<br /><br />Web Interface for Resource Manager is an ASP.NET 2.0 web application that contains several SQL queries to display useful information contained in the Citrix Resource Manager Summary Database.&nbsp; Web Interface for Resource Manager displays this information in a drill-down graphical and tabular manner.<br /><br /><br /><strong>What's new in version 2.0?</strong><br />Web Interface for Resource Manager version 2.0 includes everything in <a href="http://www.jasonconger.com/ShowPost.aspx?strID=cc81059a-3f3c-4754-b5ac-92297a76f777">version 1.2</a>, plus the following new features:</p>
<ul>
<li><strong>Concurrent usage of applications report</strong><br />See the concurrent usage of you applications within a specified date range. Also, this report will show you when the maximum number of concurrent sessions was reached. </li>
<li><strong>Server metrics report</strong><br />See captured metrics for a particular server on a specified date. Any metrics you capture via the Citrix Presentation Server Console will be reported here. </li>
<li><strong>Concurrent usage of servers report</strong><br />See how many concurrent sessions you are getting per server within a date range. This report will also show you when this max count was reached. Clicking on a row in this report will take you to the server metrics report for the particular date you reached the max count &ndash; showing you how your server was performing under the load. </li>
<li><strong>Exporting reports</strong><br />You can now export reports to CSV for further analysis using an application such as Microsoft Excel </li>
<li><strong>New calendar filtering option</strong><br />A new option on the Usage Calendar allows you to view all sessions that started per hour on a given day, or just unique users per hour. For example, if user1 started 2 or more sessions during the 11:00 hour, user1 would only be counted one time. </li>
</ul>
<p><br />&nbsp;<img src="http://www.jasonconger.com/images/zip_small.gif" alt="" align="absBottom" /> <a href="http://www.jasonconger.com/downloads/JasonConger.com_WIRMv20.zip">Download Web Interface for Resource Manager version 2.0</a> (for Presentation Server 3.0 and above)&nbsp;<br /><br /><br /><br /><strong>What's on the radar for the future?</strong></p>
<ul>
<li>Graphical configuration &ndash; no more editing Web.Config by hand.</li>
<li>Multiple language support.</li>
<li>Oracle Database support.</li>
<li>And, of course, more reports.</li>
</ul>
<p><strong><img src="http://www.jasonconger.com/images/warning.gif" alt="" align="absBottom" /> Known issues</strong><br /><br />If all database tables are not owned by <strong>dbo</strong>, you will receive errors. For more explanation on this phenomenon, see <a href="http://www.sqlservercentral.com/columnists/kKellenberger/understandingobjectownership.asp" target="_blank">this article</a>. <br /><br />If you do not properly set up your database authentication, you will not be able to view any reports. Please refer to <a href="http://msdn.microsoft.com/library/default.asp?url=/library/en-us/adminsql/ad_security_47u6.asp" target="_blank">this article</a> for database authentication guidelines.<br /><br />Note: Version 2.0 is only intended for Presentation Server 3.0 and above. This is due to the differences in the Resource Manager Summary Database schema.&nbsp; The MetaFrame XP Summary Database schema does not include the tables necessary to generate these new reports. Please use <a href="http://www.jasonconger.com/ShowPost.aspx?strID=89d8e6a3-5e50-46b9-8a94-1f8f9793ae93">Web Interface for Resource Manager Version 1.1</a> for MetaFrame XP.<br /><br /><br /><strong>Screen Shots of Web Interface for Resource Manager</strong><br /><br />New buttons on the Sessions by Hour graph to show all sessions or just unique user sessions <br />(filters out multiple sessions started by the same user in the same hour). <br /><img src="http://www.jasonconger.com/images/articleImages/WIRM/v2.0/calendarFilter_small.gif" alt="" /><br /><img src="http://www.jasonconger.com/images/magnify.gif" alt="" width="20" height="20" align="absBottom" /> <a class="enlarge" href="http://www.jasonconger.com/images/articleImages/WIRM/v2.0/calendarFilter.gif" target="_blank">Click to enlarge</a> <br /><br /><br />Report showing max concurrent sessions per server and the date this max count was reached. <br /><img src="http://www.jasonconger.com/images/articleImages/WIRM/v2.0/conServer_small.gif" alt="" /><br /><img src="http://www.jasonconger.com/images/magnify.gif" alt="" width="20" height="20" align="absBottom" /> <a class="enlarge" href="http://www.jasonconger.com/images/articleImages/WIRM/v2.0/conServer.gif" target="_blank">Click to enlarge</a> <br /><br /><br />Report showing server metrics for a specified day. <br /><img src="http://www.jasonconger.com/images/articleImages/WIRM/v2.0/metrics_small.gif" alt="" /><br /><img src="http://www.jasonconger.com/images/magnify.gif" alt="" width="20" height="20" align="absBottom" /> <a class="enlarge" href="http://www.jasonconger.com/images/articleImages/WIRM/v2.0/metrics.gif" target="_blank">Click to enlarge</a></p>