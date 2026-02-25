---
layout: post
title: "B-Rep Modelling Techniques: Chapter 08 — Product Modelling"
date: 2026-02-25 16:20:00 +0800
categories: [graphics, geometry, cad]
series: brep-modelling-techniques
chapter: 8
book_title: "Boundary Representation Modelling Techniques"
book_author: "Ian Stroud"
book_year: 2006
permalink: /graphics/brep-modelling-techniques/ch08-product-modelling/
---

> Study notes for Ian Stroud, *Boundary Representation Modelling Techniques* (Springer, 2006).

The key theme here is that “product modelling” is not a separate system you bolt on later. It must live alongside geometry and topology so information survives modelling edits.

## 1) Product modelling as layered information

The chapter explains that a model carries multiple kinds of information, including:

- shape geometry/topology
- modifiers that change shape (features, parameters)
- passive information (names, IDs, materials)
- constraints and connections
- free-standing geometry (datums, references)
- mechanisms/linkages

This leads to the concept of **information classes**: how different categories of data attach to and propagate with the model.

## 2) Information classes (categories)

The book proposes categories (a practical taxonomy), roughly spanning:

- the basic shape of the model
- shape modifiers
- features
- passive information
- constraints
- geometric frameworks (datum systems)
- connections / mechanisms

The important engineering problem is propagation:

- When you split a face, where does the metadata go?
- When you merge edges, how do you merge IDs and feature ownership?
- When you boolean two parts, how do constraints and assembly semantics update?

## 3) Handling information during modelling

A robust kernel needs explicit policies:

- attachment models: entity-based, region-based, or feature-based attachments
- identity rules: stable IDs vs. regenerated IDs (and how to map them)
- ownership: which higher-level object “owns” a given face/edge
- persistence: serialization of both geometry and product data

## Chapter outline (from the book)

**Major sections**
- 8.1 Product Modelling
- 8.2 Information Classes
- 8.3 Handling Information During Modelling

**Selected subsections**
- 8.1 Product modelling
- 8.1.1 Design information
- 8.1.2 Customer-based order information
- 8.1.3 Production planning information
- 8.2 Information classes
- 8.2.1 Category 1 - shape
- 8.2.2 Category 2 - shape modifiers
- 8.2.3 Category 3 - features
- 8.2.4 Category 4 - attributes
- 8.2.5 Category 5 - constraints
- 8.2.6 Category 6 - free-standing geometry
- 8.2.7 Category 7 - connections

## Practical notes for your blog / your kernel

- Separate “core topology IDs” from “product IDs”.
- Treat metadata as travelling with **topological regions**, not with raw geometry.
- Provide a mechanism for “retargeting” information after topology changes (the beginning of topological naming).
- Keep an audit trail:
  - operator applied
  - entities created/deleted
  - mapping from old → new entities

That audit trail becomes the backbone for feature history and for debugging.

## Product data propagation is the “topological naming” problem in disguise

When topology changes, attachments must be remapped:

- face splits: metadata must be distributed
- edge merges: IDs and ownership must merge deterministically
- booleans: you need operand attribution (“which part did this face come from?”)

Treat mapping as a first-class output of each operator.

## Practical exercises

- Design an `EntityMap` structure that records:
  - old → new mapping (1→N, N→1, deleted)
  - provenance tags (operand A/B, feature ID)
