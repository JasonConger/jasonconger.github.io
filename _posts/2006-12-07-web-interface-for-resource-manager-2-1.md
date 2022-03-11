---
id: 36
title: Web Interface for Resource Manager 2.1
date: 2006-12-07T09:51:00-06:00
author: JasonConger
excerpt: 'Got Citrix Resource Manager?  Try out Web Interface for Resource Manager! Web Interface for Resource Manager is an ASP.NET 2.0 web application that contains several SQL queries to display useful information contained in the Citrix Resource Manager Summary Database.'
layout: post
guid: /post/Web-Interface-for-Resource-Manager-21.aspx
categories:
  - Resouce Manager
tags:
  - Database
  - Download
  - Resource Manager
  - WIRM
---
<p><img style="float: right; padding-left: 15px" src="http://www.jasonconger.com/images/articleImages/WIRM/software_box.gif" alt="" /> version 2.1 <br /><br />Got Citrix Resource Manager? &nbsp;Try out Web Interface for Resource Manager!<br /><br />Web Interface for Resource Manager is an ASP.NET 2.0 web application that contains several SQL queries to display useful information contained in the Citrix Resource Manager Summary Database.&nbsp; Web Interface for Resource Manager displays this information in a drill-down graphical and tabular manner.<br /><br /><br /><strong>What's new in version 2.1?</strong><br />Web Interface for Resource Manager version 2.1 includes everything in <a href="http://www.jasonconger.com/ShowPost.aspx?strID=839f0872-3da0-4b8d-8327-4908c779b166">version 2.0</a>, plus the following new features:</p>
<ul>
<li><strong>Graphical Configuration Tool</strong><br />In the past versions of Web Interface for Resource Manager, you had to manually edit the Web.Config file to set up your database connections and time zone overrides. This new graphical tool allows you to set up your options much like you set up an ODBC connection using Windows. </li>
<li><strong>Oracle Support</strong><br />Many of you have asked for an Oracle version of Web Interface for Resource Manager. Version 2.1 has Oracle support integrated. Just open the configuration tool, select Oracle as your Database Server Type and supply your TNS Service Name. One thing to note though, you will need to have the Oracle client installed on your web server. </li>
<li><strong>Multiple Language Support</strong><br />Web Interface for Citrix Resource Manager has been globalized to support more languages. Currently, Web Interface for Resource Manager supports the following languages:
<ul>
<li>US English</li>
<li>German (thanks goes to Josef Zeiler for the translation)</li>
<li>Dutch (thanks goes to <a href="http://www.thincomputing.net/" target="_blank">Michel Roth</a> for the translation)</li>
</ul>
</li>
</ul>
<p><br />&nbsp;<img src="http://www.jasonconger.com/images/zip_small.gif" alt="" align="absBottom" /> <a href="http://www.jasonconger.com/downloads/JasonConger.com_WIRMv21.zip">Download Web Interface for Resource Manager version 2.1</a> (for Presentation Server 3.0 and above)&nbsp;<br /><br /><br /><br /><strong>What's on the radar for the future?</strong></p>
<ul>
<li>Using MFCOM and WMI to move reports beyond the Summary Database.</li>
<li>Of course, more reports.</li>
</ul>
<p><strong><img src="http://www.jasonconger.com/images/warning.gif" alt="" align="absBottom" /> Known issues</strong><br /><br />If all database tables are not owned by <strong>dbo</strong>, you will receive errors. For more explanation on this phenomenon, see <a href="http://www.sqlservercentral.com/columnists/kKellenberger/understandingobjectownership.asp" target="_blank">this article</a>. <br /><br />If you do not properly set up your database authentication, you will not be able to view any reports. Please refer to <a href="http://msdn.microsoft.com/library/default.asp?url=/library/en-us/adminsql/ad_security_47u6.asp" target="_blank">this article</a> for database authentication guidelines.<br /><br />Note: Version 2.1 is only intended for Presentation Server 3.0 and above. This is due to the differences in the Resource Manager Summary Database schema.&nbsp; The MetaFrame XP Summary Database schema does not include the tables necessary to generate these new reports. Please use <a href="http://www.jasonconger.com/ShowPost.aspx?strID=89d8e6a3-5e50-46b9-8a94-1f8f9793ae93">Web Interface for Resource Manager Version 1.1</a> for MetaFrame XP.<br /><br /><br /><strong>Screen Shot of Web Interface for Resource Manager's GUI Configuration Tool</strong><br /><br /><img src="http://www.jasonconger.com/images/articleImages/WIRM/v2.1/config_small.gif" alt="" /><br /><img src="http://www.jasonconger.com/images/magnify.gif" alt="" width="20" height="20" align="absBottom" /> <a class="enlarge" href="http://www.jasonconger.com/images/articleImages/WIRM/v2.1/config_large.gif" target="_blank">Click to enlarge</a></p>