---
id: 413
title: Migrate Citrix XenApp 6 Folder Structure Using PowerShell
date: 2011-05-31T22:02:25-05:00
author: JasonConger
excerpt: 'There are times when you need to migrate all or part of your Citrix XenApp 6 folder structure from one farm to another, or just back up a XenApp 6 folder structure.  This post will show you how to accomplish this using PowerShell.'
layout: post
image: wp-content/uploads/2010/08/PowerShell.png
categories:
  - Citrix
tags:
  - Citrix
  - PowerShell
  - XenApp
---
There are times when you want to migrate a folder structure from one Citrix XenApp 6 farm to another.  For instance, if you maintain separate test, quality assurance, and production farms and need to migrate folders and applications between the farms.  Fortunately, this is super easy in XenApp 6 using PowerShell.

<img src="http://www.jasonconger.com/images/articleImages/Note.png" alt="note" /> Note: before you get started, be sure to check out [this post on how to install the Citrix XenApp 6 PowerShell Cmdlets]]({% post_url 2010-08-02-how-to-install-the-citrix-xenapp-6-powershell-cmdlets %}).

<h2>Export Specified Folders</h2>
You can export your entire folder structure, or just certain parts of it.  In the example below, I will export only the "Testing" folder (see the screen shot below).

<img class="aligncenter size-full wp-image-436" title="XenApp 6 Testing Folder" src="http://www.jasonconger.com/wp-content/uploads/2011/05/XenApp-6-Testing-Folder.jpg" alt="" width="259" height="307" />

Here is how to export just the "Testing" folder and its subfolders using PowerShell to a XML file called "TestingFolders.xml":
~~~
Get-XAFolder -FolderPath "Applications/Testing" -Recurse | Export-Clixml c:\TestingFolders.xml
~~~

<h3>Explanation</h3>
Well, the cool thing about PowerShell is that it is pretty readable, so I don't think this command needs a lot of explanation. However, let's look at the resulting XML file.
~~~
  <s>Applications/Testing/Microsoft Office</s>
  <s>Applications/Testing/Sales</s>
  <s>Applications/Testing/Utilities</s>
  <s>Applications/Testing/Utilities/Microsoft</s>
  <s>Applications/Testing/Utilities/Citrix</s>
~~~

No rocket science there either. It is just a list of folders. You could easily hand craft one of these XML files to create a folder structure. What I am going to do here is modify the folder path so that the folders get created in the "Applications/QA" folder and then save the file as "QAfolders.xml". Here is what the XML file looks like now:

~~~xml
  <s>Applications/QA/Microsoft Office</s>
  <s>Applications/QA/Sales</s>
  <s>Applications/QA/Utilities</s>
  <s>Applications/QA/Utilities/Microsoft</s>
  <s>Applications/QA/Utilities/Citrix</s>
~~~

<h2>Import Folders</h2>
Now that you have your XML file, it is relatively easy to import. Here is how to do it:

~~~powershell
Import-Clixml c:\QAFolders.xml | New-XAFolder
~~~

Here are the results:

<img class="aligncenter size-full wp-image-493" title="XenApp 6 QA Folder" src="http://www.jasonconger.com/wp-content/uploads/2011/05/XenApp-6-QA-Folder.jpg" alt="" width="204" height="259" />

<h2>Next Steps</h2>
So all this folder structure stuff is fine, but wouldn't it be nice to import some apps into those folders? Of course it would. Here is how to [export and import XenApp 6 published applications using PowerShell]({% post_url 2011-06-13-export-and-import-citrix-xenapp-6-published-applications-using-powershell %}).