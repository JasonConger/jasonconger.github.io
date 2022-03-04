---
id: 1242
title: Using PowerShell to Retrieve Citrix Monitor Data via OData
date: 2013-10-11T14:11:20-05:00
author: jason
layout: post
guid: http://www.jasonconger.com/?p=1242
image: wp-content/uploads/2013/10/OData.jpeg
categories:
  - Citrix
tags:
  - Citrix
  - OData
  - PowerShell
  - SQL
---
Starting with XenDesktop 7, Citrix stores the data the Desktop Director displays in a SQL database. Citrix opened up this data via a Monitor Service API that uses <a title="OData" href="http://www.odata.org/" target="_blank">OData</a>.  I'm not going to go deep into the details of the API as it is fairly well <a title="Citrix Monitor Service OData API Documentation" href="http://support.citrix.com/proddocs/topic/xendesktop-7/cds-ms-odata-wrapper.html" target="_blank">documented</a> at the eDocs site.  The examples in the documentation show you how to access this data via web browser, Microsoft Excel, and LinqPad.  What I want to do in this article is show you how to use <a title="Posts tagged with PowerShell on JasonConger.com" href="http://www.jasonconger.com/post/tag/powershell/">PowerShell</a> with this API.

To start out, let's take a look at the Citrix Monitor Service schema (click to enlarge):

&nbsp;
<p style="text-align: center;"><a href="http://jasonconger.com/wp-content/uploads/2013/10/MonitorDataSchema.png" target="_blank"><img class="aligncenter  wp-image-1243" alt="MonitorDataSchema" src="http://jasonconger.com/wp-content/uploads/2013/10/MonitorDataSchema-1024x940.png" width="600" height="550" /></a></p>
<p style="text-align: left;">Suppose we want to get all sessions as well as the all the connection/disconnections to the session.  The following URL will return the data we want in XML format.</p>

<p>
http://localhost/Citrix/Monitor/Odata/v1/Data/Sessions
</p>

<p style="text-align: left;">The trick to get this working with PowerShell is to transform all this information into a nice hierarchical structure.  In the example code below, we use the <code>Invoke-ODataTransform</code> function to do this.</p>

<pre class="brush: PowerShell;">function Global:Invoke-ODataTransform ($records) {

    $propertyNames = ($records | Select -First 1).content.properties |
        Get-Member -MemberType Properties |
        Select -ExpandProperty name

    foreach($record in $records) {

        $h = @{}
        $h.ID = $record.ID
        $properties = $record.content.properties

        foreach($propertyName in $propertyNames) {
            $targetProperty = $properties.$propertyName
            if($targetProperty -is [System.Xml.XmlElement]) {
                $h.$propertyName = $targetProperty.'#text'
            } else {
                $h.$propertyName = $targetProperty
            }
        }

        [PSCustomObject]$h
    }
}

$connections = ""
$uri = "http://localhost/Citrix/Monitor/OData/v1/Data/Sessions?`$expand=Connections"
$connections = Invoke-ODataTransform(Invoke-RestMethod -Uri $uri -UseDefaultCredentials)

foreach($connection in $connections)
{
    $output = $connection | Get-Member -MemberType Properties | ForEach-Object {
        $key = $_.Name
        $value = $connection.$key
        '{0}="{1}"' -f $key,$value
    }

    Write-Host $output
}</pre>