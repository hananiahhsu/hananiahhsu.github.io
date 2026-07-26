---
layout: post
title: "Lebesgue–Stieltjes Integral: Chapter 6 — Integral Calculus"
date: 2026-02-25 14:00:00 +0800
categories: [math, analysis]
series: lebesgue-stieltjes-integral
chapter: 6
permalink: /math/lebesgue-stieltjes-integral/ch06-integral-calculus/
---

This chapter connects the measure-theoretic definition to familiar calculus. The central issue is not symbolic manipulation, but identifying the continuous, atomic, and singular parts of the integrator before applying a formula.

## Absolutely continuous integrators

Let $\alpha$ be absolutely continuous on $[a,b]$. Then $\alpha'$ exists almost everywhere, $\alpha'\in L^1$, and

$$
\alpha(x)=\alpha(a)+\int_a^x\alpha'(t)\,dt.
$$

The associated Stieltjes measure satisfies

$$
d\mu_\alpha(x)=\alpha'(x)\,dx.
$$

Therefore, for every nonnegative or $\mu_\alpha$-integrable $f$,

$$
\int_{(a,b]} f(x)\,d\alpha(x)
=\int_a^b f(x)\alpha'(x)\,dx.
$$

This reduction is exact only for the absolutely continuous part. It cannot recover atomic or singular continuous mass.

## Jumps are point masses

For a right-continuous nondecreasing $\alpha$, define its jump at $c$ by

$$
\Delta\alpha(c)=\alpha(c)-\alpha(c-).
$$

Then

$$
\mu_\alpha(\{c\})=\Delta\alpha(c).
$$

If $\alpha$ has an absolutely continuous part and jumps $a_k\ge0$ at points $x_k$, then

$$
\int f\,d\alpha
=\int f(x)\alpha'_{\mathrm{ac}}(x)\,dx
+\sum_k a_k f(x_k)
+\int f\,d\alpha_{\mathrm{sc}},
$$

where the last term is the singular continuous contribution. The decomposition is conceptual: a general monotone function may contain all three parts.

## Fundamental theorem in measure form

If $f\in L^1([a,b])$, define

$$
F(x)=\int_a^x f(t)\,dt.
$$

Then $F$ is absolutely continuous and $F'(x)=f(x)$ almost everywhere. Conversely, every absolutely continuous $F$ has this representation with $f=F'$ almost everywhere.

The almost-everywhere qualification is sharp. For the Cantor function $C$,
$C'=0$ almost everywhere, but $C(1)-C(0)=1$. Its change is carried by a singular measure and cannot be reconstructed from $C'\,dx$.

## Integration by parts

When $f$ and $\alpha$ are absolutely continuous,

$$
\int_a^b f(x)\,d\alpha(x)
=f(b)\alpha(b)-f(a)\alpha(a)
-\int_a^b\alpha(x)\,df(x),
$$

which is the classical formula

$$
\int_a^b f(x)\alpha'(x)\,dx
=f(b)\alpha(b)-f(a)\alpha(a)
-\int_a^b\alpha(x)f'(x)\,dx.
$$

For functions of bounded variation with jumps, the endpoint and one-sided-value convention must be fixed. Under a common càdlàg convention, the product rule includes the contribution of simultaneous jumps:

$$
\Delta(f\alpha)(x)
=f(x-)\Delta\alpha(x)
+\alpha(x-)\Delta f(x)
+\Delta f(x)\Delta\alpha(x).
$$

Thus copying the continuous integration-by-parts formula into a discontinuous setting can omit a jump term. The safe procedure is to state the interval convention and derive the formula from the measure decomposition.

## Change of variables as pushforward

Let $T:X\to Y$ be measurable and let $T_\#\mu$ denote the pushforward measure,

$$
(T_\#\mu)(B)=\mu(T^{-1}(B)).
$$

Then for every nonnegative measurable $g$,

$$
\int_Y g(y)\,d(T_\#\mu)(y)
=\int_X g(T(x))\,d\mu(x).
$$

This identity is the measure-theoretic core of change of variables. Jacobian factors arise when the pushforward has a density with respect to a reference measure. In one dimension, a continuously differentiable strictly increasing map $T$ gives the familiar formula

$$
\int_{T(a)}^{T(b)}g(y)\,dy
=\int_a^b g(T(x))T'(x)\,dx.
$$

The pushforward statement remains valid even when no smooth inverse or density exists.

## Worked example: distributed and concentrated response

On $[0,1]$, let

$$
\alpha(x)=x^2+4\mathbf 1_{[3/4,\,1]}(x),
\qquad f(x)=1+x.
$$

Then $d\alpha=2x\,dx+4\delta_{3/4}$, and

$$
\begin{aligned}
\int_{(0,1]}(1+x)\,d\alpha(x)
&=\int_0^1(1+x)2x\,dx
  +4\left(1+\frac34\right)\\
&=\left[x^2+\frac{2}{3}x^3\right]_0^1+7\\
&=\frac{26}{3}.
\end{aligned}
$$

Approximating the jump by a narrow smooth peak can reproduce this value only if the numerical scheme resolves the peak and preserves its area. The Stieltjes representation expresses the point contribution exactly.

## Differentiating parameterized integrals

Let

$$
I(t)=\int_XF(x,t)\,d\mu(x).
$$

If $F(\cdot,t)$ is measurable, $F(x,\cdot)$ is differentiable near $t_0$, and an integrable $g$ satisfies

$$
\left|\partial_tF(x,t)\right|\le g(x)
$$

near $t_0$, then

$$
I'(t_0)=\int_X\partial_tF(x,t_0)\,d\mu(x).
$$

This theorem gives a rigorous basis for sensitivities of mass properties, objective functions, and residual norms. If the measure itself depends on $t$, an additional derivative of the measure is required; differentiating only the integrand is incomplete.

## Computational interpretation

The practical rule is to decompose before evaluating:

- use a density integral for the absolutely continuous part;
- use exact weighted evaluations for atoms;
- retain a genuine measure representation for singular continuous mass;
- use pushforwards for parameter transformations;
- verify domination before interchanging differentiation and integration.

This preserves concentrated geometric or physical effects and makes the numerical implementation correspond to the actual mathematical object.
