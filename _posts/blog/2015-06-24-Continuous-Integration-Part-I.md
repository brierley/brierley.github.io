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
In this first of a series of posts, we'll introduce you to Docker and walk through a basic tutorial for setting up a Docker-based development environment on your local Mac or Windows machine.

Then, we'll introduce you to <a href="http://www.meteor.com/" target="_blank">**Meteor**</a> and show you how to <a href="https://docs.docker.com/userguide/dockerizing/" target="_blank">**dockerize**</a> a fullstack JavaScript application.

# The Tech Stack
First, a brief introduction to each of the technologies we'll be using. If you'd prefer, you can skip ahead to the [**`Getting Started`**](#start) section to begin the tutorial.

## Docker (Container Technology)
Docker will allow us to wrap our application stack with a Docker container for the purpose of Continuous Integration and Delivery. We'll walk through how to accomplish this later in this tutorial.

To learn more about Docker, visit <a href="https://www.docker.com/whatisdocker" target="_blank">**docker.com**</a>

## Meteor > MEAN (Fullstack JavaScript Platform)
We'll be using Meteor for our fullstack JavaScript development, but before we get too deeply into talking about Meteor, it's worth touching on the MEAN stack, the history behind it and why this tutorial uses Meteor versus leveraging an implementation of the MEAN stack.

MongoDB engineer Valeri Karpov first coined the term **MEAN** in a <a href="http://blog.mongodb.org/post/49262866911/the-mean-stack-mongodb-expressjs-angularjs-and" target="_blank">**blog post**</a> he used to describe the set of tools he and his team were using - those tools being <a href="https://www.mongodb.org" target="_blank">**M**ongoDB</a> + <a href="http://expressjs.com/" target="_blank">**E**xpress</a> + <a href="https://angularjs.org/" target="_blank">**A**ngularJS</a> + <a href="https://nodejs.org/" target="_blank">**N**ode.js</a>.

There is no such thing as **_the_** MEAN stack or framework. The acronym is simply a generic way to identify using these 4 technologies in combination. There are several implementations of the MEAN stack, a community fragmentation problem in itself. Two of the most popular MEAN implementations are:

* <a href="http://mean.io/" target="_blank">**MEAN.IO**</a>
* <a href="http://meanjs.org/" target="_blank">**MEAN.JS**</a>

Both initiatives were started by <a href="https://github.com/amoshaviv" target="_blank">**Amos Haviv**</a>, with Mean.io now being under the umbrella of a company called <a href="http://www.linnovate.net/" target="_blank">**Linnovate**</a>. You can read more about why Haviv ceased his collaboration with Linnovate, forked the Mean.io repository and created Mean.js <a href="http://blog.meanjs.org/post/76726660228/forking-out-of-an-open-source-conflict" target="_blank">**here**</a>.

But, enough about the MEAN stack, let's talk about Meteor.

Meteor is a mature, open-source, full-stack, real-time web application platform written using Node.js that has been developed by a very well-funded and highly knowledgeable team since 2011 with a large and growing <a href="https://github.com/meteor/meteor" target="_blank">**community**</a>. With the MEAN stack community so fragmented and so many competing implementation players, it's

Meteor's long-term <a href="https://www.meteor.com/about" target="_blank">**mission statement**</a> is impressive - even more so if they can pull it off:

> ...to build a new platform for cloud applications that will become as ubiquitous as previous platforms such as Unix, HTTP, and the relational database.

To say that is quite a statement is an understatement. Can they pull it off? Maybe. In just the span of a few short years, they've managed to

#### Meteor versus MEAN (by the numbers)

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

Behind every successful development project lies great tooling, with the Integrated Development Environment (IDE) being at the core of that success. For this tutorial, we'll be using GitHub's Atom IDE, an <a href="https://github.com/atom/atom" target="_blank">**open-source**</a>, hackable text editor with plenty of great plugins. In fact, this blog post was written using it!

Both Windows and OS X versions are available free for <a href="https://atom.io/" target="_blank">**download**</a>.

<a name="start"></a>

# Getting Started
First, we need to install Docker. The great thing about Docker is that although it is Linux-based, you can run it on Mac or Windows and the experience is the same thanks to boot2docker, a lightweight Linux distribution that runs inside a virtual machine.
