---
id: 28
title: Script to Manipulate APPSRV.INI
date: 2008-01-06T10:38:00-06:00
author: JasonConger
excerpt: "What happens when you need to make mass changes to APPSRV.INI?  Use this script to make changes to your user's APPSRV.INI file via login script.  The script adds or modifies .INI file key/value pairs and sections."
layout: post
guid: /post/Script-to-Manipulate-APPSRVINI.aspx
categories:
  - Citrix XenApp
tags:
  - Client
  - Customization
  - Download
  - ICA
  - Script
---
Use this script to make changes to your user's APPSRV.INI file via login script. The script adds or modifies .INI file key/value pairs and sections.

 <img src="http://www.jasonconger.com/images/zip_small.gif" alt="" align="absBottom" /> <a href="http://www.jasonconger.com/downloads/mod_appsrv/v1.1/mod_appsrv.zip">Download mod_appsrv script v1.1</a>

<span class="postHeading">The Scenario</span>
So, you have been combing through the various support forums all day long trying to find a solution for an issue. You finally find the solution, but it involves modifying every user’s APPSRV.INI file located on their workstation. One common solution that matches the above scenario has to do with Single Sign On issues with Citrix Web Interface. One of the most recommended solutions is to add the following two lines to the [WFClient] section of APPSRV.INI:

SSOnUserSetting=On
EnableSSOnThruICAFile=On

Reference: <a href="http://support.citrix.com/article/ctx368624" target="_blank">http://support.citrix.com/article/ctx368624</a>

<span class="postHeading">The Dilemma</span>
So, you try this and it fixes the issue for the user. What do you do now? Manually modify each user's APPSRV.INI? Tell your users to perform the modification themselves? Script the change? Tell your boss there is no fix for the issue?

<span class="postHeading">The Solution</span>
Script the change sounds good to me, but how do you do that? That is where this article comes in. I mentioned I had a script to manipulate APPSRV.INI in the comments of <a href="http://www.jasonconger.com/Deploying-a-Pre-Configured-Citrix-Client-using-Active-Directory.aspx">this article</a>. I have received many emails requesting the script. So, I decided to "spruce up" the script a little by adding more comments and logging and then share it. The script is written in such a way that you can add or modify any key/value pair to any section in APPSRV.INI (or any .INI file for that matter). Just modify the following section of the script to suit your needs:

~~~
'**********************************************************
' Add/modify key/value pairs
' modINISection takes 3 parameters:
'    Section name
'    Key
'    Value
'**********************************************************
modINISection "WFClient", "SSOnUserSetting", "On"
modINISection "WFClient", "EnableSSOnThruICAFile", "On"
~~~

The above example shows how to implement the solution to the delimma discussed earlier.

Here is another useful one to add that addresses clipboard issues:

~~~
modINISection "WFClient", "CbChainInterval", "2000"
~~~

From the Citrix Client 9.100 Readme <a href="http://support.citrix.com/article/CTX107650" target="_blank">http://support.citrix.com/article/CTX107650</a>
<div class="quote">"This fix introduces support for a mechanism to check at periodic intervals the client's ability to receive clipboard change notifications. If the mechanism finds the client to be unable to receive such notifications, the client will attempt to register itself to receive future notifications. To enable this functionality, you must modify users' appsrv.ini files as follows: 1. Open the appsrv.ini file located in the user profile directory using a text editor. 2. In the WFClient section, locate or add the entry: CbChainInterval=&lt;value&gt;, where value is the interval, in milliseconds, at which checks are to be performed. Supported values range from 0 to 2,000, inclusive."</div>
Think of it as an auto <a href="http://support.citrix.com/article/CTX106226" target="_blank">RepairCDBChain.exe</a>

Some quick things to note about the script:
<ul>
	<li>If you specify a section for modINISection that does not exist, the section will be created.</li>
	<li>If you specify a key that does not exist, the key will be created at the end of the section.</li>
	<li>Curretnly, there is no implementation to delete key/value pairs (I'm not sure that would even be useful for the intended usage)</li>
	<li>A log file is created in the same directory as the APPSRV.INI file. The log file is named the same as the script name. If you change the script name to match you company's naming convetion, the log file name will change automatically.</li>
</ul>
Good luck and have fun. But, as always, test test test. Make sure this script works in your environment before you throw it out there on your global login script.