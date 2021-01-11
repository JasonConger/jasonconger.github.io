---
id: 53
title: Branding the Citrix ICA Client
date: 2006-03-01T08:14:00-06:00
author: jason
excerpt: Using the techniques described in this article, it is possible to put your own custom logos on the Citrix ICA client during application launch.
layout: post
guid: /post/Branding-the-Citrix-ICA-Client.aspx
permalink: /2006/03/01/branding-the-citrix-ica-client/
categories:
  - Citrix XenApp
tags:
  - Branding
  - Citrix
  - Resource Hacker
---
<span style="font-size: 12px; line-height: 18px;">Using the techniques described in this article, it is possible to put your own custom logos on the client during application launch.  See screen shots below:</span>
<table border="0">
<tbody>
<tr>
<td style="font-size: 12px;"><img style="border: 0px initial initial;" src="http://www.jasonconger.com/images/articleImages/BrandingICA/before.gif" alt="" /></td>
<td style="font-size: 12px;"><img style="border: 0px initial initial;" src="http://www.jasonconger.com/images/articleImages/BrandingICA/after.gif" alt="" /></td>
</tr>
<tr>
<td class="caption" style="font-size: 10px;" align="center">Before</td>
<td class="caption" style="font-size: 10px;" align="center">After</td>
</tr>
</tbody>
</table>
<div><span style="font-size: 12px; line-height: 18px;"><span style="color: red;">Disclaimer: This article is for informational purposes only. Be sure to reference your license agreement before implementing this in a production environment.</span></span></div>
<div><span style="font-size: 12px; line-height: 18px;"><span class="heading" style="font-size: 14px; font-weight: bold;">Tools Needed:</span></span></div>
<span style="font-size: 12px; line-height: 18px;">
<ul>
	<li>Citrix Presentation Server Client Packager</li>
	<li><a href="http://www.angusj.com/resourcehacker/" target="_blank">Resource Hacker (free)</a></li>
	<li>Graphics Editing Software (Microsoft Paint is sufficient)</li>
</ul>
<span class="heading" style="font-size: 14px; font-weight: bold;">Step 1: Export Existing Citrix MetaFrame Image</span>This step is performed to export the existing resource image so you can replace the image with a new one with identical dimensions.

Follow these steps to complete this task:
<ul>
	<li>Launch Resource Hacker and open statuiUI.dll. Note: statuiUI.dll is located in C:\Program Files\Citrix\ICA Client\resource\en for an English installation.</li>
	<li>Navigate to Bitmap -&gt; 101 -&gt; 1033 (Note: since I am using the English version of the client, 1033 is my locale ID. Your locale ID may differ)</li>
	<li>Right click 1033 and select “Save [Bitmap : 101 : 1033]…” Save this bitmap to any desired location</li>
</ul>
<img id="IMG1" style="border: 0px initial initial;" onclick="return IMG1_onclick()" src="http://www.jasonconger.com/images/articleImages/BrandingICA/export.gif" alt="" />  <span class="heading" style="font-size: 14px; font-weight: bold;"> </span>

Step 2: Modify the Exported Image

Using your preferred graphics editor, open up the bitmap exported in step 1.
Modify the image as desired and save as a different name if desired.

<img style="border: 0px initial initial;" src="http://www.jasonconger.com/images/articleImages/BrandingICA/replace1.gif" alt="" /> <img style="border: 0px initial initial;" src="http://www.jasonconger.com/images/articleImages/BrandingICA/replace2.gif" alt="" />

<span class="heading" style="font-size: 14px; font-weight: bold;">Step 3: Replace the Resource in statuiUI.dll</span>
<ul>
	<li>Make a backup of statuiUI.dll</li>
	<li>Launch Resource Hacker</li>
	<li>Navigate to Bitmap -&gt; 101 -&gt; 1033</li>
	<li>Right click 1033 and select “Replace Resource…”</li>
	<li>Click the button labeled “Open file with new bitmap…”</li>
	<li>Navigate to the bitmap created in step 2.</li>
	<li>Click the Replace button.</li>
	<li>Save the new statuiUI.dll file.</li>
</ul>
<img style="border: 0px initial initial;" src="http://www.jasonconger.com/images/articleImages/BrandingICA/replace3.gif" alt="" />
You will now have a branded client when launching applications. Go ahead and try it out.

<img style="border: 0px initial initial;" src="http://www.jasonconger.com/images/warning.gif" alt="" /> You will probably notice that about half way through the application launch process, the picture you created in this step reverts back to the original Citrix Metaframe bitmap if you are running Presentation Server 3.0 or above. Why does this happen? Read on.

Citrix introduced an improved user logon process in Presentation Server 3.0 and above that included a progress bar indicating connection status throughout the entire application launch process. Basically, when you launch a published application, the process starts on the client computer setting up the connection to the server. Then, the process gets handed over to the server to complete the application launch (logon to the server, load the profile, etc). Prior to Presentation Server 3.0, when the launch process got handed over to the server, the Windows logon dialog boxes were displayed. This created kind of a disjointed look and feel for the end user. In Presentation Server 3.0 and above, the Windows logon dialog boxes were “replaced” with new dialogs that look like the local client dialog. This gave the end user a smooth looking look and feel throughout the entire launch process.

So, how do you stop this seemingly regression from happening? Move on to step 4.

<span class="heading" style="font-size: 14px; font-weight: bold;">
Step 4: Replace statuiUI.dll on the Server.
</span>


The “replacement” dialog box for the server piece of the launch process is located at system_drive:\Program Files\Citrix\System32\resource\en\statuiUI.dll. Simply make a backup of this file and replace it with the statuiUI.dll file created in step 3.

Note: this file may be locked if other people are logged in to the server.

Now, try launching an application again and you will notice that the branding stays throughout the entire launch process.

Another file that is fun to play with is the login screen for the PN Agent. That resource is C:\Program Files\Citrix\ICA Client\resource\en\pnagenUI.dll. Have fun!

<img style="border: 0px initial initial;" src="http://www.jasonconger.com/images/articleImages/BrandingICA/pnaBefore.gif" alt="" /><img style="border: 0px initial initial;" src="http://www.jasonconger.com/images/articleImages/BrandingICA/pnaAfter.gif" alt="" />
