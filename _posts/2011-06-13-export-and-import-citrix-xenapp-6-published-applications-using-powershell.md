---
id: 498
title: Export and Import Citrix XenApp 6 Published Applications Using PowerShell
date: 2011-06-13T08:51:02-05:00
author: jason
excerpt: 'Exporting and Importing published applications in Citrix XenApp used to be a tedious process.  Now, thanks to XenApp PowerShell Cmdlets, this process is much easier and more flexible.  No uber scripting skills needed.'
layout: post
guid: http://www.jasonconger.com/?p=498
image: wp-content/uploads/2010/08/PowerShell.png
categories:
  - Citrix
  - PowerShell
tags:
  - Citrix
  - PowerShell
---
Exporting and importing Citrix XenApp 6 published applications using PowerShell is super easy.  In this article, I will show you how to export all or some of your XenApp 6 published applications into a XML file.  Then, I will show you how to import those applications while overriding certain application properties like Worker Group and Server Names.

<img src="http://www.jasonconger.com/images/articleImages/Note.png" alt="note" /> Note: before you get started, be sure to check out <a title="How to Install the Citrix XenApp 6 PowerShell Cmdlets" href="http://www.jasonconger.com/post/how-to-install-the-citrix-xenapp-6-powershell-cmdlets/">this post on how to install the Citrix XenApp 6 PowerShell Cmdlets</a>.

&nbsp;
<h2>Exporting Citrix XenApp 6 Published Applications</h2>
The first thing we need to do is export some published applications from an existing XenApp 6 farm.  In this example, I will only export applications in a certain folder instead of the entire application inventory.

<pre class="brush: PowerShell;">
Get-XAApplicationReport * | ?{$_.FolderPath.StartsWith("Applications/Testing")} | Export-Clixml c:\testingApps.xml
</pre>


&nbsp;
<h3>Explanation</h3>
So, there are 3 parts to this export.
<ol>
<li>
<code>Get-XAApplicationReport</code> gets all properties of a published application.  If you are familiar with MFCOM, the <code>Get-XAApplicationReport</code> command is similar to calling <code>LoadData(1)</code> on an application object.

<br />
FYI - There is a command called <code>Get-XAApplication</code>, but that command doesn't get all properties of a published application.

<br />
Anyway, if you don't use the <code>Get-XAApplicationReport</code> command, you won't get all your application properties and you will be sad.
</li>
<li><code>?{$_.FolderPath.StartsWith("Applications/Testing")}</code> looks at each application object that <code>Get-XAApplicationReport</code> returns and filters out all applications whose folder path does not start with "Applications/Testing".

<br />
Note to Citrix - it would be nice to have some filtering built into the <code>Get-XAApplicationReport</code> command.  You will notice in the example, that I have to get all the published applications in a farm and filter out what I do not want.  That is a pretty expensive operation.  It would be better to just get what I want from the get go.
</li>
<li>
<code>Export-Clixml</code> saves it all to a XML file called testingApps.xml.
</li>
</ol>
&nbsp;
<h2>Importing Citrix XenApp 6 Published Applications</h2>
Now that you have the applications exported to a XML file, you can import those applications to another farm.       Here is one way to do this:

<pre class="brush: PowerShell">
Import-XmlCli c:\testingApps.xml | New-XAApplication -ServerNames [servers] -WorkerGroupNames $null
</pre>

<br />
The cool thing about this is that you can override settings during an import.  For instance, the original farm I exported from had published applications assigned to Worker Groups rather than Servers.  In the destination farm, I want to publish the applications to Servers rather than Worker Groups.  You can actually override a multitude of properties during the import process which will make your life easier.

<img src="http://www.jasonconger.com/images/articleImages/Note.png" alt="note" /> Note: if you do not create the folder structure beforehand, you will get the following error when you try to import:

<pre class="brush: xml; gutter: false">
New-XAApplication : Cannot find folder with path Applications/Testing (0x80160001)
At line:1 char:70
+ Import-Clixml C:\testingApps.xml | New-XAApplication <<<<
    + CategoryInfo : InvalidResult: (Applications/Testing:String) [New-XAApplication], CitrixException
    + FullyQualifiedErrorId : ComApp.GetFolderId,Citrix.XenApp.Commands.NewAppCmdlet
</pre>

So, check out this <a href="http://www.jasonconger.com/post/migrate-citrix-xenapp-6-folder-structure-using-powershell/">article on migrating a folder structure</a>.

<p>&nbsp;</p>
