---
layout: page
title: "RSS Reader"
description: ""
---
{% include JB/setup %}

<header class="project-downloads">
    <div><a href="https://github.com/RemyG/RSSReader/zipball/master">Download <strong>ZIP File</strong></a></div>
    <div><a href="https://github.com/RemyG/RSSReader/tarball/master">Download <strong>TAR Ball</strong></a></div>
    <div><a href="https://github.com/RemyG/RSSReader">View On <strong>GitHub</strong></a></div>
</header>

This project is a self-hosted RSS aggregator and reader.

You can find the sources of this project [on GitHub](https://github.com/RemyG/RSSReader) (you can also directly download [the Zip archive](https://github.com/RemyG/RSSReader/archive/master.zip)).

## Requirements

* PHP 5.1 or greater with support of PDO
* MySql drivers for PDO
* the Mod_Rewrite module for Apache
* the php5-tidy package

## Installation

### Download the project

#### With git

* Clone the main project:

{% highlight bash %}
$ mkdir /var/www/rss-reader
$ cd /var/www/rss-reader
$ git clone https://github.com/RemyG/RSSReader.git .
{% endhighlight %}

* Fetch the submodules Propel ORM and SimplePie:

{% highlight bash %}
$ git submodule init
$ git submodule update
{% endhighlight %}

#### Without git

* Download the application, and extract.
* Download [Propel](http://propelorm.org/download.html) and extract in `application/plugins/propel`.
* Download [SimplePie](http://simplepie.org/downloads/) and extract in `application/plugins/simplepie`.

### Configuration

* Go to `http://your_url/installation.php` in a browser.
* Fill the form with the correct infomation:
	* Site Base URL: the base URL of the application
	* DB Host: the database host URL
	* DB Name: the database name
	* DB Username: the database account username
	* DB Password: the database account password	
* Go to `BASE_URL` in a browser, and create the main user as asked.
* You're good to go!

## License

This project is released under the MIT License:

Copyright (c) 2013 Rémy Gardette

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

## External applications

This project includes 2 external applications / libraries:

* [Propel ORM](http://propelorm.org/), an open source ORM for PHP5. Propel ORM is released under the MIT License.
* [SimplePie](http://simplepie.org/), an open source feed parser. SimplePie is released under the BSD License.

## Changelog

**v0.2.0**

* jQueryMobile mobile website
* jQueryUI sortable feeds list
* preferences saving
* keyboard navigation
* old entries clean-up

**v0.1**

* First version of the project
