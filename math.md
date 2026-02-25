---
layout: page
title: "Math"
permalink: /math/
---

This is a curated **math column**: practical notes that summarize a whole book into a usable reference.

**Note:** the series below is written as my own study notes from the textbook; it is not a reproduction of the book.

## Series: The Lebesgue–Stieltjes Integral (Carter & van Brunt)

<ol class="series-list">
  {% assign lsi = site.posts | where: "series", "lebesgue-stieltjes-integral" | sort: "chapter" %}
  {% for post in lsi %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      {% if post.chapter %}<span class="series-meta">Chapter {{ post.chapter }}</span>{% endif %}
    </li>
  {% endfor %}
</ol>

## All math posts

<ul class="post-list">
  {% assign math_posts = site.posts | where_exp: "p", "p.categories contains 'math'" %}
  {% for post in math_posts %}
    <li class="post-list-item">
      <a class="post-list-title" href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <div class="post-list-meta">
        <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%Y-%m-%d" }}</time>
        {% if post.series %}
          <span class="dot">·</span>
          <span class="cats">Series: {{ post.series }}</span>
        {% endif %}
      </div>
    </li>
  {% endfor %}
</ul>
