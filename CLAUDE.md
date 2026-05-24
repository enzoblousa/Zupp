# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Status

Zupp is currently in the **Specification phase** — documentation only, no application code exists. The repository follows **Spec-Driven Development with the RPI Method** (Requirements → Plan → Implementation). Development begins after pending decisions and ADRs are closed.

## Documentation Commands

Dependencies: `pip install mkdocs mkdocs-material`

```bash
mkdocs serve              # local preview at http://127.0.0.1:8000
mkdocs build              # generate static site into site/
mkdocs gh-deploy --force  # deploy to GitHub Pages (done by CI on push to main)
```

## Documentation Structure

All docs are in `docs/`, served via `mkdocs.yml` (Material theme, Portuguese).

| File | Content |
|---|---|
| `escopo-mvp.md` | 6 mandatory MVP features — source of truth for scope |
| `pendencias.md` | 4 open decisions that must be closed before ADRs |
| `proximos-passos.md` | Phase roadmap: Pending → ADRs → Specs → Guides → Tasks |
| `restricoes.md` | Constraints: web-responsive, 3-month deadline, 2 devs, stack PENDING |
| `regulatorio.md` | OAB Provimento 205/2021 compliance notes (PENDING analysis) |

## Product Overview

On-demand legal services platform connecting clients to nearby lawyers, modeled after ride-hailing apps. Matching is proximity-based; lawyers control availability via an online/offline toggle. National scope from launch.

**MVP features:** authentication, lawyer registration with hybrid human approval, online/offline toggle, proximity-based demand dispatch (accept/refuse cascades to next nearest), automatic pool removal after accept, in-platform chat.

**Out of scope for MVP:** payment gateway, video calls, admin panel, specialty filtering, favorites, premium profiles.

**Open decisions (must be closed before ADRs):**
1. Monetization and pricing model (payments happen off-platform in MVP)
2. Who/how approves lawyer registrations (no admin persona formalized)
3. Matching tiebreaker and fallback rules
4. Regulatory compliance with OAB Provimento 205/2021
