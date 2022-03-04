---
id: 5
title: Citrix Acquires Cloud Control Panel Company EMS Cortex
date: 2011-02-22T09:00:00-06:00
author: jason
excerpt: Citrix acquired EMS Cortex – a cloud control panel company. This web-based control panel allows for provisioning of a multitude of resources including Microsoft Exchange, Citrix XenApp, Microsoft SharePoint, DNS, SQL, Hyper-V, and more.
layout: post
guid: /post/Citrix-Acquires-Cloud-Control-Panel-Company-EMS-Cortex.aspx
image: wp-content/uploads/2011/02/Citrix.png
categories:
  - Citrix
tags:
  - Citrix
  - Cortex
  - Exchange
  - SharePoint
  - SQL
---
<a href="http://www.jasonconger.com/images/articleImages/citrix%20cortex.png" target="_blank" rel="lightbox"><img style="background-image: none; margin: 0px auto; padding-left: 0px; padding-right: 0px; display: block; float: none; padding-top: 0px; border-width: 0px;" title="citrix cortex" src="http://www.jasonconger.com/images/articleImages/citrix%20cortex_thumb.png" border="0" alt="citrix cortex" width="363" height="80" /></a>

Citrix <a href="http://community.citrix.com/display/ocb/2011/02/22/Citrix+Betting+Big+on+Cloud+App+Delivery" target="_blank">announced today</a> that they have acquired a Cloud control panel company called <a href="http://ems-cortex.com/" target="_blank">EMS Cortex</a>. EMS Cortex makes a web-based cloud control panel that automates the provisioning of an array of Microsoft Products including Exchange, SharePoint, OCS, Web Hosting, SQL Server, DNS, RDS, Microsoft Dynamics CRM, and Hyper-V.&nbsp; The EMS Cortex control panel also automates the provisioning of Citrix XenApp applications and desktops.&nbsp; I am personally very excited about this news because I use Cortex in my current job at <a href="http://xcentric.com/" target="_blank">Xcentric</a>.
<h2>What is EMS Cortex?</h2>
In a multi-tenant hosting environment, it is very important to have a strict provisioning routine to ensure consistency.&nbsp; EMS Cortex makes a web-based control panel to automate the provisioning process used in multi-tenant hosting environments.&nbsp; Cortex provisions Active Directory OUs, user accounts, groups, file shares, SharePoint sites, Citrix XenApp resources, etc.&nbsp; Through the use of Cortex, you no longer have to visit multiple consoles to provision users - just set up the user in Cortex and the rest is taken care of.&nbsp; This is good because Cortex removes the human error factor.

As I mentioned before, we use Cortex at <a href="http://xcentric.com/" target="_blank">Xcentric</a>.&nbsp; Cortex is the centralized provisioning engine for our multi-tenant hosting environment.&nbsp; There are a lot of good things about Cortex and some things I wish I could change (I’ve already started talking with Cortex about the things I wish I could change).&nbsp; I’m hopeful that we, the community, will see even more Citrix-focused integration points in future releases.
<h2>How EMS Cortex Works</h2>
Cortex is a multi-tier application consisting of the following components:
<ul>
	<li>SQL Database - for configuration, users, customers, auditing and reporting.</li>
	<li>Web Services - for real time interaction with Active Directory and other hosted services.</li>
	<li>Provisioning Engine - via Microsoft Message Queue (MSMQ), provisioning requests are dispatched to the provisioning engine.</li>
</ul>
The Cortex web application is loosely coupled with the other Cortex components. This loose coupling provides several security benefits, as the web server has no dependency on Active Directory it can essentially operate outside of the managed domain.&nbsp; Cortex can also manage multiple domains.

<a href="http://www.jasonconger.com/images/articleImages/cortex%20architecture.png" target="_blank"><img style="background-image: none; margin: 0px auto; padding-left: 0px; padding-right: 0px; display: block; float: none; padding-top: 0px; border-width: 0px;" title="cortex architecture" src="http://www.jasonconger.com/images/articleImages/cortex%20architecture_thumb.png" border="0" alt="cortex architecture" width="567" height="371" /></a> Image source: <a href="http://ems-cortex.com/architecture/how-cortex-works.aspx" target="_blank">http://ems-cortex.com/architecture/how-cortex-works.aspx</a>
<h2>What will Citrix do with EMS Cortex?</h2>
Now, the things I’m about to share are purely off the top of my head and are not necessarily the direction Citrix intends on taking this product (although I hope they do).

<span style="text-decoration: underline;">Virtual Machine automation</span> – ok, I kind of cheated on this one because Cortex already integrates with Hyper-V.&nbsp; But this automation is solely based on System Center Microsoft Virtual Machine Manager.&nbsp; So, it would be cool to provision VMs for XenServer and *gasp* VMware.&nbsp; SCVMM is somewhat sketchy with VMware ESX and vSphere and there is currently no SCVMM integration with XenServer (although, there were some screenshots of SCVMM and XenServer at Synergy last year – not sure where that is now).&nbsp; So, either SCVMM will have to amp up on vendor support or Cortex will need to go native API for vendors besides Microsoft.

<span style="text-decoration: underline;">Cloud bursting</span> – this one goes along with the Virtual Machine automation.&nbsp; Citrix has been working with <a href="http://www.citrix.com/English/partners/partner.asp?partnerID=1854698" target="_blank">Amazon Web Services</a>, <a href="http://www.softlayer.com/press_2008_09_16.html" target="_blank">SoftLayer</a>, and even has their <a href="http://www.citrix.com/English/ps2/products/product.asp?contentID=1681633" target="_blank">Citrix Cloud Center (C3)</a>.&nbsp; So, it would be cool to see some hooks built in for platforms like these.&nbsp; Imagine being able to provision an tenant in one of the vendor clouds instead of provisioning local resources.

<span style="text-decoration: underline;">Access Gateway Policy provisioning</span> – Cortex provides a lot of self-service functionality for tenants.&nbsp; It would be cool to give tenants the ability to define Access Gateway policies tailored to their own needs without the help of a system administrator.

<span style="text-decoration: underline;">XenDesktop integration</span> – currently, Cortex only supports hosted apps and desktops via XenApp.&nbsp; It would be nice to see integration with XenDesktop.

<span style="text-decoration: underline;">PowerShell</span> – the current API for Cortex is a mixture of web services and a somewhat proprietary API for the&nbsp; MSMQ.&nbsp; It would be cool to see some PowerShell cmdlets to interface with the provisioning lifecycle.

<span style="text-decoration: underline;">Workflow Studio</span> – <a href="http://www.citrix.com/English/ps2/products/product.asp?contentID=1297816&amp;ntref=hp_nav_US" target="_blank">Citrix Workflow Studio</a> is all about infrastructure automation/orchestration.&nbsp; Wouldn’t it be cool if Workflow Studio has activities to create a user that utilized the Cortex provisioning engine?&nbsp; Workflow Studio already has an activity to create Active Directory users, but imagine an activity that used Cortex to create a user instead – thus provisioning all the other “stuff” like Exchange, SharePoint, file system, website access, etc. as well.&nbsp; That would be cool.

<span style="text-decoration: underline;">Storage provisioning</span> – one piece that we still have to provision manually at Xcentric is dedicated storage for each tenant.&nbsp; It would be cool to see some kind of storage provisioning system – maybe pull in the StorageLink group?

<span style="text-decoration: underline;">Single tenant support</span> – For the near term, the Cortex Cloud Control Panel will be offered as a standalone product on a subscription basis, as it was prior to the acquisition.&nbsp; Cortex is great for multi-tenant environments, but it is also very helpful in a single tenant environment.&nbsp; So, it would be cool to see Cortex rolled into one of the editions of XenDesktop or XenApp.

<span style="text-decoration: underline;">Postini integration</span> – this is another feature that currently isn’t offered by Cortex.&nbsp; Granted, Google gives you a cool utility to sync users with LDAP directories, but it would be even cooler if Cortex worked with Postini API’s directly.

I could keep making this list for a while.&nbsp; Needless to say, I’m very excited about this acquisition.