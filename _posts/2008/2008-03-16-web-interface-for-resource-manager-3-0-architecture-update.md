---
id: 25
title: Web Interface for Resource Manager 3.0 Architecture Update
date: 2008-03-16T10:47:00-05:00
author: JasonConger
excerpt: When the Web Interface for Resource Manger Roadmap was posted, I mentioned that Web Interface for Citrix Resource Manager version 3.0 would include a major architectural shift toward a Service Oriented Architecture (SOA). This shift is well underway and the purpose of this post is to share some of the progress as well as some of the nuts and bolts behind the architecture.
layout: post
guid: /post/Web-Interface-for-Resource-Manager-30-Architecture-Update.aspx
categories:
  - Resouce Manager
tags:
  - Resource Manager
  - WIRM
---
When the <a title="Web Interface for Resource Manger Roadmap" href="http://www.jasonconger.com/Web-Interface-for-Resource-Manager-Roadmap.aspx">Web Interface for Resource Manger Roadmap</a> was posted, I mentioned that Web Interface for Citrix Resource Manager version 3.0 would include a major architectural shift toward a Service Oriented Architecture (SOA). This shift is well underway and the purpose of this post is to share some of the progress as well as some of the nuts and bolts behind the architecture. Disclaimer – the following may get a little boring.

<span class="heading">Web Services</span>
I have been toying with this idea for a while and finally made the decision to move everything to <a href="http://msdn.microsoft.com/webservices/" target="_blank">Web Services</a>. Web Services allow for a greater separation of presentation and data. The thought behind creating sets of Web Services in Web Interface for Citrix Resource Manager is to allow other applications to consume the data WIRM produces. Other applications such as Microsoft SQL Server Reporting Services, SharePoint, custom portals, Project S-Bend, etc. can all consume these Web Services. And remember, WIRM is moving beyond the bounds of the Citrix Resource Manager Summary Database so there will be Web Services for the Configuration Logging database, Active Directory, MFCOM, WMI providers, third party data sources, etc. as well as the Web Services for the Citrix Resource Manager Summary Database.  Here is a screen shot of some of the Resource Manger Web Service's rendered <acronym title="Web Service Description Language">WSDL</acronym>:

<img src="http://www.jasonconger.com/images/articleImages/WIRM/v3.0_update/web_services.gif" alt="Web Services" />

<span class="heading">
Generic Database Access, DAL, and DAAB</span>
One of the challenges of querying the Citrix Resource Manager Summary Database from a generic application is that the database can be Microsoft SQL or Oracle. What I have done in the past with Web Interface for Citrix Resource Manager is maintain separate data access blocks – one for SQL and one for Oracle. Depending on the database provider specified in the database connection string in web.config, I would utilize the System.Data.SqlClient or System.Data.OracleClient namespace. This has proven to be a cumbersome and time consuming process to code and test.

Enter the <a href="http://msdn2.microsoft.com/en-us/library/aa480458.aspx">Microsoft Enterprise Library Patterns and Practices Data Access Application Block</a> (a.k.a. DAAB). Web Interface for Citrix Resource Manager implements a Data Access Layer (DAL) which is a common SOA component. The DAL is responsible for physically getting the data from the source(s) and delivering the data to the Web Service(s) - sometimes there is a façade’ in between, but that is another discussion. One of the major pieces of the DAL for Web Interface for Citrix Resource Manager is the DAAB. The DAAB allows for generic database access which means one (reduced) set of code that allows access to either Microsoft SQL or Oracle (or any other ODBC compliant database for that matter).

<a href="http://www.jasonconger.com/images/articleImages/WIRM/v3.0_update/SOA_large.gif" target="_blank"><img src="http://www.jasonconger.com/images/articleImages/WIRM/v3.0_update/SOA_small.gif" alt="SOA Architecture" /></a>

<span class="heading">"Sneak Peek" of Version 3.0</span>
The above mentioned architecture makes the information aggregation possible in version 3.0.  To get a better idea of how this all fits together, I have included this screen shot of the new configuration page.  The more information you provide on the configuration page, the more information you get in the Web Interface.

<a href="http://www.jasonconger.com/images/articleImages/WIRM/v3.0_update/configuration.gif" target="_blank"><img src="http://www.jasonconger.com/images/articleImages/WIRM/v3.0_update/configuration_small.gif" alt="" /></a>

So, stay tuned, there is still more to come...