---
id: 35
title: Web Interface for Resource Manager 2.2
date: 2007-02-12T09:52:00-06:00
author: jason
excerpt: 'Got Citrix Resource Manager?  Try out Web Interface for Resource Manager! Web Interface for Resource Manager is an ASP.NET 2.0 web application that contains several SQL queries to display useful information contained in the Citrix Resource Manager Summary Database.'
layout: post
guid: /post/Web-Interface-for-Resource-Manager-22.aspx
permalink: /2007/02/12/web-interface-for-resource-manager-2-2/
categories:
  - Resouce Manager
tags:
  - Database
  - Download
  - Resource Manager
  - WIRM
---
version 2.2

<img style="float: left; padding-right: 15px;" src="http://www.jasonconger.com/images/articleImages/WIRM/software_box.gif" alt="" /> <strong>UPDATE March 1, 2007</strong> - The resolution to errors received when saving your configuration is posted in the <a href="#KnownIssues">Known Issues</a> section of this article.

Got Citrix Resource Manager?  Try out Web Interface for Resource Manager!

Web Interface for Resource Manager is an ASP.NET 2.0 web application that contains several SQL queries to display useful information contained in the Citrix Resource Manager Summary Database.  Web Interface for Resource Manager displays this information in a drill-down graphical and tabular manner.

<strong>What's new in version 2.2?</strong>
Web Interface for Resource Manager version 2.2 includes everything in <a href="http://www.jasonconger.com/ShowPost.aspx?strID=f0d11211-b409-462b-83e7-db1c17020ce5">version 2.1</a>, plus the following new features:
<ul>
	<li><strong>New information on the Client report</strong>
<ul>
	<li>When no client version is stored in the Citrix Resource Manager Summary Database, the Client report performs a lookup based on the build number.  Special thanks goes to Alex Danilychev for creating a <a href="http://www.frameworkx.com/frameworkx/contentblogdetail.aspx?blog=61&amp;id=470" target="_blank">Client Build vs. Version chart</a>.</li>
	<li>The Client report has an icon that will show all workstations that have used a particular client. </li>
	<li>When you click on the user icon in the Client report, the workstation the user used to launch the session is displayed in the report.</li>
</ul>
</li>
There are 3 new features on the Client report:
	<li><strong>Microsoft Excel exports on every tabular report</strong>
The ability to export viewed results to Microsoft Excel is now on every report that presents tabular data.</li>
	<li><strong>Active Directory group security for Configuration options</strong>
The configuration page is now optionally securable by specifying an Active Directory group in the configuration page.</li>
	<li><strong>Web.Config connection string encryption
</strong>When you enter your database connection details in the configuration page, the resulting connection string that is stored in Web.Config is now encrypted.</li>
</ul>
 
<ul>
	<li><strong>Active Directory group security for Configuration options
</strong>The configuration page is now optionally securable by specifying an Active Directory group in the configuration page.</li>
</ul>
 
<ul>
	<li><strong>French Translation
</strong>Thanks to <a href="http://www.laurentfalguiere.fr/" target="_blank">Laurent FALGUIERE</a>, there is now a French translation of Web Interface for Resource Manager.  Resource Manager for Web Interface is also in German (thanks to Josef Zeiler), Dutch (thanks to <a href="http://www.thincomputing.net/" target="_blank">Michel Roth</a>), and English.</li>
</ul>
 
<ul>
	<li><strong>Farm name display in page titles
</strong>The name of your farm is now displayed in the title of each page.  This helps keep things straight when you have multiple farms and an instance of Web Interface for Resource Manager for each farm.<strong></strong></li>
</ul>
Another thanks goes to <a href="http://www.thincomputing.net/" target="_blank">Michel Roth</a> for creating a <a href="http://www.thincomputing.net/newsitem3073.html" target="_blank">Web Interface for Resource Manager Premo</a>.  What is a Premo? "A <a href="http://www.thincomputing.net" target="_blank">Thincomputing.net</a> Premo is a crossover between a preview and a demo of a new (version of a) product or technology in the field of Server Based Computing and Virtualization."  Be sure to <a href="http://www.thincomputing.net/newsitem3073.html">check it out...</a>

 <img src="http://www.jasonconger.com/images/zip_small.gif" alt="" align="absBottom" /> <a href="http://www.jasonconger.com/downloads/JasonConger.com_WIRMv22.zip">Download Web Interface for Resource Manager version 2.2</a> (for Presentation Server 3.0 and above) 

<strong>What's on the radar for the future?</strong>
<ul>
	<li>More "higher level" reports - meaning more reports that show entire farm data.  These reports will include drill down capabilities in to some of the more granular existing reports. </li>
</ul>
<a name="KnownIssues"></a><strong><img src="http://www.jasonconger.com/images/warning.gif" alt="" align="absBottom" /> Known issues</strong>

<strong>Issue</strong>
You receive a message stating "In order to modify configuration settings, the ASP.NET process account (either the local ASPNET or Network Service account, by default) must have write permission granted for the Web.config file in the web site directory."

<strong>Resolution</strong>
Make sure the NETWORK SERVICE account (or whichever account is configured for the IIS Application pool identity WI RM is in) has write access to the directory where Web.Config resides. This is due to the way the Configuration.Save() method works in the .Net Framework. When this method is called, a temporary config file is created before overwriting the Web.Config file. If the NETWORK SERVICE account does not have write access to the directory, the temporary file cannot be created and you will receive the error message stated above. Also, ensure Web.Config is not a Read Only file.

If all database tables are not owned by <strong>dbo</strong>, you will receive errors. For more explanation on this phenomenon, see <a href="http://www.sqlservercentral.com/columnists/kKellenberger/understandingobjectownership.asp" target="_blank">this article</a>.

If you do not properly set up your database authentication, you will not be able to view any reports. Please refer to <a href="http://msdn.microsoft.com/library/default.asp?url=/library/en-us/adminsql/ad_security_47u6.asp" target="_blank">this article</a> for database authentication guidelines.

Note: Version 2.2 is only intended for Presentation Server 3.0 and above. This is due to the differences in the Resource Manager Summary Database schema.  The MetaFrame XP Summary Database schema does not include the tables necessary to generate these new reports. Please use <a href="http://www.jasonconger.com/ShowPost.aspx?strID=89d8e6a3-5e50-46b9-8a94-1f8f9793ae93">Web Interface for Resource Manager Version 1.1</a> for MetaFrame XP.

<strong>Screen Shot of Web Interface for Resource Manager's GUI Configuration Tool</strong>

<img src="http://www.jasonconger.com/images/articleImages/WIRM/v2.2/config_small.gif" alt="" />
<img src="http://www.jasonconger.com/images/magnify.gif" alt="" width="20" height="20" align="absBottom" /> <a class="enlarge" href="http://www.jasonconger.com/images/articleImages/WIRM/v2.2/config_large.gif" target="_blank">Click to enlarge</a>

Be sure to check out <a href="http://www.xtsinc.com/product_atmps_overview.aspx" target="_blank">Access Tracking Manager (ATM)</a> from <a href="http://www.xtsinc.com/" target="_blank">XTS</a> as well. ATM leverages Microsoft SQL Server Analysis Services and OLAP Cubes to provide even more detailed reports for your Citrix environments.