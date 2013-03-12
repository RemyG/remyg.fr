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


    <div class="span4">
        {% include JB/twitter %}
        <script type="text/javascript">
        // <!--
            String.prototype.linkify = function() {
                return this.replace(/[A-Za-z]+:\/\/[A-Za-z0-9-_]+\.[A-Za-z0-9-_:%&\?\/.=]+/, 
                    function(m) {
                        return m.link(m);
                    });
            };

            function relative_time(time_value) {
                  var values = time_value.split(" ");
                  time_value = values[1] + " " + values[2] + ", " + values[5] + " " + values[3];
                  var parsed_date = Date.parse(time_value);
                  var relative_to = (arguments.length > 1) ? arguments[1] : new Date();
                  var delta = parseInt((relative_to.getTime() - parsed_date) / 1000);
                  delta = delta + (relative_to.getTimezoneOffset() * 60);
                  var r = '';
                  if (delta < 60) {
                    r = 'a minute ago';
                  } else if(delta < 120) {
                    r = 'couple of minutes ago';
                  } else if(delta < (45*60)) {
                    r = (parseInt(delta / 60)).toString() + ' minutes ago';
                  } else if(delta < (90*60)) {
                    r = 'an hour ago';
                  } else if(delta < (24*60*60)) {
                    r = '' + (parseInt(delta / 3600)).toString() + ' hours ago';
                  } else if(delta < (48*60*60)) {
                    r = '1 day ago';
                  } else {
                    r = (parseInt(delta / 86400)).toString() + ' days ago';
                  }
                  return r;
            }

            $.ajax({
                type: "GET",
                url: 'https://api.twitter.com/1/statuses/user_timeline/{{ site.twitter.user }}.json?count={{ site.twitter.tweet_count }}&callback=?',
                dataType: 'json',
                success: function(resp) {
                    if (resp.length > 0) {
                        $('#last_tweets').html('<ul></ul>');
                        $.each(resp, function(i, item) {
                            $("#last_tweets > ul").append("<li>" 
                                + item.text.linkify() 
                                + " <span class='created_at'>" 
                                + relative_time(item.created_at) 
                                + " via " 
                                + item.source
                                + "</span></li>");
                        });
                    }
                    else {
                        $('#last_tweets').html('<p>No public tweets.</p>');
                    }
                }
            });
        // -->
        </script>
    </div>
</div>