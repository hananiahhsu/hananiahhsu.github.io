---
layout: post
title: "Lebesgue–Stieltjes Integral: Chapter 4 — The Lebesgue–Stieltjes Integral"
date: 2026-02-25 10:10:00 +0800
categories: [math, analysis]
series: lebesgue-stieltjes-integral
chapter: 4
permalink: /math/lebesgue-stieltjes-integral/ch04-lebesgue-stieltjes-integral/
---

Chapter 4 is the core construction: it defines a measure on the real line from a monotone function **α**, then defines the integral by approximating functions with step-like building blocks.

## 4.1 Measure of an interval

The Stieltjes viewpoint is: instead of measuring intervals only by length, measure them by how much **α** increases.

- Think of **α** as a “cumulative distribution” (it can have jumps and flat parts).
- The measure of an interval is built from increments of α with careful attention to endpoints.

This is the minimal bridge from classical analysis (monotone functions and one-sided limits) to measure.

## 4.2 Probability measures

A major motivation for Stieltjes integration is probability.

- If α is a cumulative distribution function (CDF), the measure induced by α is exactly the probability measure.
- Lebesgue–Stieltjes integration then becomes “expected value” in a unified way that includes discrete, continuous, and mixed distributions.

## 4.3 Simple sets

To build a full measure theory without drowning in abstraction, the book introduces a practical class of “simple sets” and shows how to measure them consistently.

This mirrors how step functions are used as the simple class for functions.

## 4.4 Step functions revisited

Step functions are reintroduced in a measure-aware way:

- A step function is a finite linear combination of indicator functions of intervals.
- Its integral is “sum of heights × measure of supporting intervals.”

Once step functions are integrated, everything else is approximation.

## 4.5 Definition of the integral

The Lebesgue–Stieltjes integral is defined first for **nonnegative** measurable functions.

Operationally:

1. approximate f from below by simple/step-like functions,
2. define the integral as a supremum of the integrals of those approximants,
3. extend to signed functions via f = f⁺ − f⁻ (when both parts are integrable).

What’s new compared to Riemann:

- the “approximants” are more flexible than a single step function tied to one partition,
- and the notion of “size” is measure-based, not length-based.

## 4.6 The Lebesgue integral as a special case

If you choose **α(x) = x**, the induced measure is ordinary length and the Lebesgue–Stieltjes integral becomes the **Lebesgue integral**.

Two practical cross-checks emphasized in the book:

- If f is Riemann integrable on a closed interval, then it is also Lebesgue integrable there and the values agree.
- The equivalence does **not** automatically extend to improper Riemann integrals (conditional convergence can break Lebesgue integrability).

## Mental model

You can summarize the construction like this:

- **α** determines *what it means for a set to be small*.
- Step/simple functions provide controllable approximations.
- The integral is a *limit* of these approximations, chosen so that key limit theorems become true.

### Practice checklist

- Compute measures of intervals for simple α (purely continuous, purely jump, mixed).
- Integrate step functions against α.
- Verify how α(x)=x collapses the theory back to standard Lebesgue integration.
