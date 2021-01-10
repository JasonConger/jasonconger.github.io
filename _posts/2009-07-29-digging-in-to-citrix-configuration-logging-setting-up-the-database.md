---
id: 16
title: 'Digging in to Citrix Configuration Logging: Setting up the Database'
date: 2009-07-29T18:10:00-05:00
author: jason
excerpt: 'This is the second part in a series on Citrix XenApp Configuration Logging.  When Citrix XenApp Configuration Logging is enabled, all changes are written to a back end database.  In this part, we will look at the details of how to create the database, logins, and users.'
layout: post
guid: /post/Digging-in-to-Citrix-Configuration-Logging-Setting-up-the-Database.aspx
permalink: /2009/07/29/digging-in-to-citrix-configuration-logging-setting-up-the-database/
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
In <a href="http://www.jasonconger.com/post/Digging-in-to-Citrix-Configuration-Logging-Part-1.aspx">part 1 of the Digging in to Citrix Configuration Logging</a> series, we looked at what XenApp configuration logging was and how it worked.&nbsp; Now, we are going to focus on how to set up the Citrix XenApp configuration logging database.

All Citrix XenApp farm changes are written to a back end database. The back end database can be:
<ul>
	<li>Microsoft SQL 2000 and above (Microsoft SQL Express works too)</li>
	<li>Oracle 9.2 or 10.2&nbsp;</li>
</ul>
We will be using Microsoft SQL Server 2005 for this example.
<h2>Creating the Database</h2>
The first step in setting up the back end database for configuration logging is to create the database and user account(s).&nbsp; This is pretty easy.&nbsp; Just open up Microsoft SQL Server Management Studio, right-click Databases, and select New Database…&nbsp; Give the database a name and accept the defaults.

<img title="New Database" src="http://www.jasonconger.com/images/articleImages/newdatabase.png" alt="New Database" width="332" height="226" />
<h2>Creating the Database Login(s)</h2>
The next step is to set up the database authentication.&nbsp; In SQL Server Management Studio, expand Security, right-click Logins, and select New Login…

<a href="http://www.jasonconger.com/images/articleImages/NewSQLLogin.png" target="_blank"><img style="display: inline; border-width: 0px;" title="NewSQLLogin" src="http://www.jasonconger.com/images/articleImages/NewSQLLogin_thumb.png" border="0" alt="NewSQLLogin" width="535" height="480" /></a>

Citrix XenApp Configuration Logging supports both SQL Server authentication and Windows authentication.

If using SQL Server authentication, you can make up any login name and password you want.&nbsp; Keep in mind though that Citrix Configuration Logging <span style="text-decoration: underline;">does not</span> support blank passwords.

If using Windows authentication, you can type a user name or group name in the form of <em>domain</em>\<em>username</em> or <em>domain</em>\<em>group </em>in the Login name field.&nbsp; You can also select the “Search…” button to browse Active Directory for users or groups.
<p style="background: #ececec; height: 131px; border: #000 1px dashed; padding: 5px;"><a href="http://www.jasonconger.com/images/articleImages/SQLSelectObject.png"><img style="float: right; border-width: 0px;" title="SQLSelectObject" src="http://www.jasonconger.com/images/articleImages/SQLSelectObject_thumb.png" border="0" alt="SQLSelectObject" width="240" height="131" /></a> Tip: by default, only objects of type “User or Built-in security principal” are searched when using the “Search…” button.&nbsp; You will need to add Groups to the search by clicking the “Object Types…” button.</p>
In either case (using Windows or SQL Server authentication), be sure to change the Default database to the database created earlier.
<h2>Mapping the Login to a Database User</h2>
Even though you have created a database and a login, the two entities are not yet linked.&nbsp; In other words, the login you created cannot log on to the database.&nbsp; That is because a login is not equal to a database user.&nbsp; The next step in the process is to map the created login to a database user and assign appropriate rights.&nbsp;

In Microsoft SQL Server Management Studio, expand the Databases node, expand the database you created above, expand the Security node, right-click Users, and select New User…

<a href="http://www.jasonconger.com/images/articleImages/newDBUser.png"><img style="display: inline; border-width: 0px;" title="newDBUser" src="http://www.jasonconger.com/images/articleImages/newDBUser_thumb.png" border="0" alt="newDBUser" width="257" height="244" /></a> <a href="http://www.jasonconger.com/images/articleImages/newUser_1.png"></a>

<img style="display: inline; border: 0px;" title="newUser" src="http://www.jasonconger.com/images/articleImages/newUser_thumb_1.png" border="0" alt="newUser" width="535" height="480" />

Type a name in the Username field and type (or select) the login you created earlier in the Login name field.&nbsp; The name you type in the User name field does not have to match the name in the Login name field, but I usually keep them the same for simplicity.

You will also have to tick the <strong>db_owner</strong> box under the Role Members section for now.&nbsp; This is because the first time the Citrix XenApp farm tries to connect to the Configuration Logging database, the database schema will get created.&nbsp; After the schema gets created, you can dial back the permissions.&nbsp; I’ll explain the minimum permissions necessary in the next article.