---
layout: page
title: "Technical Journal"
description: "Technical writing by Hananiah Hsu on CAD architecture, computational geometry, C++, and applied mathematics."
permalink: /blog/
---

<header class="page-hero journal-hero">
  <p class="eyebrow">TECHNICAL JOURNAL</p>
  <h1>Architecture, algorithms, geometry, and mathematical foundations.</h1>
  <p>Working notes written to make design reasoning inspectable—from CAD system responsibilities and B-Rep techniques to analysis and function spaces.</p>
</header>

<div class="journal-summary">
  <div><strong>{{ site.posts | size }}</strong><span>published notes</span></div>
  <div><strong>02</strong><span>curated series</span></div>
  <div><strong>04</strong><span>core disciplines</span></div>
</div>

<section class="journal-archive" aria-label="All journal notes">
  {% for post in site.posts %}
    {% assign current_year = post.date | date: "%Y" %}
    {% if current_year != previous_year %}
      {% unless forloop.first %}</div>{% endunless %}
      <div class="archive-year">
        <h2>{{ current_year }}</h2>
      {% assign previous_year = current_year %}
    {% endif %}
      <article class="archive-row">
        <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%m.%d" }}</time>
        <div>
          <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
          {% if post.categories %}<p>{{ post.categories | join: " · " }}</p>{% endif %}
        </div>
        <a class="archive-arrow" href="{{ post.url | relative_url }}" aria-label="Read {{ post.title }}">↗</a>
      </article>
    {% if forloop.last %}</div>{% endif %}
  {% endfor %}
</section>
