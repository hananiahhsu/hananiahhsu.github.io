---
layout: post
title: "B-Rep Modelling Techniques: Chapter 09 — Feature Modelling"
date: 2026-02-25 16:40:00 +0800
categories: [graphics, geometry, cad]
series: brep-modelling-techniques
chapter: 9
book_title: "Boundary Representation Modelling Techniques"
book_author: "Ian Stroud"
book_year: 2006
permalink: /graphics/brep-modelling-techniques/ch09-feature-modelling/
---

> Study notes for Ian Stroud, *Boundary Representation Modelling Techniques* (Springer, 2006).

Feature modelling is where CAD becomes *design intent* rather than just geometry editing. This chapter explains both the **data structures** for features and the workflow for feature-based creation and recognition.

## 1) Feature datastructures

The chapter introduces structures that bind “a feature” to parts of the B-Rep:

- **feature facesets**: groups of faces/edges that constitute the feature’s geometric footprint
- **feature frames**: reference frames / datum context used to define the feature parameters

In modern terms, this is the bridge from:
- parametric definitions → generated boundary model
- boundary model → recognized features

## 2) Manual feature acquisition

Before automated recognition, a system must support:
- selecting faces/edges that represent a feature
- validating the selection against feature type constraints
- generating feature parameters from geometry (inference)

This is critical for edit workflows (redefine a feature from geometry) and for imported models.

## 3) Design by features

Feature-based creation becomes a pipeline:

- create a feature definition (sketch, dimensions, references, parameters)
- generate geometry
- apply a modelling operator (e.g., cut, boss, fillet)
- store mapping and ownership so the feature can be edited later

## 4) Feature recognition and verification

Feature recognition is treated as:

- identify candidate regions in the B-Rep
- classify shapes/topologies that match known patterns
- verify against geometric constraints and tolerances
- attach a feature object back onto the model

Recognition is never perfect; robust verification is essential.

## Chapter outline (from the book)

**Major sections**
- 9.1 Feature Datastructures
- 9.3 Design By Features
- 9.4 Feature Recognition
- 9.6 Structuring Features

**Selected subsections**
- 9.1 Feature datastructures
- 9.1.1 Feature facesets
- 9.1.2 Feature frames
- 9.2 Manual feature acquisition
- 9.3 Design by features
- 9.3.1 Adding features to a shape
- 9.3.2 Building objects from isolated features
- 9.4 Feature recognition
- 9.4.1 Classic feature recognition

## Implementation takeaways

- Design a **feature object model** that can:
  - own topology subsets
  - regenerate geometry/topology from parameters
  - rebuild ownership after editing (mapping)
- Build recognition in layers:
  1) simple primitives (holes, pockets, bosses)
  2) blends (fillets/chamfers)
  3) interacting features (patterns, multi-step)
- Keep feature verification separate from recognition heuristics:
  - recognition suggests
  - verification proves (or rejects)

## Feature modelling: three contracts

A robust feature system must satisfy:

1. **Creation contract**: parameters + references → geometry/topology.
2. **Edit contract**: change parameters → regen, with stable mappings.
3. **Query contract**: geometry/topology → recover feature meaning (recognition/inference).

Most systems nail (1) but struggle with (2) and (3). The chapter highlights why (2)/(3) need explicit datastructures.

## Practical exercises

- Define a minimal feature object with:
  - definition parameters
  - references (datum/edges/faces)
  - owned topology set
  - mapping after regeneration
