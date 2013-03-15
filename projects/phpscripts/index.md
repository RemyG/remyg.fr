---
layout: page
title: "PHP Scripts"
description: "Misc. PHP scripts"
---
{% include JB/setup %}

<header class="project-downloads">
  <ul>
    <li><a href="https://github.com/RemyG/PHPScripts/zipball/master">Download <strong>ZIP File</strong></a></li>
    <li><a href="https://github.com/RemyG/PHPScripts/tarball/master">Download <strong>TAR Ball</strong></a></li>
    <li><a href="https://github.com/RemyG/PHPScripts">View On <strong>GitHub</strong></a></li>
  </ul>
</header>

This project regroups several PHP scripts that I've written for my personal use. In case somebody wants to use them, I've put them on GitHub, under an MIT license.

## Download

You can download the latest version of PHPScripts in either [zip](https://github.com/RemyG/PHPScripts/zipball/master) or [tar](https://github.com/RemyG/PHPScripts/tarball/master) formats.

You can also clone the project with Git by running:

    $ git clone https://github.com/RemyG/PHPScripts.git

The different scripts present in this project are:

* [LinkedIn Scraper](#linkedinscraper) - Scrape a resume from LinkedIn.
* [MySqlBackup](#mysqlbackup) - Backup a whole MySql database
    

<h2 id="linkedinscraper" class="anchor">LinkedIn Scraper</h2>

This script is used to scrape a resume from LinkedIn, and create an XML file with the results.

### Requirements

This script is composed of 2 files:

* `linkedinscraper/linkedin.php` - contains the script
* `linkedinscraper/libs/simple_html_dom.php` - a PHP HTML parser ([external library](http://sourceforge.net/projects/simplehtmldom/))

### Functionment

To scrape a resume from LinkedIn, you just need to call the method `scrapeResume($resume_url, $dest_file)`, which will create or replace the file `$dest_file` with the XML scraping of the resume at `$resume_xml`.

The resulting XML file will have the format:

{% highlight xml %}
<?xml version="1.0" encoding="UTF-8"?>
<resume>
  <position>
    <title>position title</title>
    <company>company</company>
    <location>location</location>
    <from>from date</from>
    <to>to date</to>
    <description>description</description>
  </position>
  <position>
  ...
  </position>
</resume>
{% endhighlight %}

<h2 id="mysqlbackup" class="anchor">MySqlBackup</h2>

This script is used to back up a MySql database (or just a table).

### Functionnement

The script in ran by calling the function `backup_tables($hostname, $username, $password, $dbname, $table = '*')`. If you ommit the last parameter, the whole database will be backed up.
    
The back up is saved in a temporary file `db-backup-YYYYMMDD-HHmmss.sql` and then compressed in a file `db-backup-YYYYMMDD-HHmmss.tar.gz`.

## License

These scripts are released under the MIT License:

Copyright (c) 2013 Rémy Gardette

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
