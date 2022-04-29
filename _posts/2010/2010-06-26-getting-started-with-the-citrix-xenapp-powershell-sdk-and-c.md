---
id: 9
title: 'Getting Started with the Citrix XenApp PowerShell SDK and C#'
date: 2010-06-26T00:26:09-05:00
author: JasonConger
excerpt: 'In XenApp 6, MFCOM is out and PowerShell is in.  This post is the first in a series to help you understand how to develop appliations that utilize the Citrix XenApp 6 PowerShell SDK and Microsoft C#.'
layout: post
image: wp-content/uploads/2010/08/PowerShell.png
categories:
  - Citrix XenApp
  - MFCOM
  - PowerShell
tags:
  - 'C#'
  - MFCOM
  - PowerShell
  - XenApp
---
At <a href="http://www.briforum.com/" target="_blank">BriForum 2010</a>, <a href="http://bsonposh.com/" target="_blank">Brandon Shell</a> and I presented a session on [how to make the transition from MFCOM to PowerShell]({% post_url 2010-06-08-mfcom-to-powershell-how-to-make-the-transition %}). At the end of the session, I presented several examples on how to use the XenApp PowerShell SDK in C#. I wanted to share some of the details on those examples in a few blog posts. This first blog post will detail what is needed to get started developing applications that leverage the Citrix XenApp 6 PowerShell SDK.

<h2>What you need</h2>
To get started, you need to set up a development environment. You really only need two things:
<ul>
	<li>Visual Studio (2005 or above is recommended). You can use <a href="http://www.microsoft.com/express/" target="_blank">Visual Studio Express</a> (free) if you like.</li>
	<li><a href="http://community.citrix.com/display/xa/XenApp+6+PowerShell+SDK" target="_blank">Citrix XenApp 6 PowerShell SDK</a></li>
</ul>
Actually, there isn’t anything set in stone that says you *have* to use Visual Studio, but it will make your life a whole lot easier. I recommend installing Visual Studio on a XenApp server because remoting in PowerShell is less than desirable for these examples.

<h2>Creating your first project</h2>
After you install Visual Studio and the Citrix XenApp 6 PowerShell SDK, you are ready to get started with your first project. The examples I will be showing will be web projects. So, launch Visual Studio and select File &gt; New &gt; Project...

<a href="http://www.jasonconger.com/images/articleImages/VSNewWebsite_1.png" target="_blank"><img style="display: block; float: none; margin-left: auto; margin-right: auto; border-width: 0px;" title="Visual Studio New Project" src="http://www.jasonconger.com/images/articleImages/VSNewWebsite_thumb_1.png" border="0" alt="Visual Studio New Project" width="500" height="200" /></a>

<a href="http://www.jasonconger.com/images/articleImages/VSNewProject_1.png" target="_blank"><img style="display: block; float: none; margin-left: auto; margin-right: auto; border: 0px;" title="VSNewProject" src="http://www.jasonconger.com/images/articleImages/VSNewProject_thumb_1.png" border="0" alt="VSNewProject" width="500" height="321" /></a>

<h2>Add a Reference to System.Management.Automation</h2>
After you create your Project, you need to add a reference to <strong>System.Management.Automation.dll</strong> in order to do stuff with PowerShell in your project. If you go looking for this DLL in the file system, you will find it at %ProgramFiles%\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0 &lt;- <strong>DO NOT USE THIS FILE</strong>. The version of System.Management.Automation you want is in the GAC.

Normally, if you want to add a reference to an assembly that lives in the GAC to your project, you can just right-click your project in Visual Studio, select Add Reference and browse for the name. But, for some reason, this assembly isn’t like the others. You actually have to close your project in Visual Studio and manually add a reference to System.Management.Automation by editing the .csproj file. For example, if your project name was WebApplication1, you would need to edit WebApplication1.csproj (you can use Notepad to edit this file if you like since this file is just XML) and manually add:

~~~xml
<Reference Include="System.Management.Automation" />
~~~

Once you manually add this reference to your project file, you will want to add a couple of using statement to your code files that will deal with PowerShell:

~~~c#
using System.Management.Automation;
using System.Management.Automation.Runspaces;
~~~

<h2>To Wrap or not to Wrap</h2>
There are basically two ways to use the Citrix XenApp 6 PoweShell SDK in a C# project:
<ol>
	<li>Use "traditional" PowerShell Runspace (uses common PowerShell Runspaces)</li>
	<li>Use the XenApp 6 wrapper assemply (wraps each command and paramter in a Class for safe typing)</li>
</ol>
There are pros and cons for both:
<h3>"Traditional" PowerShell Runspace pros:</h3>
<ul>
	<li>Easy to convert existing PowerShell scripts to C#.</li>
	<li>You can log all the PowerShell commands and save before running – kind or like Microsoft Exchange 2007 does.</li>
</ul>
<h3>"Traditional" PowerShell Runspace cons:</h3>
<ul>
	<li>No type safety – meaning that commands and parameters are specified as strings – which means you can mess up by typing the wrong string making troubleshooting difficult.</li>
	<li>No IntelliSense for XenApp commands/odjects in Visual Studio.</li>
</ul>
<h3>XenApp 6 Wrapper pros:</h3>
<ul>
	<li>Type safety. Every command and parameter is wrapped in a class so there is no chance of misspelling a string parameter or passing an incorrect parameter.</li>
	<li>Enables IntelliSense in Visual Studio.</li>
</ul>
<h3>XenApp 6 Wrapper cons:</h3>
<ul>
	<li>Does not translate well to PowerShell commands. For instance, the PowerShell command to get an application is Get-XAApplication. The wrapper assembly’s command is GetXAApplicationByName().</li>
</ul>
I like using the wrapper assembly personally, but in the end it is all the same.
<h2>What’s Next?</h2>
I’ll be writing a few more posts on concrete examples of using the XenApp 6 PowerShell SDK. Stay tuned…