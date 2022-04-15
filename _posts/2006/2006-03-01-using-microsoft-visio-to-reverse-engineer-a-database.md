---
id: 54
title: Using Microsoft Visio to Reverse Engineer a Database
date: 2006-03-01T08:07:00-06:00
author: JasonConger
excerpt: This article steps you through using Microsoft Visio’s Reverse Engineer feature to reverse engineer relational databases like Citrix’s Resource Manager Summary Database.
layout: post
guid: /post/Using-Microsoft-Visio-to-Reverse-Engineer-a-Database.aspx
categories:
  - Citrix XenApp
  - Resouce Manager
tags:
  - Database
  - Resource Manager
---
There are times when you want to get a graphical representation of a relational database (say, for instance, the Citrix Resource Manager Summary Database). You could wade through a DBMS management console (such as the Microsoft’s Enterprise Manager for SQL) to get a list of all the tables and primary key/foreign key relationships, then draw out these tables in some kind of graphics software. Or, you could use Microsoft Visio to do all this work for you. All you need is an ODBC connection and Microsoft Visio Professional.
<ul>
	<li>Open Microsoft Visio Professional and create a new Database Model Diagram.</li>
	<li>Click on the Database menu and select Reverse Engineer to start the Reverse Engineer Wizard.</li>
	<li>Select an existing data source (DSN) or create a new one.</li>
<img style="border: 0px initial initial;" src="http://www.jasonconger.com/images/articleImages/VisioReverseEngineer/REWiz.gif" alt="" />
	<li>Select the information you want to add to the drawing. (I chose just the tables, primary keys, and foreign keys in this example).</li>
<img style="border: 0px initial initial;" src="http://www.jasonconger.com/images/articleImages/VisioReverseEngineer/REWiz2.gif" alt="" />
	<li>Select the checkboxes for the tables (and views, if any) that you want to graph.</li>
	<li>Select whether you want Visio to add the shapes to the drawing. If you don’t let the wizard add the shapes to the page now, you will be able to drag and drop the shapes onto the drawing after the wizard finishes extracting the information.</li>
	<li>Review the selections made and click Finish.</li>
<img style="border: 0px initial initial;" src="http://www.jasonconger.com/images/articleImages/VisioReverseEngineer/REWiz3.gif" alt="" /></ul>
I used the steps in the example demonstrated above to extract the Citrix Resource Manager Summary Database schema. As you can see from the screen shot below, Visio did a great job of extracting the information, but you’ll have to do quite a bit of moving shapes around to get a better picture of the relationships. Fortunately, I’ve already done this for you, and you can download the drawing in the Downloads section <a href="http://www.jasonconger.com/Visio-Diagram-of-the-Citrix-Resource-Manager-Summary-Database.aspx">here</a>. 

<a href="http://www.jasonconger.com/images/articleImages/VisioReverseEngineer/RMDB-large.gif" target="_blank"><img style="border: 0px initial initial;" src="http://www.jasonconger.com/images/articleImages/VisioReverseEngineer/RMDB-small.gif" alt="Click for a larger version" /></a>
(Click for a larger version) 

One last really cool thing. You can also use Visio’s database features to generate databases from a drawing as well as update databases from a drawing. I often reverse engineer a database, make changes to the drawing, and let Visio make the changes to the database for me. That way my documentation and database structure stay in synch.