---
id: 12
title: Is a User Installed Application Layer Necessary for VDI?
date: 2009-11-22T22:54:37-06:00
author: JasonConger
excerpt: 'Layering is an emerging concept for VDI.  In this article, I will draw some parallels with VDI layering and Service Oriented Architecture (SOA) to look at ways of solving the difficult User Installed Applications layer.'
layout: post
guid: /post/Is-a-User-Installed-Application-Layer-Necessary-for-VDI.aspx
image: wp-content/uploads/2009/11/VDI.png
categories:
  - VDI
tags:
  - SOA
  - VDI
---
Layering is an emerging concept for VDI.&nbsp; I am not going to try to explain layering in this post, rather I am going to discuss one aspect of layering – the user installed applications layer.&nbsp; For more information about what layering is, how it is done, and how it fits into VDI, check out <a href="http://www.brianmadden.com/blogs/gabeknuth/archive/2009/10/21/what-is-Layering-and-why-does-it-matter.aspx" target="_blank">Gabe Knuth’s article</a>.
<h2>Service Oriented Architecture</h2>
Layering is a new take on an old concept in my mind.&nbsp; I see layering as an implementation of SOA for desktops.&nbsp; A key concept of SOA is loose coupling.&nbsp; Loose coupling involves a consumer and a service.&nbsp; The consumer doesn’t need to know how a service is implemented.&nbsp; All the consumer needs to know is how to interface with the service.&nbsp; The consumer asks the service to do something and the service does it (and possibly returns something to the consumer).

Here is a real life example to illustrate: When I stay at a hotel, I usually call the front desk to schedule a wake up call.&nbsp; The front desk takes my information and calls me when I ask.&nbsp; In this example, I am the consumer and the wake up call is the service.&nbsp; I do not necessarily know how the front desk implements the wake up call – they can put the time in a computer to have an automated system call me, or maybe they write it on a call log and a human actually calls me.&nbsp; The point is, I don’t know (or care) how the service is implemented.

Another aspect of loose coupling is that the services are interchangeable.&nbsp; So, in the example above, if the hotel is using some manual method and decides to use an automated method, that is fine.&nbsp; The service still gets implemented for the consumer because the consumer interface did not change.
<h2>Layering</h2>
So, if each layer is viewed as a service (and potential consumer), then the gaps between the layers are the interfaces.&nbsp; Also, if each layer is a service, then each service should be interchangeable.&nbsp; This example works pretty well for things like the hypervisor layer (swapping in and out VMware/XenServer/Hyper-V), but maybe not so well for applications, since applications may have dependencies on one or more layers.&nbsp; Application virtualization can overcome this by packing the entire stack necessary for an application in a bubble, but do you really want to teach users the intricacies of sequencing (or profiling) applications to solve a user installed app layer?

<a href="http://www.jasonconger.com/images/articleImages/VDI%20Layers_3.png" target="_blank"><img style="display: block; float: none; margin-left: auto; margin-right: auto; border: 0px;" title="VDI Layers" src="http://www.jasonconger.com/images/articleImages/VDI%20Layers_thumb_3.png" border="0" alt="VDI Layers" width="240" height="173" /></a>
<h2>Reverse Seamless</h2>
So, this got me to thinking, is reverse seamless an answer for a user installed application layer?&nbsp; If you rely on your local desktop for user installed applications and present these applications seamlessly in a remote desktop, will that suffice?&nbsp; Maybe – maybe not.&nbsp; If the user installed applications want to interact with remote applications, you have a problem.&nbsp; If not, then yeah, maybe reverse seamless does solve this.
<h2>VDI/XenApp Double Hop</h2>
A side effect of reverse seamless is that it also solves VDI “double hop” issues when using XenApp published applications inside a VDI desktop. For example, if you allow client drive mapping from the local desktop to the VDI desktop, and you also allow client drive mapping from the VDI desktop to the published application, then end user will quickly become confused as to which drive is which when trying to save a file from the published application.&nbsp; Think about printing and USB redirection also.

<a href="http://www.jasonconger.com/images/articleImages/Double%20Hop_1.png" target="_blank"><img style="display: block; float: none; margin-left: auto; margin-right: auto; border: 0px;" title="Double Hop" src="http://www.jasonconger.com/images/articleImages/Double%20Hop_thumb_1.png" border="0" alt="Double Hop" width="450" height="246" /></a>

By using reverse seamless, both the VDI connection and the published application connection can be made from the local desktop, then “merged” seamlessly.&nbsp; This way, the VDI desktop is making one hop and the published application is making one hop.&nbsp; You still have a problem if the published applications needs to interact with the desktop applications.

<a href="http://www.jasonconger.com/images/articleImages/Single%20Hop%20with%20Reverse%20Seamless.png" target="_blank"><img style="display: block; float: none; margin-left: auto; margin-right: auto; border: 0px;" title="Single Hop with Reverse Seamless" src="http://www.jasonconger.com/images/articleImages/Single%20Hop%20with%20Reverse%20Seamless_thumb.png" border="0" alt="Single Hop with Reverse Seamless" width="450" height="333" /></a>
<h2>Type 1 client hypervisor</h2>
Will a type 1 hypervisor help with user installed applications? I think this has the most potential.&nbsp; Running a “personal” VM and “business” VM on the same physical hardware, there are all types of interaction that can happen.&nbsp; If users install applications on the personal VM, reverse seamless type technology could be used to integrate this layer in a more cohesive way.

I guess the bottom line is that user installed applications in a stateless layered model is going to be hard.