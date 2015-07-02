---
layout: post
title: 'Continuous Integration (Part I): Dockerized Development'
author: david_nirchi
modified: null
categories: blog
excerpt: null
tags: []
image:
  feature: null
date: 2015-06-24T19:39:55.000Z
---

# Introduction
In this first of a series of posts, we'll introduce you to Docker and walk through<br>a basic tutorial for setting up a Docker-based development environment on your<br>local Mac or Windows machine.

Then, we'll introduce you to <a href="http://www.meteor.com/" target="_blank">**Meteor**</a> and show you how to <a href="https://docs.docker.com/userguide/dockerizing/" target="_blank">**dockerize**</a> a fullstack application.

# The Tech Stack
First, a brief introduction to each of the technologies we'll be using. If you'd<br>prefer, you can skip ahead to the [**`Getting Started`**](#start) section to<br>begin the tutorial.

## Docker
Docker will allow us to wrap our application stack with a Docker container<br>for the purpose of Continuous Integration and Delivery. We'll walk through<br>how to accomplish this later in this tutorial.

To learn more about Docker, visit<br><a href="https://www.docker.com/whatisdocker" target="_blank">**docker.com**</a>

## Meteor (Fullstack Application)
You may have heard of the MEAN Meteor is a complete open source platform for<br>building web and mobile apps in pure JavaScript. You may have heard MEAN stack (**M**ongo, **E**xpress,<br>  **A**ngular, **N**ode.js), Meteor gives us that and much more.

# The Tools
## ATOM (IDE)
Behind every successful development project lies great tooling, with the IDE<br>being the core

<a name="start"></a>

# Getting Started
First, we need to install Docker. The great thing about Docker is that although it<br>is Linux-based, you can run it on Mac or Windows and the experience is the same<br>thanks to boot2docker.

# The MEAN Stack
You may have heard of the The MEAN stack is a collection of 4 components: MongoDB, ExpressJS, AngularJS and<br>Node.js.

# Getting Started with the MEAN Stack
The most important tool in a developer's arsenal is the IDE, so it goes without<br>saying that having a great IDE is absolutely key for any development project. In<br>order to level the playing field and avoid the environmental nuances of Windows<br>versus MacOS, we're going to cloud - <b>Cloud 9</b>, that is.

Cloud9 is great for sandboxing and rapid prototyping:
- Easily and quickly spin up clean workspaces with preinstalled modules accessible
- from anywhere.
- Complete development environment with a full Ubuntu workspace in the cloud.
- Terminal access with root to fully customize the workspace.
- Write, run and debug your code in a fully functional web-based IDE.
- Collaborate on your workspaces publicly or keep them private.

Note: You can certaily work through this tutorial locally with your favorite IDE, but<br>we will not walk through the specifics of setting up and configuring an environment for your<br>particular flavor of OS. For other cloud-based options, we also love <a href="http://pro.nitrous.io" target="_blank">Nitrous.io</a>, but their FREE tier only comes with 4 hours of active<br>use per day - hopefully this changes in the future.

To get rolling with Cloud9:

<ol><br>  <li>First, open a web browser and navigate to <a href="http://c9.io">http://c9.io</a>.</li><br>  <li>Sign up for a new account (it's FREE).</li><br>  <li>Sign in and click the <b>CREATE NEW WORKSPACE</b> button and select <b><i>Create a New Workspace</i></b>.</li><br><br><figure><br>    <img src="/images/post1-1-create-workspace.png" alt="image"><br></figure><br><br>  <li>In the dialog window, provide a name for your workspace and select Node.js.<br>Keep the defaults settings for <i>Workspace Privacy</i> and <i>Hosting</i> since<br>we're planning to use the FREE tier and host our solution on the Cloud 9 platform.</li><br>  <li>Click the <b>CREATE</b> button to generate a boilerplate Node.js project.</li><br></ol>  

Your new workspace will be created in just a few seconds (typically, 5-10). Once,<br>it's ready, go ahead and click on your workspace in the left navigation, then click<br>the <b><i>START EDITING</i></b> button at the top.

## Housekeeping
First things first - we need to take care of a few housekeeping items before we<br>can begin. We need an empty project, so go ahead and delete all the files and folders in the<br>project by right-clicking them in the left navigation pane of the IDE:

<i class="fa fa-folder"> client</i><br><br /><br><i class="fa fa-folder"> node_modules</i><br><br /><br><i class="fa fa-file-code-o"> package.json</i><br><br /><br><i class="fa fa-file-text-o"> README.md</i><br><br /><br><i class="fa fa-file-code-o"> server.js</i>

You should now have an empty project. Next, we need to update the installed version<br>of Node.js and NPM to the latest. As of this writing, the current Node.js version is<br><b>0.12.5</b>. To update, separately enter the following commands into the terminal window at the<br>of the Cloud9 IDE:

{% highlight bat %}<br>$ nvm install 0.12<br>$ nvm use 0.12<br>$ nvm alias default v0.12<br>{% endhighlight %}

That takes care of our housekeeping. Now, a bit of background on the MEAN stack!

## Installing the Tools
In this tutorial, we'll be using several tools to make life easier for ourselves.

### Bower (Package Manager)
First, we'll install something called Bower. Bower is an extremely useful package<br> manager. It works by fetching and installing packages from all over, taking<br>care of hunting, finding, downloading and saving the stuff you're looking for -<br>things like frameworks, libraries, assets, utilities and unicorns. Okay, that last<br>one I made up, but it's pretty awesome.

Enter the following into the terminal window.

```
$ npm install -g bower
```

### Grunt (JavaScript Task Runner)
Next, let's install Grunt. Why Grunt? In one word: automation. Grunt is <i>the</i><br>JavaScript task runner - it helps you automate repetitive tasks. The less work you<br>have to do when performing repetitive tasks like minification, compilation, unit<br>testing and linting happier you will be.

Enter the following into the terminal window.

```
$ npm install -g grunt-cli
```

### Yeoman (Scaffolding Tool)
Yeoman refers to itself as <i>The Web's Scaffolding Tool for Modern Webapps</i>. Yeoman<br>helps you kick start new projects, prescribing best practices and tools to help you<br>stay productive. There's also a vast, rich ecosystem of Yeoman generators - a<br>generator is basically a plugin that can be run with the `yo` command to scaffold<br>complete projects or useful parts.

Enter the following into the terminal window.

```
$ npm install -g yo
```

To learn more, visit: {% highlight html %}<a href="http://yeoman.io">yeoman.io</a>{% endhighlight %}
