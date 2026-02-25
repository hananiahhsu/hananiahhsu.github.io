---
layout: post
title: "B-Rep Modelling Techniques: Chapter 04 — Euler Operators"
date: 2026-02-25 15:00:00 +0800
categories: [graphics, geometry, cad]
series: brep-modelling-techniques
chapter: 4
book_title: "Boundary Representation Modelling Techniques"
book_author: "Ian Stroud"
book_year: 2006
permalink: /graphics/brep-modelling-techniques/ch04-euler-operators/
---

> Study notes for Ian Stroud, *Boundary Representation Modelling Techniques* (Springer, 2006).

Euler operators are the “surgery tools” of topological modelling. They let you modify a B-Rep while preserving global consistency conditions.

## What are Euler operators?

They are primitive operations that change topology in a controlled way while maintaining a valid relationship between counts of entities (the Euler–Poincaré style invariants). In practice, they are used to:

- build solids incrementally
- ensure topological correctness during splitting/merging
- provide a small, verifiable basis for more complex modelling operators

## 1) Spanning sets and decompositions

The book discusses constructing a model via a decomposition into primitives:

- choose a spanning set of entities
- build connectivity step-by-step
- ensure each step preserves validity

A useful way to think about it: Euler operators define **legal moves** on the topology graph.

## 2) Restrictions and real-world constraints

In commercial kernels, “legal” is stricter than the mathematical invariant:

- manifoldness constraints (if you require 2-manifold solids)
- orientation consistency
- geometric coherence (the geometry attached to new topology must make sense)
- tolerance constraints and coincidence handling

So in practice, Euler operators come with **preconditions** and **postconditions**.

## Chapter outline (from the book)

**Major sections**
- 4.1 Spanning Sets And Decompositions
- 4.2 Restrictions

**Selected subsections**
- 4.1 Spanning sets and decompositions
- 4.2 Restrictions

## Implementation notes (practical)

- Treat Euler operations as *internal kernel primitives*, not user-facing features.
- For each operator, define:
  - required existing entities (inputs)
  - created entities (outputs)
  - link updates (who points to whom)
  - invariants to validate (counts, orientation, loop closure)
- Make them transaction-friendly:
  - either all updates apply, or you roll back cleanly (especially important during boolean/sweep operations).

## Testing strategy

For each primitive:

1. Create the smallest model where the operator applies.
2. Apply operator.
3. Run automated validation:
   - topological graph traversal covers expected closure
   - Euler characteristic checks (if applicable)
   - geometric endpoints within tolerance
4. Apply inverse or complementary operations (where defined) and check you return to an equivalent topology.

## How Euler operators map to modern kernels

Even if you don’t expose Euler operators directly, your kernel will implement equivalents for:

- splitting/merging edges
- splitting faces by curves
- creating/deleting holes
- adding/removing handles (genus changes)

Treat them as **audited primitives** and keep their implementation small and well tested.

## Practical exercises

- Pick one operation (e.g., “split an edge at a parameter t”) and define:
  - which entities are created
  - which references are updated
  - which invariants you check after the split
