---
layout: post
title: "B-Rep Modelling Techniques: Chapter 10 — Graphics"
date: 2026-02-25 17:00:00 +0800
categories: [graphics, geometry, cad]
series: brep-modelling-techniques
chapter: 10
book_title: "Boundary Representation Modelling Techniques"
book_author: "Ian Stroud"
book_year: 2006
permalink: /graphics/brep-modelling-techniques/ch10-graphics/
---

> Study notes for Ian Stroud, *Boundary Representation Modelling Techniques* (Springer, 2006).

A modeller that cannot *show* results predictably is not usable. This chapter is about the geometry-to-graphics bridge: from B-Rep to what users see.

## Two graphics worlds: model-space vs device-space

### Model-space graphics

Operate in model coordinates:

- drawing edges and curves directly from analytic geometry
- computing silhouettes and apparent contours
- hidden line / visible line classification

Model-space rendering is precise but computationally heavier.

### Device-space graphics

Operate after projection to screen:

- faster raster-space decisions
- more aligned with real-time rendering pipelines
- depends on tessellation / faceting for performance

## Key tasks covered

- drawing styles (line types, thickness, emphasis)
- view coordinate systems and transformations
- drawing all edges in a body
- drawing edges and silhouettes (and deciding visibility)
- hidden line removal (conceptually)
- ray tracing as a reference method (for correctness)
- faceting: producing triangle meshes from analytic surfaces
- drawing free-standing geometry (datums, reference curves)
- drawing non-geometric information (annotations, feature markers)

## Chapter outline (from the book)

**Major sections**
- 10.1 Model-Space Graphics
- 10.2 Device-Space Graphics
- 10.3 Facetting An Object
- 10.4 Drawing Free-Standing Geometry
- 10.5 Drawing Non-Geometric Information

**Selected subsections**
- 10.1 Model-space graphics
- 10.1.1 Drawing styles
- 10.1.2 Viewing coordinate system and model transformation
- 10.1.3 Drawing all edges in a body
- 10.1.4 Drawing edges and silhouettes

## Implementation notes (if you build CAD UI)

- Maintain two representations:
  - **exact B-Rep** for modelling and interrogation
  - **render meshes** for interaction
- Use stable IDs to map selection:
  - screen pick → triangle → face/edge ID
- Hidden line / section view correctness typically needs model-space reasoning (or hybrid).
- Faceting quality must be controllable (chordal deviation, angular deviation) and cached per view.

## A practical test plan

- silhouette correctness on cylinders/torii/fillets
- hidden line results on nested shells
- robustness under extreme zoom (tolerance vs pixel)
- consistency of selection on tessellated faces (no “jumping” IDs)

## The selection problem ties graphics back to topology

Users select what they see; the kernel stores topology:

- pick on a triangle mesh → must map to a face/edge reliably
- highlight/hover → must be fast and stable
- hidden line and silhouette views → must reflect exact geometry, not tessellation artifacts

Design your graphics layer with explicit “pick IDs” and with cached tessellation per face.

## Practical exercises

- Implement face tessellation caching keyed by:
  - face ID
  - view-dependent deviation parameters
