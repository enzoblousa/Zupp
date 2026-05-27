# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Status

Zupp is currently in the **Specification phase** — documentation only, no application code exists. The repository follows **Spec-Driven Development with the RPI Method** (Requirements → Plan → Implementation). Requirements are complete; one pending decision (regulatory compliance) must be resolved before ADRs begin.

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
| `monetizacao.md` | Decided pricing model: R$25 base + R$2.50/km |
| `pendencias.md` | 1 open decision remaining: regulatory compliance (OAB Provimento 205/2021) |
| `proximos-passos.md` | Phase roadmap: Pending → ADRs → Specs → Guides → Tasks |
| `restricoes.md` | Constraints: web-responsive, 3-month deadline, 2 devs, stack PENDING |
| `regulatorio.md` | OAB Provimento 205/2021 compliance notes (PENDING light legal review) |

## Product Overview

On-demand legal services platform connecting clients to nearby lawyers, modeled after ride-hailing apps. Matching is proximity-based; lawyers control availability via an online/offline toggle. National scope from launch.

**MVP features:** authentication, automated lawyer validation (selfie + CNA lookup), online/offline toggle, proximity-based demand dispatch (distance primary, time-online tiebreaker, 30s timeout, 10km max radius), automatic pool removal after accept, in-platform chat.

**Pricing (decided):** R$25 base fee + R$2.50/km traveled by the lawyer. Payment off-platform in MVP; platform shows estimated value before accept.

**Out of scope for MVP:** payment gateway, video calls, admin panel, specialty filtering, favorites, premium profiles.

**Open decision (must be closed before ADRs):**
- Regulatory compliance with OAB Provimento 205/2021 — light legal review (1–2h) required before development starts.
