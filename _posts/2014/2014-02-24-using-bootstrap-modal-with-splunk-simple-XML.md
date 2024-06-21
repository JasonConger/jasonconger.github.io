---
title: Using Bootstrap Modal with Splunk Simple XML
author: jason
excerpt: While working on a performance dashboard recently, I wanted an area to further explain the performance metric currently being displayed without taking up too much screen real estate. In the end, I ended up using a Bootstrap modal dialog to display the metric details when a user clicks an information icon.
layout: post
thumbnail-img: /assets/img/2014/02/24/ModalDescription.jpg
share-img: /assets/img/2014/02/24/ModalDescription.jpg
categories:
  - Splunk Blog
tags:
  - Splunk
---
{: .box-note}
Originally posted on the Splunk official blog: [https://www.splunk.com/en_us/blog/tips-and-tricks/using-bootstrap-modal-with-splunk-simple-xml.html](https://www.splunk.com/en_us/blog/tips-and-tricks/using-bootstrap-modal-with-splunk-simple-xml.html){:target="_blank"}

While working on a performance dashboard recently, I wanted an area to further explain the performance metric currently being displayed without taking up too much screen real estate. In the end, I ended up using a Bootstrap modal dialog to display the metric details when a user clicks an information icon. Here is the end result:

![GPO Logon Perf](/assets/img/2014/02/24/ModalDescription.jpg)

## Step 1 – Add the Bootstrap modal markup to your dashboard

Pulling the syntax directly from Bootstrap [http://getbootstrap.com/javascript/#modals](http://getbootstrap.com/javascript/#modals){:target="_blank"}, this is what the Simple XML looks like:

~~~
<row grouping=”2”>
    <chart id=”chart1”> … </chart>
    <html>
        <a href="#" id="btn1" class="btnModalInfo" data-toggle="modal" data-target="#desc1">…</a>
        <div class="modal fade" id="desc1">
            <div class="modal-dialog">
                <div class="modal-content">
                    <div class="modal-header"></div>
                    <div class="modal-body">…</div>
                    <div class="modal-footer">…</div>
                </div>
            </div>
        </div>
    </html>
</row>
~~~

## Step 2 – Add JavaScript to move your buttons to the correct place

If you have a keen eye, you will notice that the button that triggers the modal dialog will appear below the chart. We want the button moved next to the title of the panel, so we use a little jQuery to reposition the button like this:

~~~
require(['jquery'], function($){ $(function() {
    // When the DOM is ready, move the modal button where we want it to be displayed
    $("#chart1 .panel-head").find("h3").after($("#btn1"));
    });
});
~~~

FYI – I got the code to move things around from the [Splunk Dashboard Examples app](http://apps.splunk.com/app/1603/){:target="_blank"} – there are lots of cool things in there so check it out.

## Step 3 – Add CSS to make things look pretty
The last step is to add some CSS to do things like float and add padding. The important part of the CSS is setting the .modal display to none. There is a bug feature in Chrome that will render controls behind the modal dialog useless even when the dialog is not displayed (reference -> [http://updates.html5rocks.com/2012/09/Stacking-Changes-Coming-to-position-fixed-elements](http://updates.html5rocks.com/2012/09/Stacking-Changes-Coming-to-position-fixed-elements){:target="_blank"}) To fix this, add the following to your stylesheet:

~~~
.modal { display: none;
}
~~~

As always, I created a sample GitHub project to put it all together. Go get it here -> [https://github.com/JasonConger/SplunkModalDescExample](https://github.com/JasonConger/SplunkModalDescExample){:target="_blank"}