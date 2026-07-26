---
layout: page
title: ""
permalink: /
---

<section class="home-hero">
  <div class="hero-copy">
    <p class="eyebrow">CAD SYSTEMS · COMPUTATIONAL GEOMETRY · APPLIED MATHEMATICS</p>
    <h1>I design computational systems that turn <em>geometry</em> into industrial decisions.</h1>
    <p class="hero-lede">I’m Hananiah Hsu, a C++ and CAD software engineer working across parametric modeling, B-Rep geometry, engineering algorithms, and the mathematical structures beneath reliable industrial software.</p>
    <div class="hero-actions">
      <a class="btn btn-primary" href="{{ '/work/' | relative_url }}">Explore engineering work <span aria-hidden="true">↗</span></a>
      <a class="btn btn-secondary" href="{{ '/blog/' | relative_url }}">Read the technical journal</a>
    </div>
    <div class="hero-facts" aria-label="Areas of practice">
      <div><strong>C++</strong><span>Systems engineering</span></div>
      <div><strong>B-Rep</strong><span>Geometry & topology</span></div>
      <div><strong>CAD / BIM</strong><span>Industrial workflows</span></div>
    </div>
  </div>

  <div class="geometry-stage" aria-label="Abstract parametric geometry visualization">
    <div class="geometry-grid"></div>
    <div class="geometry-orbit orbit-one"></div>
    <div class="geometry-orbit orbit-two"></div>
    <div class="geometry-solid">
      <span class="solid-face face-top"></span>
      <span class="solid-face face-side"></span>
      <span class="solid-face face-front"></span>
    </div>
    <div class="geometry-axis axis-x"><span>X</span></div>
    <div class="geometry-axis axis-y"><span>Y</span></div>
    <div class="geometry-caption">
      <span>PARAMETRIC SYSTEM</span>
      <span>DESIGN INTENT → REGENERATED FORM</span>
    </div>
  </div>
</section>

<section class="signal-strip" aria-label="Professional focus">
  <span>Feature-based modeling</span>
  <span>Robust topology</span>
  <span>Optimization</span>
  <span>Scientific computing</span>
  <span>Engineering automation</span>
</section>

<section class="content-section">
  <div class="section-heading">
    <div>
      <p class="eyebrow">SELECTED WORK</p>
      <h2>Systems built around demanding engineering problems.</h2>
    </div>
    <a class="text-link" href="{{ '/work/' | relative_url }}">View all work →</a>
  </div>

  <div class="work-grid">
    <article class="feature-card feature-card-wide">
      <div class="card-index">01 / PLATFORM ENGINEERING</div>
      <div class="feature-card-body">
        <div>
          <p class="work-label">SolidDesigner / Alice</p>
          <h3>A parametric CAD platform shaped by design intent.</h3>
          <p>Architecture for feature creation and editing, persistent document identity, B-Rep generation, selection, interaction, and high-performance visualization.</p>
        </div>
        <ul class="compact-list">
          <li>Parametric feature history</li>
          <li>OCCT geometry integration</li>
          <li>Document transactions</li>
          <li>Commercial CAD interaction</li>
        </ul>
      </div>
      <a class="card-link" href="{{ '/projects/' | relative_url }}" aria-label="Read about SolidDesigner and Alice">Platform notes <span>↗</span></a>
    </article>

    <article class="feature-card feature-card-accent">
      <div class="card-index">02 / INDUSTRIAL SOFTWARE</div>
      <p class="work-label">Tusyndon · 图随形动</p>
      <h3>CAD, manufacturing data, and BIM workflows.</h3>
      <p>Professional work spanning engineering drawing automation, PMI/MBD review, assembly architecture, nesting optimization, pressure-vessel engineering, and IFC data workflows.</p>
      <a class="card-link" href="{{ '/work/' | relative_url }}#tusyndon">Explore Tusyndon work <span>↗</span></a>
    </article>
  </div>
</section>

<section class="content-section discipline-section">
  <div class="section-heading">
    <div>
      <p class="eyebrow">ENGINEERING DISCIPLINES</p>
      <h2>Depth at the intersection of four fields.</h2>
    </div>
  </div>

  <div class="discipline-grid">
    <article class="discipline-card">
      <span class="discipline-number">01</span>
      <h3>CAD systems</h3>
      <p>Feature semantics, regeneration, document identity, transactions, selection, commands, and production interaction design.</p>
    </article>
    <article class="discipline-card">
      <span class="discipline-number">02</span>
      <h3>Computational geometry</h3>
      <p>B-Rep topology, Euler operators, free-form geometry, robust modeling operations, and geometric representation.</p>
    </article>
    <article class="discipline-card">
      <span class="discipline-number">03</span>
      <h3>Industrial algorithms</h3>
      <p>Nesting, rule validation, engineering data extraction, comparison, and automation that produce measurable workflow outcomes.</p>
    </article>
    <article class="discipline-card">
      <span class="discipline-number">04</span>
      <h3>Applied mathematics</h3>
      <p>Real analysis, measure and integration, function spaces, approximation, and the mathematical reasoning behind numerical systems.</p>
    </article>
  </div>
</section>

<section class="content-section">
  <div class="section-heading">
    <div>
      <p class="eyebrow">TECHNICAL JOURNAL</p>
      <h2>Writing that exposes the reasoning, not only the result.</h2>
    </div>
    <a class="text-link" href="{{ '/blog/' | relative_url }}">All {{ site.posts | size }} notes →</a>
  </div>

  <div class="journal-grid">
    {% assign latest = site.posts | slice: 0, 6 %}
    {% for post in latest %}
    <article class="journal-card">
      <div class="journal-meta">
        <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%Y.%m.%d" }}</time>
        {% if post.categories %}<span>{{ post.categories | first }}</span>{% endif %}
      </div>
      <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
      {% if post.excerpt %}
      <p>{{ post.excerpt | strip_html | truncate: 150 }}</p>
      {% endif %}
      <a class="journal-arrow" href="{{ post.url | relative_url }}" aria-label="Read {{ post.title }}">↗</a>
    </article>
    {% endfor %}
  </div>
</section>

<section class="closing-panel">
  <div>
    <p class="eyebrow">INDUSTRIAL COLLABORATION</p>
    <h2>Complex geometry deserves precise engineering.</h2>
  </div>
  <div>
    <p>I work on CAD architecture, engineering algorithms, and industry-specific software where correctness, performance, and design intent matter.</p>
    <a class="btn btn-primary" href="mailto:{{ site.email }}">Start a technical conversation <span aria-hidden="true">↗</span></a>
  </div>
</section>
