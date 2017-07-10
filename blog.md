---
layout: default
title: blog
pagename: blog
---
{% include header.html %}
<div class="contianer">
<div class="list-menu pull-right">
<ul class="post-list">
{% for post in site.posts %}
  <li>{{ post.date | date_to_string }} <a href="{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}
</ul>
</div>
</div>