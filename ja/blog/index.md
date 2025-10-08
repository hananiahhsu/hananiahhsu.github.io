---
layout: page
title: ブログ
permalink: /ja/blog/
lang: ja
---

{% include lang-switch.html %}
{% include topnav.html %}

<ul>
{% assign items = site.posts_ja | sort: 'date' | reverse %}
{% for post in items %}
  <li><span class="muted">{{ post.date | date: "%Y-%m-%d" }}</span> — <a href="{{ post.url | relative_url }}">{{ post.title }}</a></li>
{% endfor %}
</ul>
