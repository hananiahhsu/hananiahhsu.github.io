---
layout: page
title: "Applied Mathematics"
description: "Study notes in real analysis, measure and integration, function spaces, and the mathematics behind engineering computation."
permalink: /math/
---

<header class="page-hero math-hero">
  <p class="eyebrow">APPLIED MATHEMATICS</p>
  <h1>Mathematical structure for computational engineering.</h1>
  <p>Notes on analysis, integration, function spaces, approximation, and the ideas that make numerical and geometric systems understandable.</p>
  <div class="formula-line" aria-hidden="true">
    <span>∫ f dα</span>
    <span>‖f‖<sub>p</sub></span>
    <span>⟨f, g⟩</span>
    <span>L²(μ)</span>
  </div>
</header>

<section class="series-intro">
  <div>
    <p class="eyebrow">CURATED SERIES</p>
    <h2>The Lebesgue–Stieltjes Integral</h2>
    <p>A chapter-by-chapter engineering study of Carter and van Brunt: from the real numbers and Riemann integration to measure, L<sup>p</sup> spaces, Hilbert spaces, and approximation.</p>
  </div>
  <div class="series-stat">
    {% assign lsi = site.posts | where: "series", "lebesgue-stieltjes-integral" | sort: "chapter" %}
    <strong>{{ lsi | size }}</strong>
    <span>chapters</span>
  </div>
</section>

<ol class="chapter-grid">
  {% for post in lsi %}
    <li>
      <a href="{{ post.url | relative_url }}">
        <span class="chapter-number">{% if post.chapter < 10 %}0{% endif %}{{ post.chapter }}</span>
        <span class="chapter-title">{{ post.title | split: "— " | last }}</span>
        <span class="chapter-arrow" aria-hidden="true">↗</span>
      </a>
    </li>
  {% endfor %}
</ol>

<section class="content-section math-context">
  <div class="section-heading">
    <div>
      <p class="eyebrow">ENGINEERING CONNECTION</p>
      <h2>Why this mathematics matters.</h2>
    </div>
  </div>
  <div class="discipline-grid">
    <article class="discipline-card"><span class="discipline-number">01</span><h3>Approximation</h3><p>Projection, bases, norms, and convergence clarify what an algorithm preserves and how error should be measured.</p></article>
    <article class="discipline-card"><span class="discipline-number">02</span><h3>Numerical methods</h3><p>Integration and function spaces give finite computations a rigorous relationship to continuous problems.</p></article>
    <article class="discipline-card"><span class="discipline-number">03</span><h3>Geometry processing</h3><p>Continuity, parameterization, measure, and transformations shape reliable geometric representations.</p></article>
    <article class="discipline-card"><span class="discipline-number">04</span><h3>Simulation</h3><p>Hilbert-space geometry and variational ideas underlie least squares, spectral methods, and many engineering solvers.</p></article>
  </div>
</section>
