---
layout: post
title: "Lebesgue–Stieltjes Integral: Chapter 1 — Real Numbers"
date: 2026-02-25 09:00:00 +0800
categories: [math, analysis]
series: lebesgue-stieltjes-integral
chapter: 1
permalink: /math/lebesgue-stieltjes-integral/ch01-real-numbers/
---

This book starts *before* integration, because Lebesgue-style arguments lean heavily on the structure of the real line and on limiting processes.

## 1) Dense sets: rationals and irrationals

Two facts that keep resurfacing:

- Between any two real numbers **a < b**, there exist **both** a rational and an irrational number.
- In fact, there are **infinitely many** of each between *any* two reals.

Why this matters: density is what makes “arbitrarily fine approximation” possible. Later, step functions approximate measurable functions by carving the domain into small intervals; density ensures those partitions behave as expected.

## 2) Countable vs. uncountable

The chapter reminds you of a hierarchy:

- **ℕ**, **ℤ**, **ℚ** are *countable* (their elements can be listed as a sequence).
- Any nontrivial real interval, e.g. **(0, 1)**, is *uncountable*.

A practical takeaway you’ll use later: **countable sets are “small”** in measure theory. In Lebesgue integration, countable sets typically become *null sets* under reasonable measures, so changing a function on such a set doesn’t affect integrals.

## 3) The extended real line

It’s convenient to work with

- **ℝₑ = ℝ ∪ {+∞, −∞}**

and allow intervals like **(−∞, b]** or **(a, +∞)**.

This is not just notation. It keeps statements uniform when you later define measures and integrals on *arbitrary* intervals, not only closed bounded ones.

## 4) Supremum and infimum

A key completeness property is packaged as:

- Every nonempty subset of **ℝₑ** has a **least upper bound** (supremum) and a **greatest lower bound** (infimum).

Two patterns to internalize:

- **sup S** may or may not belong to **S**.
- When **sup S** is finite, it can be characterized by the “ε-approximation” condition: for every **ε > 0**, there exists **x ∈ S** with **sup S − ε < x ≤ sup S**.

This “for every ε, exists x” template is the same logical shape you’ll see later in:

- definitions of limits,
- definitions of integrals via approximation,
- convergence theorems.

## Mental model for later chapters

If you want a one-line bridge to integration:

> **Integration is controlled approximation, and controlled approximation is powered by completeness + limits.**

Lebesgue–Stieltjes theory will generalize “length” to a *measure* defined via a monotone function α. This only works smoothly when the underlying number system supports sup/inf, one-sided limits, and carefully defined intervals.

### Practice checklist

Before moving on, make sure you can do these quickly:

- Use density to find rationals/irrationals inside arbitrary intervals.
- Prove basic countability facts (unions, images under simple maps).
- Compute **sup/inf** for simple sets and verify the ε-characterization.
