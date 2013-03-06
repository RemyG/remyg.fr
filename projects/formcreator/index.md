---
layout: page
title: "FormCreator"
description: "An HTML form generator"
tags: [Test]
categories: [Project]
---
{% include JB/setup %}

<header class="project-downloads">
  <ul>
    <li><a href="https://github.com/RemyG/FormCreator/zipball/master">Download <strong>ZIP File</strong></a></li>
    <li><a href="https://github.com/RemyG/FormCreator/tarball/master">Download <strong>TAR Ball</strong></a></li>
    <li><a href="https://github.com/RemyG/FormCreator">View on <strong>GitHub</strong></a></li>
  </ul>
</header>

This project is an HTML/Javascript application, meant to be used as a development help.

I often need to simulate HTTP POST requests, and it's always a real pain to paste the parameters in a text editor, delete all the useless text, create an input tag for each parameter, then save the file as an HTML page and open it in a browser.

That's what FormCreator is meant to do. It won't create a nice form, but it will parse the parameters you put in and transform them into hidden inputs, so you can test your HTTP request.

## Usage

* Put the action of the request in the "Action" input.
* Select the method of the request (POST/GET) in the "Method" list.
* Put the format of the parameters in the field "Paremeters as Regex". It should contain two strings (.+?), used for the parameters names and their values. Currently, the parameter name must appear before its value.

## Changelog

**v1.0** - Initial version