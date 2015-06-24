---
layout: post
title: "Continuous Integration in the Cloud with the MEAN stack (Part I)"
author: david_nirchi
modified:
categories: blog
excerpt:
tags: []
image:
  feature:
date: 2015-06-24T15:39:55-04:00
---

# Setting Up Your Cloud Development Environment

In order to level the playing field and avoid the environmental
nuances of Windows versus MacOS, we're going to cloud - Cloud 9, that is. We
also like <a href="http://pro.nitrous.io" target="_blank">Nitrous.io</a>, but
their FREE tier only comes with 4 hours of active use per day - hopefully
this changes in the future.

<ol>
  <li>First, open a web browser and navigate to <a href="http://c9.io">http://c9.io</a>.</li>
  <li>Sign up for a new account (it's FREE).</li>
  <li>Sign in and click the <b>CREATE NEW WORKSPACE</b> button and select <b><i>Create a New Workspace</i></b>.</li>

<figure>
	<img src="/images/post1-1-create-workspace.png" alt="image">
</figure>

  <li>In the dialog window, provide a name for your workspace and select Node.js.
Keep the defaults settings for <i>Workspace Privacy</i> and <i>Hosting</i> since
we're planning to use the FREE tier and host our solution on the Cloud 9 platform.</li>
  <li>Click the <b>CREATE</b> button to generate a boilerplate Node.js project.</li>
</ol>
