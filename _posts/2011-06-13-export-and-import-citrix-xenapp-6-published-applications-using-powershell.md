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

<img src="http://www.jasonconger.com/images/articleImages/Note.png" alt="note" /> Note: before you get started, be sure to check out [this post on how to install the Citrix XenApp 6 PowerShell Cmdlets]({% post_url 2010-08-02-how-to-install-the-citrix-xenapp-6-powershell-cmdlets %}).

<h2>Exporting Citrix XenApp 6 Published Applications</h2>
The first thing we need to do is export some published applications from an existing XenApp 6 farm.  In this example, I will only export applications in a certain folder instead of the entire application inventory.

```powershell
Get-XAApplicationReport * | ?{$_.FolderPath.StartsWith("Applications/Testing")} | Export-Clixml c:\testingApps.xml
```

<h3>Explanation</h3>
So, there are 3 parts to this export.

  1. `Get-XAApplicationReport` gets all properties of a published application.  If you are familiar with MFCOM, the `Get-XAApplicationReport` command is similar to calling `LoadData(1)` on an application object.
  FYI - There is a command called `Get-XAApplication`, but that command doesn't get all properties of a published application.
  Anyway, if you don't use the `Get-XAApplicationReport` command, you won't get all your application properties and you will be sad.
  
  2. `?{$_.FolderPath.StartsWith("Applications/Testing")}` looks at each application object that `Get-XAApplicationReport` returns and filters out all applications whose folder path does not start with "Applications/Testing".
  Note to Citrix - it would be nice to have some filtering built into the `Get-XAApplicationReport` command.  You will notice in the example, that I have to get all the published applications in a farm and filter out what I do not want.  That is a pretty expensive operation.  It would be better to just get what I want from the get go.
  
  3. `Export-Clixml` saves it all to a XML file called testingApps.xml.

<h2>Importing Citrix XenApp 6 Published Applications</h2>
Now that you have the applications exported to a XML file, you can import those applications to another farm.       Here is one way to do this:

```powershell
Import-XmlCli c:\testingApps.xml | New-XAApplication -ServerNames [servers] -WorkerGroupNames $null
```

The cool thing about this is that you can override settings during an import.  For instance, the original farm I exported from had published applications assigned to Worker Groups rather than Servers.  In the destination farm, I want to publish the applications to Servers rather than Worker Groups.  You can actually override a multitude of properties during the import process which will make your life easier.

<img src="http://www.jasonconger.com/images/articleImages/Note.png" alt="note" /> Note: if you do not create the folder structure beforehand, you will get the following error when you try to import:

```xml
New-XAApplication : Cannot find folder with path Applications/Testing (0x80160001)
At line:1 char:70
+ Import-Clixml C:\testingApps.xml | New-XAApplication <<<<
    + CategoryInfo : InvalidResult: (Applications/Testing:String) [New-XAApplication], CitrixException
    + FullyQualifiedErrorId : ComApp.GetFolderId,Citrix.XenApp.Commands.NewAppCmdlet
```

So, check out this [article on migrating a folder structure]({% post_url 2011-05-31-migrate-citrix-xenapp-6-folder-structure-using-powershell %}).