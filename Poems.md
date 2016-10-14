---
layout: page
title: Poems 古体诗
permalink: /Poems/
---
偶尔学作几句古体诗，聊以自娱。按照时间顺序整理了一下，有些可能还图文并茂。
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
