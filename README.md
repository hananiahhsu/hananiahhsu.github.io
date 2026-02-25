# GitHub Pages Blog

This repository is a lightweight **GitHub Pages + Jekyll (Minima)** blog.

## Structure

- Posts: `_posts/YYYY-MM-DD-title.md`
- Pages:
  - Home: `/` (index.md)
  - Blog: `/blog/`
  - Math column: `/math/`
  - Projects: `/projects/`
  - About: `/about/`

## Publish

Push to the default branch and enable:

- **Settings → Pages → Deploy from a branch**
- Branch: `main` (or your default branch)

## Write a new post

Create a Markdown file:

- `_posts/YYYY-MM-DD-your-title.md`

Example front matter:

```yaml
---
layout: post
title: "Your Title"
date: 2026-02-25 10:00:00 +0800
categories: [cad, architecture]
---
```
