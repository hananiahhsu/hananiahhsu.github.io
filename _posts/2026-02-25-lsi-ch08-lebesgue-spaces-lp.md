---
layout: post
title: "Lebesgue–Stieltjes Integral: Chapter 8 — The Lebesgue Spaces L^p"
date: 2026-02-25 12:10:00 +0800
categories: [math, analysis]
series: lebesgue-stieltjes-integral
chapter: 8
permalink: /math/lebesgue-stieltjes-integral/ch08-lebesgue-spaces-lp/
---

The book now pivots from integration as a numeric operation to integration as a foundation for **function spaces**.

The message: once you have a robust integral, you can treat functions as vectors, define norms, and do analysis with completeness and convergence in a principled way.

## 8.1 Normed spaces

A normed vector space formalizes the idea of “size” and “distance” between vectors.

In analysis, the key is that convergence in norm implies strong control (much stronger than pointwise convergence).

## 8.2 Banach spaces

A Banach space is a complete normed space: every Cauchy sequence converges.

Completeness is not a luxury; it’s what guarantees that limits of approximations stay inside the space.

## 8.3 Completion of spaces

Many naturally occurring spaces are not complete.

Completion is the systematic way to add missing limit points while preserving the metric/norm structure. This is exactly the lens through which L^p spaces are introduced.

## 8.4 The space L¹

L¹ is the space of (equivalence classes of) integrable functions with norm

- ‖f‖₁ = ∫ |f|.

Important idea: functions that differ only on a null set are treated as the same object. This is what makes the norm well-defined and the space well-behaved.

## 8.5 The Lebesgue spaces L^p

Generalizing L¹:

- ‖f‖ₚ = (∫ |f|^p)^{1/p}, 1 ≤ p < ∞
- ‖f‖_∞ = ess sup |f|

The standard inequalities appear here:

- Hölder inequality
- Minkowski inequality

These inequalities are the “algebra” that makes L^p usable: they control products, sums, and limits.

## 8.6 Separable spaces

Separability (existence of a countable dense subset) matters for approximation and for connecting abstract spaces back to computation.

In practice, separability tells you whether you can approximate functions with sequences drawn from a manageable family.

## 8.7 Complex L^p spaces

Same story, but for complex-valued functions. This matters for Fourier analysis and signal-like applications.

## 8.8 Hardy spaces H^p

Hardy spaces are alternative function spaces tuned for complex analysis and boundary behavior.

Even if you don’t use them directly, it’s useful to see that “integrability + structure” produces many different spaces specialized for different problems.

## 8.9 Sobolev spaces W^{k,p}

Sobolev spaces incorporate weak derivatives into the norm.

This is one of the main bridges to PDEs and numerical methods: regularity (smoothness) becomes a measurable property.

## Mental model

Chapter 8 turns “∫” into a geometry:

- a norm defines distance,
- completeness defines stability under limits,
- inequalities define algebraic control.

### Practice checklist

- Prove (or at least apply) Hölder and Minkowski fluently.
- Build intuition for L^p nesting: when does L^q ⊂ L^p hold?
- Get comfortable with “equal a.e.” as an equivalence relation.
