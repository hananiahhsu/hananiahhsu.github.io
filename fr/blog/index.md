---
layout: page
title: Blog
permalink: /fr/blog/
lang: fr
---

{% include lang-switch.html %}
{% include topnav.html %}

<ul>
{% assign items = site.posts_fr | sort: 'date' | reverse %}
{% for post in items %}
  <li><span class="muted">{{ post.date | date: "%Y-%m-%d" }}</span> — <a href="{{ post.url | relative_url }}">{{ post.title }}</a></li>
{% endfor %}
</ul>
