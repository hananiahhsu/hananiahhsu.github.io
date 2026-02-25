---
layout: post
title: "B-Rep Modelling Techniques: Chapter 03 — Datastructures and Tools"
date: 2026-02-25 14:40:00 +0800
categories: [graphics, geometry, cad]
series: brep-modelling-techniques
chapter: 3
book_title: "Boundary Representation Modelling Techniques"
book_author: "Ian Stroud"
book_year: 2006
permalink: /graphics/brep-modelling-techniques/ch03-datastructures-tools/
---

> Study notes for Ian Stroud, *Boundary Representation Modelling Techniques* (Springer, 2006).

This chapter is the engineering heart of the book: it spells out the **entity graph** and the toolbelt required to make B-Rep modelling practical.

## The core message

A boundary model is not “faces + edges”. It is a **connected, navigable datastructure** that must support:

- fast adjacency and incidence queries
- mutation while preserving invariants
- attribute storage (features, constraints, IDs)
- multiple representations (wireframe/sheet/solid) and conversions

## 1) Modelling datastructures: topology + geometry

A clean kernel separates:

- **Topology:** vertex/edge/loop/face/shell/body, plus the directed “use” entities (e.g., coedges) that encode orientation.
- **Geometry:** curves and surfaces, plus parameter-space trimming data.

Key implementation principle:

- topology references geometry (and vice versa only via weak references or queries), so you can swap geometry representations, cache evaluations, and avoid circular ownership.

## 2) Topological connections

The book emphasizes explicit links (pointers/handles/indices) between:

- vertex ↔ incident edges
- edge ↔ its two directed uses (or a ring of uses in non-manifold cases)
- face ↔ boundary loops ↔ coedges
- shell ↔ its faces
- body ↔ its shells

This is what makes operations feasible: most algorithms are “walk a neighbourhood, split/merge a few elements, update links, verify”.

## 3) Modelling facilities: traversal and utilities

A real modeller needs a standard library of navigation and queries:

- traverse all related elements (closure of adjacency)
- single-step traversals (next coedge, adjacent face across edge, etc.)
- topological utilities (orientation fixes, loop rebuilds, consistency checks)
- geometric interrogations (normals, curvature, projections, closest points)
- general utilities (markers/flags, temporary sets, hashing/ID maps)

The important architectural point: **operators should not reimplement traversal logic**. You want a stable, tested set of traversal primitives and utilities that every operator uses.

## 4) Assembly structures (bridge to product modelling)

Even at the B-Rep level, the system must understand assemblies:

- instance handling (same part reused with transforms)
- constraints / connections
- mechanism libraries (for motion/kinematics)

This hints at a dual-view of data:

- geometric-topological core for parts
- higher-level graph for assemblies and constraints

## Chapter outline (from the book)

**Major sections**
- 3.1 Modelling Datastructures
- 3.2 Topological Connections
- 3.3 Modelling Facilities

**Selected subsections**
- 3.1.1 Open questions
- 3.1.2 Elements of the datastructure
- 3.1.3 Geometry
- 3.1.4 Arbitrary representations

## A “kernel implementer’s” checklist

- Define your entity set explicitly and freeze it early.
- Provide traversal APIs for:
  - vertex → incident edges
  - edge → adjacent faces
  - face → loops → coedges → edges → vertices
  - body/shell closures
- Provide mutation utilities:
  - create/delete with ownership rules
  - split/merge edges
  - split faces with a curve
  - rebuild loops after trimming changes
- Add verification:
  - every operator ends with `ValidateTopology()` and `ValidateGeometry()` (and fails loudly in debug).

## A canonical B-Rep entity set (implementation-oriented)

Many kernels converge on a small set of topological entities:

- **Vertex**: point location (often via tolerance cluster).
- **Edge**: bounded curve segment; usually referenced by *two* vertices.
- **Coedge / Half-edge**: a directed use of an edge on a face loop.
- **Loop**: a cyclic list of coedges bounding a face.
- **Face**: a trimmed surface + one outer loop (and possibly inner loops/holes).
- **Shell**: an oriented set of faces.
- **Body**: one or more shells (outer + inner voids).

Even if your naming differs, the functional roles are the same.

## Geometry side: what you need beyond curves/surfaces

For production behaviour, geometry needs:

- parameter-space curves (p-curves) for trimming
- robust evaluation (point, derivatives, normals)
- intersection and projection tools
- caching and acceleration structures

## Common failure modes

- Edge endpoints drift away from vertex positions (tolerance mismatch).
- Loops are not closed in parametric space even if they appear closed in 3D.
- Orientation is inconsistent after local edits (coedge directions wrong).
- Deleting entities leaves dangling references (ownership unclear).

## Practical exercises

- Implement a traversal: given a face, visit all adjacent faces across its boundary edges.
- Implement a validation pass:
  - for each loop: check cyclic closure and coedge consistency
  - for each face: check that trims lie on the surface within tolerance
