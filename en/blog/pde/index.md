---
layout: page
title: PDE
permalink: /en/blog/pde/
lang: en
---

{% include lang-switch.html %} 
{% include topnav.html %}

<h2>PDE</h2>
<ul>
{% assign items = site.posts_en | where_exp: "p", "p.categories contains 'pde'" | sort: "date" | reverse %}
{% if items.size > 0 %}
  {% for post in items %}
    <li><span class="muted">{{ post.date | date: "%Y-%m-%d" }}</span> — <a href="{{ post.url | relative_url }}">{{ post.title }}</a></li>
  {% endfor %}
{% else %}
  <li>No posts yet.</li>
{% endif %}
</ul>
