---
layout: page
title: AI
permalink: /zh/blog/ai/
lang: zh
---

{% include lang-switch.html %} 
{% include topnav.html %}

<h2>AI</h2>
<ul>
{% assign items = site.posts_zh | where_exp: "p", "p.categories contains 'ai'" | sort: "date" | reverse %}
{% if items.size > 0 %}
  {% for post in items %}
    <li><span class="muted">{{ post.date | date: "%Y-%m-%d" }}</span> — <a href="{{ post.url | relative_url }}">{{ post.title }}</a></li>
  {% endfor %}
{% else %}
  <li>暂无文章。</li>
{% endif %}
</ul>
