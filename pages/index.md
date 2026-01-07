---
layout: default
title: CODIGUIN
permalink: /
---

<h2>Recentes</h2>
<div class="container_latest">
    {% for post in site.posts limit: 2 %}
        <div class="posts_latest">
            <div> 
                <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
                <h3> {{ post.subtitle }} </h3>
                <p> {{post.author}} | {{ post.date | date: "%d %b %Y" }} </p>
            </div>
        </div>
    {% endfor %}
</div>

<h2>Posts</h2>
<div class="container_posts">
    {% for post in site.posts %}
        {% if forloop.index0 >= 2 %}
            <div class="posts_order">
                <div>
                    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
                    <h3> {{ post.subtitle }} </h3>
                    <p> {{post.author}} | {{ post.date | date: "%d %b %Y" }} </p>
                </div>
            </div>
        {% endif %}
    {% endfor %}
</div>