---
title: "Quick Tip: Wildcard Sourcetypes in Props.conf"
author: jason
excerpt: Here is a quick tip to use wildcards in Splunk props.conf stanzas.
layout: post
categories:
  - Splunk
  - Splunk Blog
tags:
  - Splunk
---
{: .box-note}
Originally posted on the Splunk official blog: [https://www.splunk.com/en_us/blog/tips-and-tricks/quick-tip-wildcard-sourcetypes-in-props-conf.html](https://www.splunk.com/en_us/blog/tips-and-tricks/quick-tip-wildcard-sourcetypes-in-props-conf.html){:target="_blank"}

Here is a quick one I use often.  Here is an excerpt from [props.conf.spec](https://docs.splunk.com/Documentation/Splunk/latest/Admin/propsconf){:target="_blank"}:

~~~
[<spec>]
* This stanza enables properties for a given <spec>.

<spec> can be:
1. <sourcetype>, the source type of an event.
2. host::<host>, where <host> is the host, or host-matching pattern, for an event.
3. source::<source>, where <source> is the source, or source-matching pattern, for an event.
4. rule::<rulename>, where <rulename> is a unique name of a source type classification rule.
5. delayedrule::<rulename>, where <rulename> is a unique name of a delayed source type
   classification rule.
These are only considered as a last resort before generating a new source type based on the
source seen.
~~~

However, I often want to wildcard a sourcetype for things like lookups.  Here is an example, suppose I have the following sourcetypes:

* acme:users
* acme:logins
* acme:sessions

It would be nice to have a stanza in props.conf that read something like:

CAUTION – THIS DOES NOT WORK

~~~
[acme:*]
LOOKUP-acme = lookup acme_users user_id AS user_id OUTPUTNEW user_name AS user_name FirstName AS FirstName LastName AS LastName
~~~~

So that doesn’t work, but this regex magic does work:

~~~
[(?::){0}acme:*]
LOOKUP-acme = lookup acme_users user_id AS user_id OUTPUTNEW user_name AS user_name FirstName AS FirstName LastName AS LastName
~~~