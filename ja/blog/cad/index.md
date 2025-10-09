---
layout: page
title: CAD
permalink: /ja/blog/cad/
lang: ja
---

{% include lang-switch.html %} 
{% include topnav.html %}

<h2>CAD</h2>
<ul>
{% assign items = site.posts_ja | where_exp: "p", "p.categories contains 'cad'" | sort: "date" | reverse %}
{% if items.size > 0 %}
  {% for post in items %}
    <li><span class="muted">{{ post.date | date: "%Y-%m-%d" }}</span> — <a href="{{ post.url | relative_url }}">{{ post.title }}</a></li>
  {% endfor %}
{% else %}
  <li>まだ記事がありません。</li>
{% endif %}
</ul>
