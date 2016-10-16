---
layout: page
title: Poems 古体诗
permalink: /poems/
---
偶尔学作几句古体诗，聊以自娱。
<ul>
  {% for post in site.posts %}
	{% if post.categories contains 'poem' %} 
		<li>
		  <a href="{{ post.url }}">{{ post.title }}</a>
		  <span>({{ post.date | date:"%Y-%m-%d" }})</span>
		  {{ post.excerpt }}
		</li>
	 {% endif %} 
	{% endfor %}
</ul>
