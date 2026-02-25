---
layout: post
title: "Lebesgue–Stieltjes Integral: Chapter 10 — Epilogue"
date: 2026-02-25 13:10:00 +0800
categories: [math, analysis]
series: lebesgue-stieltjes-integral
chapter: 10
permalink: /math/lebesgue-stieltjes-integral/ch10-epilogue/
---

The epilogue steps back and answers a natural question:

> If Lebesgue (and Lebesgue–Stieltjes) integration is so powerful, why do people still invent new integrals?

## 10.1 The Lebesgue integral and its successors

Lebesgue integration is a foundation, but it is not the end of the story.

Some later integrals were designed to capture functions that are not Lebesgue integrable while preserving certain calculus identities.

A recurring tension:

- **Generality**: integrate more functions.
- **Structure**: keep familiar theorems (FTC, substitution, etc.).

Pushing one often compromises the other.

## 10.2 “Riemann strikes back”

The chapter discusses integrals that look more “Riemann-like” (partition-based) but are powerful enough to integrate broader classes than the classical Riemann integral.

The general pattern is:

- allow partitions that adapt to the function (gauge-like refinement rules),
- regain strong versions of the Fundamental Theorem of Calculus,
- integrate some derivatives that are not Lebesgue integrable.

These integrals are relevant when your goal is not measure theory but rather **calculus restoration**.

## How to place Lebesgue–Stieltjes in the bigger map

My takeaway from the book’s arc:

- Use **Lebesgue–Stieltjes** when you care about convergence, probability, and functional-analytic structure.
- Look at “successor integrals” when you specifically need stronger calculus identities for pathological objects.

For engineering and applied work, Lebesgue–Stieltjes is often the sweet spot: powerful enough for real analysis and probability, yet concrete enough to compute with (especially when α has a probabilistic interpretation).

### Practice checklist

- Be able to explain *why* Lebesgue beats Riemann (convergence + null sets).
- Be able to explain *why* some gauge integrals beat Lebesgue for derivatives.
- Keep a mental separation between: “integration as area/measure” vs “integration as inverse differentiation.”
