---
layout: post
title: "Lebesgue–Stieltjes Integral: Chapter 10 — Beyond Lebesgue Integration"
date: 2026-02-25 18:00:00 +0800
categories: [math, analysis]
series: lebesgue-stieltjes-integral
chapter: 10
permalink: /math/lebesgue-stieltjes-integral/ch10-epilogue/
---

Lebesgue integration provides a powerful synthesis of measure, convergence, $L^p$ spaces, probability, and functional analysis. It does not, however, integrate every derivative. The final chapter clarifies what later integration theories extend and what they give up.

## The derivative problem

If $F$ is absolutely continuous on $[a,b]$, then

$$
F(b)-F(a)=\int_a^bF'(x)\,dx
$$

with $F'\in L^1$. For a merely differentiable $F$, the derivative need not be Lebesgue integrable. Derivatives satisfy the Darboux property, but they can oscillate too strongly to be absolutely integrable.

This reveals a mismatch:

- differentiation is local and sensitive to cancellation;
- finite Lebesgue integrability requires
  $\int|f|<\infty$, an absolute global condition.

The Newton integral asks for an antiderivative first. Measure-theoretic integration asks for a measurable function with controlled positive and negative parts. Gauge integration supplies another route.

## Henstock–Kurzweil construction

Let $f:[a,b]\to\mathbb R$. A **gauge** is a positive function

$$
\delta:[a,b]\to(0,\infty).
$$

A tagged partition

$$
\mathcal P=\{([x_{i-1},x_i],t_i)\}_{i=1}^{n}
$$

is $\delta$-fine when

$$
[x_{i-1},x_i]
\subset
(t_i-\delta(t_i),t_i+\delta(t_i))
$$

for every $i$. The Henstock–Kurzweil integral of $f$ is $I$ if for every $\varepsilon>0$ there exists a gauge $\delta$ such that every $\delta$-fine tagged partition satisfies

$$
\left|
\sum_{i=1}^{n}f(t_i)(x_i-x_{i-1})-I
\right|<\varepsilon.
$$

The crucial difference from the Riemann definition is that interval size is controlled locally by the tag. Near a singular or rapidly oscillating point, the gauge can demand a much finer interval.

The Henstock–Kurzweil integral contains the Riemann and Lebesgue integrals on compact intervals and integrates every finite derivative, restoring a broad form of the Fundamental Theorem of Calculus.

## A canonical example

Define

$$
F(x)=
\begin{cases}
x^2\sin(x^{-4}),&x\ne0,\\
0,&x=0.
\end{cases}
$$

Then $F$ is differentiable at $0$, with $F'(0)=0$, and for $x\ne0$,

$$
F'(x)
=2x\sin(x^{-4})
-4x^{-3}\cos(x^{-4}).
$$

The derivative is not absolutely integrable near $0$. Indeed, the magnitude of the second term behaves like $x^{-3}|\cos(x^{-4})|$, whose integral diverges. Nevertheless, $F'$ is Henstock–Kurzweil integrable and

$$
\operatorname{HK}\!\int_{-1}^{1}F'(x)\,dx
=F(1)-F(-1)=0.
$$

The value depends on cancellation encoded by the derivative structure, not on finite total variation.

## What the extension does not replace

Broader integrability is not automatically a better foundation for every problem. Lebesgue integration remains the standard framework when the task needs:

- countably additive measures;
- $L^p$ and Hilbert-space completeness;
- product measures and probability;
- Radon–Nikodym derivatives;
- robust monotone and dominated convergence theorems;
- weak convergence and functional analysis.

Gauge integration is particularly natural for recovering antiderivatives and handling conditionally integrable oscillations. Its convergence and product theories require their own hypotheses; one must not import every Lebesgue theorem unchanged.

## Comparison by mathematical requirement

| Requirement | Natural framework |
|---|---|
| continuous function on a compact interval | Riemann |
| measurable accumulation, probability, $L^p$ | Lebesgue |
| density plus atoms or a cumulative integrator | Lebesgue–Stieltjes |
| recovery of highly irregular derivatives | Henstock–Kurzweil |
| operator and projection geometry | Hilbert-space integration |

The frameworks form an expanding toolkit, not a ranking. The appropriate integral is the one whose convergence rules and structural objects match the problem.

## Implications for numerical computation

A gauge resembles an adaptive local resolution rule, but a numerical adaptive quadrature routine is not automatically a Henstock–Kurzweil implementation. A finite computation must still provide:

- a representation of singular points or oscillatory regions;
- an error estimator tied to a stated function class;
- a stopping criterion;
- a finite-precision analysis;
- reproducible behavior under interval subdivision.

For CAD and simulation, Lebesgue–Stieltjes integration remains especially valuable because it combines distributed fields and concentrated feature contributions in a measure compatible with product spaces and $L^p$ analysis. Gauge integration becomes relevant when parameter sensitivities or analytic derivatives exhibit cancellation beyond absolute integrability.

## Closing synthesis

The series begins with completeness of $\mathbb R$ and ends with complete function spaces. Between them lies one continuous line of ideas:

$$
\text{order}
\longrightarrow
\text{measure}
\longrightarrow
\text{integral}
\longrightarrow
\text{convergence}
\longrightarrow
L^p
\longrightarrow
\text{Hilbert geometry}.
$$

The professional value of the theory is not notation. It is the ability to state exactly what is being accumulated, which exceptional sets matter, how approximation converges, and which transformations preserve the result.
