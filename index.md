---
layout: page
title: (*)nixlog
tagline: another bit in the wall
---
{% include JB/setup %}

This blog used to be on www.shaafshah.com till roughly about 2010 as I recall and was hosted as a wordpress blog. Even though wordpress has all the kool friendly features, I didnt understand the need of running a database engine to host the blog, so I moved to Jekyll and also actually played a bit with Pelican. Well anyways, blogging is always an interesting hobby, I havent blogged for a long while but I hope to keep up with it. 


This blog uses Jekyll and JekyllBootstrap.
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


