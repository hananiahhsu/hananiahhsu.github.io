---
layout: post
title:  "SolidDesigner/Alice: what I'm building"
date:   2025-10-08 20:00:00 +0800
categories: cad architecture
---

I’m building **SolidDesigner/Alice**, a modular CAD/BIM platform.

### Goals

- **Creo/NX-level UX parity** where it matters: workbenches, Ribbon, feature history, selection, view behaviors.
- **Commercial-grade document model**: stable IDs, robust serialization, upgrade paths.
- **Geometry-first engineering**: OCCT B-Rep, topological naming, reliable regen.
- **Scalable rendering**: representation → display → render pipeline; OCCT Viewer as the first backend.

### How this blog helps

I use the blog as a public lab notebook:

- design constraints & tradeoffs
- architecture diagrams
- debugging postmortems
- math foundations that show up in real engineering
