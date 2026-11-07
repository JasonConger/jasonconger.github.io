---
layout: post
title: "\"Hi, this is IT"
date: 2026-10-29
categories:
 - LinkedIn
tags:
 - "CiscoPartnerSummit"
 - "Splunk"
 - "Cisco"
 - "CyberSecurity"
 - "MFA"
author: JasonConger
linkedin-url: https://www.linkedin.com/feed/update/urn%3Ali%3AugcPost%3A7521360509061734400
excerpt: "\"Hi, this is IT. We noticed you're on a remote network. Just approve this request and we'll fix it.\" At Cisco Partner Summit, Gino Corleto, Industry Solutions Architect at Cisco, walked me through a demo of exactly that attack: a reused password phished in another breach, an MFA push the user approves, and a hacker..."
comments: false
featured: false
---
"Hi, this is IT. We noticed you're on a remote network. Just approve this request and we'll fix it."

At Cisco Partner Summit, Gino Corleto, Industry Solutions Architect at Cisco, walked me through a demo of exactly that attack: a reused password phished in another breach, an MFA push the user approves, and a hacker moving east-west until the production line goes down.

And how Cisco and Splunk stop it:

🔹 Duo Proximity Verification checks over Bluetooth that you're actually in front of the device you're logging in from. A hacker in South America can't fake being in Vancouver.
🔹 If someone does get in, firewalls, Secure Network Analytics and Cyber Vision send the anomaly (an HR user suddenly reaching for the production line) into Splunk.
🔹 Cloud Control pulls it together and recommends isolating the user, resetting the password and revoking the session, and it can run as an automated flow without a SOC operator.

Gino's point: it usually takes customers 8 to 14 days to find out they had a breach. This gets the fix down to minutes.

\#CiscoPartnerSummit #Splunk #Cisco #CyberSecurity #MFA

*Originally posted on LinkedIn: [view the original post](https://www.linkedin.com/feed/update/urn%3Ali%3AugcPost%3A7521360509061734400).*
