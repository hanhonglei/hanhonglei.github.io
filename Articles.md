---
layout: page
title: Articles 杂文
permalink: /articles/
---
<ul>
  {% for post in site.posts %}
  {% if post.categories contains 'article' %} 
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
	  <span>({{ post.date | date:"%Y-%m-%d" }})</span>
    </li>
  {% endif %} 
  {% endfor %}
</ul>
