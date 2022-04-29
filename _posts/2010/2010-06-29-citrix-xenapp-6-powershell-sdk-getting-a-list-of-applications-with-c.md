---
id: 8
title: 'Citrix XenApp 6 PowerShell SDK: Getting a List of Applications with C#'
date: 2010-06-29T09:33:00-05:00
author: JasonConger
excerpt: This post will show you how to use the Citrix XenApp 6 PowerShell SDK to obtain a list of applications from your XenApp 6 farm.  We'll look at how to do this with using the PowerShell Runspace and how to do this using the Citrix XenApp 6 wrapper assembly.
layout: post
image: wp-content/uploads/2010/08/PowerShell.png
categories:
  - Citrix XenApp
  - PowerShell
tags:
  - 'C#'
  - PowerShell
  - SDK
  - XenApp
---
This post will show you how to use the Citrix XenApp 6 PowerShell SDK to obtain a list of applications from your XenApp 6 farm.  We’ll look at how to do this with using the PowerShell Runspace and how to do this using the Citrix XenApp 6 wrapper assembly.  The examples used in this post will be using an ASP.NET website, but the code can be reused in a Windows application, Console application, web service, etc.

<img style="display: inline; margin-left: 0px; margin-right: 0px; border-width: 0px;" title="Note" src="http://www.jasonconger.com/images/articleImages/Note.png" border="0" alt="Note" width="16" height="16" /> Note: Be sure to read the [getting started post]({% post_url 2010-06-26-getting-started-with-the-citrix-xenapp-powershell-sdk-and-c %}) for information about adding the correct references to your project.
<h2>Using the PowerShell Runspace</h2>
I added a Web Form to my project named RunSpaceFactory.aspx.  Here is what it looks like:

~~~c#
using System.Management.Automation;
using System.Management.Automation.Runspaces;

namespace WebApplication1
{
    public partial class RunSpaceFactory : System.Web.UI.Page
    {
        protected void Page_Load(object sender, EventArgs e)
        {
            Runspace rs = RunspaceFactory.CreateRunspace();
            rs.Open();

            PowerShell ps = PowerShell.Create();
            ps.Runspace = rs;

            PSSnapInException ex;
            rs.RunspaceConfiguration.AddPSSnapIn("Citrix.XenApp.Commands", out ex);

            ps.AddCommand("Get-XAApplication");

            // You can add a search string like this:
            // ps.AddCommand("Get-XAApplication").AddParameter("BrowserName", "n*");

            foreach (PSObject app in ps.Invoke())
            {
                Response.Write(app.Properties["DisplayName"].Value);
                Response.Write("");
            }

            rs.Close();
        }
    }
}
~~~

<span style="text-decoration: underline;">Lines 10 – 14</span> are standard PowerShell things you would do to work with PowerShell in any C# application.

<span style="text-decoration: underline;">Line 17</span> adds the Citrix PowerShell SnapIn to the Runspace so we can execute the Citrix commands.

<span style="text-decoration: underline;">Lines 19 – 28</span> lists all the applications in the XenApp 6 farm.

<span style="text-decoration: underline;">Note line 21 &amp; 22</span>. If line 22 was uncommented, this excerpt would list all the applications that start with the letter ‘n’ by adding a parameter to the Get-XAApplication command.  You can use any matching pattern here like ‘%o*’ which would get all applications whose second letter is ‘o’.
<h2>Using the Citrix XenApp 6 Wrapper Assembly</h2>
When using the Citrix XenApp 6 wrapper assembly, you first need to add references to the appropriate DLLs to your project.  The DLLs can be found in <strong>%ProgramFiles%\Citrix\XenApp Server SDK\bin</strong>

<a href="http://www.jasonconger.com/images/articleImages/AddXenApp6Reference.png" target="_blank"><img style="display: block; float: none; margin-left: auto; margin-right: auto; border-width: 0px;" title="AddXenApp6Reference" src="http://www.jasonconger.com/images/articleImages/AddXenApp6Reference_thumb.png" border="0" alt="AddXenApp6Reference" width="482" height="408" /></a>

After adding the references, here is the code to accomplish the same task from above:

~~~c#
using System.Management.Automation;
using System.Management.Automation.Runspaces;

using Citrix.Management.Automation;
using Citrix.XenApp.Sdk;
using Citrix.XenApp.Commands;

namespace WebApplication1
{
    public partial class ListApplications : System.Web.UI.Page
    {
        protected void Page_Load(object sender, EventArgs e)
        {
            GetXAApplicationByName apps = new GetXAApplicationByName();
            apps.BrowserName = new string[] {"*"};

            foreach (PSObject _app in CitrixRunspaceFactory.DefaultRunspace.ExecuteCommand(apps))
            {
                XAApplication app = (XAApplication)_app.BaseObject;

                Response.Write(app.BrowserName);
                Response.Write("");
            }
        }
    }
}
~~~

As you can see, there is quite a bit less code here.

<span style="text-decoration: underline;">Line 14</span> sets up all your Runspace stuff and adds the appropriate command.

<span style="text-decoration: underline;">Line 15</span> adds a parameter to the command.  This is an interesting line because the BrowserName property expects an array of strings.  I’m just passing one string here, but you could pass several to match.  For example, string[] {“n*”, “%o*”} would find all apps that either started with the letter ‘n’ or the second letter was ‘o’.

We loop through the results in lines 18 – 24.  Note that I cast the PSObject (generic PowerShell object) to a XAApplication object.  This helps with the type safety and IntelliSense.  To be fair, you can do the exact same thing in the PowerShell Runspace example above if you wanted.
<h2>The Results</h2>
Here is what the Citrix Delivery Services Console looks like concerning published applications:

<a href="http://www.jasonconger.com/images/articleImages/CDSCApps_1.png" target="_blank"><img style="display: block; float: none; margin-left: auto; margin-right: auto; border-width: 0px;" title="Citrix Delivery Services Console Applications" src="http://www.jasonconger.com/images/articleImages/CDSCApps_thumb_1.png" border="0" alt="Citrix Delivery Services Console Applications" width="500" height="339" /></a>

Here is the output from both examples:

<a href="http://www.jasonconger.com/images/articleImages/WebAppPS.png" target="_blank"><img style="display: block; float: none; margin-left: auto; margin-right: auto; border: 0px;" title="WebAppPS" src="http://www.jasonconger.com/images/articleImages/WebAppPS_thumb.png" border="0" alt="WebAppPS" width="471" height="440" /></a>
<h2>What’s Next?</h2>
The next examples will show you how to publish and application as well as how to manage sessions.  You can also get a jump start by downloading the example code below:
<div class="download">Download: <a href="http://www.jasonconger.com/downloads/XenApp6SDK/JasonConger.com_XenApp6SDK_Samples.zip">Citrix XenApp 6 PowerShell SDK Examples</a></div>