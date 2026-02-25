---
layout: page
title: ""
permalink: /
---

<div class="hero">
  <h1 class="hero-title">Engineering notes on CAD, geometry, and applied mathematics.</h1>
  <p class="hero-subtitle">I build <strong>SolidDesigner/Alice</strong> (a modular CAD/BIM platform) and write down the architecture, algorithms, and tools that make it work.</p>

  <div class="hero-cta">
    <a class="btn" href="/blog/">Read the blog</a>
    <a class="btn btn-ghost" href="/math/">Math column</a>
  </div>
</div>

## What you'll find here

- **CAD platform architecture**: plugins, commands, interaction graphs, document & storage, rendering pipelines.
- **Geometry kernel notes**: B-Rep fundamentals, OCCT, robust modeling concerns.
- **Math for engineers**: practical real analysis / integration / function spaces.

## Latest posts

<ul class="post-grid">
  {% assign latest = site.posts | slice: 0, 6 %}
  {% for post in latest %}
  <li class="post-card">
    <a class="post-card-title" href="{{ post.url | relative_url }}">{{ post.title }}</a>
    <div class="post-card-meta">
      <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%Y-%m-%d" }}</time>
      {% if post.categories %}
        <span class="dot">·</span>
        <span class="cats">{{ post.categories | join: ", " }}</span>
      {% endif %}
    </div>
    {% if post.excerpt %}
      <div class="post-card-excerpt">{{ post.excerpt | strip_html | truncate: 140 }}</div>
    {% endif %}
  </li>
  {% endfor %}
</ul>

<div class="section-links">
  <a href="/blog/">All posts →</a>
</div>
