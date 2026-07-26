---
layout: page
title: "SolidDesigner / Alice"
description: "Architecture direction for the SolidDesigner and Alice parametric CAD platform."
permalink: /projects/
---

<header class="page-hero project-hero">
  <p class="eyebrow">PARAMETRIC CAD PLATFORM</p>
  <h1>SolidDesigner / Alice</h1>
  <p>A modular CAD/BIM platform designed around feature semantics, persistent design intent, robust geometry, and professional interaction behavior.</p>
</header>

<section class="project-thesis">
  <p class="project-thesis-label">DESIGN THESIS</p>
  <blockquote>A CAD system is not a collection of modeling commands. It is a consistent contract between user intent, parametric definitions, persistent references, geometric results, and every edit that follows.</blockquote>
</section>

<section class="content-section">
  <div class="section-heading">
    <div>
      <p class="eyebrow">ARCHITECTURE CONCERNS</p>
      <h2>The platform is organized by stable CAD responsibilities.</h2>
    </div>
  </div>
  <div class="discipline-grid project-grid">
    <article class="discipline-card">
      <span class="discipline-number">01</span>
      <h3>Feature modeling</h3>
      <p>Sketch-driven and reference-driven features with creation, redefinition, regeneration, suppression, and failure behavior aligned with professional parametric CAD.</p>
    </article>
    <article class="discipline-card">
      <span class="discipline-number">02</span>
      <h3>Document model</h3>
      <p>Object identity, persistent references, undoable transactions, versioned serialization, and controlled document evolution.</p>
    </article>
    <article class="discipline-card">
      <span class="discipline-number">03</span>
      <h3>Geometry foundation</h3>
      <p>OCCT-backed B-Rep, topology-aware modeling operations, tolerance management, and mappings between regenerated results.</p>
    </article>
    <article class="discipline-card">
      <span class="discipline-number">04</span>
      <h3>Visualization</h3>
      <p>A structured path from model representation to interactive display, selection, highlighting, and high-performance rendering.</p>
    </article>
  </div>
</section>

<section class="content-section">
  <div class="section-heading">
    <div>
      <p class="eyebrow">PRODUCT STANDARD</p>
      <h2>Feature behavior is defined as an end-to-end contract.</h2>
    </div>
  </div>
  <div class="workflow-line">
    <article><span>01</span><h3>Create</h3><p>Collect valid references and parameters through a professional CAD interaction.</p></article>
    <article><span>02</span><h3>Regenerate</h3><p>Evaluate dependencies and produce topology with controlled failure behavior.</p></article>
    <article><span>03</span><h3>Edit</h3><p>Recover feature meaning, preserve intent, and present consistent redefinition semantics.</p></article>
    <article><span>04</span><h3>Persist</h3><p>Maintain identity and references across save, reopen, upgrade, and downstream use.</p></article>
  </div>
</section>

<section class="closing-panel compact-closing">
  <div>
    <p class="eyebrow">ENGINEERING NOTES</p>
    <h2>Follow the platform as it develops.</h2>
  </div>
  <div>
    <p>Architecture notes, modeling research, and mathematical foundations are published in the technical journal.</p>
    <a class="btn btn-primary" href="{{ '/blog/' | relative_url }}">Browse the journal <span aria-hidden="true">↗</span></a>
  </div>
</section>
