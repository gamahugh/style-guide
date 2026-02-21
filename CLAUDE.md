# CLAUDE.md

This repo contains **Vesper**, an HTML/CSS style guide and template system for creating dark-themed, editorial single-page documents.

## Repo Structure

- `style_guide.md` — Detailed style reference (colors, typography, spacing, component specs)
- `tokens.css` — Complete drop-in stylesheet with CSS custom properties and all component styles
- `template.html` — Starter HTML file demonstrating every component
- `README.md` — Overview and quick start

## Style Rules

When creating or modifying HTML documents in this style:

- Use CSS custom properties defined in `tokens.css` — never hardcode color values
- Headings (h1–h3) use **DM Serif Display**. Body text and card titles use **DM Sans**. Labels, tags, and metadata use **JetBrains Mono**
- Body text defaults to `--text-dim`. Use `--text` for headings and `<strong>`. Use `--text-faint` for labels and captions
- Sections are numbered with monospace labels in the format `01 — Label`
- Flow cards require a semantic class (`capture`, `refine`, `execute`, `batch`, or `accent`) for the colored top bar
- Pipeline stages require a semantic class prefixed with `s-` (e.g., `s-capture`)
- Tags require a class prefixed with `t-` (e.g., `t-capture`)
- Container max-width is 900px. Use `full-bleed` class on diagram wraps to expand to 1100px
- Keep the four semantic color categories (green/amber/red/blue) consistent — map them to whatever domain concepts fit, but maintain the visual meaning of each color
- SVG diagrams: use `DM Sans` for text, dashed lines for connections (`stroke-dasharray: 4,3`), and `rx="12"` for node rounded corners
