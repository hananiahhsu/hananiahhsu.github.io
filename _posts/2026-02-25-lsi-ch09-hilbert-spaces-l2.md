---
layout: post
title: "Lebesgue–Stieltjes Integral: Chapter 9 — Hilbert Spaces and L²"
date: 2026-02-25 17:00:00 +0800
categories: [math, analysis]
series: lebesgue-stieltjes-integral
chapter: 9
permalink: /math/lebesgue-stieltjes-integral/ch09-hilbert-spaces-l2/
---

The space $L^2$ is distinguished among the $L^p$ spaces because its norm comes from an inner product. Orthogonality, projection, Fourier coefficients, and least-squares approximation are consequences of this geometry.

## Hilbert-space structure

A complex inner-product space $H$ has a map
$\langle\cdot,\cdot\rangle:H\times H\to\mathbb C$ satisfying linearity in one argument, conjugate symmetry, and positive definiteness. The induced norm is

$$
\|u\|=\sqrt{\langle u,u\rangle}.
$$

A Hilbert space is an inner-product space complete in this norm.

For a measure space $(X,\mathcal M,\mu)$,

$$
L^2(\mu)
=\left\{f:\int_X|f|^2\,d\mu<\infty\right\}/\!\sim
$$

is a Hilbert space with

$$
\langle f,g\rangle
=\int_X f(x)\overline{g(x)}\,d\mu(x).
$$

The Cauchy–Schwarz inequality

$$
|\langle f,g\rangle|
\le\|f\|_2\|g\|_2
$$

ensures that the inner product is finite and continuous.

## Projection theorem

Let $M\subset H$ be a nonempty closed convex set. For each $u\in H$, there is a unique $m^\ast\in M$ minimizing the distance:

$$
\|u-m^\ast\|
=\inf_{m\in M}\|u-m\|.
$$

If $M$ is a closed linear subspace, the minimizer is characterized by

$$
u-m^\ast\perp M.
$$

For a finite-dimensional subspace
$M=\operatorname{span}\{\phi_1,\ldots,\phi_n\}$, write

$$
m^\ast=\sum_{j=1}^{n}c_j\phi_j.
$$

The orthogonality conditions yield the normal equations

$$
\sum_{j=1}^{n}
\langle\phi_j,\phi_i\rangle c_j
=\langle u,\phi_i\rangle,
\qquad i=1,\ldots,n.
$$

The matrix $G_{ij}=\langle\phi_j,\phi_i\rangle$ is the Gram matrix. An orthonormal basis makes $G=I$; an ill-conditioned basis makes the numerical problem sensitive even though the projection is mathematically unique.

## Orthonormal systems

A family $(e_n)$ is orthonormal when

$$
\langle e_m,e_n\rangle=\delta_{mn}.
$$

For every $u\in H$, Bessel’s inequality gives

$$
\sum_n|\langle u,e_n\rangle|^2\le\|u\|^2.
$$

If the system is complete, Parseval’s identity holds:

$$
\|u\|^2
=\sum_n|\langle u,e_n\rangle|^2,
$$

and

$$
u=\sum_n\langle u,e_n\rangle e_n
$$

with convergence in the Hilbert-space norm.

The convergence mode must be stated. $L^2$ convergence means

$$
\left\|u-\sum_{n=1}^{N}
\langle u,e_n\rangle e_n\right\|_2\to0.
$$

It does not by itself imply pointwise or uniform convergence.

## Fourier series in L²

On $(-\pi,\pi)$, the normalized exponentials

$$
e_n(x)=\frac{1}{\sqrt{2\pi}}e^{inx},
\qquad n\in\mathbb Z,
$$

form an orthonormal basis of $L^2(-\pi,\pi)$. The Fourier coefficient is

$$
\widehat f(n)
=\langle f,e_n\rangle
=\frac{1}{\sqrt{2\pi}}
\int_{-\pi}^{\pi}f(x)e^{-inx}\,dx.
$$

The partial sums converge to $f$ in $L^2$, and Parseval gives conservation of squared norm:

$$
\|f\|_2^2=\sum_{n\in\mathbb Z}|\widehat f(n)|^2.
$$

Stronger convergence requires stronger hypotheses or different summation procedures. A spectral approximation should therefore report whether its guarantee is in mean square, pointwise, or uniform norm.

## Sturm–Liouville structure

A regular Sturm–Liouville problem has the form

$$
-\frac{d}{dx}\!\left(p(x)y'(x)\right)
+q(x)y(x)
=\lambda w(x)y(x)
$$

on $[a,b]$, together with boundary conditions that make the operator self-adjoint. Here $p>0$ and $w>0$ under the standard regular assumptions.

If $y_m,y_n$ correspond to distinct eigenvalues, integration by parts and the boundary conditions give

$$
(\lambda_m-\lambda_n)
\int_a^b y_m(x)\overline{y_n(x)}w(x)\,dx=0.
$$

Hence the eigenfunctions are orthogonal in the weighted space
$L^2((a,b),w(x)\,dx)$, or equivalently in the Stieltjes space with
$d\alpha=w\,dx$. Completeness and spectral behavior require the precise operator domain and endpoint hypotheses; formal orthogonality alone is not a spectral theorem.

## Riesz representation

Every bounded linear functional $\Lambda:H\to\mathbb C$ has a unique representing vector $g\in H$ such that

$$
\Lambda(f)=\langle f,g\rangle,
\qquad
\|\Lambda\|=\|g\|.
$$

This identifies dual quantities with vectors in the same Hilbert space. In weak formulations, it converts a continuous linear load functional into an inner-product representation whenever the selected Hilbert structure permits it.

## CAD and computational geometry

Hilbert-space projection is the mathematical core of many engineering algorithms:

- fitting a curve or surface in a finite basis;
- minimizing mean-square geometric deviation;
- projecting residuals onto trial spaces;
- spectral decomposition of parameterized fields;
- reduced-order approximation.

The mathematics also exposes the limits. A least-squares optimum minimizes the declared $L^2$ error, not necessarily the maximum deviation. Parameter-space $L^2$ fitting is not invariant under reparameterization unless the measure is transformed appropriately. For a surface, using physical area measure rather than uniform parameter measure prevents the basis fit from being biased by parameter stretching.

Professional use of $L^2$ therefore specifies the measure, the subspace, the convergence norm, and the conditioning of the chosen basis.
