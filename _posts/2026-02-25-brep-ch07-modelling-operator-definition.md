---
layout: post
title: "B-Rep Modelling Techniques: Chapter 07 — Modelling Operator Definition"
date: 2026-02-25 16:00:00 +0800
categories: [graphics, geometry, cad]
series: brep-modelling-techniques
chapter: 7
book_title: "Boundary Representation Modelling Techniques"
book_author: "Ian Stroud"
book_year: 2006
permalink: /graphics/brep-modelling-techniques/ch07-modelling-operator-definition/
---

> Study notes for Ian Stroud, *Boundary Representation Modelling Techniques* (Springer, 2006).

This chapter is about *how to design modelling operations*, not just how to implement them. It treats an operator as a product feature: requirements, decomposition, and pathological cases.

## 1) Define requirements like an engineer

A modelling operator is constrained by:

- what the user expects (interaction contract)
- what the representation can support
- what manufacturing or downstream tools require
- what robustness policies allow (tolerances, degeneracies)

The book groups operations into classes such as:
- finishing/manufacturing-style operations
- conversion operations (degenerate/non-manifold conversions, partial models)
- other general modifications

## 2) Task decomposition: from intention to kernel steps

The recommended approach is “pipeline decomposition”:

1. identify the topological neighbourhood affected
2. compute geometric constructions (offsets, intersections, projections)
3. apply controlled topological edits (often in Euler-operator style)
4. rebuild trims and loops
5. validate + heal

This decomposition is exactly what makes complex operators debuggable.

## 3) Pathological conditions

The chapter stresses that you must design for bad cases:

- tiny edges and sliver faces
- tangency and near-tangency
- coincident or nearly coincident faces
- self-intersections produced by offsets
- ambiguous trimming due to tolerance overlaps

The difference between a prototype kernel and an industrial one is how well you **predict and handle** these.

## 4) Examples

The examples show how to take a practical modelling intent (e.g., machining-like operations) and decompose it into robust steps that operate on the representation.

## Chapter outline (from the book)

**Major sections**
- 7.1 Definition Of Requirements
- 7.2 Task Decomposition
- 7.3 Pathological Conditions
- 7.4 Examples

**Selected subsections**
- 7.1 Definition of requirements
- 7.1.1 Finishing and manufacturing operations
- 7.1.2 Converting degenerate models and parts of models
- 7.1.3 Other operations
- 7.2 Task decomposition
- 7.2.1 Finishing operation task decomposition
- 7.2.2 Model conversion task decomposition
- 7.2.3 Complex operation task decomposition

## A reusable template for operator specs

When you implement an operator in your kernel, write the spec as:

- **Purpose:** what it does, what it doesn’t do
- **Inputs:** selected entities + parameters
- **Outputs:** modified topology + created faces/edges
- **Preconditions:** validity requirements
- **Algorithm:** stepwise stages
- **Heuristics:** tolerance and healing decisions
- **Failure modes:** how you report and how you recover
- **Validation:** what checks must pass

Do this and you will debug 10× faster.

## Operator specification: why it’s worth the time

A spec forces you to make explicit decisions about:

- tolerances used (and where)
- which degeneracies you accept vs reject
- how you choose between multiple valid results (determinism)

This becomes critical for regression testing: the same input must produce the same output.

## Practical exercises

Write an operator spec for “draft faces”:
- what faces can be drafted?
- how do you treat tangency chains?
- what happens when drafted faces self-intersect?
