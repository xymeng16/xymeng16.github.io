---
layout: page
title: Xiangyi's Blog!
tagline: Supporting tagline
---
{% include JB/setup %}
## Life is quite long but busy, for each person, we should devote ourselves to make the world better.


<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

