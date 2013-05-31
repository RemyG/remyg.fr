---
layout: page
title: "Projects"
header: "My personnal projects"
group: navigation
colorcategory: dev
js: [jquery]
weight: 2
---
{% include JB/setup %}

This page regroups the projects I work on in my free time.

{% comment %}
{% include projects_en.html %}
{% endcomment %}

<div class="row-fluid">
	<div class="span4 box-project" data-href="{{ HOME_PATH }}projects/comics-calendar/">
		<header>
			<h1>ComicsCalendar</h1>
			<div class="description">An online calendar to follow the new issues of all your comics</div>
		</header>
		<div class="link">&rarr; See the project page</div>
	</div>
	<div class="span4 box-project" data-href="http://remyg.github.io/RSSReader/index.html">
		<header>
			<h1>RSS Reader</h1>
			<div class="description">Self-hosted RSS aggregator and reader</div>
		</header>
		<div class="link">&rarr; Go to the project website</div>
	</div>
	<div class="span4 box-project" data-href="{{ HOME_PATH }}projects/pfp/">
		<header>
			<h1>PFP - PHP Framework</h1>
			<div class="description">Tiny PHP MVC framework</div>
		</header>
		<div class="link">&rarr; See the project page</div>
	</div>
</div>
<div class="row-fluid">
	<div class="span4 box-project" data-href="{{ HOME_PATH }}projects/rgresponsive/">
		<header>
			<h1>RGResponsive</h1>
			<div class="description">Responsive theme for Wordpress</div>
		</header>
		<div class="link">&rarr; See the project page</div>
	</div>
	<div class="span4 box-project" data-href="http://mybooks.remyg.fr/home">
		<header>
			<h1>My Books</h1>
			<div class="description">Social literature website (reviews, collections, forums...)</div>
		</header>
		<div class="link">&rarr; Go to the website</div>
	</div>
	<div class="span4 box-project" data-href="{{ HOME_PATH }}projects/formcreator">
		<header>
			<h1>Form Creator</h1>
			<div class="description">Small web-app allowing you to automatically generate HTML forms with hidden fields, based on a list of names / values.</div>
		</header>
		<div class="link">&rarr; See the project page</div>
	</div>	
</div>
<div class="row-fluid">	
	<div class="span4 box-project" data-href="{{ HOME_PATH }}projects/rgwordstrap/">
		<header>
			<h1>RGWordstrap</h1>
			<div class="description">Responsive theme for Wordpress, based on Twitter Bootstrap</div>
		</header>
		<div class="link">&rarr; See the project page</div>
	</div>	
	<div class="span4 box-project" data-href="{{ HOME_PATH }}projects/phpscripts/">
		<header>
			<h1>PHP Scripts</h1>
			<div class="description">Misc. PHP scripts (retrieval of professional experience from LinkedIn,...)</div>
		</header>
		<div class="link">&rarr; See the project page</div>
	</div>
	<div class="span4 box-project" data-href="https://github.com/RemyG/PythonScripts">
		<header>
			<h1>Python Scripts</h1>
			<div class="description">Misc. Python scripts (retrieval of professional experience from LinkedIn,...)</div>
		</header>
		<div class="link">&rarr; See the project on GitHub</div>
	</div>
</div>

<script type="text/javascript">
$(document).ready(function() {
	var i = 0;
	$('.box-project').each(function() {
		//$(this).addClass('color-' + Math.round(Math.random()*5));
		$(this).addClass('color-' + i);
		i = i + 1;
		i = i % 6;
	});
});
$('.box-project').click(function() {
    window.location.href = $(this).data('href');
});
$('.box-project').hover(
    function () {
        $(this).find('.link').slideDown(300);
    },
    function () {
        $(this).find('.link').slideUp(200);
    }
);
</script>