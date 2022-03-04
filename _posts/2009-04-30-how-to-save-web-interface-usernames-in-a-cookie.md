---
id: 19
title: How to Save Web Interface Usernames in a Cookie
date: 2009-04-30T16:31:00-05:00
author: jason
excerpt: 'In the article titled “How to Enable AutoComplete for Web Interface Logon”, I explained how to enable the AutoComplete functionality of web browsers in order to save usernames and/or passwords for Citrix Web Interface.  As the article explained, there are a lot of moving parts to the solution such as web browser settings, Protected Storage, JavaScript workarounds, etc.  In this article, I will explain how to accomplish something similar by using cookies to remember the last username entered for Web Interface.'
layout: post
guid: /post/How-to-Save-Web-Interface-Usernames-in-a-Cookie.aspx
image: wp-content/uploads/2009/04/Web-Interface.png
categories:
  - Web Interface
tags:
  - 'C#'
  - Customization
  - Download
  - HTML
  - Web Interface
---
In the article titled “<a href="http://www.jasonconger.com/post/How-to-Enable-AutoComplete-for-Web-Interface-Logon.aspx">How to Enable AutoComplete for Web Interface Logon</a>”, I explained how to enable the AutoComplete functionality of web browsers in order to save usernames and/or passwords for Citrix Web Interface. As the article explained, there are a lot of moving parts to the solution such as web browser settings, Protected Storage, JavaScript workarounds, etc. In this article, I will explain how to accomplish something similar by using cookies to remember the last username entered for Web Interface.

<strong>How it Works </strong>(if you do not really care how it works, you can just download the modification at the end of this post)

There are really only two parts to this solution. Part 1 – store the username in a cookie. Part 2 – get the username from the cookie and populate the “user name” field at logon. There is a little Web Interface <acronym title="Software Development Kit">SDK</acronym> work to obtain the username, but I will explain what is going on.

&nbsp;

<strong>Part 1 – Storing the Username in a Cookie</strong>

There are two steps to accomplish this part.

First, we need to get the username after it is validated by Web Interface. An ideal place to get the authenticated username is applistView.ascx. applistView.ascx is the user control in Web Interface that is responsible for displaying a list of applications a user has access to. So, we know if we got to applistView.ascx in the Web Interface logon/application enumeration process that a username should be available.

Second, we need to store the username in a cookie (this is pretty easy in comparison to getting the username).

Here is the code:

Modify <em>applistView.ascx</em>

Find the following text (around line 10):

&lt;!--#include file="../serverscripts/include.aspxf"--&gt;

Paste the following right after this line
<pre class="brush: c-sharp;">
<%

//----------------------------------------------------------------
// WI mod
//----------------------------------------------------------------

string username = String.Empty;

// Get username
com.citrix.authentication.tokens.AccessToken accessToken = com.citrix.wi.pageutils.Authentication.authGetPrimaryAccessToken(wiContext.getWebAbstraction());
if(accessToken != null)
{
if(accessToken is com.citrix.authentication.tokens.GuestToken)
{
// Guest
username = wiContext.getString("Guest");
}
else
{
username = accessToken.getUserIdentity();
}
}

HttpCookie userCookie = Request.Cookies.Get("WI_username");

if(userCookie == null)
{
// Cookie doesn't exist, so create it
userCookie = new HttpCookie("WI_username");
}
else if(userCookie.Value != username)
{
// Need to update the cookie value
Response.Cookies.Set(Request.Cookies.Get("WI_username"));
}

userCookie.Value = username;
userCookie.Expires = DateTime.Now.AddDays(100);
Response.Cookies.Add(userCookie);

//----------------------------------------------------------------
// End WI mod
//----------------------------------------------------------------

%>
</pre>
Code explanation:

First, we need to get an AccessToken (see line 10 above). In the Web Interface object model, an AccessToken “…encapsulates information that may be used for authorization and authentication when a Subject requires access to a resource.” What that means in layman's terms is an AcessToken basically holds your username, password, domain, identity, etc. (you can actually use the PasswordBasedToken Interface to get the password of a user if you wanted to as described in <a href="http://www.jasonconger.com/post/How-to-get-the-Username-AND-Password-of-a-user-in-Citrix-Web-Interface-40.aspx">this article</a>).

After we get the AccessToken, we can test to see if this is an anonymous user or not (an anonymous user would have a GuestToken) on lines 12-23 above. If the token is not a GuestToken, then we know we have an authenticated user. There are currently 3 methods you can use to get the user details from the AccessToken:
<ol>
	<li>getAccountIdentity() – gets an AccountIdentiy object.</li>
	<li>getShortUserName() – returns the username as a string. Example – if your user identity was domain&#92;jasonco, getShortUserName() returns "jasonco".</li>
	<li>getUserIdentity() – returns the entire logon identity as a string. Example: <em>domain&#92;username</em> or <em>user@domain</em> (if using UPN). I chose getUserIdentity() in the code above.</li>
</ol>
The rest of the code is pretty straight forward – it just creates or updates the cookie named WI_username. You could actually name this cookie anything you wanted.

<strong>Part 2 – Retrieving/Populating the Username from the Cookie</strong>

This part is quite a bit easier than the first part. All we need to do is to get the cookie, if any, from the previous code and populate the username field on the log on screen. The logon screen code can be found in loginMainForm.inc.

Here is the code:

Modify <em>loginMainForm.inc</em>

Find the following text (around line 106):
<pre class="brush: xml">&lt;td colspan="2"&gt;
    &lt;input type='text' name='&lt;%=Constants.ID_USER%&gt;' id='&lt;%=Constants.ID_USER%&gt;'
        class='loginEntries&lt;%=viewControl.getExplicitDisabled()?" loginEntriesDisabled":""%&gt;'
        maxlength='&lt;%=Constants.LOGIN_ENTRY_MAX_LENGTH%&gt;' &lt;%=viewControl.getExplicitDisabledStr()%&gt;
        tabindex='&lt;%=Constants.TAB_INDEX_FORM%&gt;'</pre>
Paste the following right after this text:
<pre class="brush: c-sharp">&lt;%
//----------------------------------------------------------------
//       WI mod
//----------------------------------------------------------------

HttpCookie userCookie = Request.Cookies.Get("WI_username");

if(userCookie != null)
{
%&gt;
    value='&lt;%=userCookie.Value %&gt;'
&lt;%

}

//----------------------------------------------------------------
//       End WI mod
//----------------------------------------------------------------
%&gt;</pre>
Code explanation:

The &lt;input… tag above is the field where you fill in your username in loginMainForm.inc. The code inserted above sets the value of the input tag to whatever was stored in the WI_username cookie (if there was anything stored in the cookie at all).

If you want to implement this in your environment and do not feel like copying and pasting all this code, you can download the modified files below:

<img src="/assets/images/zip_small.gif" alt="download" align="absBottom" /> <a href="http://www.jasonconger.com/downloads/2009/5/WI51_Cookie_Mod.zip">Modification for Web Interface 5.1</a>