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

[**View demo &raquo;**](http://formcreator.remyg.fr)

I often need to simulate HTTP POST requests, and it's always a real pain to paste the parameters in a text editor, delete all the useless text, create an input tag for each parameter, then save the file as an HTML page and open it in a browser.

That's what FormCreator is meant to do. It won't create a nice form, but it will parse the parameters you put in and transform them into hidden inputs, so you can test your HTTP request.

## Usage

* Put the action of the request in the "Action" input.
* Select the method of the request (POST/GET) in the "Method" list.
* Put the format of the parameters in the field "Paremeters as Regex". It should contain two strings (.+?), used for the parameters names and their values. Currently, the parameter name must appear before its value.

## License

This project is released under the MIT License:

Copyright (c) 2013 Rémy Gardette

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

## Changelog

**v1.0** - Initial version