---
id: 1704
title: Use PowerShell to get the Citrix Configuration Log as well as Old and New Property Values
date: 2015-10-15T11:00:59-05:00
author: jason
excerpt: This is a quick tip to show you how to get the Citrix Configuration Log, plus all the old and new property values, and convert this all to JSON.
layout: post
guid: http://www.jasonconger.com/?p=1704
permalink: /2015/10/15/use-powershell-to-get-the-citrix-configuration-log-as-well-as-old-and-new-property-values/
image: wp-content/uploads/2010/08/PowerShell.png
categories:
  - Citrix
  - PowerShell
tags:
  - Citrix
  - Configuration Logging
  - PowerShell
---
Here is a quick tip for you. I had a need to get the Citrix Configuration Log, so I dropped into PowerShell and ran Get-CtxConfigurationLogReport. That is all good and well, but you do not get all the old and new values of the changed properties. However, converting this output to JSON will do just what I want. Plus, converting to JSON is better for me anyway as I want to push this stuff over to <a href="http://www.jasonconger.com/post/tag/splunk/" target="_blank">Splunk</a> to do some analytics. Here is what you need to do:
<h1>Step 1 – Create your UDL file to connect to the database</h1>
<pre class="brush: PowerShell;">Add-Content C:\conflog.udl –Value $null; Start-Process C:\conflog.udl</pre>
This will prompt you for your SQL credentials. You can use Windows integrated security if you like, but I’m saving my creds for later use outside of my interactive PowerShell session later.

<a href="http://www.jasonconger.com/wp-content/uploads/2015/10/Citrix-Config-Log-UDL.png"><img class="aligncenter size-medium wp-image-1706" src="http://www.jasonconger.com/wp-content/uploads/2015/10/Citrix-Config-Log-UDL-243x300.png" alt="Citrix Config Log UDL" width="243" height="300" /></a>

&nbsp;
<h1>Step 2 – Get the things</h1>
<pre class="brush: PowerShell;"># Load the Citrix Common Commands Snapin
Get-PSSnapin -Registered "Citrix.Common.Commands" | Add-PSSnapin

# Get the configuration log and convert to JSON
Get-CtxConfigurationLogReport -DataLinkPath C:\conflog.udl | ConvertTo-Json -Depth 10</pre>
&nbsp;

Here is some sample output (notice the property old and new values)
<pre class="brush: PowerShell;">{
    "EntryId":  "3_0_3",
    "Date":  "\/Date(1443804400000)\/",
    "Account":  "LAB\\administrator",
    "TaskType":  2,
    "ItemType":  0,
    "ItemName":  "Calc",
    "Description":  "Published application Calc was modified.",
    "Details":  [
                    {
                        "PropertyName":  "Application Description",
                        "OldValue":  "Calculator",
                        "NewValue":  "Calculator 123"
                    }
                ],
    "References":  [
                   ]
}</pre>
Note, this requires <a href="http://www.microsoft.com/en-us/download/details.aspx?id=34595" target="_blank">PowerShell 3.0</a>

Here is a Gist as well -&gt; <a href="https://gist.github.com/JasonConger/62b9c6ce165503a3112c" target="_blank">https://gist.github.com/JasonConger/62b9c6ce165503a3112c</a>

&nbsp;