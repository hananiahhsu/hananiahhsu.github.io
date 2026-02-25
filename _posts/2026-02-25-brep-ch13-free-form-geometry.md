---
layout: post
title: "B-Rep Modelling Techniques: Chapter 13 — Free-form Geometry"
date: 2026-02-25 18:00:00 +0800
categories: [graphics, geometry, cad]
series: brep-modelling-techniques
chapter: 13
book_title: "Boundary Representation Modelling Techniques"
book_author: "Ian Stroud"
book_year: 2006
permalink: /graphics/brep-modelling-techniques/ch13-free-form-geometry/
---

> Study notes for Ian Stroud, *Boundary Representation Modelling Techniques* (Springer, 2006).

Free-form geometry is where analytic comfort ends. This chapter provides the essential toolkit: Bézier, B-splines, rational forms, and NURBS—plus practical notes on how to build surfaces from curves and patches.

## 1) Basics: curve/surface families

- **Bézier**: intuitive control-point formulation; good for local modelling but global influence for high degree.
- **B-spline**: knot vectors and piecewise polynomials; local control and stability.
- **Rational forms**: represent conics exactly (circles/ellipses) and enable projective behaviour.
- **NURBS**: the workhorse representation for industrial CAD.

## 2) Interpolation and lofting

Real workflows require:

- interpolating curves through points (with continuity constraints)
- lofting surfaces from multiple section curves
- handling mixed constraints (positional, tangency, curvature)

The chapter also discusses the “engineering reality”:
- parameterization choices matter
- continuity conditions are easy to state but hard to satisfy robustly
- input data is noisy

## 3) Handling problems and sculpting methods

Free-form operations can fail due to:
- self-intersections
- oscillations from poor parameterization
- patch mismatch and continuity breaks

“Sculpting” style methods and smoothing are introduced as pragmatic tools:
- adjust control points
- apply fairness energies
- trade accuracy for smoothness

## Chapter outline (from the book)

**Major sections**
- 13.1 Basics
- 13.2 Interpolation
- 13.3 Lofting

**Selected subsections**
- 13.1.1 B ezier geometry
- 13.1.2 B-spline geometry
- 13.1.3 Rational forms
- 13.1.4 NURBS geometry

## Implementation checklist

- Standardize on NURBS as your canonical free-form curve/surface representation.
- Provide utilities:
  - evaluation (point/derivatives)
  - closest point / projection
  - intersection (curve/curve, curve/surface, surface/surface)
  - reparameterization and knot insertion
- Add “quality tools”:
  - curvature plots
  - deviation metrics
  - fairness/smoothing controls

## Free-form geometry: the hidden costs

- evaluation is easy; robust intersection is not
- trimming is where most bugs live
- continuity (G1/G2) is hard to preserve under edits

Invest in good numerical tooling: robust solvers, tolerance-aware predicates, and stable parameterizations.

## Practical exercises

- Fit a NURBS curve to sample points and measure deviation.
- Implement knot insertion and show it preserves the curve shape.
