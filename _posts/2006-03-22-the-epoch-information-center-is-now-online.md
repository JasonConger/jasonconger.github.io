---
id: 50
title: The Epoch Information Center is now online
date: 2006-03-22T08:33:00-06:00
author: jason
excerpt: 'Use the Epoch Information Center to get epoch offsets from Date/Time values, or get Date/Time values from an epoch offset.  This information is useful for things like manipulating the Terminal Server shadow registry.'
layout: post
guid: /post/The-Epoch-Information-Center-is-now-online.aspx
permalink: /2006/03/22/the-epoch-information-center-is-now-online/
categories:
  - General
tags:
  - Epoch
  - Registry
  - Shadow Key
---
The what is now online? The <a href="https://www.epochconverter.com/">Epoch Information Center</a>. Okay, so what is an epoch and why should I care in a Terminal Server environment?

<span class="heading">What is an epoch?</span>
Epoch has many <a href="http://dictionary.reference.com/search?q=epoch" target="_blank" rel="noopener">definitions</a>. The definition we're interested in is the <a href="http://en.wikipedia.org/wiki/Unix_epoch" target="_blank" rel="noopener">UNIX definition</a>. The UNIX definition specifies that the epoch is January 1, 1970 at midnight (UTC) (a.k.a. 01-01-1970 00:00:00). This Date/Time value can be considered "Time 0". The epoch is used as a beacon to measure time in many computer programs (such as the Windows registry). Time can be measured as the number of seconds since the epoch or before the epoch (returning a positive or negative offset). This also allows you to compare Date/Time values.

<span class="heading">Why should I care about an epoch in a Terminal Server environment?</span>
There is one main reason you should care about the epoch offset in a Terminal Server environment. That reason is the shadow registry (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Terminal Server\Install\Software). <a href="http://www.brianmadden.com" target="_blank" rel="noopener">Brian Madden</a> has written an <a href="http://www.brianmadden.com/content/content.asp?id=224" target="_blank" rel="noopener">excellent article</a> on the shadow registry key and how it's used. I've used his article and the <a href="https://www.epochconverter.com/">Epoch Information Center</a> to manipulate the shadow registry's "LatestRegistryKey" value in a couple of scenarios.

<span class="heading">Usage Scenarios</span>

<span class="heading">Scenario 1 (setting the LatestRegistryKey back in time):</span>
The first usage scenario is addressed in <a href="http://www.brianmadden.com/content/content.asp?id=224" target="_blank" rel="noopener">Brian Madden's article</a>. This scenario involves setting the "LatestRegistryKey" value back in time.
<div style="border: 1px solid #000; padding: 5px; background-color: #ececec; font-family: Arial, Sans-Serif;">

Quote from <a href="http://www.brianmadden.com/content/content.asp?id=224" target="_blank" rel="noopener">Brian Madden's article</a>:

. . . Imagine that you have multiple Terminal Servers or Citrix servers that are all running the same application, such as Microsoft Office. If you're like most companies, you probably installed Office on those servers a several months or even years ago. Since Office was originally installed via a user session operating in install mode, the server's shadow key was created and timestamped with the original install time. Any users who did not have the appropriate Office settings in their own personal HKCU key received them when they logged on to the server for the first time.

Now, fast forward to today. What happens if you want to add more capacity to your server farm? Most likely you’d build a few more servers, install Office on them, and load-balance them with your existing servers.

Can you see the problem here? The timestamp on the shadow key area of the new Terminal Servers will be current, and in fact much newer than each user’s individual HKCU last update timestamp. Therefore, upon logging on to one of the new servers, userinit.exe will start comparing the key-by-key timestamps of all the HCKU\Software keys to the server’s shadow area software keys. Since the server just got a fresh install of Microsoft Office, those timestamps will be much newer than any of the user’s personalized settings in their own HKCU. The result? Mass deletion of all the Microsoft Office-specific keys in the user’s HKCU\Software hive.

From the user's standpoint, it will appear as if all of their Office settings reverted back to the defaults, all because they were randomly load-balanced to a new Terminal Server. . .

</div>
Brian suggests a couple of solutions to address this exact problem. Another solution you could use is go to the Epoch Information Center, grab an epoch offset earlier than the other existing servers in the farm, and plug that offset in to the "LatestRegistryKey" value.  See below:

<img src="http://www.jasonconger.com/images/articleImages/EpochInformationCenter/LatestRegistryKey.gif" alt="" />
Note: be sure to select decimal when inserting the new value.

<span class="heading">Scenario 2 (setting the LatestRegistryKey to the current time):</span>
Imagine that you wanted to add a registry key to each user's HKEY_CURRENT_USER\Software registry hive. You could write a logon script to do it, or you could add the registry keys to the shadow registry, use the Epoch Information Center to get the current (or future) epoch offset, and plug the epoch offset into the "LatestRegistryKey" (thus emulating the server install mode). The advantage of doing it without a login script is that you don't have to come up with some logic in your script to figure out if this setting has already been applied, Windows takes care of that part for you.

Anyway, I hope you find the Epoch Information Center useful. The reason I put it online is because I've needed to get an epoch offset in the past and I thought some of you might find it useful as well.