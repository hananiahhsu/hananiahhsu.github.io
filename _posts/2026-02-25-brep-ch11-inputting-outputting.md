---
layout: post
title: "B-Rep Modelling Techniques: Chapter 11 — Inputting and Outputting"
date: 2026-02-25 17:20:00 +0800
categories: [graphics, geometry, cad]
series: brep-modelling-techniques
chapter: 11
book_title: "Boundary Representation Modelling Techniques"
book_author: "Ian Stroud"
book_year: 2006
permalink: /graphics/brep-modelling-techniques/ch11-inputting-outputting/
---

> Study notes for Ian Stroud, *Boundary Representation Modelling Techniques* (Springer, 2006).

Input/output is where modelling systems meet reality: persistence, interoperability, and long-term maintainability.

## 1) Writing to disk: persistence is a design decision

A modeller must decide:

- what constitutes the “truth” (B-Rep only? plus history? plus attributes?)
- how to store topological graphs (IDs, references, ownership)
- how to store geometry (analytic parameters, NURBS, trims, p-curves)
- how to store product modelling information (constraints, assemblies, metadata)

## 2) Reading from disk and backward compatibility

Reading is harder than writing because:

- files live for years
- schemas evolve
- bugs in old versions become data you must accept

This requires:
- versioning
- upgrade pipelines
- robust validation + healing at load time

## 3) Communication with other modellers and STEP

Interoperability introduces:

- representation mismatch (e.g., different trim conventions)
- tolerance mismatch
- topology naming mismatch
- attribute mapping issues

STEP is discussed as an exchange route, but the deeper point is: exchange formats force you to clearly define **what your kernel means** by face/edge/loop, surface parameterization, and tolerances.

## 4) Printing models

“Printing” is not just output; it tests your ability to generate:
- stable drawing edges / silhouettes
- hidden line views
- sectioned views
- annotation placement

## Chapter outline (from the book)

**Major sections**
- 11.1 Writing To Disc
- 11.2 Reading From Disc
- 11.3 Reading Old Discfiles
- 11.4 Examples
- 11.6 Communication With Other Modellers
- 11.7 Step

**Selected subsections**
- 11.2 Reading from disc
- 11.3 Reading old discfiles
- 11.4 Examples

## Implementation checklist

- Add explicit file format versioning.
- Store stable IDs and references (with integrity checks).
- Implement:
  - `Load → Validate → Heal → Upgrade → Save`
- Separate “core geometry/topology” from “derived caches” (meshes, acceleration structures).
- Provide export/import test suites with known-good reference models.

## Persistence tip: store intent when possible

If you only store final B-Rep, you lose:

- parametric definitions
- feature history
- constraints
- provenance/mapping

If you store both:
- you gain editability
- but you must support upgrade paths and regeneration consistency

## Practical exercises

- Add a versioned schema section to your file format and implement a “migration” stub (even if it does nothing yet).
