---
layout: post
title: "B-Rep Modelling Techniques: Chapter 12 — Modeller Access"
date: 2026-02-25 17:40:00 +0800
categories: [graphics, geometry, cad]
series: brep-modelling-techniques
chapter: 12
book_title: "Boundary Representation Modelling Techniques"
book_author: "Ian Stroud"
book_year: 2006
permalink: /graphics/brep-modelling-techniques/ch12-modeller-access/
---

> Study notes for Ian Stroud, *Boundary Representation Modelling Techniques* (Springer, 2006).

A modelling kernel is a library; a modelling system is an interactive environment. This chapter discusses how users and applications *access* modelling capability.

## 1) Command interpreter architecture

The book describes an interpreter-style architecture:

- commands map to modelling operators
- a working stack or context manages intermediate state
- sub-interpreters handle specialized command groups

This is a useful pattern even today because it gives:
- reproducible scripting
- debugging via command traces
- a clean separation between UI and kernel

## 2) Syntax handling and model element identification

Two nontrivial problems:

- parsing user commands (or scripts) into structured operator calls
- identifying model elements robustly (face/edge/vertex selection with stable references)

Element identification touches the hardest CAD problem: **topological naming**. Even if you do not fully solve it, you must provide:
- stable IDs where possible
- mapping tables after operations
- selection references that degrade gracefully

## 3) Multi-user modelling and macros

Once you have a command language and stable persistence, you can:

- support multi-user workflows (at least at the file/assembly level)
- support macros and automation
- offer programmatic APIs

## Chapter outline (from the book)

**Major sections**
- 12.1 Command Interpreter Architecture
- 12.2 Syntax Handling
- 12.3 Model Element Identification
- 12.4 Multi-User Modelling
- 12.5 Command Files And Macro-Languages
- 12.6 Application Programming Interfaces

**Selected subsections**
- 12.1 Command interpreter architecture
- 12.1.1 Working stacks
- 12.1.2 Command structures (sub-interpreters)
- 12.2 Syntax handling
- 12.3 Model element identification

## Implementation notes

- Design your kernel API as a stable ABI boundary (handles/IDs, not raw pointers).
- Treat every modelling operator as:
  - callable from UI
  - callable from scripting
  - serializable for replay (for debugging/regression)
- Add a command log:
  - makes bugs reproducible
  - enables “feature history” style regeneration later

## Access tip: replayability is a superpower

If every operation can be replayed from a command log, you get:

- deterministic debugging
- regression testing
- the backbone of feature history

## Practical exercises

- Design a JSON (or similar) command record format for one operator and implement a replay stub.
