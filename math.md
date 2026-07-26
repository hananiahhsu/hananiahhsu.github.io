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
    <p>A rigorous chapter-by-chapter study of Carter and van Brunt: from the completeness of the real line to measure construction, convergence theorems, L<sup>p</sup> spaces, Hilbert geometry, and gauge integration.</p>
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

<section class="content-section">
  <div class="section-heading">
    <div>
      <p class="eyebrow">EDITORIAL STANDARD</p>
      <h2>Definitions, hypotheses, derivations, and failure cases.</h2>
    </div>
  </div>
  <div class="discipline-grid">
    <article class="discipline-card"><span class="discipline-number">01</span><h3>Precise conventions</h3><p>Every article fixes its measure, interval convention, function space, and convergence mode before using a theorem.</p></article>
    <article class="discipline-card"><span class="discipline-number">02</span><h3>Qualified theorems</h3><p>Results state the necessary measurability, integrability, monotonicity, continuity, and finiteness hypotheses.</p></article>
    <article class="discipline-card"><span class="discipline-number">03</span><h3>Counterexamples</h3><p>Boundary cases show exactly where an interchange of limits, integrals, or summation order ceases to be valid.</p></article>
    <article class="discipline-card"><span class="discipline-number">04</span><h3>Computational meaning</h3><p>Each chapter connects the analytical result to approximation, geometry processing, numerical integration, or simulation.</p></article>
  </div>
</section>

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

<section class="content-section">
  <div class="section-heading">
    <div>
      <p class="eyebrow">PRIMARY REFERENCES</p>
      <h2>Sources used to verify notation and results.</h2>
    </div>
  </div>
  <div class="writing-list">
    <a class="writing-row" href="https://doi.org/10.1007/978-1-4612-1174-7">
      <span class="writing-index">01</span>
      <span><strong>Carter &amp; van Brunt</strong><small>The Lebesgue–Stieltjes Integral: A Practical Introduction</small></span>
      <span class="writing-arrow" aria-hidden="true">↗</span>
    </a>
    <a class="writing-row" href="https://math.mit.edu/~dyatlov/125spring16/">
      <span class="writing-index">02</span>
      <span><strong>MIT 18.125</strong><small>Measure Theory and Analysis lecture materials</small></span>
      <span class="writing-arrow" aria-hidden="true">↗</span>
    </a>
    <a class="writing-row" href="https://dlmf.nist.gov/1.18">
      <span class="writing-index">03</span>
      <span><strong>NIST Digital Library of Mathematical Functions</strong><small>Hilbert spaces, L² spaces, and eigenfunction expansions</small></span>
      <span class="writing-arrow" aria-hidden="true">↗</span>
    </a>
    <a class="writing-row" href="https://arxiv.org/abs/1602.02993">
      <span class="writing-index">04</span>
      <span><strong>Ralph Henstock</strong><small>Lectures on the Theory of Integration</small></span>
      <span class="writing-arrow" aria-hidden="true">↗</span>
    </a>
  </div>
</section>
