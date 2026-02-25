---
layout: post
title: "Lebesgue–Stieltjes Integral: Chapter 3 — The Riemann Integral"
date: 2026-02-25 09:40:00 +0800
categories: [math, analysis]
series: lebesgue-stieltjes-integral
chapter: 3
permalink: /math/lebesgue-stieltjes-integral/ch03-riemann-integral/
---

This chapter revisits the Riemann integral in a way that sets up the motivation for Lebesgue–Stieltjes: Riemann integration is intuitive, but it fails exactly where modern analysis needs stability.

## 3.1 Definition of the integral

The Riemann integral is introduced via partitions and step-function bounds:

- lower sums approximate from below,
- upper sums approximate from above,
- integrability means the gap between them can be made arbitrarily small.

A good conceptual point: the Riemann integral approximates the “area under the graph” by chopping the **domain** into subintervals.

## 3.2 Improper integrals

The chapter emphasizes how extending Riemann integration beyond closed bounded intervals requires *extra conventions* (limits at endpoints or infinity).

Two important warnings:

- Continuity on a semiopen interval does **not** guarantee the improper integral exists.
- Conditional convergence is fragile: ∫ f may converge while ∫ |f| diverges.

A canonical example is the oscillatory integral of sin(x)/x over an unbounded interval: it converges conditionally but is not absolutely convergent.

## 3.3 A nonintegrable function

Here the book highlights a function that defeats Riemann’s approach (the details vary by text, but the pattern is the same):

- the function oscillates “too much” on every interval,
- any domain-partition-based approximation cannot pin down a single limit.

This is the first punchline:

> **Riemann integration is sensitive to the behavior of a function on complicated sets, and it is not stable under the limiting operations that analysis wants to perform.**

## What changes in Lebesgue’s approach

Lebesgue integration flips the approximation viewpoint:

- Instead of partitioning the **domain** (x-axis), it groups points by the **values** of the function (y-axis).
- It replaces “length of subintervals” with a generalized notion of size: **measure**.

The rest of the book can be seen as designing the smallest amount of measure theory needed to make that shift practical.

### Practice checklist

- Work fluently with upper/lower sums and integrability criteria.
- Classify improper integrals as absolute vs conditional.
- Internalize why “domain partitions” can’t control highly discontinuous functions.
