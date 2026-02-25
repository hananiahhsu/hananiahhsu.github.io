---
layout: post
title: "Lebesgue–Stieltjes Integral: Chapter 6 — Integral Calculus"
date: 2026-02-25 11:10:00 +0800
categories: [math, analysis]
series: lebesgue-stieltjes-integral
chapter: 6
permalink: /math/lebesgue-stieltjes-integral/ch06-integral-calculus/
---

Up to Chapter 5, the Lebesgue–Stieltjes integral is a *definition* with good abstract properties. Chapter 6 turns it into a **computational tool**: how do you actually evaluate integrals and do calculus with them?

## 6.1 Evaluation of integrals

The practical theme is that Stieltjes measures can have both:

- a **continuous part** (like ordinary length), and
- an **atomic/jump part** (point masses).

So computations often split into:

1) an ordinary integral on intervals where α behaves smoothly, and
2) explicit “point contributions” at discontinuities of α.

A typical rule of thumb:

- On open intervals where α is constant, the integral is zero.
- At a jump point a, the integral over the single-point interval contributes **f(a) · (α(a+) − α(a−))**.

This is the Stieltjes analog of “probability mass at a point.”

## 6.2 Two theorems of integral calculus

This section is where you recognize familiar calculus laws in Stieltjes form.

Expect versions of:

- **change of variable** (substitution)
- **integration by parts**

…but with extra bookkeeping for jumps and one-sided behavior.

If you think probabilistically: integration by parts is the engine behind many expectation identities, and change of variable is the engine behind distribution transforms.

## 6.3 Integration and differentiation

Here the book connects Lebesgue–Stieltjes integration to derivatives and to “differentiate under the integral sign” arguments.

The key message is: differentiation interacts nicely with the integral **when you have control** (uniform bounds, domination, or regularity of the integrand in parameters).

This is where Lebesgue theory becomes dramatically more pleasant than Riemann theory: you can justify interchange of limit processes with integrals under precise hypotheses.

## Mental model

When α is smooth, Lebesgue–Stieltjes calculus looks like ordinary calculus.

When α has jumps, you get a hybrid calculus:

- continuous integration + discrete summation.

That hybrid viewpoint is exactly what you need for real-world models (e.g., mixed distributions).

### Practice checklist

- For a step-like α, practice turning ∫ f dα into a finite sum of point masses.
- For a differentiable α, practice converting ∫ f dα into an ordinary integral involving α′.
- Keep a habit: **always check where α is discontinuous**, and treat those points separately.
