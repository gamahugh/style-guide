# Physicist — Style Guide

A void-and-spectrum design system with near-black backgrounds, Cherenkov cyan accents, geometric sans-serif headings, instrument readout panels, and the clean precision of a modern physics lab. Intended for technical reports, observation logs, and data-driven documents.

---

## Color Palette

### The Void (Backgrounds)

| Token         | Hex       | Usage                                  |
|---------------|-----------|----------------------------------------|
| `--bg`        | `#08090e` | Page background (near-black, blue tint)|
| `--surface`   | `#11131c` | Cards, observation boxes, panels       |
| `--surface-2` | `#191c28` | Nested surfaces, code backgrounds      |
| `--border`    | `#252838` | Borders, dividers                      |
| `--border-light` | `#323650` | Lighter borders for emphasis        |

### Text

| Token          | Hex       | Usage                                  |
|----------------|-----------|----------------------------------------|
| `--text`       | `#e4e6f0` | Primary — headings, values, emphasis   |
| `--text-dim`   | `#8890a8` | Body paragraphs, descriptions          |
| `--text-faint` | `#4a5068` | Labels, units, metadata                |

### Cherenkov Cyan (Primary Accent)

| Token          | Hex       | Usage                                   |
|----------------|-----------|------------------------------------------|
| `--photon`     | `#22d3ee` | H3 headings, observation borders, primary accent |
| `--photon-dim` | `#0e7490` | Muted cyan, borders, dim labels         |
| `--photon-fill`| `rgba(34,211,238,0.06)` | Callout/tag backgrounds   |

### Spectrum Colors

Each has full, dim, and fill (6% opacity) variants.

| Token     | Hex       | EM Region      | Typical Use            |
|-----------|-----------|----------------|------------------------|
| `--violet`| `#a78bfa` | Ultraviolet    | Hypotheses, theory     |
| `--blue`  | `#60a5fa` | Blue           | Secondary data         |
| `--green` | `#4ade80` | Green          | Constants, confirmed   |
| `--amber` | `#fbbf24` | Yellow/amber   | Laws, established      |
| `--red`   | `#f87171` | Red/infrared   | Experiments, alerts    |

---

## Typography

### Font Stack

| Role      | Family        | Google Fonts Import                    |
|-----------|---------------|----------------------------------------|
| Headings  | Space Grotesk | `Space+Grotesk:wght@400;500;600;700`  |
| Body      | Inter         | `Inter:wght@300;400;500;600`           |
| Mono      | Space Mono    | `Space+Mono:wght@400;700`             |

```html
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;600;700&family=Inter:wght@300;400;500;600&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet">
```

### Type Scale

| Element        | Family        | Size                          | Weight | Notes                       |
|----------------|---------------|-------------------------------|--------|-----------------------------|
| Hero h1        | Space Grotesk | `clamp(3rem, 8vw, 5.5rem)`   | 700    | `letter-spacing: -0.02em`   |
| Section h2     | Space Grotesk | `2rem`                        | 600    | `letter-spacing: -0.01em`   |
| Subsection h3  | Space Grotesk | `1.2rem`                      | 600    | Color: `--photon`           |
| Card title h4  | Space Grotesk | `0.88rem`                     | 600    |                             |
| Body           | Inter         | `0.92rem`                     | 400    | Color: `--text-dim`         |
| Readout value  | Space Grotesk | `1.6rem`                      | 700    | `letter-spacing: -0.02em`   |
| Section label  | Space Mono    | `0.6rem`                      | 400    | Uppercase, `letter-spacing: 0.25em` |
| Tag            | Space Mono    | `0.55rem`                     | 400    | Uppercase, `letter-spacing: 0.1em`  |

**Key convention:** Headings use **negative** letter-spacing for a tight, modern feel. Labels use **positive** letter-spacing for a data-readout feel.

---

## Layout

- **Container:** max-width 880px, centered, 2rem horizontal padding
- **Sections:** 5rem vertical padding, `1px solid var(--border)` top divider
- **Border radius:** 4px on cards, tags, containers (barely rounded, not sharp like Engineer)
- **No grid background** (that's Engineer's thing)
- **No shadows** — depth from surface color layering
- **Full-bleed:** max-width 1040px for diagram containers

---

## Hero Section

- Full viewport, flex-centered, void background
- Dual radial gradient glow (cyan + violet, very subtle)
- Accent `<span>` in `--photon` cyan
- Hero label: Space Mono, uppercase, `--photon-dim`
- Staggered fade-up animation

---

## Components

### Observation Boxes

Five variants for physics statement types:

| Variant      | Class          | Border Color  |
|-------------|----------------|---------------|
| Observation | `.observation`  | `--photon`    |
| Hypothesis  | `.hypothesis`   | `--violet`    |
| Law         | `.law`          | `--amber`     |
| Constant    | `.constant`     | `--green`     |
| Experiment  | `.experiment`   | `--red`       |

Structure:
- `--surface` background, `1px` border, `3px` colored left border, `4px` radius
- Head: Space Mono, uppercase, letter-spaced, in matching color
- Body: Inter, `--text-dim`

### Readout Panel

The signature unique component — instrument-style data display.

- CSS Grid with `1px` gap (borders show through as grid lines)
- `auto-fit, minmax(160px, 1fr)` for responsive columns
- Each cell: monospace label (tiny, faint), large colored value (Space Grotesk, 1.6rem, weight 700), monospace unit
- Color the value via spectrum class on the cell: `.readout-cell.photon`, `.readout-cell.violet`, etc.

### Spectrum Bar

- Full-width gradient bar spanning violet → blue → cyan → green → amber → red
- Default: 4px tall, `border-radius: 2px`
- `.thin` variant: 2px tall
- Use as a decorative section divider or color legend

### Equation Display

- Centered, Space Grotesk, `1.3rem`, weight 500
- Optional right-aligned `.eq-num` in Space Mono
- Upright (not italic — contrast with Mathematician's italic equations)

### Physics Cards (2-Column Grid)

- **Grid:** 2 columns, `1.25rem` gap
- **Card:** `--surface` bg, `1px` border, `4px` radius, `1.5rem` padding
- **Top accent bar:** 2px, color from class (`photon`, `violet`, `blue`, `green`, `amber`, `red`)
- **Card label:** Space Mono, tiny uppercase

### Pipeline

- Flex row with `0.5rem` gap (separated cards, like Excalidraw)
- Arrow (`→`) connector via `::after` pseudo-element
- Top accent bar: 2px via `::before`
- Labels: Space Mono numbers, Space Grotesk names

### Numbered List

- Vertical stack with `0.5rem` gap
- Numbers: Space Grotesk, `1.6rem`, weight 700, `--photon-dim`
- `4px` border-radius on items

### Callout Variants

| Variant  | Class              | Border Color | Background       |
|----------|--------------------|--------------|------------------|
| Default  | `.callout`         | `--photon`   | `--photon-fill`  |
| Warning  | `.callout.warning` | `--amber`    | `--amber-fill`   |
| Danger   | `.callout.danger`  | `--red`      | `--red-fill`     |

### Tags

- Space Mono, `0.55rem`, uppercase, letter-spaced
- Bordered with `1px` solid dim color, fill background, `2px` radius
- Prefix: `t-` (e.g., `t-photon`, `t-violet`)

### Unit Annotation

- Inline `<span class="unit">` for physical units
- Space Mono, `0.7rem`, `--text-faint`

### Tables

- Full width, collapsed borders
- **Headers:** Space Mono, uppercase, `0.6rem`, letter-spaced, `--text-faint`
- **Cells:** `0.85rem`, `--text-dim`, `1px` bottom border
- **First column:** `--text`, weight 500

### Diagram Container

- `--surface` background, `1px` border, `4px` radius
- Label in Space Mono, small uppercase (e.g., "Fig. 01 — Title")
- SVG text in Space Mono
- Nodes: no fill, spectrum-colored strokes, `4px` radius
- Labels: uppercase, letter-spaced
- Connectors: dashed, with small triangle arrowheads in matching color

---

## Comparison with All Systems

| Aspect          | Vesper            | Excalidraw        | Engineer            | Mathematician       | Physicist            |
|-----------------|-------------------|-------------------|---------------------|---------------------|----------------------|
| Theme           | Dark (purple)     | Light (white)     | Dark (navy)         | Dark (green)        | Dark (void/black)    |
| Background      | Flat              | Flat              | Grid overlay        | Flat                | Flat                 |
| Border radius   | 10–16px           | 8px               | 0                   | 0                   | 4px                  |
| Heading font    | DM Serif Display  | Caveat            | Barlow Condensed    | EB Garamond         | Space Grotesk        |
| Body font       | DM Sans           | Nunito            | IBM Plex Sans       | Source Serif 4      | Inter                |
| Mono font       | JetBrains Mono    | Fira Code         | IBM Plex Mono       | JetBrains Mono      | Space Mono           |
| Letter-spacing  | Normal            | Normal            | Positive (wide)     | Normal              | Negative (tight)     |
| Primary accent  | Purple #c4a0ff    | (multi-color)     | Cyan #4fc3f7        | Yellow #f0d060      | Cyan #22d3ee         |
| Color model     | 4 semantic        | 8 stroke + fill   | 1 + 4 status        | 5 chalk             | 1 primary + 5 spectrum |
| Unique elements | —                 | Sticky notes      | Stamps, title block | Theorem/proof, QED  | Readout panel, spectrum bar |
| Vibe            | Editorial         | Whiteboard        | Technical           | Academic            | Laboratory           |
