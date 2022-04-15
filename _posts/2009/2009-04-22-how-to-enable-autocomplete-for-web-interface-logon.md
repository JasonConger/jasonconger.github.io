---
id: 20
title: How to Enable AutoComplete for Web Interface Logon
date: 2009-04-22T20:23:00-05:00
author: JasonConger
excerpt: 'The logon page for Citrix Web Interface explicitly disables the web browser functionality of saving form data.  But, what if you want to let your users save their username (especially if they have a particularly long UPN)?  This article will show you how to re-enable this functionality for both Web Interface 4.x and 5.x.'
layout: post
guid: /post/How-to-Enable-AutoComplete-for-Web-Interface-Logon.aspx
image: wp-content/uploads/2009/04/Web-Interface.png
categories:
  - Web Interface
tags:
  - Citrix
  - Web Interface
---
The logon page for Citrix Web Interface explicitly disables the web browser functionality of saving form data. But, what if you want to let your users save their username (especially if they have a particularly long UPN)? This article will show you how to enable AutoComplete functionality for both Web Interface 4.x and 5.x.

{: .box-warning}
Disclaimer – I would highly recommend only implementing this solution in a secure internal environment. You do not want your usernames or passwords floating around out there in the public.

<a href="http://www.jasonconger.com/images/articleImages/WI-AutoComplete.gif"><img style="display: inline; border-width: 0px;" title="Citrix Web Interface AutoComplete" src="http://www.jasonconger.com/images/articleImages/WI-AutoComplete_thumb.gif" border="0" alt="Citrix Web Interface AutoComplete" width="471" height="214" /></a>

## How Web Interface disables AutoComplete

Web Interface hasn’t always disabled the AutoComplete functionality of web browsers.  I actually think it is wise Citrix did start disabling AutoComplete by default because a lot of Web Interface sites are external-facing and AutoComplete can be a bad thing in an external scenario. The way Web Interface disables AutoComplete is by adding a property to the <code>&lt;form&gt;</code> tag in the HTML.  Simply adding autocomplete=”off” will disable AutoComplete for all <code>&lt;input&gt;</code> elements within the <code>&lt;form&gt;</code>. If you look at the rendered WI login page’s HTML, you will see <code>&lt;form… autocomplete=”off”&gt;</code>.


## Enabling AutoComplete for Web Interface 4.x

Enabling AutoComplete for Web Interface 4.x is actually quite simple.  All you really need to do is get rid of the autocomplete=”off” property in the <code>&lt;form&gt;</code> tag.  To do this:

Modify loginView.ascx

Change this:  <code>&lt;form method="POST" action="&lt;%=PAGE_LOGIN%&gt;" name="NFuseForm" autocomplete=”off”&gt; </code>

To this:  <code>&lt;form method="POST" action="&lt;%=PAGE_LOGIN%&gt;" name="NFuseForm"&gt; </code>

A possible downside to this is that passwords will be saved as well.  If you do not want passwords to be saved, you can tell just the password field to disable AutoComplete.  To do this:

Modify loginMainForm.inc

Change this: <code>&lt;input type='password'… </code>

To this: <code>&lt;input autocomplete="off" type='password'… </code>


## Enabling AutoComplete for Web Interface 5.x
Enabling AutoComplete for web Interface 5.x is the same as enabling AutoComplete in Web Interface 4.x with one exception.  Web Interface 5.x does not use a <code>&lt;input type=”submit” /&gt;</code> button to submit form data.  Instead, Web Interface 5.x uses JavaScript to submit the form data.  This causes an issue with AutoComplete because AutoComplete only commits data to Protected Storage via a <code>&lt;input type=”submit” /&gt;</code> button.  So, to get around this <span style="text-decoration: line-through;">bug</span> “feature”, we need to do some trickery.

Since AutoComplete only works with <code>&lt;input type=”submit” /&gt;</code> buttons, we need to add one of these buttons to our login page.  We do not actually want to see this button since it is just there to facilitate the AutoComplete functionality, so we set the display style on the submit button to none (<code>&lt;input type=”submit” style=”display: none” /&gt;</code>)

Finally, we need to manipulate the Web Interface JavaScript code that submits to form to tell it to “virtually press” our hidden submit button (this will cause AutoComplete to save the data).  Here are all the steps necessary to implement AutoComplete in Web Interface 5.x:

<em>Step 1</em> – Modify layout.ascx

Change this:  <code>&lt;form method="post" action="&lt;%=FormAction%&gt;" name="&lt;%=Constants.ID_CITRIX_FORM%&gt;" autocomplete="off"&gt; </code>

To this: <code>&lt;form method="post" action="&lt;%=FormAction%&gt;" name="&lt;%=Constants.ID_CITRIX_FORM%&gt;"&gt; </code>

<em> </em>

<em>Step 2</em> – Modify loginMainForm.inc

Add the following to the bottom (right after <code>&lt;/table&gt;</code>):

<code>&lt;input type="submit" value="submit" id="hiddenSubmitButton" style="display:none" /&gt; </code>

This is our hidden fake submit button that will trigger AutoComplete to save the data.

<em>Step 3</em> – Modify login.js

Change this:
~~~
function submitForm() {
    if (!isSubmitted) {
        changeLoginBtnColor(false);

        isSubmitted = true;

        var loginBtn = document.getElementById("loginButtonWrapper");
        if(loginBtn){
            loginBtn.style.color = "#aaaaaa";
        }

        disableLinks();

        document.forms[0].submit();
    }
}
~~~

To this:
~~~
function submitForm() {
    if (!isSubmitted) {
        changeLoginBtnColor(false);

        isSubmitted = true;

        var loginBtn = document.getElementById("loginButtonWrapper");
        if(loginBtn){
            loginBtn.style.color = "#aaaaaa";
        }

        disableLinks();

        <span style="background-color: yellow;">var hiddenSubmitBtn = document.getElementById("hiddenSubmitButton");
        if(hiddenSubmitBtn.click) {

                hiddenSubmitBtn.click();
        }
        else {</span>
                document.forms[0].submit();
        <span style="background-color: yellow;">}
        return false;</span>
    }
}
~~~

The highlighted code basically tells the JavaScript submit function to “virtually click” the hidden submit button we added to loginMainForm.inc.
Again, if you want to disable passwords from being saved, add autocomplete=”off” to all the <code>&lt;input type=’password’ … /&gt;</code> fields in loginMainForm.inc.

<strong>Other factors of using AutoComplete</strong>
In order for AutoComplete to save form data, the feature needs to be turned on in your web browser.  For Internet Explorer, this can be found by going to Tools -&gt; Internet Options -&gt; Content tab.

<a href="http://www.jasonconger.com/images/articleImages/IE-AutoComplete.png"><img style="display: block; float: none; margin-left: auto; margin-right: auto; border: 0px;" title="Internet Explorer AutoComplete" src="http://www.jasonconger.com/images/articleImages/IE-AutoComplete_thumb.png" border="0" alt="Internet Explorer AutoComplete" width="512" height="634" /></a>

For Firefox, this can be found by going to Tools -&gt; Options -&gt; Privacy.

<a href="http://www.jasonconger.com/images/articleImages/FF-AutoComplete.png"><img style="display: block; float: none; margin-left: auto; margin-right: auto; border: 0px;" title="FF-AutoComplete" src="http://www.jasonconger.com/images/articleImages/FF-AutoComplete_thumb.png" border="0" alt="FF-AutoComplete" width="543" height="524" /></a>

AutoComplete stores form data in Protected Storage – which means that the Protected Storage service needs to be running.   Protected Storage can, on occasion, get corrupted.  See this Microsoft support article about this situation: <a href="http://support.microsoft.com/kb/306895">http://support.microsoft.com/kb/306895</a>