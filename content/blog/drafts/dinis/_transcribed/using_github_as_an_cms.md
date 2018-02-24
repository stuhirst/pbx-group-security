---
draft  : true
title  : Using Git as an CMS
author : Dinis Cruz
notes:
 - english and structure needs fixing
---

Using Git repos' to manage answers

Using GitHub as a CMS


The hardest part of maintaining content is the loop of creation, edit, review, publishing. The point of a content management system is to make that easy, is to allow editors to easily edit and publish content. I have multiple experience, all the way through my IT career, and is always being a pinpoint, in fact, I've actually developed and created a bunch of that, and programmed a bunch of them. It's always the hard part, because there is a lot of moving parts that you need. And a couple of years ago, it kind of struck for me that a great CMS, once you start to build websites that consume static data, or that consume data from Git repositories, is actually, GitHub.

So, GitHub is actually a really good content management system, when you build a website that feeds data from it. Specially, when you build a website that is dynamically rebuild from content in GitHub, which is what we do, and we have static websites. If you look at the West Summit website, if you look the PBX Group Security website, they are dynamic sites. So, they are static generate sites, so that means that the whole site is created in one go, there is no dynamic pages, there is no dynamic generators on the front page, which is risk implementation, but actually, is very powerful. Because not only it makes it very easy to host, because the site in this case is hosted in stream bucket, it also allows you to, basically maintain the website by just pushing those files. 

So, then, the workflow gets very powerful, because what you actually have is a situation, that you go to GitHub, you make a file in GitHub, a change, once that push to maters, then you got a GitHub hook, who triggers the build of the website, and the CI environment, and that just pushes to a stream, and there you go, the site is live. And at the moment, that happens now within literally 5-10 seconds of the code change being made. So, you should look at the PBX Group Security website, we are pushing to production, literally, dozens of hundreds of times a day. And all the team is empowered, and especially the ones who merge, to actually do that. So, then, what you have is a really powerful way of content management, because if you are making change, if you commit it to the Github repo. So, basically you make a current change, you propose a change by the pull request, and that allow the rest of the team to review it, to make comments, you can have threads, which is very important. So, you can talk about the change, you can talk about what is actually happening, and then, you merge it. So, the pull request, becomes actually the way you manage content, which is really powerful. It can also have issues, so you can talk about the content that you want, you can have threads about the content that you create, so in a way, GitHub provides you all the core components that you want from a content management system. And add to the fact, that GitHub natively will render mark down pages, so the UI is quite nice. If you use stuff for example, like Gecko powered website, you can even run it off GitHub, and again, you make a change, and the things is launched almost straight away. 

So, I found this a really powerful web-tools that solved a lot of problems, and empowers contribution, which is kind of what you want, that's basically, the key, kind of requirements, of a content management system, is to make it really to edit. Make it really easy to review changes. And make it really easy to publish those changes. And that's what we do with GitHub.
