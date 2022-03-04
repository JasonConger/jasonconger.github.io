---
id: 13
title: 'Digging in to Citrix Configuration Logging: Exploring the Database'
date: 2009-09-03T07:57:00-05:00
author: jason
excerpt: 'This is the fifth part in a series on Citrix XenApp Configuration Logging.  This part will focus on the database schema, the information contained in the database, and how to decode certain parts of the data.'
layout: post
guid: /post/Digging-in-to-Citrix-Configuration-Logging-Exploring-the-Database.aspx
image: wp-content/uploads/2009/09/Citrix-XenApp.png
categories:
  - Citrix XenApp
tags:
  - Citrix
  - Configuration Logging
  - Database
  - SQL
  - XenApp
  - XML
---
This is the fifth part in the Citrix Configuration Logging Series. In <a href="http://www.jasonconger.com/post/Digging-in-to-Citrix-Configuration-Logging-Part-1.aspx">part 1</a>, we discussed what Citrix Configuration Logging was.  In <a href="http://www.jasonconger.com/post/Digging-in-to-Citrix-Configuration-Logging-Setting-up-the-Database.aspx">part 2</a>, we discussed how to prepare the database to log configuration changes. In <a href="http://www.jasonconger.com/post/Digging-in-to-Citrix-Configuration-Logging-Setting-up-the-Citrix-XenApp-farm-for-Configuration-Logging.aspx">part 3</a>, we discussed how to set up the Citrix XenApp farm for Configuration Logging, in <a href="http://www.jasonconger.com/post/Digging-in-to-Citrix-Configuration-Logging-Reporting.aspx">part 4</a>, we looked at the “out of the box” reporting tools. In this part, we will look at the back end database schema.
<h2>Schema on the Surface</h2>
Here is what the database schema looks like on the surface.

<a href="file:///C:/Users/Jason%20Conger/AppData/Local/Temp/WindowsLiveWriter1286139640/supfiles29671B56/ConfigLogSchema3.png" target="_blank"><img style="display: block; float: none; margin-left: auto; margin-right: auto; border: 0px;" title="ConfigLogSchema_thumb1" src="http://www.jasonconger.com/images/articleImages/ConfigLogSchema_thumb1.png" alt="ConfigLogSchema_thumb1" width="400" height="385" border="0" /></a>

Just 3 tables – looks pretty easy…  But, if you look at some of the data in those tables, things become less obvious.  Let’s break each table down:
<table class="stats" border="1">
<tbody>
<tr>
<td class="hed" colspan="2">CtxLog_AdminTask_LogEntry – Every change to the XenApp farms creates a new row here.</td>
</tr>
<tr>
<td>LogEntry_RecordID</td>
<td>Unique Identifier (primary key)</td>
</tr>
<tr>
<td>SiteId</td>
<td>I honestly don’t know why this is here.  It seems like it might be some kind of farm identifier, but you can only have one farm per database.</td>
</tr>
<tr>
<td>LogEvent</td>
<td>This holds events that happen on the log (database) as a whole.  This is a numeric value that corresponds to an enumeration.  Possible values are:
<ul>
	<li>0= None</li>
	<li>1= Created</li>
	<li>2= Cleared</li>
</ul>
</td>
</tr>
<tr>
<td>DateTime</td>
<td>Date/Time the change occurred.</td>
</tr>
<tr>
<td>LogonUserName</td>
<td>The user that made the change.</td>
</tr>
<tr>
<td>LogonUserId</td>
<td>The <acronym title="Security Identifier">SID</acronym> of the user that made the change.</td>
</tr>
<tr>
<td>LogonHostName</td>
<td>Hostname of server that joins the farm.</td>
</tr>
<tr>
<td>LogonHostId</td>
<td>SID of a server that joins the farm.</td>
</tr>
<tr>
<td>HostName</td>
<td>IMA server used to make the change – remember that every change has to go through IMA.</td>
</tr>
<tr>
<td>HostId</td>
<td>SID of the host HostName above.</td>
</tr>
<tr>
<td>Status</td>
<td>Status of the change.  This is a numeric value that corresponds to an enumeration.  Possible values are:
<ul>
	<li>0 = Success</li>
	<li>1 = Neither success nor failure</li>
	<li>2 = Failure</li>
</ul>
</td>
</tr>
</tbody>
</table>
<table class="stats" border="1">
<tbody>
<tr>
<td class="hed" colspan="2">CtxLog_AdminTask_Object – Object(s) changed.</td>
</tr>
<tr>
<td>Object_RecordID</td>
<td>Unique Identifier (primary key)</td>
</tr>
<tr>
<td>SiteId</td>
<td>Again – don’t know why this is here.</td>
</tr>
<tr>
<td>LogEntry_RecordID</td>
<td>Foreign key to CtxLog_AdminTask_LogEntry table.</td>
</tr>
<tr>
<td>SequenceID</td>
<td>Another one I’m not sure about.</td>
</tr>
<tr>
<td>AdminTaskType</td>
<td>Enumeration - type of task performed:
<ul>
	<li>0 = None</li>
	<li>1 = Created</li>
	<li>2 = Modified</li>
	<li>3 = Removed</li>
</ul>
</td>
</tr>
<tr>
<td>ObjectType</td>
<td>Enumeration:
<ul>
	<li>0 = Application</li>
	<li>1 = Application Isolation Environment (AIE)</li>
	<li>2 = AIE Application</li>
	<li>4 = Farm</li>
	<li>5 = File Type Association</li>
	<li>6 = Folder</li>
	<li>7 = Installation Manager Application</li>
	<li>8 = Printer</li>
	<li>9 = Server</li>
	<li>10 = Server Group</li>
	<li>11 = User</li>
	<li>12 = Policy</li>
	<li>13 = Monitoring Profile</li>
	<li>14 = Load Manager</li>
	<li>15 = Virtual IP Farm Range</li>
	<li>16 = Virtual IP Server Range</li>
	<li>17 = Print Driver</li>
	<li>18 = Database</li>
	<li>19 = Zone</li>
</ul>
</td>
</tr>
<tr>
<td>ObjectName</td>
<td>Name of the object changed.</td>
</tr>
<tr>
<td>ObjectUid</td>
<td>Internal object ID.  More specifically, this value comes from the object’s ID property in MFCOM.</td>
</tr>
<tr>
<td>PropertyList</td>
<td>XML field.  Holds before and after values.</td>
</tr>
<tr>
<td>AdminTaskFormatResID</td>
<td>ID of field in language specific resource file.</td>
</tr>
</tbody>
</table>
<table class="stats" border="1">
<tbody>
<tr>
<td class="hed" colspan="2">CtxLog_AdminTask_ReferenceList – Some objects reference other objects.  For instance, a published application can reference many server objects.  This table keeps track of changes to referenced objects.</td>
</tr>
<tr>
<td>ReferenceList_RecordID</td>
<td>Unique Identifier (primary key)</td>
</tr>
<tr>
<td>SiteId</td>
<td>-</td>
</tr>
<tr>
<td>Object_RecordID</td>
<td>Foreign key to CtxLog_AdminTask_Object table.</td>
</tr>
<tr>
<td>SequenceID</td>
<td>-</td>
</tr>
<tr>
<td>ObjectType</td>
<td>Same as parent table.</td>
</tr>
<tr>
<td>ObjectNamesOriginal</td>
<td>Tab delimited list of the names of the original referenced objects.</td>
</tr>
<tr>
<td>ObjectIdsOriginal</td>
<td>Tab delimited list of internal object IDs of the original referenced objects.</td>
</tr>
<tr>
<td>ObjectNamesAdded</td>
<td>Tab delimited list of the names of the added referenced objects.</td>
</tr>
<tr>
<td>ObjectIdsAdded</td>
<td>Tab delimited list of internal object IDs of the added referenced objects.</td>
</tr>
<tr>
<td>ObjectNamesRemoved</td>
<td>Tab delimited list of the names of the removed referenced objects.</td>
</tr>
<tr>
<td>FormatResId_Added</td>
<td>Resource IDs of added objects.</td>
</tr>
<tr>
<td>FormatResId_Removed</td>
<td>Resource IDs of removed objects.</td>
</tr>
</tbody>
</table>
&nbsp;
<h2>Identifying Changes</h2>
As stated above, the PropertyList field in the CtxLog_AdminTask_Object table is a XML field.  This field maps out the before and after values of each property of an object after a change.  Here is an excerpt of what a PropertyList field looks like:
<pre class="brush: xml;">&lt;?xml version="1.0"?&gt;
&lt;propertylist&gt;
  . . .
  &lt;property nameresid="290042"&gt;
    &lt;valuelist original="0"&gt;
      &lt;value&gt;
        &lt;valstr&gt;Notepad - test&lt;/valstr&gt;
      &lt;/value&gt;
    &lt;/valuelist&gt;
    &lt;valuelist original="1"&gt;
      &lt;value&gt;
        &lt;valstr&gt;Notepad&lt;/valstr&gt;
      &lt;/value&gt;
    &lt;/valuelist&gt;
    . . .</pre>
Notice that each property has a value where original=”0” or original=”1”.   If the two values are different, that is a change.  Original=”1” is the before value and original=”0” is the after value (that seems backwards to me).  So, from the excerpt above, we can see that “Notepad” was renamed to “Notepad – test”.
<h2>Resource IDs</h2>
Several of the fields have “ResID” somewhere in their name.  This is short for Resource ID.  The values in these fields are numeric and correspond to a language specific <a href="http://msdn.microsoft.com/en-us/library/aa380599(VS.85).aspx" target="_blank">Resource File</a>.  For instance, the nameresid in the excerpt above is 290042.  This maps to “Display Name” in the en-US resource file; however, 290042 maps to “Anzeigename” in the de-DE resource file.  The resource file(s) used to decode the numbers can be found on the computer running the AMC at:

%ProgramFiles%\Common Files\Citrix\Access Management Console – Report Center\Reports\ConfigurationLoggingReport

The English resources are located in ConfigurationLoggingReport.dll.  Other localized languages can be found in a subdirectory of the path given above.  For instance, the German language resources would be in:

&lt;above path&gt;\de\ConfigurationLoggingReport.resources.dll

This concludes our “behind the scenes” look at the database schema.  Now that we know exactly what information is stored in the database and how to decipher the data, we will look at how to do some custom reporting in the final post in this series.