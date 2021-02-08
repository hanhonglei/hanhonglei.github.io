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

<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-85986843-1', 'auto');
  ga('send', 'pageview');

</script>