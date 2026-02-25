---
layout: post
title: "Lebesgue–Stieltjes Integral: Chapter 9 — Hilbert Spaces and L²"
date: 2026-02-25 12:40:00 +0800
categories: [math, analysis]
series: lebesgue-stieltjes-integral
chapter: 9
permalink: /math/lebesgue-stieltjes-integral/ch09-hilbert-spaces-l2/
---

If L^p spaces are the general normed/Banach story, L² is the special case where geometry becomes **inner-product geometry**. That extra structure unlocks orthogonality, projections, and Fourier methods.

## 9.1 Hilbert spaces

A Hilbert space is a complete inner product space.

The inner product ⟨f, g⟩ induces the norm:

- ‖f‖ = √⟨f, f⟩

In L², the inner product is typically:

- ⟨f, g⟩ = ∫ f(x) \overline{g(x)} \, dμ(x)

Completeness ensures that orthogonal expansions converge to a limit inside the space.

## 9.2 Orthogonal sets

Orthogonality is the engine for “coordinate systems” in infinite dimensions.

Key working tools:

- orthonormal sets
- Fourier coefficients (projections)
- Pythagorean identity and Bessel-type inequalities

The big idea: with an orthonormal basis, approximation becomes projection onto finite-dimensional subspaces.

## 9.3 Classical Fourier series

Fourier series are presented as the archetype:

- represent a function (in L² sense) as a sum of sines/cosines.

Important nuance:

- convergence is typically in the L² norm (mean-square), not necessarily pointwise.

This is a recurring theme in applied math: “energy convergence” is often the right notion.

## 9.4 The Sturm–Liouville problem

Sturm–Liouville theory produces orthogonal families from differential equations.

Why it belongs here:

- it explains where many classical orthogonal bases come from (eigenfunction expansions)
- it connects functional analysis back to PDE/physics

## 9.5 Other bases for L²

The chapter closes by showing that trigonometric functions are not the only game in town.

Depending on boundary conditions and domains, you may prefer:

- orthogonal polynomials
- eigenfunction systems
- or other structured bases

## Mental model

Hilbert space theory is what makes “least squares,” “best approximation,” and “spectral methods” rigorous.

Once you see L² as a geometric space, many results become intuitive:

- approximation = projection
- error = orthogonal residual
- expansions = coordinates

### Practice checklist

- Compute Fourier coefficients as inner products.
- Practice proving orthogonality and using it to simplify integrals.
- Interpret convergence in L² vs pointwise convergence.
