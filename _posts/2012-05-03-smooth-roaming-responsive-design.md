---
id: 998
title: Smooth Roaming + Responsive Design
date: 2012-05-03T08:05:04-05:00
author: jason
excerpt: 'In this post, we look at adding session reconnection event handling to our responsive design prototype using the Citrix XenApp Mobile Application SDK.  <a href="http://www.jasonconger.com/enterprise-application-responsive-design-prototype">Be sure to check out the video of the prototype</a>.'
layout: post
guid: http://www.jasonconger.com/?p=998
image: wp-content/uploads/2012/04/Responsive-Design-Icon.png
categories:
  - Citrix XenApp
tags:
  - 'C#'
  - mobility
  - Responsive Design
  - XAMP
  - XenApp
---
In a previous article, we looked at using <a title="Responsive Design for Enterprise Applications" href="http://www.jasonconger.com/post/responsive-design-for-enterprise-applications/">responsive design with enterprise applications</a> by utilizing the <a href="http://www.jasonconger.com/post/installing-and-using-the-citrix-xenapp-6-5-mobile-application-sdk/">Citrix XenApp Mobile Application SDK</a>. Jonathan Chin left an interesting comment about hooking up an event handler to apply the responsive design to a reconnection event.  So, I decided to investigate doing just that and, as it turns out, it isn't that hard.  

In the previous version, the responsive design code only kicked in on session initiation (i.e. logon) - meaning if you started a session on a fat client and then reconnected to the session on a mobile device, then the fat client display would show up on the mobile device.  We don't want that.  So, by catching the reconnection event, we can re-style the app at any point (session initiation or reconnection).  Start the application on a fat client and then reconnect via a mobile device and the mobile style will kick in (and vice versa).

Here's the bit of code to take care of it (if you don't care about the code and just want to skip to the download, just <a title="Responsive Design Prototype" href="http://www.jasonconger.com/enterprise-application-responsive-design-prototype">follow this link</a>):

&nbsp;

<pre class="brush: csharp">
[DllImport("WtsApi32.dll")]
private static extern bool WTSRegisterSessionNotification(IntPtr hWnd, [MarshalAs(UnmanagedType.U4)]int dwFlags);

[DllImport("WtsApi32.dll")]
private static extern bool WTSUnRegisterSessionNotification(IntPtr hWnd);

private const int NOTIFY_FOR_THIS_SESSION = 0;
private const int WM_WTSSESSION_CHANGE = 0x2b1;
private const int WTS_REMOTE_CONNECT = 0x3;
private const int WTS_REMOTE_DISCONNECT = 0x4;
private bool registered = false;

protected override void OnHandleDestroyed(EventArgs e)
{
    // unregister the handle before it gets destroyed
    if(registered)
        WTSUnRegisterSessionNotification(this.Handle);

    base.OnHandleDestroyed(e);
}

protected override void OnHandleCreated(EventArgs e)
{
    base.OnHandleCreated(e);
    registered = WTSRegisterSessionNotification(Handle, NOTIFY_FOR_THIS_SESSION);
}

protected override void WndProc(ref Message m)
{
    if (m.Msg == WM_WTSSESSION_CHANGE)
    {
        if (m.WParam.ToInt32() == WTS_REMOTE_CONNECT)
        {
            // The session is in the reconnect state, so style the app for the new session
            setAppStyle();
        }

        if (m.WParam.ToInt32() == WTS_REMOTE_DISCONNECT)
        {
            // The session is in the disconnect state, so close the CMP if it is open
            if (this.cmp != null && this.cmp.IsChannelOpen())
            {
                try
                {
                    this.cmp.CloseChannel();
                }
                catch {}
            }
        }
    }
    base.WndProc(ref m);
}
</pre>

&nbsp;
<h2>Try It Out Yourself</h2>
Want to try it out yourself?  I have made the program and the source available so you can beat it up and come up with some more ideas.  You can <a title="Responsive Design Prototype" href="http://www.jasonconger.com/enterprise-application-responsive-design-prototype">download it here</a>.

&nbsp;