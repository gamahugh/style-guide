# HTML Document Style Guide

A dark, editorial design system for single-page HTML documents. Purple-tinted surfaces, semantic color coding, and clean typographic hierarchy.

**[Live Style Guide](https://gamahugh.github.io/style-guide/)** · **[Starter Template](https://gamahugh.github.io/style-guide/template.html)**

## Files

| File | Purpose |
|------|---------|
| `index.html` | Live style guide — the design system rendered in its own style |
| `style_guide.md` | Full reference — color tokens, type scale, spacing, component specs |
| `tokens.css` | Drop-in stylesheet with all variables, reset, and component styles |
| `template.html` | Starter document with every component wired up and ready to customize |

## Quick Start

1. Copy `template.html` and `tokens.css` into your project
2. Edit the hero, sections, and components in the HTML
3. Refer to `style_guide.md` for detailed specs when needed

## Fonts

The system uses three Google Fonts loaded via CSS import in `tokens.css`:

- **DM Serif Display** — headings (h1–h3, decorative numbers)
- **DM Sans** — body text, card titles, table content
- **JetBrains Mono** — labels, tags, metadata, section numbers

## Color System

Dark backgrounds with a purple undertone. Text uses a three-tier hierarchy (primary, dim, faint). Four semantic accent colors for categorization:

| Color | Token | Hex |
|-------|-------|-----|
| Purple (accent) | `--accent` | `#c4a0ff` |
| Green | `--capture` | `#6ecfb5` |
| Amber | `--refine` | `#f0b866` |
| Red | `--execute` | `#f07272` |
| Blue | `--batch` | `#6aaef0` |

## Components

- **Hero** — full-viewport title section with fade-up animation
- **Flow Cards** — 2-column grid with colored top accent bars
- **Pipeline** — horizontal connected stages for linear processes
- **Principle List** — numbered items with serif numbers
- **Callout** — left-bordered aside for important notes
- **Tags** — small monospace pills with tinted backgrounds
- **Tables** — minimal borders, uppercase headers
- **Diagram Containers** — rounded surface panels for SVGs

See `template.html` for working examples of each component.
