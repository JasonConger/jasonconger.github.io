---
id: 1324
title: 'Citrix Workspace Services &#8211; Friend or Foe for the Citrix Service Providers (CSP)?'
date: 2014-05-14T08:21:00-05:00
author: jason
excerpt: 'At Citrix Synergy this year, the "one more thing" at the end of the keynote was a new offering called Citrix Workspace Services.  There was immediate debate on Twitter as to how this impacts certain market segments.  This article covers ways in which Citrix Workspace Services could help or hinder the Citrix Service Provider Market.'
layout: post
guid: http://www.jasonconger.com/?p=1324
image: wp-content/uploads/2014/05/question-thumb.png
categories:
  - Citrix
tags:
  - Azure
  - XenApp
  - XenDesktop
---
At Citrix Synergy this year, the "one more thing" at the end of the <a title="Citrix Synergy 2014 Live Blog" href="http://www.jasonconger.com/post/citrix-synergy-2014-live-blog/">keynote</a> was a new offering called <a title="Citrix Workspace Services" href="http://www.citrix.com/news/announcements/may-2014/workspace-services-announcement.html" target="_blank">Citrix Workspace Services</a>.  <a href="http://www.brianmadden.com/blogs/brianmadden/archive/2014/05/12/why-citrix-workspace-services-is-the-future-of-xenapp-and-xendesktop-and-why-it-s-awesome.aspx" target="_blank">Brian Madden wrote an article explaining what CWS is and isn't</a>, but I wanted to take a look at this from a Citrix Service Provider's perspective.
<h1>Where Citrix Workspace Services Fit</h1>
Automation and self-service are two major factors for CSPs.  Citrix Workspace Services potentially helps with both of these factors.  Since CWS isn't a real thing yet that we can get our hands on, I'm not quite sure to what extent we can automate things.  This is important because CSPs have to automate in order to keep costs down and still maintain enough margin to remain profitable.  Automation is also key because CSPs are not merely delivering just a remote desktop; they are delivering a suite of services, apps, data, backup, etc. and Citrix is a portion of the overall offering.  Self-service is also important for CSPs because people are expensive.  The more you can offload to the tenant via self-service (which relies on automation) the less man power you need.

&nbsp;
<h1>How Citrix Workspace Services Work</h1>
XenApp and XenDesktop environments need five basic things to work:
<ol>
	<li>Database</li>
	<li>License Server</li>
	<li>Controller(s)</li>
	<li>VDA(s)</li>
	<li>StoreFront</li>
</ol>
Citrix Workspace Services can move 4 out of 5 of those things to the cloud (Azure for now).  Basically, all you need is the workloads (VDAs) on your premises.  Then, you just point those VDAs to the provisioned Citrix Workspace Service instance in Azure and off you go.  Since a picture is worth a thousand words, here ya go:

<a href="http://www.jasonconger.com/wp-content/uploads/2014/05/Citrix-Workspace-Services.png"><img class="aligncenter size-full wp-image-1331" src="http://www.jasonconger.com/wp-content/uploads/2014/05/Citrix-Workspace-Services.png" alt="Citrix Workspace Services" width="932" height="590" /></a>

&nbsp;
<h1>Does this help or hurt the CSP?</h1>
So the question is, "is Citrix Workspace Services a slap in the face to CSPs"?  I personally believe CWS could be a huge help to CSPs.  When I was the Director of Technology for <a href="http://www.xcentric.com" target="_blank">Xcentric</a> (a CSP), I would have loved to have this.  There are less moving parts for me to manage and on-boarding new clients could potentially be sped up as there is less work for the CSP to do.  Keep in mind that a lot of my opinion hinges on the automation aspects of CWS (which is still unknown at the time of this writing).  There could be some inherent risk in potential down time, but a CSP tenant is already prepared for a risk like this by the shear nature that they signed up for a hosted service the CSP provides in the first place.

On the converse, stealing a line from <a href="https://twitter.com/shawnbass" target="_blank">@Shawn Bass</a>, CWS could potentially cause a CSP market saturation as CWS lowers the bar of entry.  You no longer need a significant capital expenditure to get started as a CSP.  I personally do not see this happening, but time will tell.

&nbsp;
<h1>What is lacking (potentially)?</h1>
The automation question is still up in the air.  I believe Citrix will make this a solution that can be automated with APIs, but how easily CSP can hook into whatever Citrix offers could potentially hinder the CSPs workflow.

Compliance (SAS, HIPPA, PCI, etc.).  In most cases, data is still kept with the CSP, but potential identifiable information could flow from CSP to Azure and back (although this is yet to be determined).  This could be a show stopper for certain markets.

Moving from Citrix Workspace Services to on premises.  Since CWS was built using Azure services like Azure App Services, Azure Active Directory and Azure Virtual Network, it would be nearly impossible to move from CWS back to on premises.  It's kind of like the Mob - once you're in you're in, and you're not getting out.

Reporting is yet to be seen, but I sure hope Citrix builds this in for SPLA-like reporting.  All CSPs have to report to at least Microsoft and Citrix on a monthly basis about usage and pay up as you go/grow.  I used to rely on home-grown tools to do this, but it would be better to have this from the vendor.

&nbsp;
<h1>Conclusion</h1>
So, I think CWS will be a major help to CSPs as long as there is a strong and extensible automation engine involved.  Could there be downtime that has nothing to do with the CSP-owned infrastructure?  Sure, but that is the nature of the business in the first place.  There are still lots of unknowns, but I'm hopeful as this just seems to make sense to me.

What do you think?

&nbsp;

&nbsp;