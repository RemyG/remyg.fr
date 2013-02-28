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

* [LinkedInScraper](#linkedinscraper) - Scrape a resume from LinkedIn.
* [MySqlBackup](#mysqlbackup) - Backup a whole MySql database
    

## <a id="linkedinscraper"> </a>LinkedInScraper

This script is used to scrape a resume from LinkedIn, and create an XML file with the results.

### Requirements

This script is composed of 2 files:

* `linkedinscraper/linkedin.php` - contains the script
* `linkedinscraper/libs/simple_html_dom.php` - a PHP HTML parser ([external library](http://sourceforge.net/projects/simplehtmldom/))

### Functionment

To scrape a resume from LinkedIn, you just need to call the method `scrapeResume($resume_url, $dest_file)`, which will create or replace the file `$dest_file` with the XML scraping of the resume at `$resume_xml`.

The resulting XML file will have the format:

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

## <a id="mysqlbackup"> </a>MySqlBackup

This script is used to back up a MySql database (or just a table).

### Functionnement

The script in ran by calling the function `backup_tables($hostname, $username, $password, $dbname, $table = '*')`. If you ommit the last parameter, the whole database will be backed up.
    
The back up is saved in a temporary file `db-backup-YYYYMMDD-HHmmss.sql` and then compressed in a file `db-backup-YYYYMMDD-HHmmss.tar.gz`.

## Author and license

Released under the MIT License by [Remy Gardette](http://remyg.fr/en).
