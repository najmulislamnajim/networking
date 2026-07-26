# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A free, Bangla-language networking course delivered as a static website, hosted on GitHub Pages at `networking.najmulislam.dev` (see `CNAME`). There is **no build system, no dependencies, no tests, and no package manager** — every page is a hand-written, self-contained HTML file with all CSS inlined in a `<style>` block and any JS inlined in a `<script>` block.

To preview a change, open the HTML file directly in a browser (or run any static server such as `python -m http.server`). Deployment is automatic: push to `main` and GitHub Pages serves the files as-is.

## Page structure

- `index.html` — landing page. Distinct layout (topbar, hero, course cards, roadmap, FAQ, footer). Links out to the four course pages.
- `zero.html` → `beginner.html` → `intermediate.html` → `deep-dive.html` — the four learning levels, in order. These are the content pages and share a common layout: a sticky sidebar `<aside>` table of contents + a `<main>` column of `<section class="chapter">` blocks. Each course builds on the previous one (Zero = no prior knowledge → Deep Dive = CCNA exam prep).

The four course pages share the same design system but each carries its own copy of the CSS. Editing shared styling means changing each file — there is no shared stylesheet.

## Conventions

- **Language**: All user-facing content is Bengali (`lang="bn"`), including Bengali numerals (০০, ০১…) for chapter/level numbers. Technical terms (TCP, OSI, VLAN, ping) stay in English/Latin script. Keep both.
- **Design system**: Colors come from CSS custom properties defined in `:root` — a warm "paper" palette (`--paper`, `--ink`, `--line`) with accent colors (`--teal`/`--accent`, `--rust`/`--accent2`, blue, plum). Each level has a signature accent color used consistently on `index.html` cards and inside that level's page. Reuse these variables rather than hardcoding hex values.
- **Fonts**: `Hind Siliguri` for Bangla body text, `JetBrains Mono` for code, numbers, and eyebrow/kicker labels — loaded from Google Fonts. The `.mono` class applies the mono font.
- **Diagrams** are hand-authored inline SVG (network topologies, packet layouts, TCP handshakes), often with SVG `<animate>` for packet-flow effects. When adding diagrams, follow this inline-SVG approach rather than pulling in image files or libraries.
- **Sidebar TOC**: the `<aside>` nav anchors must stay in sync with the `id`s on the `<section class="chapter">` elements in `<main>`; the active-link highlighting relies on those anchors.

When adding or editing content, match the surrounding chapter's structure and the analogy-first, then diagram, then hands-on-command teaching pattern the course uses throughout.
