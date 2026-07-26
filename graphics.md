---
layout: page
title: "Computational Geometry"
description: "B-Rep modeling, topology, geometric algorithms, feature modeling, and CAD graphics engineering."
permalink: /graphics/
---

<header class="page-hero geometry-hero">
  <p class="eyebrow">COMPUTATIONAL GEOMETRY</p>
  <h1>Topology, geometry, and the machinery of CAD.</h1>
  <p>A structured study of boundary representation, modeling operators, features, product models, free-form geometry, and the path from mathematical shape to interactive engineering object.</p>
</header>

<section class="series-intro">
  <div>
    <p class="eyebrow">CURATED SERIES</p>
    <h2>Boundary Representation Modelling Techniques</h2>
    <p>A systematic reading of Ian Stroud’s work, translated into practical concerns for modern CAD architecture and geometric software.</p>
  </div>
  <div class="series-stat">
    {% assign brep = site.posts | where: "series", "brep-modelling-techniques" | sort: "chapter" %}
    <strong>{{ brep | size }}</strong>
    <span>chapters</span>
  </div>
</section>

<ol class="chapter-grid geometry-chapters">
  {% for post in brep %}
    <li>
      <a href="{{ post.url | relative_url }}">
        <span class="chapter-number">{% if post.chapter < 10 %}0{% endif %}{{ post.chapter }}</span>
        <span class="chapter-title">{{ post.title | split: "— " | last }}</span>
        <span class="chapter-arrow" aria-hidden="true">↗</span>
      </a>
    </li>
  {% endfor %}
</ol>

<section class="content-section geometry-map">
  <div class="section-heading">
    <div>
      <p class="eyebrow">KNOWLEDGE MAP</p>
      <h2>From topological validity to design intent.</h2>
    </div>
  </div>
  <div class="workflow-line">
    <article><span>01</span><h3>Represent</h3><p>Vertices, edges, loops, faces, shells, regions, and their topological relationships.</p></article>
    <article><span>02</span><h3>Operate</h3><p>Euler operations, stepwise modeling algorithms, Booleans, blends, and transformations.</p></article>
    <article><span>03</span><h3>Interpret</h3><p>Product semantics, feature recognition, parametric definitions, and persistent meaning.</p></article>
    <article><span>04</span><h3>Present</h3><p>Tessellation, display structures, selection, interaction, and engineering visualization.</p></article>
  </div>
</section>
