---
layout: post
title: "Lebesgue–Stieltjes Integral: Chapter 1 — Real Numbers"
date: 2026-02-25 09:00:00 +0800
categories: [math, analysis]
series: lebesgue-stieltjes-integral
chapter: 1
permalink: /math/lebesgue-stieltjes-integral/ch01-real-numbers/
---

Integration theory rests on order, completeness, and limits. This chapter isolates those foundations because every later construction—from outer measure to $L^p$ convergence—uses them explicitly.

## Scope and notation

Throughout the series, $\mathbb N=\{1,2,\ldots\}$, $\mathbb Q$ denotes the rational numbers, and

$$
\infty,\,-\infty\in\overline{\mathbb R}
  :=\mathbb R\cup\{-\infty,+\infty\}.
$$

An interval written $(a,b]$ is open at $a$ and closed at $b$. This convention will later align with a right-continuous integrator $\alpha$ through
$\mu_\alpha((a,b])=\alpha(b)-\alpha(a)$.

## Completeness is the decisive property

The real numbers form a complete ordered field. The operative statement is the **least-upper-bound axiom**:

> Every nonempty set $E\subset\mathbb R$ that is bounded above has a unique supremum $\sup E\in\mathbb R$.

The infimum follows by $\inf E=-\sup(-E)$. Completeness is stronger than the algebraic field laws; it is precisely what $\mathbb Q$ lacks. For example,

$$
E=\{q\in\mathbb Q:q^2<2\}
$$

is nonempty and bounded above in $\mathbb Q$, but has no rational supremum. In $\mathbb R$, its supremum is $\sqrt2$.

This axiom drives the monotone convergence principle. If $x_1\le x_2\le\cdots$ and $(x_n)$ is bounded above, set $x=\sup_n x_n$. For every $\varepsilon>0$, $x-\varepsilon$ cannot be an upper bound, so some $x_N>x-\varepsilon$; monotonicity then gives

$$
x-\varepsilon<x_n\le x,\qquad n\ge N.
$$

Hence $x_n\to x$. Measure theory repeatedly lifts this order argument from numbers to sets and functions.

## Density and countability

The Archimedean property implies that for $a<b$ one can choose $n\in\mathbb N$ with $n(b-a)>1$, then an integer $m$ satisfying

$$
na<m<nb.
$$

Thus $a<m/n<b$, proving that $\mathbb Q$ is dense in $\mathbb R$. Because $\sqrt2\,\mathbb Q$ is also dense and contains irrationals away from zero, the irrationals are dense as well.

Density and cardinality must not be confused:

- $\mathbb Q$ is countable and dense.
- $\mathbb R\setminus\mathbb Q$ is uncountable and dense.
- A set can therefore be topologically pervasive while remaining small for a particular measure.

The last qualification matters. Every countable set has Lebesgue measure zero, but a countable set need not have zero Lebesgue–Stieltjes measure. If

$$
\alpha(x)=\sum_{k=1}^{\infty}2^{-k}\mathbf 1_{[k,\infty)}(x),
$$

then $\mu_\alpha(\{k\})=2^{-k}$ and
$\mu_\alpha(\mathbb N)=1$. “Countable implies null” is valid for nonatomic measures such as Lebesgue measure, not for arbitrary Stieltjes measures.

## Extended real values

The extended real line makes monotone limits and integrals of nonnegative functions total: they always exist in $[0,+\infty]$. Its order is natural,

$$
-\infty < x < +\infty \quad (x\in\mathbb R),
$$

but its arithmetic is deliberately partial. Expressions such as $+\infty-\infty$ and $0\cdot\infty$ are undefined. This is not a technical nuisance. It explains why the integral of a signed function is defined only when at least one of
$\int f^+\,d\mu$ and $\int f^-\,d\mu$ is finite, and why finite integrability requires both to be finite.

For a sequence $(x_n)\subset\overline{\mathbb R}$,

$$
\limsup_{n\to\infty}x_n
=\inf_{N\ge1}\sup_{n\ge N}x_n,\qquad
\liminf_{n\to\infty}x_n
=\sup_{N\ge1}\inf_{n\ge N}x_n.
$$

These values always exist in $\overline{\mathbb R}$, and $x_n$ converges exactly when the two agree.

## Worked example: an infimum not attained

Consider $E=(0,1)$. Then $\inf E=0$ and $\sup E=1$, although neither endpoint belongs to $E$. An extremum is a member of the set; a supremum or infimum need only be the sharp order bound. The distinction is essential in optimization:

$$
\inf_{x\in E}F(x)
$$

can exist without a minimizer. Existence of a minimizing design therefore needs additional structure, commonly compactness of the admissible set and lower semicontinuity of $F$.

## Computational interpretation

Exact completeness is a property of $\mathbb R$, not of floating-point numbers. A floating-point type is finite and discrete; rounding can destroy associativity and order comparisons near a tolerance. Reliable geometric computation therefore separates:

- the mathematical existence statement, established in $\mathbb R$;
- the approximation algorithm, which produces a finite representation;
- the error contract, which states the metric, scale, and tolerance under which the result is accepted.

This separation becomes particularly important in CAD algorithms. Intersection points, closest-point parameters, and extremal curvature values may be defined through a supremum or infimum even when the numerical routine can only approximate them. The theorem establishes what the target is; numerical analysis establishes whether the implementation reaches it with a controlled error.

## What this chapter establishes

The reusable foundation is now precise: completeness turns bounded monotone processes into limits; density supports approximation; countability does not by itself determine measure; and extended real values allow convergence theorems to be stated without artificial finite bounds. The next chapter transfers these ideas from numbers to functions.
