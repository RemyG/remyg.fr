---
layout: post
title: "Auto-upload Jekyll after pushing to GitHub"
description: ""
category: 
tags: []
date: 2013-03-05 18:30
---
{% include JB/setup %}

My Jekyll site is hosted on a shared web hosting service, provided by OVH. It's the most basic service, which consists of a PHP server, a MySql database, and that's about it. The only way to change the files on the server is to access it via FTP, as there is no SSH connection available.

So, with the concept of Jekyll, which is to generate static HTML files and use them for the final web site, the only option I had was to manually upload the `_site` folder each time I made some changes in the source code. And this after pushing my changes to GitHub (the sources and generated files are stored in a public GitHub repository).

But I've actually found another way to automate the process. For this I need my personnal server, which is an old eeePc running Debian I have at home (but can't use as a web server, for basic QoS reasons).

<!--more-->

## Clone the git repository

I started by cloning the repository on my personnal server:

    $ cd /var/www
    $ git clone https://github.com/RemyG/remyg.fr.git

This create a clone of the repository in `/var/www/remyg.fr`.

## Create the FTP upload script

To automatically upload my files via FTP, I used `ftp-upload`:

    $ sudo apt-get install ftp-upload

Then I've created the script used to upload my `_site` folder to the shared server:

    $ touch /usr/local/bin/ftp-upload-jekyll.sh
    $ chmod +x /usr/local/bin/ftp-upload-jekyll.sh
    $ vim /usr/local/bin/ftp-upload-jekyll.sh

The script consists of a single command:

    #!/bin/sh
    ftp-upload --passive -u "username" --password "password" -h "dest_url" -d dest_folder orig_folder/*
	
When this script is executed, it will upload the content of `orig_folder` into `dest_folder`, on the host `dest_url`.

## Create a GitHub post-receive hook

### On my personnal server

I've just created a PHP file, which is exposed on Internet, and in the same folder as the git repository.

    $ cd /var/www/remyg.fr
    $ vim github-hook.php

The content of this file is very simple: first it pulls the repository, then it calls the script `ftp-upload-jekyll.sh` to upload the content of the `_site` folder to the shared server.

    <?php
        `git pull`;
        `sh /usr/local/bin/ftp-upload-jekyll.sh`;
    ?>

### On GitHub

Then I just had to create the post-receive hook on GitHub, as described on the [GitHub documentation](https://help.github.com/articles/post-receive-hooks). The WebHook URL is the URL of the PHP file on my personnal server.

## Conclusion

Now, each time I push some changes to my GitHub repository, they are automatically uploaded to my web server, and instantly available to be browsed.