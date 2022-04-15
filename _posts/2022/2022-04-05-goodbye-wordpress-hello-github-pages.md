---
layout: post
title: Goodbye WordPress - Hello GitHub Pages
subtitle: Why I moved my blog to GitHub Pages
cover-img: /assets/img/2022/04/github-pages-banner.jpg
thumbnail-img: /assets/img/2022/04/github-octocat-thumb.jpg
share-img: /assets/img/2022/04/github-pages-banner.jpg
categories:
 - General
 - PowerShell
tags:
 - WordPress
 - GitHub
author: JasonConger
readtime: true
excerpt: Is GitHub Pages better than WordPress? Maybe. For me, GitHub Pages seems to have everything I need, so I moved my blog there, and I'm not looking back. Here's the story as to why I made that move.
featured: true
---
Is GitHub Pages better than WordPress? Maybe. For me, GitHub Pages seems to have everything I need, so I moved my blog there, and I'm not looking back. Here's the story as to why I made that move.

# Blog Platform Backstory
My blog platform has [changed multiple times over the years](https://web.archive.org/web/*/jasonconger.com){:target="_blank"}. I started out with a custom-built site built on ASP.NET. It utilized IIS, a Microsoft SQL backend, and code written in C#. This gave me a lot of control, but when new shiny things came along that I wanted to implement, I had to go through a "learn, code, implement" cycle. This got old after a while, so I began the search for a new blog platform.

Since my platform was already based on .NET, I went hunting for something in that realm and found [BlogEngine.NET](https://blogengine.io){:target="_blank"}. BlogEngine.NET served me well for a while, but the development of the software slowed down back when I was using it, and I ended back up in the "learn, code, implement" cycle to extend the platform. Time to find a new platform.

WordPress was the obvious choice based on widespread adoption, so I bit the bullet and migrated all my custom stuff over to WordPress which is an HTML/CSS/JavaScript front-end, PHP middleware, and MySQL back end. I stuck with WordPress for several years, but honestly, my personal blogging activity grew stale.

## So, why change now?
Well, I had a heart-to-heart conversation with myself about keeping this blog going or calling it quits. My blogging focus used to be End User Computing, and I'm not really in that world anymore. Do I have more to say about other topics? The answer is "yes". I've got some developer topics, Microsoft cloud (Azure, Office 365, Azure Active Directory) topics, and Splunk topics up my sleeve.

So, I evaluated whether WordPress was still meeting my needs as I've been paying for a platform I haven't really used that much. There's nothing wrong with WordPress, but it is overkill for what I need. I didn't really know what the alternatives were anymore, so I went looking around and found [GitHub Pages](https://pages.github.com){:target="_blank"}.

# Benefits of GitHub Pages
## Cost
WordPress hosting isn't terribly expensive for a personal blog like mine (I was using [Bluehost](https://www.bluehost.com){:target="_blank"} at the time), but it isn't free either. Sure, I could use [WordPress.com](https://wordpress.com/pricing/){:target="_blank"} to host for free, but that is extremely limited too (no custom domain, no plugins, very limited storage, etc.).

GitHub Pages is free for my purposes. But, sometimes with free stuff, you get exactly what you pay for. However, I found GitHub pages to have quite a lot of features. And, in some cases, these features are even better than what I was paying for with WordPress.

## Source Control
My site is literally just a [GitHub repository](https://github.com/JasonConger/jasonconger.github.io){:target="_blank"} now which means I get a lot of Git features for free. For example, I used to run a WordPress plugin to back up my site to Dropbox. The backup produced was a database export and a tarball of files. Now, I have every version of every file that has ever changed on my site along with the exact changes for each file. Plus, all these files are on my local machine by design and I can just edit -> commit -> push, and my changes are live. I can also use repository branches and workflow actions (I don't yet, but I could).

## Running my site locally
Here's an [agile user story](https://www.atlassian.com/agile/project-management/user-stories){:target="_blank"} for the agile fans out there:

> As a site admin, I want to run an exact copy of my site locally, so that I can experiment and then push changes.

Yeah, I could run WordPress locally with a [WAMP/MAMP/LAMP stack](https://www.geeksforgeeks.org/what-is-the-difference-between-lamp-stack-mamp-stack-and-wamp-stack/){:target="_blank"}, but then I'd have to sync database schema changes, export/import content to the database, make sure plugin versions are the same in both local and remote instances, etc. With GitHub Pages, all I have to do is issue the following command from the command line within the repository directory:

    bundle exec jekyll serve --watch

Easy! Now my site is running locally with the "production" source. I can make changes, test locally, and then, when I'm ready, push the changes to my production repository. That's it - no export/import shenanigans.

# Conclusion
So far, Im really loving GitHub pages. The price is right, the features are great for my purposes, and it is easy to use.