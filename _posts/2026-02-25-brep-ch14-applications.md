---
layout: post
title: "B-Rep Modelling Techniques: Chapter 14 — Applications"
date: 2026-02-25 18:20:00 +0800
categories: [graphics, geometry, cad]
series: brep-modelling-techniques
chapter: 14
book_title: "Boundary Representation Modelling Techniques"
book_author: "Ian Stroud"
book_year: 2006
permalink: /graphics/brep-modelling-techniques/ch14-applications/
---

> Study notes for Ian Stroud, *Boundary Representation Modelling Techniques* (Springer, 2006).

This chapter is a survey of “what a modeller must do in the real world”: verification, healing, format conversion, and downstream computations.

## 1) Model verification

Verification is the discipline of proving your model is internally consistent:

- topological checks (closure, orientation, manifoldness where required)
- geometric checks (curve/surface consistency, trims within tolerance)
- intersection checks (self-intersections, invalid overlaps)

The book contrasts how different systems approach verification, highlighting that it’s not just a function—it’s a workflow and a toolchain.

## 2) Model healing

Healing is the practical complement to verification:

- assembly healing (aligning and fixing component relationships)
- topological healing (fixing broken adjacency, missing loops, inconsistent use entities)
- geometric healing (rebuilding curves/surfaces, smoothing, retolerancing)
- combined healing strategies (because geometry and topology errors interact)

Healing policy is part of your product identity: aggressive healing can surprise users; conservative healing can leave unusable models.

## 3) Recreating a B-Rep from an STL file

This is a classic hard problem:

- STL gives triangles, not analytic faces.
- You must segment the mesh, fit surfaces, and rebuild topology.
- The result is rarely perfect; you need tolerances, snapping, and verification.

## 4) Rapid prototyping, reverse engineering, and computation

The chapter also discusses:
- using models for prototyping workflows
- reverse engineering pipelines
- computing volume
- tetrahedral decomposition (bridge to FEM/CAE)
- patterns (repeated features/instances)

## Chapter outline (from the book)

**Major sections**
- 14.1 Model Verification
- 14.4 Recreating A B-Rep From An Stl File

**Selected subsections**
- 14.1.1 Justification
- 14.1.2 Verifications
- 14.1.3 Model verification in ACIS

## Implementation checklist

- Treat verification/healing as a first-class module, not a debug-only add-on.
- Provide “diagnostics output”:
  - what failed, where, and with what tolerance
- Build conversion tools:
  - B-Rep ↔ mesh pipelines with controlled deviation
- For volume and tetrahedralization:
  - ensure solids are watertight
  - provide fallback strategies when not watertight

## Verification + healing: make it user-facing

Industrial CAD exposes healing tools because imports are messy:

- show diagnostics
- allow controlled healing steps
- keep audit logs of changes

## Practical exercises

- Implement a topology validation report:
  - list invalid faces/loops
  - count self-intersections
  - output a “repair suggestion” list (even if manual)
