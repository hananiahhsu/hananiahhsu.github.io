---
layout: post
title: "Lebesgue–Stieltjes Integral: Chapter 8 — Lebesgue Spaces Lᵖ"
date: 2026-02-25 16:00:00 +0800
categories: [math, analysis]
series: lebesgue-stieltjes-integral
chapter: 8
permalink: /math/lebesgue-stieltjes-integral/ch08-lebesgue-spaces-lp/
---

An integral becomes an analytical working environment when it induces a norm and a complete function space. The $L^p$ spaces provide the standard language for approximation error, stability, duality, and weak formulations.

Let $(X,\mathcal M,\mu)$ be a measure space.

## Definition and almost-everywhere equivalence

For $1\le p<\infty$,

$$
\|f\|_{L^p(\mu)}
=\left(\int_X|f|^p\,d\mu\right)^{1/p}.
$$

The expression is initially a seminorm on measurable functions because
$\|f\|_p=0$ means only that $f=0$ almost everywhere. The space $L^p(\mu)$ therefore consists of equivalence classes under

$$
f\sim g
\quad\Longleftrightarrow\quad
f=g\ \text{almost everywhere}.
$$

For $p=\infty$,

$$
\|f\|_\infty
=\operatorname*{ess\,sup}_{x\in X}|f(x)|
=\inf\{M\ge0:|f|\le M\text{ almost everywhere}\}.
$$

The essential supremum ignores null-set anomalies; the pointwise maximum does not.

## Hölder’s inequality

Let $1<p<\infty$ and $q$ satisfy

$$
\frac1p+\frac1q=1.
$$

Then

$$
\int_X|fg|\,d\mu
\le\|f\|_p\|g\|_q.
$$

After normalizing $\|f\|_p=\|g\|_q=1$, the inequality follows from Young’s inequality

$$
ab\le\frac{a^p}{p}+\frac{b^q}{q}.
$$

The endpoint cases pair $L^1$ with $L^\infty$. Hölder shows that multiplication defines a continuous bilinear map

$$
L^p\times L^q\longrightarrow L^1.
$$

## Minkowski’s inequality

For $1\le p\le\infty$,

$$
\|f+g\|_p\le\|f\|_p+\|g\|_p.
$$

For $1<p<\infty$, write

$$
|f+g|^p=|f+g|\cdot|f+g|^{p-1}
$$

and apply Hölder separately to the $f$ and $g$ terms. Minkowski supplies the triangle inequality and therefore makes $L^p$ a normed vector space.

## Completeness

The Riesz–Fischer theorem states that $L^p(\mu)$ is complete for
$1\le p\le\infty$: every Cauchy sequence in the $L^p$ norm converges in that norm to an element of $L^p$.

Completeness is essential for analysis. An iterative algorithm may generate only approximants $f_n$; the Cauchy property guarantees that the limiting object remains inside the declared solution space.

Norm convergence implies convergence in measure when the measure is finite, and every $L^p$-convergent sequence has a subsequence converging almost everywhere. Full pointwise convergence need not follow.

## Inclusion depends on the measure space

If $\mu(X)<\infty$ and $1\le p<q\le\infty$, then

$$
L^q(\mu)\subset L^p(\mu),\qquad
\|f\|_p
\le\mu(X)^{\,1/p-1/q}\|f\|_q.
$$

On an infinite-measure space there is no general inclusion in either direction. For instance on $(1,\infty)$, power functions $x^{-a}$ can belong to one $L^p$ space but not another depending on the exponent. Any statement comparing $L^p$ spaces must therefore name the underlying measure and whether its total mass is finite.

## Duality and separability

For $1<p<\infty$ under standard hypotheses, every bounded linear functional on $L^p$ has the form

$$
\Lambda_g(f)=\int_X f\,\overline g\,d\mu,
\qquad g\in L^q.
$$

Thus $(L^p)^*\cong L^q$. The case $p=1$ also has dual $L^\infty$ on the usual localizable settings, whereas the dual of $L^\infty$ is generally larger than $L^1$.

For Borel measures on separable metric spaces, and more generally for suitably countably generated $\sigma$-algebras, $L^p$ is separable when $1\le p<\infty$. $L^\infty$ is generally not separable. These qualifications matter when selecting countable approximation bases.

## Sobolev spaces

For an open set $\Omega\subset\mathbb R^n$,

$$
W^{k,p}(\Omega)
=\{f\in L^p(\Omega):
D^\beta f\in L^p(\Omega)
\text{ for all }|\beta|\le k\},
$$

where $D^\beta f$ is understood in the weak, distributional sense. A standard norm is

$$
\|f\|_{W^{k,p}}
=\left(
\sum_{|\beta|\le k}\|D^\beta f\|_p^p
\right)^{1/p}
$$

for $p<\infty$, with the analogous maximum norm for $p=\infty$.

Sobolev spaces measure both field magnitude and derivative regularity. They are the natural domains of weak differential operators and finite-element formulations; they are not merely “smoother $L^p$ spaces.”

## Selecting an error norm

Different norms encode different engineering objectives:

| Norm | Emphasis | Typical interpretation |
|---|---|---|
| $L^1$ | total absolute error | robust aggregate discrepancy |
| $L^2$ | energy and orthogonality | least squares, projection, spectral methods |
| $L^\infty$ | worst essential error | tolerance envelopes |
| $W^{1,2}$ | value and weak gradient | elliptic energy, finite elements |

A small $L^2$ error can coexist with a large localized pointwise error; a small $L^\infty$ error says nothing directly about derivative quality. The norm is part of the requirement, not an after-the-fact reporting choice.

For geometric approximation, the metric must also respect parameterization and physical measure. Measuring a surface error uniformly in parameter coordinates can overweight compressed regions and underweight stretched ones. Integrating with the surface Jacobian aligns the norm with physical area.
