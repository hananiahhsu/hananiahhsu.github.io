---
layout: post
title: "Lebesgue–Stieltjes Integral: Chapter 5 — Core Properties and Convergence"
date: 2026-02-25 13:00:00 +0800
categories: [math, analysis]
series: lebesgue-stieltjes-integral
chapter: 5
permalink: /math/lebesgue-stieltjes-integral/ch05-properties-of-the-integral/
---

The central strength of Lebesgue integration is not that it evaluates more elementary antiderivatives. Its strength is the disciplined exchange of limits and integrals. This chapter records the hypotheses under which those exchanges are valid.

Let $(X,\mathcal M,\mu)$ be a measure space. Every theorem below applies to a Lebesgue–Stieltjes measure by taking $\mu=\mu_\alpha$.

## Algebra and order

For integrable functions $f,g$ and scalars $a,b$,

$$
\int_X(af+bg)\,d\mu
=a\int_X f\,d\mu+b\int_X g\,d\mu.
$$

If $f\le g$ almost everywhere, then

$$
\int_X f\,d\mu\le\int_X g\,d\mu.
$$

The absolute-value estimate

$$
\left|\int_X f\,d\mu\right|
\le\int_X|f|\,d\mu
$$

follows from $-|f|\le f\le|f|$.

If $f=g$ almost everywhere, their integrals agree whenever either side is defined. The converse is false: equal integrals do not imply almost-everywhere equality.

## Monotone Convergence Theorem

> **Theorem.** Let $f_n:X\to[0,+\infty]$ be measurable and satisfy
> $f_n(x)\uparrow f(x)$ almost everywhere. Then
> $$
> \lim_{n\to\infty}\int_X f_n\,d\mu
> =\int_X f\,d\mu,
> $$
> with both sides allowed to equal $+\infty$.

The proof reflects the definition of the nonnegative integral. Monotonicity gives the easy inequality
$\lim_n\int f_n\le\int f$. For a simple function
$0\le\varphi\le f$ and $0<c<1$, the sets

$$
E_n=\{x:f_n(x)\ge c\varphi(x)\}
$$

increase to $X$, up to a null set. Continuity of measure from below yields

$$
\liminf_n\int f_n\,d\mu
\ge c\int\varphi\,d\mu.
$$

Taking the supremum over $\varphi$, then letting $c\uparrow1$, gives the reverse inequality.

This theorem needs monotonicity and nonnegativity. A decreasing sequence is handled by applying the theorem to $f_1-f_n$, provided $\int f_1\,d\mu<\infty$.

## Fatou’s lemma

> **Lemma.** For nonnegative measurable functions $f_n$,
> $$
> \int_X\liminf_{n\to\infty}f_n\,d\mu
> \le
> \liminf_{n\to\infty}\int_X f_n\,d\mu.
> $$

Set $g_n=\inf_{k\ge n}f_k$. Then $g_n\uparrow\liminf f_n$, so Monotone Convergence applies, while $g_n\le f_k$ for $k\ge n$. Fatou’s lemma is therefore an order-theoretic lower-semicontinuity result.

It generally gives an inequality, not equality. On $\mathbb R$, let
$f_n=\mathbf 1_{[n,n+1]}$. Then $f_n\to0$ pointwise, but
$\int f_n\,dx=1$ for every $n$. Mass escapes to infinity.

## Dominated Convergence Theorem

> **Theorem.** Suppose $f_n\to f$ almost everywhere and there exists
> $g\in L^1(\mu)$ such that $|f_n|\le g$ almost everywhere for every $n$.
> Then $f\in L^1(\mu)$ and
> $$
> \lim_{n\to\infty}\int_X f_n\,d\mu
> =\int_X f\,d\mu.
> $$
> In fact, $\|f_n-f\|_{L^1}\to0$.

Apply Fatou’s lemma to $g+f_n$ and $g-f_n$. The integrable majorant is the mechanism that prevents mass from concentrating or escaping.

Pointwise convergence alone is insufficient. On $(0,1)$, define

$$
f_n(x)=n\,\mathbf 1_{(0,1/n)}(x).
$$

Then $f_n(x)\to0$ for every $x>0$, but

$$
\int_0^1 f_n(x)\,dx=1.
$$

There is no single integrable function dominating the sequence.

## A practical decision rule

When evaluating $\lim_n\int f_n\,d\mu$, inspect the approximation structure:

| Available structure | Appropriate result | Required control |
|---|---|---|
| $0\le f_n\uparrow f$ | Monotone Convergence | order |
| $f_n\ge0$, no monotonicity | Fatou | lower bound only |
| $f_n\to f$, $|f_n|\le g\in L^1$ | Dominated Convergence | integrable majorant |
| $\sum_n\int |f_n|\,d\mu<\infty$ | Tonelli plus absolute convergence | summable total mass |

The theorem must be selected from verified hypotheses; visual convergence of plots is not a substitute.

## Differentiation under the integral sign

Dominated Convergence also supports parameter differentiation. Suppose $F(x,t)$ is differentiable in $t$ near $t_0$, and

$$
\left|\frac{\partial F}{\partial t}(x,t)\right|
\le g(x)
$$

for an integrable $g$, uniformly for $t$ near $t_0$. Under the standard measurability assumptions,

$$
\frac{d}{dt}\int_XF(x,t)\,d\mu(x)\Big|_{t=t_0}
=\int_X\frac{\partial F}{\partial t}(x,t_0)\,d\mu(x).
$$

The proof applies Dominated Convergence to the difference quotients.

## Engineering interpretation

Convergence theorems are verification contracts for approximation algorithms:

- a nested nonnegative approximation naturally supports Monotone Convergence;
- a stable envelope supports Dominated Convergence;
- failure to control concentration is exposed by examples like $n\mathbf1_{(0,1/n)}$;
- finite-domain sampling does not detect mass that moves outside the observed window.

For CAD and simulation, these distinctions matter in mesh refinement, adaptive quadrature, parameter sensitivity, and geometric regularization. A numerical sequence can converge pointwise at every sampled location while its integrated quantity remains wrong. Professional validation therefore records not only a residual plot, but the theorem hypotheses that justify passing from discrete approximants to the continuous target.
