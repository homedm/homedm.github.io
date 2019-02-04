---
layout: blog
title: All Posts
---

<div class="posts-all-list">
    <h1>All Posts</h1>
    <ul>
        {% for post in site.posts %}
        <li>
            <span>{{ post.date | date_to_string }} - <a href="{{ post.url }}">{{ post.title }}</a></span>
        </li>
        {% endfor %}
    </ul>
</div>
