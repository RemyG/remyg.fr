---
layout: page
title : Articles
header : Articles
group: navigation
weight: 1
flattrable: false
rss: true
---
{% include JB/setup %}

{% for post in site.posts limit: 10 %}

<article class="post">
	<header>
		<div class="row-fluid">
			<div class="span10 date">
				<i class="icon-time"> </i>
				{{ post.date | date:"%Y-%m-%d" }}
			</div>			
			<div class="span2 comments-heading">
				<i class="icon-comments"> </i>
				<a href="{{ post.url }}/#disqus_thread">Comments</a>
			</div>
		</div>
		<div class="row-fluid">
			<div class="span12 post-title">
				<h1>
					<a title="Permalink to {{ post.title }}" href="{{post.url}}/">{{ post.title }}</a>
					{% if post.tagline %}<small> - {{post.tagline}}</small>{% endif %}
				</h1>
			</div>
		</div>
	</header>
	<div class="row-fluid">
		<div class="span12 post-wrapper">
			<div class="post-content">
				{{ post.content | postmorefilter: post.url, "Continue Reading &raquo;" }}
			</div>
			<div class="flattr-div">
				<a class="FlattrButton" 
					href="http://remyg.fr{{ page.url }}" 
					title="{{ page.title }}" 
					rel="flattr;tags:blog;"> </a>
			</div>
			{% unless post.tags == empty %}
				<div>
					<i class="icon-tags valign-middle float-left"> </i>
					<ul class="tag_box inline valign-middle">
						{% assign tags_list = post.tags %}
						{% include JB/tags_list %}
					</ul>
				</div>
			{% endunless %}  
			{% unless post.categories == empty %}
			<div>
				<i class="icon-folder-open valign-middle float-left"> </i>
				<ul class="tag_box inline valign-middle">
					{% assign categories_list = post.categories %}
					{% include JB/categories_list %}
				</ul>
			</div>
			{% endunless %} 
		</div>
	</div>
	<div class="row-fluid">
		<div class="span12">
			<hr/>
		</div>
	</div>
</article>

{% endfor %}

<p>
<a href="{{ BASE_PATH }}{{ site.JB.archive_path }}">Posts Archive</a>
</p>