---
layout: page
title: Rémy Gardette
tagline: Java / PHP developer
js: [jquery]
---
{% include JB/setup %}

<div class="row-fluid">

<div class="span9" markdown="1">

Hello, and welcome on my home page!

I am a **software engineer**, since I graduated from the [INSA Lyon](http://www.insa-lyon.fr/en), one of the most prestigious French engineering universities, in July 2009.

I currently work for [Multicom](http://www.multicom.co.uk/), a software editor, in Bristol (UK).

You can find on this website my personal information, where to find me on the internet, how to contact me...

</div>

<div class="span3">
	<img src="{{ '/img/picture.jpeg' }}" class="img-rounded" alt="Rémy Gardette" title="Rémy Gardette">
</div>

</div>

<div class="row-fluid">

    <div class="span4">
        <section>
            <h2>Last articles</h2>        
            {% for post in site.posts limit: 5 %}
                <article>
                    <i class="icon-time"> </i>
                    {{ post.date | date:"%Y-%m-%d" }}
                    <h4>
                        <a title="Permalink to {{ post.title }}" href="{{post.url}}/">{{ post.title }}</a>
                    </h4>
                </article>
            {% endfor %}
            <p>
                <a href="{{ BASE_PATH }}{{ site.JB.archive_path }}">See Archive</a>
            </p>
        </section>
    </div>

    <div class="span4">
        {% include JB/github %}
        <script type="text/javascript">
        // <!--
            $.ajax({
                type: "GET",
                url: 'https://api.github.com/users/{{ site.github.user }}/repos?callback=?',
                data: { type: "all", sort: "pushed", direction: "desc" },
                dataType: 'json',
                success: function(resp) {
                    if (resp.data.length > 0) {
                        $('#gh_repos').html('<ul></ul>');
                        for(var i = 0; i < $(resp.data).length && i < {{ site.github.repo_count }}; i++) 
                        {
                           $('#gh_repos > ul').append(
                                '<li><a href="' + resp.data[i]['html_url'] + '">'
                                + resp.data[i]['name'] + '</a>'
                                + '<p>' 
                                + (resp.data[i]['description'] ? resp.data[i]['description'] : '(No description)') 
                                + '</p></li>'
                            );
                        }
                    }
                    else {
                        $('#gh_repos').html('<p>No public repositories.</p>');
                    }
                }
            });
        // -->
        </script>
    </div>

</div>