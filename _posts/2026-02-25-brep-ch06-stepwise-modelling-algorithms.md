---
layout: post
title: "B-Rep Modelling Techniques: Chapter 06 — Stepwise Modelling Algorithms"
date: 2026-02-25 15:40:00 +0800
categories: [graphics, geometry, cad]
series: brep-modelling-techniques
chapter: 6
book_title: "Boundary Representation Modelling Techniques"
book_author: "Ian Stroud"
book_year: 2006
permalink: /graphics/brep-modelling-techniques/ch06-stepwise-modelling-algorithms/
---

> Study notes for Ian Stroud, *Boundary Representation Modelling Techniques* (Springer, 2006).

This is one of the most important chapters for kernel builders: it lays out “stepwise” algorithms for complex modelling operations, especially **Boolean operations** and a family of shape-editing operators.

## 1) Boolean operations: the canonical hard problem

A B-Rep Boolean (union / intersection / difference) is not one algorithm; it is a pipeline:

1. **Find interactions** between the two objects (candidate intersecting face pairs).
2. **Compute intersections** of surfaces and build intersection curves.
3. **Build intersection boundaries** as topological entities (edges/coedges, loop fragments).
4. **Classify regions** (inside/outside) and decide what to keep.
5. **Merge and rebuild shells** with consistent orientations and valid loops.
6. **Heal and simplify** (remove tiny edges/faces, merge coincident geometry within tolerance).

The book emphasizes that the success of Booleans depends heavily on:
- data structures that allow fast adjacency updates
- robust intersection computation and curve management
- well-defined tolerance and coincidence rules

## 2) Stepwise operators beyond Booleans

A “commercial modeller” needs far more than Booleans. The chapter covers (conceptually) operations such as:

- sweeping wireframes / edges to create surfaces and solids
- reflecting models
- bending and sheet-thickening workflows
- planar sectioning
- imprinting (projecting / embedding curves and splitting faces)
- dual constructions (building a dual/topological counterpart)
- setting/replacing a face’s underlying surface
- drafting and taper-like modifications
- gluing/joining operations (coincident topology, non-matching face joins)

The unifying pattern is stepwise construction:
- do simple, verifiable transformations
- maintain topology coherence at each step
- validate aggressively

## Chapter outline (from the book)

**Major sections**
- 6.1 Boolean Operations
- 6.3 Sweeping Wireframe Models

**Selected subsections**
- 6.1 Boolean operations
- 6.1.1 Finding the Boolean interactions
- 6.1.2 Special cases in intersection boundary creation
- 6.1.3 Creating the intersection boundary
- 6.1.4 Merging the objects (creating new shells)

## Practical implementation notes

### Boolean “engineering checklist”
- broad-phase filtering: bounding boxes / spatial indices for face candidates
- robust curve/surface intersection with tolerance-aware stitching
- consistent creation of new edges and trimming curves
- region classification: point-in-solid tests + topological propagation
- deterministic healing rules (sliver removal, edge merging)

### Operator design rule
Every operator should expose:
- **inputs** (selected topology + parameters)
- **preconditions** (what must be true)
- **modifications** (created/deleted entities)
- **postconditions** (what must be validated)

## Suggested test suite

- Simple primitives (box ⊕ cylinder, etc.)
- Tangential cases (cylinder union cylinder with tangency)
- Nearly coincident faces within tolerance
- Thin-sheet cases (bends and thickness)
- Imprint on high-curvature surfaces
- Randomized fuzz tests with validation after each operation

## Boolean operations: a deeper checklist

**Intersection stage**
- candidate face-pair filtering (BVH / AABB trees)
- surface/surface intersection (produce intersection curves)
- curve/face trimming (clip intersection curves to face domains)

**Topology build stage**
- split existing edges where intersection hits
- insert new intersection edges into both operands
- rebuild loops and face boundaries

**Classification stage**
- classify regions via point-in-solid tests (with tolerance)
- propagate classification through adjacency to avoid redundant tests

**Merge stage**
- stitch coincident edges/vertices (tolerance clustering)
- delete discarded regions
- ensure shell orientation and closure

## Failure modes to design for

- tangential intersections (curve multiplicity, unstable trimming)
- near-coincident faces (classification ambiguity)
- extremely thin slivers (numerically unstable)
- self-intersections introduced by offsets/thickening

## Practical exercises

- Implement a “debug dump” for booleans:
  - export intersection curves
  - color faces by classification (keep/discard)
  - list created/deleted entity IDs
