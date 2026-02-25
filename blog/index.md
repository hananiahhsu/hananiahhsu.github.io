---
layout: page
title: "Blog"
permalink: /blog/
---

<ul class="post-list">
  {% for post in site.posts %}
    <li class="post-list-item">
      <a class="post-list-title" href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <div class="post-list-meta">
        <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%Y-%m-%d" }}</time>
        {% if post.categories %}
          <span class="dot">·</span>
          <span class="cats">{{ post.categories | join: ", " }}</span>
        {% endif %}
      </div>
      {% if post.excerpt %}
        <div class="post-list-excerpt">{{ post.excerpt | strip_html | truncate: 220 }}</div>
      {% endif %}
    </li>
  {% endfor %}
</ul>
