---
layout: page
title: Movies
permalink: /movies/
---

<div class="container">
    <div class="main-content">
        <div class="row">
            {% assign movies_posts = site.posts | where_exp: "post", "post.tags contains 'movies'" %}
            {% for post in movies_posts %}
            <div class="col-md-6">
                <div class="card">
                    {% if post.image %}
                    <div class="card-img-top">
                        <a href="{{ site.baseurl }}{{ post.url }}">
                            <img class="img-fluid" src="{{ site.baseurl }}/{{ post.image }}" alt="{{ post.title }}">
                        </a>
                    </div>
                    {% endif %}
                    <div class="card-body">
                        <h2 class="card-title">
                            <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a>
                        </h2>
                        <h4 class="card-text">{{ post.description }}</h4>
                        <div class="metafooter">
                            <div class="wrapfooter">
                                <span class="meta-footer-thumb">
                                    {% if post.author %}
                                    <img class="author-thumb" src="https://www.gravatar.com/avatar/{{ post.author.gravatar }}?s=250&d=mm&r=x" alt="{{ post.author.display_name }}">
                                    {% endif %}
                                </span>
                                <span class="author-meta">
                                    <span class="post-name">
                                        {% if post.author %}
                                        {{ post.author.display_name }}
                                        {% else %}
                                        {{ site.name }}
                                        {% endif %}
                                    </span><br/>
                                    <span class="post-date">{{ post.date | date_to_string }}</span>
                                </span>
                                <span class="post-read-more">
                                    <a href="{{ site.baseurl }}{{ post.url }}" title="Read Story">
                                        <svg class="svgIcon-use" width="25" height="25" viewbox="0 0 25 25">
                                            <path d="M19 6c0-1.1-.9-2-2-2H8c-1.1 0-2 .9-2 2v6.4l3.9-3.9c.8-.8 2-.8 2.8 0l3.9 3.9V6z"/>
                                        </svg>
                                    </a>
                                </span>
                                <div class="clearfix"></div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            {% endfor %}
        </div>
        
        {% if movies_posts.size == 0 %}
        <div class="text-center">
            <h3>No movie posts found.</h3>
            <p>Posts tagged with "movies" will appear here.</p>
        </div>
        {% endif %}
    </div>
</div>
