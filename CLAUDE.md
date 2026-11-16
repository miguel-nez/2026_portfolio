# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development

No build step. Open with VS Code Live Server (default port 5500) and open `http://localhost:5500` in a browser. The `.vscode/tasks.json` is pre-configured to open that URL on folder open.

The site is deployed to `nuneznunez.xyz` via GitHub Pages (see `CNAME`).

## Architecture

A static HTML/CSS portfolio site with no JavaScript framework or bundler. Five pages share a single stylesheet.

**Pages:**
- `index.html` — homepage with hero, work snippet cards, and about section
- `ard.html`, `sds.html`, `tracker.html`, `accessibility.html` — individual case study pages

**Styles:**
- `css/styles.css` — the only stylesheet, shared by all pages. Organised as: reset → tokens → base → sidebar → hero/tags → sections/project cards → about → footer → animations → case study layout (`.cs-*`) → responsive breakpoints

**Key CSS tokens** (defined in `:root`):
- `--ink: #111110` — the single text/border colour used everywhere
- `--sans` — DM Sans (Google Fonts)
- `--sidebar-w: 220px`
- `--page-max: 1600px` — max page width for wide screens

**Layout:**
- Desktop: fixed left sidebar (220px) + scrollable main content offset by `--sidebar-w`
- ≤799px: sidebar collapses to a horizontal top bar; contact links move to the page footer
- ≤1220px: project cards stack vertically

**Scroll animations:** Each page includes an inline `<script>` using `IntersectionObserver` to add the `.in` class to `.fade` elements on scroll. No external JS dependencies.

**Case study pages** share a `.cs-*` class vocabulary: `.cs-header`, `.cs-meta-row`, `.cs-section`, `.cs-body`, `.cs-image`, `.cs-findings`, `.cs-quote`, `.cs-outcomes`, `.cs-next`. Adding a new case study means copying this structure and adding a sidebar nav link in every other page.

**Assets:** `assets/images/<case-study-slug>/` — one subdirectory per case study.
