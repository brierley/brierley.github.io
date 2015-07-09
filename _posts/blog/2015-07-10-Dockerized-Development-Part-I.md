---
layout: post
title: 'Dockerized Development With Meteor (Part I)'
author: david_nirchi
modified: null
categories: blog
excerpt: null
comments: true
tags: []
image:
  feature: container.jpg
date: 2015-07-10T19:39:55.000Z
---

![alt text](/images/docker-whale.png "Docker") ![alt text](/images/meteor.png "Meteor")

# Introduction
In this first of a series of posts, we'll introduce you to Docker and walk through a basic tutorial for setting up a Docker-based development environment on your local Mac or Windows machine.

Then, we'll introduce you to <a href="http://www.meteor.com/" target="_blank">**Meteor**</a> and show you how to <a href="https://docs.docker.com/userguide/dockerizing/" target="_blank">**dockerize**</a> a full-stack JavaScript application.

# The Tech Stack
First, a brief introduction to each of the technologies we'll be using. If you'd prefer, you can skip ahead to the [**`Getting Started`**](#start) section to begin the tutorial.

## Docker (Container Technology)

So, what's with all the hype? Is Docker really that awesome?

According to <a href="http://www.docker.com/" target="_blank">**docker.com**</a>

> The Docker platform helps developers build and ship better software faster and streamline how sysadmins run distributed applications anywhere.

Exactly how does Docker do this, you may be asking? The simple answer: Containers. Docker containers allow you to wrap up a piece of software in a complete, self-contained file system that has everything it needs to run: code, runtime, system tools, system libraries, etc - basically anything you can install on an instance of Linux. The really cool part about this is that containers will always run and behave the same, regardless of the environment the container is running in.

In the tutorial, Docker will allow us to wrap our application stack with Docker containers for the purpose of Continuous Integration and Delivery. With Docker, we can logically separate major components of the stack (ie: web server, database) into individualized containers that can then be orchestrated to work seamlessly together. What used to take weeks or months in terms of setup and configuration, now takes hours or days and is easily repeatable and reusable across in Development, Test and Production environments.

#### Boot2Docker

Docker is based on open standards, allowing containers on to run on all major Linux distributions. That's great, but what about Windows and Mac OS X you ask? Don't fret - Docker runs on those, too, thanks to something called <a href="https://github.com/boot2docker/boot2docker" target="_blank">**Boot2Docker**</a>, a lightweight Linux distribution that runs inside a virtual machine. Boot2Docker includes a VirtualBox Virtual Machine (VM), Docker itself and the Boot2Docker management tool.

#### Docker Engine

The Docker Engine is the core of the Docker platform, a lightweight runtime responsible that builds and runs your Docker containers.

Learn more about <a href="https://www.docker.com/docker-engine" target="_blank">**Docker Engine**</a>.

#### Docker Hub Registry

Another great thing about Docker is the Docker Hub, where you can add/manage your private and public Docker repositories just like you would a source code repository on GitHub. Docker Hub let's you collaborate effortlessly with the broader Docker community or within your own team. And just like with GitHub, you can also make use of containers created by others through the <a href="https://registry.hub.docker.com/" target="_blank">**Docker Hub Registry**</a> to rapidly build and deploy endless stack combinations.

We'll walk through how to quickly get up and running with Docker in the [**`tutorial`**](#start).

#### Kitematic

Kitematic makes installing and using Docker dead-simple by offering a one-click install and configuration with all the necessary components to run Docker on your laptop or desktop, plus a fully functional GUI that works seamlessly with the Docker CLI for managing your containers.

Learn more about <a href="https://www.docker.com/docker-kitematic" target="_blank">**Kitematic**</a>.

## Meteor > MEAN ( full-stack JavaScript Platform)
We'll be using Meteor for our full-stack JavaScript development, but before we get too deeply into talking about Meteor, it's worth touching on the MEAN stack, the history behind it and why this tutorial uses Meteor versus leveraging an implementation of the MEAN stack.

MongoDB engineer Valeri Karpov first coined the term **MEAN** in a <a href="http://blog.mongodb.org/post/49262866911/the-mean-stack-mongodb-expressjs-angularjs-and" target="_blank">**blog post**</a> he used to describe the set of tools he and his team were using - those tools being <a href="https://www.mongodb.org" target="_blank">**M**ongoDB</a> + <a href="http://expressjs.com/" target="_blank">**E**xpress</a> + <a href="https://angularjs.org/" target="_blank">**A**ngularJS</a> + <a href="https://nodejs.org/" target="_blank">**N**ode.js</a>.

There is no such thing as **_the_** MEAN stack or framework. The acronym is simply a generic way to identify using these 4 technologies in combination. There are several implementations of the MEAN stack, a community fragmentation problem in itself. Two of the most popular MEAN implementations are:

* <a href="http://mean.io/" target="_blank">**MEAN.IO**</a>
* <a href="http://meanjs.org/" target="_blank">**MEAN.JS**</a>

Both initiatives were started by <a href="https://github.com/amoshaviv" target="_blank">**Amos Haviv**</a>, with Mean.io now being under the umbrella of a company called <a href="http://www.linnovate.net/" target="_blank">**Linnovate**</a>. You can read more about why Haviv ceased his collaboration with Linnovate, forked the Mean.io repository and created Mean.js <a href="http://blog.meanjs.org/post/76726660228/forking-out-of-an-open-source-conflict" target="_blank">**here**</a>. With the MEAN stack community so fragmented and so many competing implementation players, MEAN's future is uncertain and a risky venture for those just starting out building full-stack JavaScript applications.

But, enough about the MEAN stack, let's talk about Meteor.

Meteor is a mature, open-source, full-stack, real-time web application platform written using Node.js that has been developed by a very well-funded and highly knowledgeable and cohesive team since 2011 with a large and growing <a href="https://github.com/meteor/meteor" target="_blank">**community**</a>.

Meteor's long-term <a href="https://www.meteor.com/about" target="_blank">**mission statement**</a> is impressive - even more so if they can pull it off:

> ...to build a new platform for cloud applications that will become as ubiquitous as previous platforms such as Unix, HTTP, and the relational database.

To say that is quite a statement is an understatement. Can they pull it off? Maybe. In just the span of a few short years, they've managed to build a tremendous following, attract extremely talented developers and <a href="http://techcrunch.com/2015/05/19/meteor-raises-20m-to-build-the-one-javascript-stack-to-rule-them-all/" target="_blank">**recently raise $20M in funding**</a> in addition to the initial $11.2M raised in 2012.

Meteor is showing no signs of slowing down, with major initiatives in the pipeline such as <a href="http://info.meteor.com/blog/meteor-and-a-galaxy-of-containers-with-kubernetes" target="_blank">**Galaxy**</a>, a cloud-based system for deploying, hosting and running Meteor applications based on Google's open source <a href="http://kubernetes.io/" target="_blank">**Kubernetes**</a> project and more direct support for other UI frameworks such as <a href="https://youtu.be/s6IgKYsZAyI" target="_blank">**Angular**</a> or <a href="http://info.meteor.com/blog/two-weeks-with-react-and-meteor" target="_blank">**React**</a>.

#### Meteor versus MEAN By the Numbers

| Metric                    | Meteor              | Mean.io       | Mean.js     |
| :-------------            | :-------------:     | :-----:       | :------:    |
| StackOverflow Questions   | 13197               | 169           | 387         |
| GitHub Contributors       | 213                 | 143           | 93          |
| GitHub Stars              | 26140               | 6948          | 2280        |
| GitHub Commits            | 13843               | 1216          | 650         |
| GitHub Forks              | 2977                | 2076          | 767         |
| Twitter Followers         | 42780               | 3038          | 2440        |
| Tweets About URL          | 1968                | 976           | 681         |
| Facebook Shares           | 3115                | 1367          | 455         |
| LinkedIn Shares           | 602                 | 42            | 102         |
| Google+ Shares            | 7936                | 434           | 76          |

## Atom (IDE)

Behind every successful development project lies great tooling, with the Integrated Development Environment (IDE) being at the core of that success. For this tutorial, we'll be using GitHub's Atom IDE, an <a href="https://github.com/atom/atom" target="_blank">**open-source**</a>, hackable text editor with plenty of great plugins. In fact, this blog post was written using it, complete with <a href="https://help.github.com/articles/markdown-basics/" target="_blank">**GitHub Markdown**</a> syntax highlighting!

Both Windows and OS X versions are available free for <a href="https://atom.io/" target="_blank">**download**</a>.

# The Tutorial - Part I: Setting Up the Development Environment

In **_Part I_** of our tutorial, we'll walk through getting your development environment set up with Docker and Meteor, and then walk through a few basic examples of using Docker before we go deeper into Meteor development in **_Part II_**.

<a name="start"></a>

## Getting Started

Okay, enough talk. Let's get to work on building and packaging our full-stack application with the help of Docker.

### 1. Installing Docker

#### Mac OS X

If you've got a Mac, you have two installation options: <a href="https://kitematic.com/" target="_blank">**Kitematic**</a> (recommended) or Boot2Docker. Although not required, Kitematic is the easier of the two ways to start using Docker because the installer neatly takes care of installing everything you'll need and Kitematic also gives you a nice, modern User Interface (UI) at runtime so that you can visually manage your docker containers. Kitematic is also designed to work seamlessly with the Docker Command Line Interface (CLI). Boot2Docker will also install everything needed to run Docker without a UI (CLI-only).

Both options will install Oracle VirtualBox (if not already installed) with a pre-installed lightweight Linux VM made specifically for running Docker containers. The VM runs completely in RAM and is relatively small (~24MB download).

If you run into trouble with either installation approach, Docker has great documentation <a href="https://docs.docker.com/installation/mac/" target="_blank">**here**</a>.

##### Option 1 - Kitematic (Recommended)

Follow the Kitematic installation instructions <a href="https://kitematic.com/docs/" target="_blank">**here**</a>.

##### Option 2 - Boot2Docker

Download the latest Doot2Docker install package (Boot2Docker-*.pkg) <a href="https://github.com/boot2docker/osx-installer/releases/" target="_blank">**here**</a>.

#### Windows

If you're running on a Windows-based machine, you have two installation options: <a href="https://kitematic.com/" target="_blank">**Kitematic**</a> (alpha-only) or Boot2Docker (recommended). At the time of this writing, the Windows version of Kitematic is in alpha, so be forewarned.

Depending on your preference, the benefits the Kitematic User Interface (UI) provides may outweigh the risks of using alpha software. Kitematic is optional, so if you choose to go the Boot2Docker route, the Boot2Docker installer will provide everything you need with the exception of the UI (Kitematic). You'll be working exclusively with the Docker CLI via Windows command prompt.

As with the Mac installation, both the Kitematic and Boot2Docker options will install Oracle VirtualBox (if not already installed) with a pre-installed lightweight Linux VM made specifically for running Docker containers. The VM runs completely in RAM and is relatively small (~24MB download).

If you run into trouble with either installation approach, Docker has great documentation <a href="https://docs.docker.com/installation/mac/" target="_blank">**here**</a>.

##### Option 1 - Kitematic (alpha-only)

Download the latest Kitematic installer <a href="https://github.com/kitematic/kitematic/releases/" target="_blank">**here**</a>. At the time of this writing, the latest version of the installer file is called <a href="https://github.com/kitematic/kitematic/releases/download/v0.7.4/KitematicSetup-0.7.4-Windows-Alpha.exe" target="_blank">_**KitematicSetup-0.7.4-Windows-Alpha.exe**_</a>.

##### Option 2 - Boot2Docker (recommended)

Download the latest Doot2Docker install package (Boot2Docker-*.pkg) <a href="https://github.com/boot2docker/windows-installer/releases" target="_blank">**here**</a>, which will install the Docker Client for Windows, VirtualBox, Git for Windows (MSYS-git), the boot2docker Linux ISO, and the Boot2Docker management tool.

### 2. Taking Docker for a Spin

By this point, you should have Docker installed, either via the Kitematic installer or Boot2Docker. The Boot2Docker virtual machine should be running inside Oracle VirtualBox.

Let's go through a few steps to make sure everything installed correctly. Open a terminal (command prompt) window and run this command to start the Boot2Docker VM:

{% highlight bash %}
$ boot2docker up
{% endhighlight %}

You should see something like this:

{% highlight text %}
$ boot2docker up
Waiting for VM and Docker daemon to start...
....................ooo
Started.
Writing /Users/<your_username>/.boot2docker/certs/boot2docker-vm/ca.pem
Writing /Users/<your_username>/.boot2docker/certs/boot2docker-vm/cert.pem
Writing /Users/<your_username>/.boot2docker/certs/boot2docker-vm/key.pem

To connect the Docker client to the Docker daemon, please set:
    export DOCKER_HOST=tcp://192.168.59.103:2376
    export DOCKER_CERT_PATH=/Users/<your_username>/.boot2docker/certs/boot2docker-vm
    export DOCKER_TLS_VERIFY=1

$

{% endhighlight %}

Now that the Boot2Docker VM is running, let's log into the VM via ssh (Secure Shell) with the following command:

{% highlight bash %}
$ boot2docker ssh
{% endhighlight %}

If Boot2Docker is running smoothly, you should see something like this in your terminal window:

{% highlight text %}
$ boot2docker ssh
                         ##         .
                   ## ## ##        ==
                ## ## ## ## ##    ===
            /"""""""""""""""""\___/ ===
       ~~~ {~~ ~~~~ ~~~ ~~~~ ~~~ ~ /  ===- ~~~
            \______ o           __/
             \    \         __/
              \____\_______/
 _                 _   ____     _            _
| |__   ___   ___ | |_|___ \ __| | ___   ___| | _____ _ __
| '_ \ / _ \ / _ \| __| __) / _` |/ _ \ / __| |/ / _ \ '__|
| |_) | (_) | (_) | |_ / __/ (_| | (_) | (__|   <  __/ |
|_.__/ \___/ \___/ \__|_____\__,_|\___/ \___|_|\_\___|_|
Boot2Docker version 1.7.0, build master : 7960f90 - Thu Jun 18 18:31:45 UTC 2015
Docker version 1.7.0, build 0baf609

docker@boot2docker:~$

{% endhighlight %}

One quick and easy way to verify that everything is setup correctly is to run the _hello-world_ container. Enter the following command:

{% highlight bash %}
$ docker run hello-world
{% endhighlight %}

If everything is working correctly, you should see the following:

{% highlight text %}

Unable to find image 'hello-world:latest' locally
latest: Pulling from hello-world
a8219747be10: Pull complete
91c95931e552: Already exists
hello-world:latest: The image you are pulling has been verified. Important: image verification is a tech preview feature and should not be relied on to provide security.
Digest: sha256:aa03e5d0d5553b4c3473e89c8619cf79df368babd18681cf5daeb82aab55838d
Status: Downloaded newer image for hello-world:latest
Hello from Docker.
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (Assuming it was not already locally available.)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

For more examples and ideas, visit:
 http://docs.docker.com/userguide/

{% endhighlight %}

##### What just happened?

By issuing this command, we asked Docker to run the <a href="https://docs.docker.com/docker-hub/official_repos/" target="_blank">**official**</a> _hello-world_ Docker image. As we can see from the command output above, we did not have the image so Docker automatically initiated a download/pull request from the hello-world Docker Hub repository.
