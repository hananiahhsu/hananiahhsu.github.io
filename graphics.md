---
layout: page
title: "Graphics"
permalink: /graphics/
---

This column is for **computer graphics / CAD geometry / modelling** notes: robust representations, topology, modelling operators,
visualization, and the engineering details that make CAD systems reliable.

## Series: Boundary Representation Modelling Techniques (Ian Stroud)

<ol class="series-list">
  {% assign brep = site.posts | where: "series", "brep-modelling-techniques" | sort: "chapter" %}
  {% for post in brep %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      {% if post.chapter %}<span class="series-meta">Chapter {{ post.chapter }}</span>{% endif %}
    </li>
  {% endfor %}
</ol>

## All graphics posts

<ul class="post-list">
  {% assign gfx_posts = site.posts | where_exp: "p", "p.categories contains 'graphics'" %}
  {% for post in gfx_posts %}
    <li class="post-list-item">
      <a class="post-list-title" href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <div class="post-list-meta">
        <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%Y-%m-%d" }}</time>
        {% if post.categories %}
          <span class="post-cats">
            {% for c in post.categories %}
              <span class="tag">{{ c }}</span>
            {% endfor %}
          </span>
        {% endif %}
      </div>
    </li>
  {% endfor %}
</ul>
