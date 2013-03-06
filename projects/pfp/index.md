---
layout: page
title: "PFP"
description: "PFP - A tiny PHP MVC framework"
tagline: "A tiny PHP MVC framework"
categories: [Project]
---
{% include JB/setup %}

<header class="project-downloads">
	<ul>
		<li><a href="https://github.com/RemyG/PFP/zipball/master">Download <strong>ZIP File</strong></a></li>
		<li><a href="https://github.com/RemyG/PFP/tarball/master">Download <strong>TAR Ball</strong></a></li>
		<li><a href="https://github.com/RemyG/PFP">View On <strong>GitHub</strong></a></li>
	</ul>
</header>

PFP is a tiny PHP application framework built for people who use a LAMP stack. PFP aims to be as simple as possible to set up and use.

This version is a fork of the original PIP project by [Gilbert Pellegrom](http://gilbert.pellegrom.me/). You can find the original project at [https://github.com/gilbitron/PIP/](https://github.com/gilbitron/PIP/).

## Requirements

* PHP 5.1 or greater with support of PDO
* Drivers for any DBMS compatible with PDO ([list here](http://php.net/manual/en/pdo.drivers.php))
* The mod_rewrite Apache module


## Download

You can download the latest version of PFP in either [zip](https://github.com/RemyG/PFP/zipball/master) or [tar](https://github.com/RemyG/PFP/tarball/master) formats.

You can also clone the project with [Gittoto](http://git-scm.com) by running:

    $ git clone https://github.com/RemyG/PFP.git

## Installation

* Download PFP and extract
* Navigate to `application/config/config.php` and fill in your `BASE_URL`
* You are ready to rock! Point your browser to your `BASE_URL` and hopefully see a welcome message.

## Documentation

PFP is very similar in it's architecture to [CodeIgniter](http://codeigniter.com/) and will likely look very familiar to you if you already have experince with CodeIgniter. However remember that PFP is a tiny framework and does not include a lot of the functionality that comes with CodeIgniter.

### Model-View-Controller

PFP is based on the Model-View-Controller development pattern. MVC is a software approach that separates application logic from presentation. In practice, it permits your web pages to contain minimal scripting since the presentation is separate from the PHP scripting.

* **The Model** represents your data structures. Typically your model classes will contain functions that help you retrieve, insert, and update information in your database.
* **The View** is the information that is being presented to a user. A View will normally be a web page, but can be any type of "page".
* **The Controller** serves as an intermediary between the Model, the View, and any other resources needed to process the HTTP request and generate a web page.

### Folder Structure
    
With MVC in mind the physical layout of PFP is fairly simple. Your application specific files go in the "application" folder (you don't need to touch the system folder). Inside the application folder there are folders for all of the specific application entities:

* config
* controllers
* helpers
* models
* plugins
* views

When PFP loads files it assumes they are in the corresponding folders. So make sure you place your files in the correct folders.
        
We encourage you to use the "static" folder in the root to store you static resource files (CSS, JS etc) however you can put them anywhere. You can also use the `BASE_URL` variable to help include files in your HTML. For example:

    <link rel="stylesheet" href="<?php echo BASE_URL; ?>static/css/style.css" type="text/css" media="screen" />
        
### Naming Conventions

All classes in PFP use [PascalCase](http://c2.com/cgi/wiki?PascalCase) naming. The associated file names must be the same except all lower case. So for example the class `ThisIsAClass` would have the filename `thisisaclass.php`. Underscores in classes must be included in file names as well.
        
### <a id="urls"> </a>URL Structure
    
By default, URLs in PFP are designed to be search-engine and human friendly. Rather than using the standard "query string" approach to URLs that is synonymous with dynamic systems, PFP uses a segment-based approach:

    example.com/class/function/param
        
By default `index.php` is hidden in the URL. This is done using the `.htaccess` file in the root directory.
        
### <a id="controllers"> </a>Controllers
    
Controllers are the driving force of a PFP application. As you can see from the [URL structure](#urls), segments of the URL are mapped to a class and function. These classes are controllers stored in the "application/controller" directory. So for example the URL...
        
    example.com/auth/login
        
...would map to the following Controller with the filename `auth.php`:
        
    <?php

        class Auth extends Controller {

            function index()
            {
                // This is the default function 
                // (i.e. no function is set in the URL)
            }
            
            function login()
            {
                echo 'Hello World!';
            }

        }

    ?>

...and the output would be "Hello World!".
        
The default controller and error controller can be set in `application/config/config.php`
        
Note that if you need to declare a contructor you must also call the parent constructor like:
        
    <?php

        class Example extends Controller {

            public function __construct()
            {
                parent::__construct();
                // Your own constructor code
            }

        }

    ?>

There are several helper functions that can also be used in controllers. Most of these functions take the parameter `$name` of the corresponding class:

* `loadModel($name)` - Load a model
* `loadView($name)` - Load a view
* `loadPlugin($name)` - Load a plugin
* `loadHelper($name)` - Load a helper
* `redirect($location)` - Redirect to a page without having to include the base URL. E.g:

        $this->redirect('some_class/some_function');

### Views

This version of PFP automatically appends a header and a footer to every view. The content of these sections is in `application/views/header.php` and `application/views/header.php`.

Usually, the header will look like:

    <html>
      <head>
        <title>My Site</title>
      </head>
      <body>

And the footer:

      </body>
    </html>

This means that the views usually contain the "content section" of a page. Views are almost always loaded by [Controllers](#controllers). So for example if you had a view called `main_view.php` that contained the following HTML:
        
    <h1>Welcome to my Site!</h1>

... you would load it in a controller by doing the following:
        
    <?php

        class Main extends Controller {

            function index()
            {
                $template = $this->loadView('main_view');
                $template->render();
            }
            
        }

    ?>

The resulting HTML page would then be:

    <html>
      <head>
        <title>My Site</title>
      </head>
      <body>
        <h1>Welcome to my Site!</h1>
      </body>
    </html>

The View class has a helper function called `set($key, $val)` that allows you to pass variables from the Controller to the View.
        
    $template = $this->loadView('main_view');
    $template->set('someval', 200);
    $template->render();

...then in the view you could do:
        
    <?php echo $someval; ?>
        
...and the output would be `200`. Any kind of PHP variable can be passed to a view in this way.
        
### Models

In PFP models are classes whose sole responsiblity it is to deal with data (usually from a database).

For example:
        
    <?php

        class Example_model extends Model {

            public function getSomething($id)
            {
                $stmt = $this->prepareStatement('
                  SELECT *
                  FROM something
                  WHERE id = ?');
                $stmt->bindValue(1, $id, PDO::PARAM_INT);
                $result = $this->executeStatement($stmt);
                if(count($result) == 1) {
                  return $result[0];
                }
                return null;
            }

        }

    ?>
        
...then in a controller you would do:
        
    function index()
    {
        $example = $this->loadModel('Example_model');
        $something = $example->getSomething($id);
        
        $template = $this->loadView('main_view');
        $template->set('someval', $something);
        $template->render();
    }

Now the results of your database query would be available in your view in `$someval`. Note that in the above code there are no steps to connect to the database. That is because this is done automatically. For this to work you must provide your database details in `config.php`:
        
    define('DB_DSN', 'mysql:dbname=test;host=localhost'); // Database DSN
    define('DB_USERNAME', ''); // Database username
    define('DB_PASSWORD', ''); // Database password

There are several helper functions that can also be used in models:

* `prepareStatement($sql)` - Prepares and returns a statement from a query
* `executeStatement($statement, $parameters = null)` - Executes a statement, with or without parameters as an array, and returns an array containing all of the result set rows (indexed by column name)
* `executeStatementUpdate($statement, $parameters = null)` - Executes an update statement, and returns the number of updated rows
* `executeStatementInsert($statement, $parameters = null)` - Executes an insert statement, and returns the last inserted id

### Helpers & Plugins

There are two types of additional resources you can use in PFP.

* **Helpers** are classes which you can use that don't fall under the category of "controllers". These will usually be classes that provide extra functionality that you can use in your controllers. PFP ships with two helper classes (`Session_helper` and `Url_helper`) which are examples of how to use helpers.
* **Plugins** are literally any PHP files and can provide any functionality you want. By loading a plugin you are simply including the PHP file from the "plugins" folder. This can be useful if you want to use third party libraries in your PFP application.

## License

This theme is released under the MIT License:

Copyright (c) 2013 Rémy Gardette

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

## Changelog

**v0.1** - Initial fork:

* Forked from [https://github.com/gilbitron/PIP/](https://github.com/gilbitron/PIP/), version 0.5.3
* Replaced `global` variables by constants.
* Implemented use of the PDO extension.