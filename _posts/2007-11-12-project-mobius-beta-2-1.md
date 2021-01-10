---
id: 30
title: Project Mobius Beta 2.1
date: 2007-11-12T10:35:00-06:00
author: jason
excerpt: Migrating or maintaining multiple Citrix farms? Project Mobius is a Microsoft Windows application that allows you to drag and drop published applications and/or folders from one Citrix Presentation Server farm to one or more separate Citrix Presentation Server farms.
layout: post
guid: /post/Project-Mobius-Beta-21.aspx
permalink: /2007/11/12/project-mobius-beta-2-1/
categories:
  - MFCOM
tags:
  - Download
  - MFCOM
  - Project Mobius
  - XenApp
---
Project Mobius Beta 2.1 includes some visual enhancements as well as some bug fixes. The main bug fixed in Project Mobius Beta 2.1 addresses an issue when migrating applications from a Citrix MetaFrame XP farm to a Citrix Presentation Server 3.0 or above farm. You may receive an error that states:

<code>Failed to copy published application ({App_Name}). </code>

Details: Unable to cast COM object of type 'System.__ComObject' to interface type 'MetaFrameCom.IMetaFrameApplication4', This operation failed because the QueryInterface call on the COM component for the interface with IID'{ED62F58D-63C2-11D4-94D8-00C04FB0F326}' failed due to the following error: no such interface supported (Exception from HRESULT: 0x80004002 {E_NOINTERFACE)).

This issue has been resolved in the latest code.

 <img src="http://www.jasonconger.com/images/zip_small.gif" alt="" align="absBottom" /> <a href="http://www.jasonconger.com/downloads/Mobius/JasonConger.com_MobiusB21.zip">Download Project Mobius Beta 2.1</a>

While we're on the topic of Project Mobius, let me quickly address Project Mobius Beta 3. Project Mobius Beta 3 will include a "best effort" policy migration. What does a "best effort" policy migration mean you may ask? To explain this, I first need to tell you about my adventures with policies in MFCOM. Let's just say that the stability of policy manipulation in MFCOM is, um, less that 100%. I consistently received errors on certain methods when trying to manipulate polices programmatically that, according to the documentation, should have worked. That being said, I almost scrapped Beta 3 of Project Mobius altogether.

Fast forward to <a href="http://www.briforum.com/europe/2007/" target="_blank">BriForum Europe 2007</a>. I was chatting with <a href="http://www.shawnbass.com/" target="_blank">Shawn Bass</a> and <a href="http://www.thomaskoetzing.de/" target="_blank">Thomas Koetzing</a> during a break and relaying my frustration concerning the roadblocks I was running into with programmatically manipulating policies via MFCOM. Then, a suggestion was made to me. Why not migrate everything you can in code. Then, create a report on anything that failed during the process. That way, you can get 85% - 90% of the way there programmatically on the policy settings and only have to do 10% - 15% manually. That sounded good to me, so I resurrected Beta 3 and started to implement this "best effort" policy migration. Look for this in Project Mobius Beta 3.