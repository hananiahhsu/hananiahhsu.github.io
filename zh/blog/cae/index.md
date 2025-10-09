---
layout: page
title: CAE
permalink: /zh/blog/cae/
lang: zh
---

{% include lang-switch.html %} 
{% include topnav.html %}

<h2>CAE</h2>
<ul>
{% assign items = site.posts_zh | where_exp: "p", "p.categories contains 'cae'" | sort: "date" | reverse %}
{% if items.size > 0 %}
  {% for post in items %}
    <li><span class="muted">{{ post.date | date: "%Y-%m-%d" }}</span> — <a href="{{ post.url | relative_url }}">{{ post.title }}</a></li>
  {% endfor %}
{% else %}
  <li>暂无文章。</li>
{% endif %}
</ul>
