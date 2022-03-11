---
id: 40
title: MFCOM Script to List Applications Only in Specified Folders
date: 2006-08-28T09:27:00-05:00
author: JasonConger
excerpt: MFCOM Script to List Applications Only in Specified Folders
layout: post
guid: /post/MFCOM-Script-to-List-Applications-Only-in-Specified-Folders.aspx
categories:
  - MFCOM
tags:
  - Download
  - MFCOM
  - Script
  - VBScript
---
Here is a quick MFCOM script to list all the published applications and folders in a specified folder or folders. There are two options for using the script. Option one takes any number of command line arguments. Each command line argument represents a folder name. Option two takes no command line arguments and relies on hard-coded folder names within the script.

<img src="http://www.jasonconger.com/images/zip_small.gif" alt="" align="absBottom" /> <a href="http://www.jasonconger.com/downloads/GetAppsInFolders.zip">GetAppsInFolders.zip</a>

Suppose you had the following tree structure for your published applications:

<img style="border: 1px solid #000" src="http://www.jasonconger.com/images/articleImages/MFCOMGetApps/PSC.gif" alt="" />

Now, say you wanted to run a script that only returned applications in the Testing folder and Microsoft Applications folder. To accomplish this, run the following at a command prompt:

~~~
cscript //Nologo GetAppsInFolders.wsf "Testing" "Microsoft Applications"
~~~

The above command produces the following results:

<img src="http://www.jasonconger.com/images/articleImages/MFCOMGetApps/results1.gif" alt="" />

Note that every folder specified is a child of the "Applications" folder.&nbsp; To specify a folder that is not a child of the "Applications" folder, you must specify the path relative from "Applications". For instance, if you wanted to get only the applications published in the "New Folder" under "Testing", run the following command:

~~~
cscript //Nologo GetAppsInFolders.wsf "Testing/New Folder"
~~~

The above command produces the following results:

<img src="http://www.jasonconger.com/images/articleImages/MFCOMGetApps/results2.gif" alt="" />

To set up the hard-coded folders, open the script in a text editor and look for the following lines (starting around line 31):</p>

```vb
    '
    ' If no command line arguments, use hard-coded folders
    '
    if  WScript.Arguments.Count = 0 Then
        ReDim arrFolders(2)
        arrFolders(0) = "Testing"
        arrFolders(1) = "Microsoft Applications"
    Else
```

Change ReDim arrFolders(2) to ReDim arrFolders(<em>x</em>) where <em>x</em> represents the number of folders you want to hard code.
Next, add arrFolders(<em>n</em>) = "Folder Name" for each folder you want to hard code (where <em>n</em> is a distinct number between 0 and <em>x</em>).

So what is all this good for anyway?&nbsp; Suppose you wanted to export applications in a few select folders, then import those applications in to a different farm. <a href="http://support.citrix.com/article/CTX102982&amp;searchID=27955070" target="_blank">This Citrix article</a> demonstrates how to use EXPORT and NEWAPP from the Citrix APSDK.&nbsp; Using EXPORT and NEWAPP along with GetAppsInFolders.wsf, you can export bulk applications from select specified folders and then import those applications into a different farm.