---
layout: page
title: Welcome to
tagline: ./code.geek.sh
---
{% include JB/setup %}

> Welcome to my blog!
> 
> Below you'll find a list of posts I've written, hopefully
> you find something interesting to read.

Posts
-----

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
