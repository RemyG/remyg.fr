---
layout: post
title: "PFP"
tagline: "A tiny PHP application framework"
date: 2013-01-15 18:00
comments: false
external-url:
tags: [PHP, Framework, PDO] 
categories: [Dev]
---
In my free time, I often work on small personal PHP projects. This allows me to keep in touch with the new technologies, frameworks,... For instance, I've recently started using Bootstrap to create well presented web-applications.

My issue was that, each time I started a new project, I had to re-create the skeleton for the application. This basically meant copying an old project, remove everything specific, clean all the configuration values,... before I could start working. That's why I decided to create an independant project, which I could use as a skeleton for almost all my PHP applications.

<!-- more -->

But while looking at several existing solutions (Zend, CakePHP, FuelPHP,...), I've decided that these frameworks were way too heavy and complicated for my needs. I only needed a basic MVC skeleton. Then I found [PIP](http://gilbitron.github.com/PIP/), which is a tiny, lightweight MVC framework for LAMP stacks.

I've forked the project as [PFP](https://github.com/RemyG/PFP), so I could alter it to match my needs. The main modification I've made so far are:

* converting all global variables to constants
* using PDO instead of the mysql functions
* creating a global header and footer for the whole application

With these modifications, I've got my generic application skeleton, that I can use for all my PHP website developments.

You can find all the information about this project on [this page]({{ root_url }}/projects/pfp).

This project is released on GitHub [here](https://github.com/RemyG/PFP) under an MIT license.

