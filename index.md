---
layout: page
title: Rémy Gardette
tagline: Java / PHP developer
js: [jquery]
---
{% include JB/setup %}

<div class="row-fluid">
    <div class="span3 main-box dev" data-href="http://blog.remyg.fr">
        <header>
            Blog
        </header>
        <div class="desc">
            My blog
        </div>
    </div>
    <div class="span3 main-box dev" data-href="articles.html">
        <header>
            Articles
        </header>
        <div class="desc">
            Articles on my development work
        </div>
    </div>
    <div class="span3 main-box dev" data-href="projects/index.html">
        <header>
            Projects
        </header>
        <div class="desc">
            <span>My personal projects</span>
        </div>
    </div>
    <div class="span3 main-box pro" data-href="resume.html">
        <header>
            Resume
        </header>
        <div class="desc">
            My resume
        </div>
    </div>    
</div>

<div class="row-fluid">
    <div class="span3 main-box pro" data-href="skills.html">
        <header>
            Skills
        </header>
        <div class="desc">
            My IT skills
        </div>
    </div>
    <div class="span3 main-box misc" data-href="contact.html">
        <header>
            Contact
        </header>
        <div class="desc">
            How to contact me
        </div>
    </div>
    <div class="span3 main-box misc" data-href="about.html">
        <header>
            About
        </header>
        <div class="desc">
            About me
        </div>
    </div>
</div>


<script type="text/javascript">
// <!--
$('.main-box').click(function() {
    window.location.href = $(this).data('href');
});

$('.main-box').hover(
    function () {
        $(this).find('.desc').slideDown(300);
    },
    function () {
        $(this).find('.desc').slideUp(200);
    }
);
// -->
</script>

<div class="row-fluid">

    <div class="span4 last-articles">
        <section>
            <h2>Last articles</h2>        
            {% for post in site.posts limit: 5 %}
                <article>                    
                    <h3 class="home-small-title">
                        <a title="Permalink to {{ post.title }}" href="{{post.url}}/">{{ post.title }}</a>
                        <small><i class="icon-time"> </i>
                        {{ post.date | date:"%Y-%m-%d" }}</small>
                    </h3>
                </article>
            {% endfor %}
            <p>
                <a href="{{ BASE_PATH }}{{ site.JB.archive_path }}">See Archive</a>
            </p>
        </section>
    </div>

    <div class="span4 last-repositories">
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
                        $('#gh_repos').html('');
                        for(var i = 0; i < $(resp.data).length && i < {{ site.github.repo_count }}; i++) 
                        {
                           $('#gh_repos').append(
                                '<h3 class="home-small-title"><a href="' + resp.data[i]['html_url'] + '">'
                                + resp.data[i]['name'] + '</a></h3>'
                                + '<p>' 
                                + (resp.data[i]['description'] ? resp.data[i]['description'] : '(No description)') 
                                + '</p>'
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
                        $('#last_tweets').html('');
                        $.each(resp, function(i, item) {
                            $("#last_tweets").append(
                                '<div class="tweet-content">' + item.text.linkify() + '</div>'
                                + "<div class='tweet-info'>" 
                                + relative_time(item.created_at) 
                                + " via " 
                                + item.source
                                + "</div>");
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