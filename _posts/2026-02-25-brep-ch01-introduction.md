---
layout: post
title: "B-Rep Modelling Techniques: Chapter 01 — Introduction"
date: 2026-02-25 14:00:00 +0800
categories: [graphics, geometry, cad]
series: brep-modelling-techniques
chapter: 1
book_title: "Boundary Representation Modelling Techniques"
book_author: "Ian Stroud"
book_year: 2006
permalink: /graphics/brep-modelling-techniques/ch01-introduction/
---

> Study notes for Ian Stroud, *Boundary Representation Modelling Techniques* (Springer, 2006).

This chapter frames **why solid modelling exists** and why “representation choice” dominates everything that comes after: what operations you can do, how robust they are, and how expensive they become.

## What you should get out of Chapter 1

- A mental map of the main representation families used in geometric modelling.
- Why **Boundary Representation (B-Rep)** is a practical centre of gravity for CAD kernels, despite its complexity.
- Why a “solid modeller” is never just geometry: you inevitably grow into **product modelling** (metadata, intent, constraints, manufacturing context).

## Representation families: the trade-space

The book contrasts several ways to represent solids. Each representation is a bundle of choices about:

- **What is stored** (cells, primitives, boundaries…)
- **What is computed** (membership tests, intersections, adjacency…)
- **What operations are “native”** vs. require heavy conversion

### 1) Cell decomposition (spatial subdivision)

Think voxel-like occupancy grids, octrees, BSP trees, etc.:

- Pros: membership (“inside/outside”) is straightforward; Boolean operations can be cheap and robust.
- Cons: geometry accuracy depends on resolution; boundaries are *derived*, not explicit; precise engineering features are hard.

### 2) Sweeping / generative construction

Extrusions, revolutions, generalized sweeps:

- Pros: great for “manufacturing-like” shapes; the construction parameters are meaningful.
- Cons: limited expressiveness without composition; intersections and downstream editing still need a more general representation.

### 3) Set-theoretic / CSG (Constructive Solid Geometry)

Solids as Boolean trees over primitives:

- Pros: compact, parametric, and Boolean operations are conceptually native.
- Cons: you still need boundary evaluation to display, to mesh, to export, and to interoperate; robust evaluation and trimming are nontrivial.

### 4) Boundary representation (B-Rep)

Solids defined by their **bounding surfaces** and a **topological structure** describing adjacency:

- Pros: aligns with what CAD must deliver (faces/edges/vertices), supports local edits, and matches downstream needs (meshing, drawing, manufacturing).
- Cons: requires careful topological invariants, tolerance management, and very disciplined algorithms for trimming/intersection.

## Commercialisation implications

A “research modeller” can tolerate occasional failures; a production CAD kernel cannot. Chapter 1 highlights constraints that become **product requirements**:

- **Robustness:** handle degeneracies, near-coincidence, and tolerance-scale noise.
- **Consistency:** topology must remain valid after every operation (no dangling links, invalid loops, inconsistent orientations).
- **Performance:** users expect interactive modelling; algorithms must be incremental and cached.
- **Interoperability:** import/export and healing become first-class concerns.

## Product modelling preview

The chapter closes by pointing out that geometry is only one slice of “a product”:

- identification and versioning
- assemblies and configurations
- constraints / connections
- process planning and manufacturing intent

**If you’re building your own kernel:** treat B-Rep as the geometric core, but design extension points early for “non-geometric” information to travel with topology.

## Chapter outline (from the book)

**Major sections**
- 1.2 Representations For Solid Modelling
- 1.4 Product Modelling

**Selected subsections**
- 1.2 Representations for solid modelling
- 1.2.1 Cell decomposition
- 1.2.2 General sweeping
- 1.2.3 Set theoretic
- 1.2.4 Boundary representation
- 1.3 Implications for commercialisation
- 1.4 Product modelling

## Implementation checklist

- Decide early on a **separation between topology and geometry** (topo entities reference geometry, not embed it).
- Define explicit rules for **orientation** (face normals, loop directions, coedge directions).
- Define your tolerance model: at minimum *position* and *angle* tolerances, and a strategy for comparisons.
- Make conversions (CSG → B-Rep, sweep → B-Rep) a pipeline, not an afterthought.

## Key vocabulary

- **Solid**: a region of 3D space with an inside/outside.
- **Boundary**: the set of faces that encloses a region.
- **Topology vs geometry**: adjacency/structure vs continuous shape.
- **Trim**: restricting a parametric surface to a bounded face region.
- **Validity**: not just “no crashes”—closed shells, consistent orientations, and coherent trims.

## Practical exercises

1. Take a simple CSG tree (box union cylinder) and list what you must compute to display it as a B-Rep.
2. For an extrusion, identify which parts are “generative” (sweep path and profile) and which become B-Rep entities (side faces, cap faces, edges).
3. Write down your kernel’s *representation boundary*: what must be exact (analytic curves/surfaces) and what can be approximated (render mesh).

## Cross-links

- Chapter 3 turns this representation discussion into concrete datastructures.
- Chapters 6–7 show how representation choices determine algorithm structure and failure modes.
