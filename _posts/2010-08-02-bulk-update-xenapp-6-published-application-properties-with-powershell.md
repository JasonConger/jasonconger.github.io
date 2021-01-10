---
id: 7
title: Bulk Update XenApp 6 Published Application Properties with PowerShell
date: 2010-08-02T13:47:00-05:00
author: jason
excerpt: 'There are times when you need to update a property on multiple XenApp published applications.  If you only have a few applications to update, this can be done via the management console.  However, if you have more than a few applications to update, then PowerShell is the way to go.  In this post, I will show you how to use PowerShell to update published application properties on multiple applications at the same time.'
layout: post
guid: /post/Bulk-Update-XenApp-6-Published-Application-Properties-with-PowerShell.aspx
permalink: /2010/08/02/bulk-update-xenapp-6-published-application-properties-with-powershell/
image: wp-content/uploads/2010/08/PowerShell.png
categories:
  - Citrix XenApp
  - PowerShell
tags:
  - PowerShell
  - XenApp
---
<span style="color: #ff0000;">Disclaimer: This article deals with Citrix XenApp 6 and above only. PowerShell cmdlets are available for XenApp 5.0 on Windows Server 2003 and 2008; however, the cmdlets are CTP (Community Technology Preview) and will likely never get “officially” released. The cmdlets in XenApp 5 are not always the same as the cmdlets in XenApp 6.</span>

Have you ever had the need to update a lot of Citrix XenApp published application properties at the same time?&nbsp; For instance, suppose you publish all your Citrix XenApp applications with sound disabled.&nbsp; Then, somebody comes up to you and says “hey, we need to have all our applications support sound.&nbsp; Thanks.”&nbsp; If the only tool you had to use was the Citrix console, you will probably get carpal tunnel syndrome from all the mouse clicking you will need to do.&nbsp; Luckily, the management console is not your only tool to solve this dilemma.&nbsp; By using PowerShell and the Citrix XenApp 6 PowerShell cmdlets, this task is reduced to a single command.
<h2>Updating all Citrix XenApp 6 Published Applications with PowerShell</h2>
<img style="display: inline; margin-left: 0px; margin-right: 0px; border: 0px;" title="Note" src="http://www.jasonconger.com/images/articleImages/info.png" border="0" alt="Note" width="16" height="16" align="left" /> Note: if you haven’t already done so, you need to install the Citrix XenApp 6 PowerShell SDK to use the XenApp PowerShell cmdlets.&nbsp; Refer to <a title="How to Install the Citrix XenApp 6 PowerShell Cmdlets" href="http://www.jasonconger.com/post/How-to-Install-the-Citrix-XenApp-6-PowerShell-Cmdlets.aspx">this post</a> for more information.

The following command will set every published application in the farm to have an audio type of Basic:
<pre class="brush: PowerShell;">Set-XAApplication * -AudioType Basic</pre>
To break this down some more:
<ul>
	<li>Set-XAApplication will set a property on any application</li>
	<li>The * is the search string to match.&nbsp; If you wanted to match any application that started with <em>test</em>, you could use <em>test</em>*.</li>
	<li>-AudioType is the property we are setting.&nbsp; In this case, AudioType is an enumeration.&nbsp; AudioType can be set to Unknown, None, or Basic</li>
</ul>
To see a list of all the properties that can be set on a XenApp published application, check out the help file that comes with the XenApp 6 PowerShell SDK, use Get-Member in PowerShell, or check out <a title="Citrix XenApp 6 Application Properties" href="http://www.jasonconger.com/page/Citrix-XenApp-6-Application-Properties.aspx">this page</a>.
<h2>Updating Citrix XenApp 6 Published Applications in a Folder</h2>
If you only wanted to update some publised applications in a particular folder, you can first select all applications in a folder and then pass those application objects to the Set-XAApplication cmdlet like so:
<pre class="brush: PowerShell;">Get-XAApplication –FolderPath Applications/Testing | Set-XAApplication –PassThru –AudioType Basic</pre>
Breaking it down:
<ul>
	<li>Get-XAApplication gets a collection of XenApp applications</li>
	<li>-FolderPath lets Get-XAApplication know that we just want to get applications in a particular folder</li>
	<li>Applications/Testing is the folder that holds the applications we want.</li>
	<li>We then pipe (using the pipe ‘|’ character) all these XenApp application objects into the Set-XAApplication cmdlet (the same cmdlet we used above)</li>
	<li>This time, we use the –PassThru parameter to let Set-XAApplication cmdlet know that we are not going to search for some applications, but instead we are going to pass one or more XenApp application objects to it.</li>
	<li>The rest of the parameters are the same as above</li>
</ul>
There you have it.&nbsp; We have now set a property for all applications using one command, as well as set application properties using selection criteria.&nbsp; Hope this helps you out with your XenApp environment.