---
layout: page
title: Functional Analysis
permalink: /ja/blog/functional-analysis/
lang: ja
---

{% include lang-switch.html %} 
{% include topnav.html %}

<h2>Functional Analysis</h2>
<ul>
{% assign items = site.posts_ja | where_exp: "p", "p.categories contains 'functional-analysis'" | sort: "date" | reverse %}
{% if items.size > 0 %}
  {% for post in items %}
    <li><span class="muted">{{ post.date | date: "%Y-%m-%d" }}</span> — <a href="{{ post.url | relative_url }}">{{ post.title }}</a></li>
  {% endfor %}
{% else %}
  <li>まだ記事がありません。</li>
{% endif %}
</ul>
