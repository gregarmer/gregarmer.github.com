---
layout: page
title: ./sigterm.sh
tagline: Just another geek blog...
---
{% include JB/setup %}

<div class="jumbotron">
    <h1>Welcome to my blog!</h1>
    <p class="lead">
      There are many blogs on the internet, but this one is mine. 
    </p>
    <a onmouseout="$(this).children().attr('class', 'facebook');" onmouseover="$(this).children().attr('class', 'facebook-over');" href="http://www.facebook.com/gregarmer" target="_blank"><img class="facebook" src="assets/images/img_trans.gif"/></a>
    <a onmouseout="$(this).children().attr('class', 'twitter');" onmouseover="$(this).children().attr('class', 'twitter-over');" href="http://twitter.com/gregarmer" target="_blank"><img class="twitter" src="assets/images/img_trans.gif"/></a>
    <a onmouseout="$(this).children().attr('class', 'googleplus');" onmouseover="$(this).children().attr('class', 'googleplus-over');" href="https://plus.google.com/u/0/104342657896837088642" target="_blank"><img class="googleplus" src="assets/images/img_trans.gif"/></a>
    <a onmouseout="$(this).children().attr('class', 'linkedin');" onmouseover="$(this).children().attr('class', 'linkedin-over');" href="http://www.linkedin.com/in/gregarmer" target="_blank"><img class="linkedin" src="assets/images/img_trans.gif"/></a>
    <a onmouseout="$(this).children().attr('class', 'github');" onmouseover="$(this).children().attr('class', 'github-over');" href="http://github.com/gregarmer" target="_blank"><img class="github" src="assets/images/img_trans.gif"/></a>
    <a onmouseout="$(this).children().attr('class', 'atom');" onmouseover="$(this).children().attr('class', 'atom-over');" href="http://sigterm.sh/atom.xml" target="_blank"><img class="atom" src="assets/images/img_trans.gif"/></a>
</div>

<div class="row">
  <div class="span12">
    <h3>Recent Posts <small>A few of the latest ramblings</small></h3>
    <table class="table table-condensed">
      <tr>
        <th>Published</th>
        <th>Title</th>
        <th>Category</th>
        <th>Tags</th>
      </tr>
      {% for post in site.posts limit:10 %}
      <tr>
        <td>{{ post.date | date_to_string }}</td>
        <td><a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></td>
        <td>{{ post.category }}</td>
        <td>{% for tag in post.tags %}{{ tag }}{% if forloop.last %}{% else %}, {% endif %}{% endfor %}</td>
      </tr>  
      {% endfor %}
    </table>
  </div>
</div>
