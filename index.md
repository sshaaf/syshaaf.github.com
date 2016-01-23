---
layout: page
title: Hello World!
tagline: another jekyll blog
---
{% include JB/setup %}

Read [Jekyll Quick Start](http://jekyllbootstrap.com/usage/jekyll-quick-start.html)

Complete usage and documentation available at: [Jekyll Bootstrap](http://jekyllbootstrap.com)


<div class="posts">
  {% for post in site.posts %}
    <div class="post">
  <h3 class="title"><a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></h3>
  {{ post.excerpt }}
  <a class="more" href="{{ BASE_PATH }}{{ post.url }}">Read More...</a>
  <span class="date">Posted: {{ post.date | date_to_string }}</span>
    </div>
  {% endfor %}
</div>



## To-Do

This theme is still unfinished. If you'd like to be added as a contributor, [please fork](http://github.com/plusjade/jekyll-bootstrap)!
We need to clean up the themes, make theme usage guides with theme-specific markup examples.


