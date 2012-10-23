---
layout: page
title: ./sigterm.sh
tagline: Just another geek blog...
---
{% include JB/setup %}

> Welcome to my blog!
> 
> Below you'll find a list of posts I've written:

<table class="table table-condensed">
  <tr>
    <th>Published</th>
    <th>Category</th>
    <th>Title</th>
  </tr>
  {% for post in site.posts %}
  <tr>
    <td>{{ post.date | date_to_string }}</td>
    <td>{{ post.category }}</td>
    <td><a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></td>
  </tr>  
  {% endfor %}
</table>
