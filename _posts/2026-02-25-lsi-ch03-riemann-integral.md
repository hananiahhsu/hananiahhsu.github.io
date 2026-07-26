---
layout: post
title: "Lebesgue–Stieltjes Integral: Chapter 3 — The Riemann Integral"
date: 2026-02-25 11:00:00 +0800
categories: [math, analysis]
series: lebesgue-stieltjes-integral
chapter: 3
permalink: /math/lebesgue-stieltjes-integral/ch03-riemann-integral/
---

The Riemann integral is not merely a preliminary technique. It is the correct theory for many bounded functions on compact intervals, and its limitations identify exactly why measure is needed.

## Darboux construction

Let $f:[a,b]\to\mathbb R$ be bounded and let
$P:a=x_0<\cdots<x_n=b$ be a partition. On
$I_j=[x_{j-1},x_j]$, set

$$
m_j=\inf_{x\in I_j}f(x),\qquad
M_j=\sup_{x\in I_j}f(x).
$$

The lower and upper Darboux sums are

$$
L(f,P)=\sum_{j=1}^{n}m_j(x_j-x_{j-1}),\qquad
U(f,P)=\sum_{j=1}^{n}M_j(x_j-x_{j-1}).
$$

Refining a partition can only increase $L$ and decrease $U$. The lower and upper integrals are therefore

$$
\underline{\int_a^b}f
=\sup_P L(f,P),\qquad
\overline{\int_a^b}f
=\inf_P U(f,P).
$$

The function is Riemann integrable when these values agree. Equivalently, for every $\varepsilon>0$ there exists a partition $P$ such that

$$
U(f,P)-L(f,P)<\varepsilon.
$$

This criterion is often the most useful proof tool because it expresses integrability through total oscillation over finitely many subintervals.

## What Riemann integrability actually permits

Continuity is sufficient but not necessary. The precise Lebesgue criterion states:

> A bounded function on $[a,b]$ is Riemann integrable if and only if its set of discontinuities has Lebesgue measure zero.

The theorem explains two standard examples.

The Dirichlet function

$$
f(x)=\mathbf 1_{\mathbb Q}(x)
$$

is discontinuous everywhere because both rationals and irrationals are dense. Every interval has infimum $0$ and supremum $1$; consequently, every lower sum is $0$ and every upper sum is $b-a$. It is not Riemann integrable.

By contrast, Thomae’s function on $[0,1]$,

$$
t(x)=
\begin{cases}
1/q,&x=p/q\text{ in lowest terms},\\
0,&x\notin\mathbb Q,
\end{cases}
$$

is discontinuous exactly at the rational points, a countable set. It is Riemann integrable with integral $0$. Dense discontinuities are possible; positive measure of the discontinuity set is the obstruction.

## Improper integrals are a different extension

The Riemann integral assumes a bounded function on a compact interval. Improper integration extends it by taking limits, for example

$$
\int_a^\infty f(x)\,dx
:=\lim_{R\to\infty}\int_a^R f(x)\,dx,
$$

when the limit exists. This admits conditionally convergent expressions such as

$$
\int_1^\infty\frac{\sin x}{x}\,dx.
$$

However,

$$
\int_1^\infty\left|\frac{\sin x}{x}\right|dx=\infty,
$$

so the same function is not Lebesgue integrable on $[1,\infty)$. The distinction is structural:

- an improper integral can encode cancellation imposed by a particular limiting order;
- finite Lebesgue integrability requires absolute integrability.

When rearrangement, product integration, or order-independent accumulation matters, absolute integrability is the safer contract.

## Riemann sums and numerical quadrature

Given sample points $\xi_j\in[x_{j-1},x_j]$, the Riemann sum is

$$
S(f,P,\xi)
=\sum_{j=1}^{n}f(\xi_j)(x_j-x_{j-1}).
$$

For a Riemann-integrable $f$, these sums converge to $\int_a^b f(x)\,dx$ as the mesh
$\|P\|=\max_j(x_j-x_{j-1})$ tends to zero, uniformly over the choice of sample points.

Numerical quadrature should not be identified with the definition itself. Trapezoidal, Gaussian, and adaptive rules add approximation models and error estimators. Their convergence rates depend on regularity far beyond mere integrability. For example, Gaussian quadrature can be exact for high-degree polynomials, while a jump discontinuity can defeat the smoothness assumptions behind its nominal rate.

## Why measure changes the construction

Riemann integration controls oscillation on intervals in the domain. Lebesgue integration first assigns a size $\mu(E)$ to measurable sets and integrates simple functions by finite sums:

$$
\int \sum_{j=1}^{N}c_j\mathbf 1_{E_j}\,d\mu
=\sum_{j=1}^{N}c_j\mu(E_j).
$$

It then reaches general functions by monotone approximation. This is more than “partitioning the range”: the decisive change is that the theory is built on a countably additive measure and an almost-everywhere equivalence.

For the Dirichlet function under Lebesgue measure, $\mathbb Q\cap[a,b]$ is null, so

$$
\int_a^b\mathbf 1_{\mathbb Q}(x)\,dx=0.
$$

Under an atomic Stieltjes measure concentrated on the rationals, the result may instead be positive. Integrability and integral values always depend on the selected measure.

## CAD and numerical geometry

Riemann integration remains natural for smooth parameterized curves and surfaces. Arc length, mass properties, and many quadrature kernels are evaluated over compact parameter domains where the integrand is continuous or piecewise smooth.

Measure theory becomes necessary when the computation must also represent:

- trim boundaries and exceptional parameter sets;
- point masses, impulses, or event contributions;
- limits of approximations with only almost-everywhere convergence;
- functions defined up to null sets;
- product domains and repeated integration under precise hypotheses.

The correct engineering question is therefore not “Which integral is more modern?” It is “Which convergence and data model does the algorithm require?”
