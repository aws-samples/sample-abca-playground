# AGENTS.md

Static HTML/CSS travel site deployed as-is to GitHub Pages. No build step, no framework, no JS.

## Commands

Tooling is managed by [mise](https://mise.jdx.dev) (`mise.toml`); it installs the linters on demand.

- `mise run build` — validate HTML is well-formed (`html-validate`)
- `mise run lint` — `htmlhint` + `stylelint`

Run these before committing; a push to `main` deploys straight to GitHub Pages via `.github/workflows/static.yml` (no gate). There are no tests.

## Structure

- `*-region.html` (5 continents) — the **only** files that use the shared `region.css`.
- `*-guide.html` (6 destinations) + `index.html` + `destinations.html` — each carries its own `<style>` block; there is no shared stylesheet for these. Match a sibling page's inline conventions when editing.

When adding a page, keep the Google Fonts `<link>` preconnect/stylesheet block consistent with existing pages, and pick region.css vs. inline styles based on whether it's a region or guide page.
