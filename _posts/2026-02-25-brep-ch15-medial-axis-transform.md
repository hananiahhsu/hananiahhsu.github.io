---
layout: post
title: "B-Rep Modelling Techniques: Chapter 15 — The Medial Axis Transform"
date: 2026-02-25 18:40:00 +0800
categories: [graphics, geometry, cad]
series: brep-modelling-techniques
chapter: 15
book_title: "Boundary Representation Modelling Techniques"
book_author: "Ian Stroud"
book_year: 2006
permalink: /graphics/brep-modelling-techniques/ch15-medial-axis-transform/
---

> Study notes for Ian Stroud, *Boundary Representation Modelling Techniques* (Springer, 2006).

The Medial Axis Transform (MAT) is a powerful conceptual tool for shape analysis, offsetting, and feature reasoning. This chapter focuses on computing and using the MAT for solids.

## 1) What the MAT represents

Informally, the medial axis is the set of centres of maximal inscribed balls. It captures:

- thickness and local radius information
- “skeleton” structure of a shape
- critical points where topology or proximity relationships change

For CAD kernels, MAT ideas show up in:
- offsetting and shelling
- feature recognition (thin walls, ribs)
- collision and clearance reasoning

## 2) Critical points and dual space

The book discusses:

- how to identify critical events where the medial structure changes
- representing relationships in a dual space to simplify computation

## 3) Algorithms

Two algorithmic approaches are highlighted:

- multiple start point strategies
- divide-and-conquer strategies

Both reflect a common theme in geometric computing: you need careful control of numeric robustness and of combinatorial explosion.

## 4) Negative MAT, subdivision, and offsetting

Negative MAT and subdivision relate to:
- inward/outward offsets
- handling concavities
- producing practical engineering offsets without self-intersections

## Chapter outline (from the book)

**Major sections**
- 15.2 Mat Of A Solid Object
- 15.3 Calculating Critical Points
- 15.5 The Multiple Start Point Algorithm
- 15.6 The Divide-And-Conquer Algorithm

**Selected subsections**
- 15.2 MAT of a solid object
- 15.2.1 MAT terminology
- 15.3 Calculating critical points
- 15.4 Dual space
- 15.5 The multiple start point algorithm

## Implementation notes

- MAT computation is sensitive to tolerance and to surface/curve intersection accuracy.
- For engineering use, you often want:
  - an approximate MAT that is stable
  - guaranteed bounds on error
- Tie MAT tools to verification:
  - offsets can create self-intersections; detect and resolve them systematically.

## Where MAT connects to everyday CAD

- offsets/shells: MAT highlights where offsets pinch off and self-intersect
- feature inference: thin walls and ribs are “medial” phenomena
- clearance analysis: distance-to-boundary fields are MAT-adjacent concepts

## Practical exercises

- Compute an approximate medial axis for a 2D polygon and use it to estimate local thickness.
