---
id: 15
title: 'Digging in to Citrix Configuration Logging: Setting up the Citrix XenApp farm for Configuration Logging'
date: 2009-08-10T17:57:00-05:00
author: JasonConger
excerpt: 'This is the third part in a series on Citrix XenApp Configuration Logging.  This part will show you how to configure your Citrix XenApp farm for Configuration Logging, what all the settings mean, what happens when you configure your farm for logging, what happens when things go wrong, and more.'
layout: post
guid: /post/Digging-in-to-Citrix-Configuration-Logging-Setting-up-the-Citrix-XenApp-farm-for-Configuration-Logging.aspx
image: wp-content/uploads/2009/09/Citrix-XenApp.png
categories:
  - Citrix XenApp
tags:
  - Citrix
  - Configuration Logging
  - Database
  - SQL
  - XenApp
---
This is the third part in the Citrix Configuration Logging Series. In [part 1]({% post_url /2009/2009-07-12-digging-in-to-citrix-configuration-logging-part-1 %}), we discussed what Citrix Configuration Logging was. In [part 2]({% post_url /2009/2009-07-29-digging-in-to-citrix-configuration-logging-setting-up-the-database %}), we discussed how to prepare the database to log configuration changes. In this part, we will discuss how to set up the Citrix XenApp farm to use the database and what happens under the covers when we do this.

<h2>Configuring the Citrix XenApp Farm to use the Database</h2>
You use the Access Management Console to configure the XenApp farm for Configuration Logging. Configuration Logging is a farm setting, so once you open the Access Management Console, simply right-click your farm name and select “Properties”. Select “Configuration Logging” from the Farm-wide properties.

<a href="http://www.jasonconger.com/images/articleImages/ConfigLoggingFarm_1.png" target="_blank"><img style="display: block; float: none; margin-left: auto; margin-right: auto; border-width: 0px;" title="ConfigLoggingFarm" src="http://www.jasonconger.com/images/articleImages/ConfigLoggingFarm_thumb_1.png" border="0" alt="ConfigLoggingFarm" width="582" height="456" /></a>

Now, we need to point our farm to the [database we created before]({% post_url /2009/2009-07-29-digging-in-to-citrix-configuration-logging-setting-up-the-database %}). To do this, click the “Configure Database…” button to start the database configuration wizard.

<a href="http://www.jasonconger.com/images/articleImages/DBWizardStep1.png" target="_blank"><img style="display: block; float: none; margin-left: auto; margin-right: auto; border-width: 0px;" title="DBWizardStep1" src="http://www.jasonconger.com/images/articleImages/DBWizardStep1_thumb.png" border="0" alt="DBWizardStep1" width="573" height="480" /></a>

The screen shot above is pretty self-explanatory, but here are a couple of tips:
<ul>
	<li>Even though there is a drop down next to the “Server name” box, the discovery does not always work. I suggest just typing in the database server name or IP address.</li>
	<li>Be sure to specify server&#92;instance if you are not using the default database instance.</li>
	<li>If using Windows integrated security, type domain&#92;username in the “User name” field</li>
	<li>Keep in mind that the username and password is saved in the data store. So, be sure that the password does not expire, or remember to change this when the password does expire.</li>
	<li>Discovery does not work well with the database name on the next step either. Again, you will most likely have to type in the database name.</li>
</ul>
<a href="http://www.jasonconger.com/images/articleImages/DBWizardStep3.png" target="_blank"><img style="display: block; float: none; margin-left: auto; margin-right: auto; border-width: 0px;" title="DBWizardStep3" src="http://www.jasonconger.com/images/articleImages/DBWizardStep3_thumb.png" border="0" alt="DBWizardStep3" width="583" height="480" /></a>

The screen shot above shows a lot of settings, but there is not a lot of explanation of what these settings do. Remember, Configuration Logging is built on top of ADO.NET. In order to make sense of these settings, you can look at ADO.NET properties. So, here ya go:
<ul>
	<li><span style="text-decoration: underline;">Connection time-out (seconds)</span> – amount of time to wait for a command to execute. If a database write command cannot execute in 20 seconds, you’ve got a problem.</li>
	<li><span style="text-decoration: underline;">Packet size (bytes)</span> – the size of the network packet. 8192 is the default. This value can be anywhere from 512 to 32767.</li>
	<li><span style="text-decoration: underline;">Use encryption</span> – more on this in a minute…</li>
	<li><span style="text-decoration: underline;">Connection pooling enabled</span> – connection pooling is just like session sharing. Building up and tearing down database connections can be an expensive process. Connection pooling allows a connection to stay up for an amount of time before closing just in case another database request comes in. If another database request comes in before the time out, the request will use the same connection.</li>
	<li><span style="text-decoration: underline;">Minimum pool size</span> – specifies the minimum number of connections to maintain in a pool. If you set this number to 3, for example, ADO.NET would create 3 connections the first time you connect to the server. Zero is the ADO.NET default.</li>
	<li><span style="text-decoration: underline;">Maximum pool size</span> – maximum number of connections in a pool. 100 is the ADO.NET default.</li>
	<li><span style="text-decoration: underline;">Connection lifetime (seconds)</span> – specifies the maximum age of connections. If a connection has been open for more than this number of seconds when you call its Close() or Dispose() method, it will be destroyed rather than being returned to the pool. Zero is the ADO.NET default, which means that connections are kept in the pool regardless of age.</li>
	<li><span style="text-decoration: underline;">Connection reset</span> – specifies whether the database connection is reset when being removed from the pool. True is the ADO.NET default.</li>
	<li><span style="text-decoration: underline;">Enlist</span> – specifies whether to enlist this connection into a current transaction context of the creation thread. In other words, if this is set to true and the database server is doing some transactions, let the connection use the already generated transaction. True is the ADO.NET default.</li>
</ul>
Almost all of those defaults are just great. The only one you need to be careful about is the “Use encryption” option. This option is set to “Yes” by default. But, in order to use Configuration Logging encryption, you must be using IMA encryption. If you are not using IMA encryption, you cannot use Configuration Logging encryption. You will get this nasty undescriptive error when you test the connection if there is a mismatch:

<a href="http://www.jasonconger.com/images/articleImages/EncryptionError.png" target="_blank"><img style="display: block; float: none; margin-left: auto; margin-right: auto; border-width: 0px;" title="EncryptionError" src="http://www.jasonconger.com/images/articleImages/EncryptionError_thumb.png" border="0" alt="EncryptionError" width="406" height="255" /></a>

For information on how to setup IMA encryption, <a href="http://support.citrix.com/proddocs/index.jsp?topic=/xenapp5fp-w2k8/ps-install-create-farm-ima-encryption-v2.html" target="_blank">check out the Citrix XenApp documentation</a>.
<h2>Configuring the Citrix XenApp farm to Log Changes</h2>
Now that we have the farm configured to point to the database, we have some options on how to log changes. Remember this screen shot?

<a href="http://www.jasonconger.com/images/articleImages/ConfigLoggingFarm_1.png" target="_blank"><img style="display: block; float: none; margin-left: auto; margin-right: auto; border-width: 0px;" title="ConfigLoggingFarm" src="http://www.jasonconger.com/images/articleImages/ConfigLoggingFarm_thumb_1.png" alt="ConfigLoggingFarm" width="582" height="456" /></a>

This is pretty easy, there are only 3 checkboxes:
* <span style="text-decoration: underline;">Log administrative tasks to logging database</span> – this is what tells the IMA service to use the `CitrixLogServer.dll` hook to log changes explained in [part 1]({% post_url /2009/2009-07-12-digging-in-to-citrix-configuration-logging-part-1 %}).
* <span style="text-decoration: underline;">Allow changes to the farm when database is disconnected</span> – this is self explanatory.
* <span style="text-decoration: underline;">Require administrators to enter database credentials before clearing the log</span> - “the log” referred to in this option is all the data in the database. An administrator can clear the log by opening the AMC, right-clicking on the farm name - &gt; All Tasks –&gt; Clear configuration log.

If you do not allow changes to be made to your farm and your Configuration Logging database is offline, you will get the following error message when trying to make a change:

<a href="http://www.jasonconger.com/images/articleImages/error.png" target="_blank"><img style="display: block; float: none; margin-left: auto; margin-right: auto; border: 0px;" title="error" src="http://www.jasonconger.com/images/articleImages/error_thumb.png" border="0" alt="error" width="405" height="255" /></a>

Wow – that error message is actually pretty descriptive!

Note – even if you do not allow changes to be made to your Citrix XenApp farm when the Configuration Logging database cannot be reached, you can still change which database your farm uses. That means if you are trying to make a change and your database took a dive and it doesn’t look like it will be back up anytime soon, you can always change which database logs the changes and carry on. Of course, changing which database logs changes gets logged &lt;- say that 5 times fast...

<h2>Adjusting Database Permissions</h2>
As you may recall, [when we created the data base user in part 2]({% post_url /2009/2009-07-29-digging-in-to-citrix-configuration-logging-setting-up-the-database %}), we had to make sure the database user belonged to the <strong>db_owner</strong> role. This is due to the fact when the XenApp farm connects to the database, the schema is checked. If the schema does not exit, it is created – which requires db_owner rights. So, after that first connection, you can dial back the permissions. Here are the minimum operating permissions:
<table class="stats" border="0">
<tbody>
<tr>
<td class="hed" width="252">Configuration Logging Task</td>
<td class="hed">Database permissions needed</td>
</tr>
<tr>
<td width="252">To create log entries in the database tables</td>
<td><strong>INSERT</strong> for the database tables,
<strong>EXECUTE</strong> for the stored procedures, and
<strong>SELECT</strong> for sysobjects and sysusers (SQL Server) or sys.all_objects (Oracle)

(Oracle also requires <strong>SELECT</strong> for sequence objects and the create session system privilege)</td>
</tr>
<tr>
<td width="252">To clear the log</td>
<td><strong>DELETE/INSERT</strong> for the database tables,
<strong>EXECUTE</strong> for the GetFarmData stored procedure, and
<strong>SELECT</strong> for sysobjects and sysusers (SQL Server)
or sys.all_objects (Oracle) (Oracle also requires <strong>SELECT</strong> for sequence objects and the create session system privilege)</td>
</tr>
<tr>
<td width="252">To create a report</td>
<td><strong>EXECUTE</strong> for the Citrix Configuration Logging
stored procedures
<strong>SELECT</strong> for sysobjects and sysusers (SQL Server) or sys.all_objects (Oracle)
(Oracle also requires the create session system
privilege)</td>
</tr>
</tbody>
</table>

<h2>Delegated Administration</h2>
Delegated administration is supported to an extent. It is basically an on or off thing. It is a good idea to make sure administrators have to enter credentials to clear the log as well.

<a href="http://www.jasonconger.com/images/articleImages/delegatedadmin.png" target="_blank"><img style="display: block; float: none; margin-left: auto; margin-right: auto; border: 0px;" title="delegatedadmin" src="http://www.jasonconger.com/images/articleImages/delegatedadmin_thumb.png" border="0" alt="delegatedadmin" width="473" height="127" /></a>