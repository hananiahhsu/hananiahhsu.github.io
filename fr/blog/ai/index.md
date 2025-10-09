---
layout: page
title: IA
permalink: /fr/blog/ai/
lang: fr
---

{% include lang-switch.html %} 
{% include topnav.html %}

<h2>IA</h2>
<ul>
{% assign items = site.posts_fr | where_exp: "p", "p.categories contains 'ai'" | sort: "date" | reverse %}
{% if items.size > 0 %}
  {% for post in items %}
    <li><span class="muted">{{ post.date | date: "%Y-%m-%d" }}</span> — <a href="{{ post.url | relative_url }}">{{ post.title }}</a></li>
  {% endfor %}
{% else %}
  <li>Aucun article pour le moment.</li>
{% endif %}
</ul>
