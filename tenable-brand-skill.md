---
name: "tenable-brand-skill"
author: "nreynolds-pub-git"
github_url: "https://github.com/nreynolds-pub-git/tenable-brand-skill"
description: "Tenable brand guidelines as a Claude skill — colors, typography, accessibility rules, and code snippets for on-brand output"
license: "MIT"
tier: "unreviewed"
tags: ["branding", "design-system", "tenable", "ui", "accessibility", "code-snippets"]
integrations: []
date_added: 2026-06-19
compatible_platforms: ["Claude Code", "Claude Desktop"]
invocation: "/tenable-brand"
---

A Claude Skill that captures the canonical Tenable brand guidelines as a reference Claude loads on demand. Once installed, any Claude chat where you're building UI, dashboards, reports, presentations, or any customer-facing material will automatically produce output that matches Tenable's brand — without you having to paste the guidelines, the color hex codes, or the do's and don'ts every time.

## What it does

The skill provides instant access to:
- Primary color palette with exact hex codes (Soft Black #1E2426, White, Highlight Yellow #E7FF00)
- Accessibility constraints — the six allowed color combinations and two forbidden ones
- Dark mode and light mode tokens with implementation patterns
- Full data palette for charts and canonical severity color mapping for security data
- Typography rules (Aeonik Pro primary, Work Sans fallback with -3% tracking)
- Ready-to-use code snippets: CSS variables, Tailwind config, HTML examples, Python color dicts, python-docx examples

Particularly useful for documents, reportings, presentations, or UX design for anyone at Tenable generating customer-facing artifacts via Claude.

## How it works

The skill triggers automatically when you mention dashboards, reports, visual deliverables, or anything Tenable-branded. It injects the complete brand specification into Claude's context, ensuring all generated code, styles, and design decisions align with Tenable's published brand guidelines without manual reference lookups.
