---
id: 33
title: Project Mobius Beta 2
date: 2007-07-18T09:55:00-05:00
author: jason
excerpt: 'Migrating or maintaining multiple Citrix farms?  Project Mobius is a Microsoft Windows application that allows you to drag and drop published applications and/or folders from one Citrix Presentation Server farm to one or more separate Citrix Presentation Server farms.'
layout: post
guid: /post/Project-Mobius-Beta-2.aspx
categories:
  - MFCOM
tags:
  - Download
  - MFCOM
  - Project Mobius
  - XenApp
---
One of the most popular ways to migrate from one Citrix Presentation Server farm to a new Citrix Presentation Server farm is to build the farms in parallel and use Web Interface to aggregate the two separate farms’ published applications. This is a great strategy and I have used parallel farms many times in the past to migrate users to a new farm. One of the challenges of this strategy is duplicating published applications and policies from the old farm to the new farm. Traditionally, you would need to either manually create each published application in the new farm or use scripting to export/import published applications. This is where Project Mobius comes in. Project Mobius is a Microsoft Windows application that allows you to drag and drop published applications and/or folders from one Citrix Presentation Server farm to one or more separate Citrix Presentation Server farms. Project Mobius currently only has capabilities to migrate published applications and content, but the capability to migrate policies is slated for a future release.

 <img src="http://www.jasonconger.com/images/zip_small.gif" alt="" align="absBottom" /> <a href="http://www.jasonconger.com/downloads/Mobius/JasonConger.com_MobiusB2.zip">Download Project Mobius Beta 2</a>

<strong>What's New in Beta 2?</strong>
The following enhancements have been made for Beta 2:
<ul>
	<li>Supports migrating published content.</li>
	<li>Supports migrating content redirection file type associations.</li>
	<li>Supports migrating nearly all application settings using a "least common denominator" methodology. This means that applications can be migrated upward or downward across Citrix platforms. For instance, a published application can be migrated from a MetaFrame XP farm to a Presentation Server 4.5 farm. Or, vice versa, a published application can be migrated from a Presentation Server 4.5 farm to a MetaFrame XP farm.</li>
	<li>Numerous visual feedback enhancements.</li>
	<li>No policy migration yet. I am still working on getting the bugs ironed out of policy migration. I have a lot of the policy migration code written, but it is still a little "less than stable" so I excluded it from the latest build. If you would like to be a tester for Beta 3 (with policy migration), shoot me an email.</li>
</ul>
* Special thanks goes to David Taig for enhancement suggestions and testing the various builds of Project Mobius. <strong></strong>
Project Mobius requires <a href="http://www.microsoft.com/downloads/details.aspx?familyid=0856EACB-4362-4B0D-8EDD-AAB15C5E04F5&amp;displaylang=en" target="_blank">Microsoft .Net Framework version 2.0</a>.

Installation

Project Mobius utilizes MFCOM to perform application migration. Thus, Project Mobius must be run from either a Citrix Presentation Server or a workstation that has the <a href="http://support.citrix.com/article/CTX107029" target="_blank">Citrix Presentation Server SDK</a> installed and registered for DCOM (utilizing mfreg.exe).

Project Mobius does not require an install. Simply copy Mobius.exe as well as Interop.MetaFrameCOM.dll to a location on your Presentation Server (or workstation).

<strong>Tested Platforms</strong>
The MFCOM interfaces and methods used in the source code for Project Mobius should be compatible with Citrix MetaFrame XP 1.0 and above. However, Project Mobius has specifically been tested on the following platforms:
<ul>
	<li>Citrix MetaFrame XP FR3 (Microsoft Windows 2000)</li>
	<li>Citrix Presentation Server 3.0 (Microsoft Windows 2003)</li>
	<li>Citrix Presentation Server 4.0 (Microsoft Windows 2003)</li>
	<li>Citrix Presentation Server 4.5 (Microsoft Windows 2003)</li>
</ul>
<strong>Using Project Mobius</strong>

<span style="text-decoration: underline;">Step 1</span> - Click File -&gt; Connect to Farm. Then, specify any Citrix Presentation/MetaFrame Server in any farm you want to manage.  Project Mobius uses the specified server to enumerate all published applications and folders in a given farm.  Repeat this step for any additional farms you want to manage. (Tip: you may also right click on the Enterprise Farms tree node or click the Connect to Farm icon to connect to a farm.

<a class="enlarge" href="http://www.jasonconger.com/images/articleImages/Mobius/v1.0/Connect_large.jpg" target="_blank"><img src="http://www.jasonconger.com/images/articleImages/Mobius/v1.0/Connect_thumb.jpg" alt="Connect to Farm" />
<img src="http://www.jasonconger.com/images/magnify.gif" alt="Click to enlarge" width="20" height="20" align="absBottom" /> Click to enlarge</a>

<span style="text-decoration: underline;">
Step 2</span> - Highlight a folder in the left hand tree view containing the published applications and folders you want to migrate.  Drag and drop the published applications and folders from the right hand side to the appropriate location in any farm on the left hand side. (Tip: you may use Ctrl or Shift to select multiple published applications or folders).

<a class="enlarge" href="http://www.jasonconger.com/images/articleImages/Mobius/v1.0/FarmApps_large.jpg" target="_blank"><img src="http://www.jasonconger.com/images/articleImages/Mobius/v1.0/FarmApps_thumb.jpg" alt="Farm Applications" />
<img src="http://www.jasonconger.com/images/magnify.gif" alt="Click to enlarge" width="20" height="20" align="absBottom" /> Click to enlarge</a>
<span style="text-decoration: underline;">
Optional</span> - Farms that have a large number of applications may take several minutes to enumerate all published applications.  This is due to the fact that Project Mobius has to use the LoadData() method of the IMetaFrameApplication interface for each published application in order to retrieve the application object and bind the object to the tree view.  This can be time consuming as each call to LoadData retrieves all properties for a published application.  To mitigate this time consuming process, click on Tools -&gt; Options.  Then, select Enable dynamic population.  This option will only load published applications for the selected folder.  Each time you highlight a new folder, Project Mobius will dynamically retrieve the published applications within the folder.

<a class="enlarge" href="http://www.jasonconger.com/images/articleImages/Mobius/v1.0/Options_large.jpg" target="_blank"><img src="http://www.jasonconger.com/images/articleImages/Mobius/v1.0/Options_thumb.jpg" alt="Options" />
<img src="http://www.jasonconger.com/images/magnify.gif" alt="Click to enlarge" width="20" height="20" align="absBottom" /> Click to enlarge</a>

<strong>Trivial Information</strong>
For those of you still reading and wondering why this piece of software is called Project Mobius, let me explain. Citrix code names Presentation Server after rivers (Hudson = Presentation Server 3.0; Colorado = Presentation Server 4.0; Ohio = Presentation Server 4.5; etc.). I was pondering what to name this project and I decided to name products after wakeboard tricks. One wakeboard trick that has a cool sounding name in my opinion is called a Mobius. A Mobius is a back side roll (flip) with a 360 degree handle pass rotation.  If you want to see what it looks like, <a href="videos/Mobius.mov">check out this video</a>.  So, all in all, this project has no hidden tie in to the wakeboarding Mobius.  I just think it is a cool name (and trick).