# Mathematician — Style Guide

A chalkboard-inspired design system with academic serif typography, chalk-colored accents, theorem/proof structure, and the quiet rigor of a mathematics lecture hall. Intended for formal write-ups, research notes, and structured arguments.

---

## Color Palette

### Chalkboard Surfaces

| Token         | Hex       | Usage                                  |
|---------------|-----------|----------------------------------------|
| `--bg`        | `#1a2b1a` | Page background (deep matte green)     |
| `--surface`   | `#1e321e` | Theorem boxes, cards, diagram panels   |
| `--surface-2` | `#243a24` | Nested surfaces, code backgrounds      |
| `--border`    | `#2e4c2e` | Borders, dividers                      |
| `--border-light` | `#3a5e3a` | Proof indent lines, lighter borders |

### Chalk (Text)

| Token          | Hex       | Usage                                    |
|----------------|-----------|------------------------------------------|
| `--chalk`      | `#e8e4d4` | Primary — headings, emphasis, theorems   |
| `--chalk-dim`  | `#a8a492` | Body text, proofs, descriptions          |
| `--chalk-faint`| `#6a7a6a` | Labels, section numbers, captions        |

### Chalk Accent Colors

Each has full, dim, and fill (7% opacity) variants.

| Token      | Hex       | Role                               |
|------------|-----------|-------------------------------------|
| `--yellow` | `#f0d060` | Theorems, primary results, h3 color |
| `--blue`   | `#7ab8e0` | Lemmas, supporting results          |
| `--pink`   | `#e88898` | Definitions                         |
| `--green`  | `#80c898` | Corollaries                         |
| `--orange` | `#e0a060` | Examples                            |

---

## Typography

### Font Stack

| Role      | Family         | Google Fonts Import                          |
|-----------|----------------|----------------------------------------------|
| Display   | EB Garamond    | `EB+Garamond:ital,wght@0,400;0,500;0,600;0,700;1,400;1,500` |
| Body      | Source Serif 4 | `Source+Serif+4:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400` |
| Mono      | JetBrains Mono | `JetBrains+Mono:wght@400;500`               |

```html
<link href="https://fonts.googleapis.com/css2?family=EB+Garamond:ital,wght@0,400;0,500;0,600;0,700;1,400;1,500&family=Source+Serif+4:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
```

### Type Scale

| Element        | Family         | Size                          | Weight      | Notes                    |
|----------------|----------------|-------------------------------|-------------|--------------------------|
| Hero h1        | EB Garamond    | `clamp(2.8rem, 7vw, 4.8rem)` | 500, italic | Italic by default        |
| Section h2     | EB Garamond    | `2rem`                        | 500         | Upright                  |
| Subsection h3  | EB Garamond    | `1.35rem`                     | 500, italic | Color: `--yellow`        |
| Card title h4  | EB Garamond    | `1rem`                        | 600         |                          |
| Body           | Source Serif 4 | `0.95rem`                     | 400         | Color: `--chalk-dim`     |
| Theorem body   | Source Serif 4 | `0.92rem`                     | 400         | `em` in `--chalk`        |
| Section label  | EB Garamond    | `0.9rem`                      | 400, italic | Uses §n notation         |
| Tag            | EB Garamond    | `0.75rem`                     | 400, italic | Underline instead of bg  |
| Table header   | EB Garamond    | `0.85rem`                     | 600, italic |                          |

**Key conventions:**
- h1 and h3 are italic; h2 is upright
- Heavy use of italics for mathematical terms (via `<em>`)
- Both display and body fonts are serif

---

## Layout

- **Container:** max-width **760px** (narrower than other systems — academic text is narrow)
- **Sections:** 4.5rem vertical padding
- **Section dividers:** centered asterism `* * *` (via `::before` pseudo-element on `section + section`)
- **Section numbering:** uses § symbol — `§1 — Name`
- **Line height:** 1.8 on body (generous for mathematical readability)
- **Full-bleed diagrams:** max-width 960px
- **No border-radius** on any component

---

## Hero Section

- Full viewport, flex-centered, dark green background
- Subtle radial gradient glow (yellow, 3% opacity)
- h1 is **italic** by default; accent `<span>` is yellow and non-italic
- Hero label: monospace, uppercase (the only uppercase element)
- Version/date string in monospace
- Staggered fade-up animation

---

## Components

### Theorem Boxes

The signature component. Six variants:

| Variant      | Class         | Border Color  | Head Class         |
|-------------|---------------|---------------|--------------------|
| Theorem     | `.theorem`    | `--yellow`    | `.theorem-head`    |
| Lemma       | `.lemma`      | `--blue`      | `.lemma-head`      |
| Definition  | `.definition` | `--pink`      | `.definition-head` |
| Corollary   | `.corollary`  | `--green`     | `.corollary-head`  |
| Example     | `.example`    | `--orange`    | `.example-head`    |
| Remark      | `.remark`     | `--chalk-faint` | `.remark-head`   |

Structure:
- `--surface` background, `1px` border, `3px` colored left border
- Head: EB Garamond, weight 700, uppercase, letter-spaced, in the matching color
- Body: Source Serif 4, `--chalk-dim`. Use `<em>` for variables (renders in `--chalk`)

### Proof Block

- Left padding + thin `--border-light` left border (no background color)
- Opens with `.proof-head` ("Proof." in italic)
- Closes with `.qed` (&#8718; symbol, right-aligned)
- Body in `--chalk-dim`

### Equation Display

- Centered flex container, padding `2rem`
- EB Garamond, `1.3rem`, italic
- Optional right-aligned `.eq-num` for equation numbering: `(1)`, `(2)`, etc.

### Chalk Cards (2-Column Grid)

- **Grid:** 2 columns, `1.25rem` gap. Single column at `640px`.
- **Card:** `--surface` background, `1px` border, no border-radius, `1.5rem` padding
- **Top accent bar:** 2px, set by color class (`yellow`, `blue`, `pink`, `green`, `orange`)
- **Card label:** EB Garamond italic in `--chalk-faint`

### Pipeline

- Connected stages (shared borders), same as Engineer
- Labels: roman numerals in italic serif (`i.`, `ii.`, `iii.`)
- Names in EB Garamond, weight 600
- Top border: 2px in chalk color via `s-` prefix

### Numbered Propositions

- CSS counter auto-numbering (no manual numbers needed)
- Items separated by `1px` border lines (top and bottom)
- Numbers: EB Garamond, `1.2rem`, weight 600, `--yellow-dim`
- h4 titles are italic

### Callout (Nota Bene)

- Entire callout is italic (via `font-style: italic` on container)
- `--surface` background, `1px` border, `3px` left border in `--chalk-faint`
- `<strong>` inside renders upright and in full `--chalk` (typically "N.B." prefix)

### Margin Note

- Small italic aside: Source Serif 4, `0.78rem`, `--chalk-faint`
- Left padding + thin left border
- Quieter than a callout — for supplementary remarks

### Tags

- EB Garamond italic, `0.75rem`
- Styled with an **underline** (bottom border) instead of a background fill
- Color classes: `t-yellow`, `t-blue`, `t-pink`, `t-green`, `t-orange`

### Tables

- Full width, collapsed borders
- **Headers:** EB Garamond, italic, `0.85rem`, weight 600, `--chalk-faint`, `2px` bottom border
- **Cells:** `0.88rem`, `--chalk-dim`, `1px` bottom border
- **First column:** `--chalk`, weight 500

### Diagram Container

- `--surface` background, `1px` border, no border-radius
- Diagram label: EB Garamond italic
- Diagram caption: Source Serif 4, centered, italic, `--chalk-faint`
- SVG text: EB Garamond (serif italic for mathematical letters)
- Arrows: simple solid lines with small chevron markers in `--chalk-dim`
- Labels on arrows in chalk accent colors (yellow for morphisms, blue for secondary)

---

## Comparison with Other Systems

| Aspect          | Vesper               | Excalidraw            | Engineer               | Mathematician           |
|-----------------|----------------------|-----------------------|------------------------|-------------------------|
| Theme           | Dark (purple)        | Light (warm white)    | Dark (navy)            | Dark (green)            |
| Background      | Flat                 | Flat                  | Grid overlay           | Flat                    |
| Border radius   | 10–16px              | 8px                   | 0                      | 0                       |
| Heading font    | DM Serif Display     | Caveat (handwritten)  | Barlow Condensed (caps)| EB Garamond (italic)    |
| Body font       | DM Sans              | Nunito                | IBM Plex Sans          | Source Serif 4          |
| Mono font       | JetBrains Mono       | Fira Code             | IBM Plex Mono          | JetBrains Mono          |
| Body serif?     | No (sans)            | No (sans)             | No (sans)              | Yes (both serif)        |
| Color model     | 4 semantic           | 8 stroke + fill       | 1 accent + 4 status    | 5 chalk colors          |
| Section divider | Solid border         | Dashed line           | Solid border           | Asterism (* * *)        |
| Section labels  | `01 — Label`         | `01 — Label`          | `SEC 01 — Label`       | `§1 — Label`            |
| Unique elements | —                    | Sticky notes          | Stamps, title blocks   | Theorem/proof, QED, equations |
| Vibe            | Editorial, refined   | Sketch, whiteboard    | Technical, precise     | Academic, rigorous       |
