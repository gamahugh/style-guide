# Excalidraw — Style Guide

A light, sketch-inspired design system with handwritten headings, pastel fills, and the friendly whiteboard feel of Excalidraw. Intended for informal documents, brainstorm write-ups, and playful technical reports.

---

## Color Palette

### Canvas & Surfaces

| Token          | Hex       | Usage                                |
|----------------|-----------|--------------------------------------|
| `--bg`         | `#ffffff` | Pure white (hero, overlays)          |
| `--canvas`     | `#fafaf9` | Page background (warm off-white)     |
| `--surface`    | `#ffffff` | Cards, containers                    |
| `--surface-tint` | `#f8f7f5` | Subtle tinted backgrounds          |
| `--border`     | `#d6d3d1` | Card borders, table lines            |
| `--border-sketch` | `#c4c1bc` | Dashed section dividers           |

### Text

| Token          | Hex       | Usage                                |
|----------------|-----------|--------------------------------------|
| `--text`       | `#1e1e1e` | Primary — headings, strong, labels   |
| `--text-mid`   | `#57534e` | Body paragraphs, descriptions        |
| `--text-light` | `#a8a29e` | Captions, metadata, section numbers  |

### Stroke Colors (bold, saturated)

| Token       | Hex       |
|-------------|-----------|
| `--red`     | `#e03131` |
| `--pink`    | `#c2255c` |
| `--purple`  | `#6741d9` |
| `--blue`    | `#1971c2` |
| `--cyan`    | `#0c8599` |
| `--green`   | `#2f9e44` |
| `--lime`    | `#5c940d` |
| `--orange`  | `#f08c00` |

### Pastel Fills (soft backgrounds)

| Token           | Hex       |
|-----------------|-----------|
| `--red-fill`    | `#ffc9c9` |
| `--pink-fill`   | `#fcc2d7` |
| `--purple-fill` | `#d0bfff` |
| `--blue-fill`   | `#a5d8ff` |
| `--cyan-fill`   | `#c3fae8` |
| `--green-fill`  | `#b2f2bb` |
| `--lime-fill`   | `#d8f5a2` |
| `--orange-fill` | `#ffec99` |

### Shadows

| Token         | Value                                |
|---------------|--------------------------------------|
| `--shadow-sm` | `0 1px 3px rgba(0, 0, 0, 0.06)`     |
| `--shadow-md` | `0 2px 8px rgba(0, 0, 0, 0.08)`     |
| `--shadow-lg` | `0 4px 16px rgba(0, 0, 0, 0.1)`     |

---

## Typography

### Font Stack

| Role      | Family       | Google Fonts Import             |
|-----------|--------------|---------------------------------|
| Headings  | Caveat       | `Caveat:wght@400;500;600;700`   |
| Body      | Nunito       | `Nunito:wght@300;400;500;600;700` |
| Mono      | Fira Code    | `Fira+Code:wght@400;500`       |

```html
<link href="https://fonts.googleapis.com/css2?family=Caveat:wght@400;500;600;700&family=Nunito:wght@300;400;500;600;700&family=Fira+Code:wght@400;500&display=swap" rel="stylesheet">
```

### Type Scale

| Element          | Family  | Size                          | Weight |
|------------------|---------|-------------------------------|--------|
| Hero h1          | Caveat  | `clamp(3.5rem, 9vw, 6.5rem)` | 600    |
| Section h2       | Caveat  | `2.8rem`                      | 600    |
| Subsection h3    | Caveat  | `1.8rem`                      | 600    |
| Card title h4    | Nunito  | `0.9rem`                      | 700    |
| Body paragraph   | Nunito  | `0.95rem`                     | 400    |
| Card body        | Nunito  | `0.85rem`                     | 400    |
| Section label    | Caveat  | `1.1rem`                      | 500    |
| Hero label       | Fira Code | `0.7rem`                    | 400    |
| Tag              | Nunito  | `0.7rem`                      | 600    |
| Table header     | Caveat  | `1.1rem`                      | 600    |

---

## Layout

- **Container:** max-width 880px, centered, 2rem horizontal padding
- **Sections:** 5rem vertical padding
- **Section dividers:** dashed lines via `repeating-linear-gradient` (sketch-style, not solid)
- **Depth:** three levels of box-shadow (sm, md, lg) — no surface color layering
- **Full-bleed:** max-width 1060px for diagram containers
- **Responsive:** fluid hero type, card grids collapse to 1 column at 640px

---

## Hero Section

- Full viewport height, flex-centered, white background
- Multi-color radial gradient wash behind content (blue, orange, purple at ~20% opacity)
- Highlighted word in h1 via `<span>` gets a pastel underline marker (rotated orange fill)
- Staggered fade-up animation (0s, 0.1s, 0.2s, 0.3s delays)
- Version tag in Fira Code monospace

---

## Components

### Sketch Cards (2-Column Grid)

- **Grid:** 2 columns, `1.25rem` gap. Single column at `640px`.
- **Card:** white background, `1.5px` border, `border-radius: 8px`, `padding: 1.5rem`, soft shadow
- **Hover:** lift (`translateY(-1px)`) and shadow increase
- **Top accent bar:** 3px, color set by class name (`red`, `blue`, `green`, `orange`, `purple`, `pink`, `cyan`, `lime`)
- **Content:** Icon (emoji, `1.5rem`) → h4 title → body paragraph

### Pipeline (Horizontal Stages)

- Flex row with `0.75rem` gap (separated cards, not connected borders)
- Each stage is a rounded card with a small triangle arrow `::after` pointing right
- Top border: 3px in semantic color via `s-` prefix class
- Labels in Caveat (handwritten), descriptions in Nunito
- Last stage has no arrow

### Numbered List

- Vertical flex column, `0.75rem` gap
- Each item: flex row with large Caveat number (2rem, blue), standard h4 + p content
- White card with border, shadow

### Callout

- White card with `1.5px` border, `3px` left border in blue
- Border-radius: `4px 8px 8px 4px`
- Strong text uses primary text color (not a special accent)

### Tags / Pills

- Bordered pills: `1.5px` solid border in stroke color, pastel fill background
- Nunito at `0.7rem`, weight 600
- Class prefix: `t-` (e.g., `t-red`, `t-blue`)

### Sticky Notes

- Pastel-filled cards with Caveat text
- Slight rotation (`transform: rotate`) for hand-placed feel
- Soft shadow (`--shadow-md`)
- Color classes: `yellow`, `blue`, `green`, `pink`, `purple`

### Highlight Markers

- Inline `<span class="highlight color">` wrapping text
- Pastel underline via `::after` pseudo-element (8px tall, 50% opacity)
- Colors: `yellow`, `blue`, `green`, `pink`, `purple`

### Tables

- Full width, collapsed borders
- **Header:** Caveat handwritten, `1.1rem`, weight 600
- **Body cells:** `0.85rem`, `--text-mid`, light bottom borders (#eee)
- **First column:** `--text`, weight 600

### Diagram Containers

- White card, `1.5px` border, `border-radius: 8px`, `padding: 2rem`, soft shadow
- Label in Caveat (handwritten)
- SVGs use Caveat for text, pastel fills for node backgrounds, stroke colors for borders
- Dashed connectors (`stroke-dasharray: 6,4`) with small triangle arrowheads

---

## Key Differences from Vesper

| Aspect           | Vesper                          | Excalidraw                         |
|------------------|---------------------------------|------------------------------------|
| Theme            | Dark                            | Light                              |
| Backgrounds      | Purple-tinted darks             | Warm white, pure white cards       |
| Depth            | Surface color layering          | Box shadows (sm/md/lg)             |
| Heading font     | DM Serif Display (elegant)      | Caveat (handwritten)               |
| Body font        | DM Sans (clean, light)          | Nunito (rounded, friendly)         |
| Mono font        | JetBrains Mono                  | Fira Code                          |
| Colors           | 4 semantic + accent             | 8 stroke colors + 8 pastel fills  |
| Section dividers | Solid 1px borders               | Dashed sketch lines                |
| Borders          | Subtle, same-tone               | Visible, warm gray                 |
| Unique elements  | —                               | Sticky notes, highlight markers    |
| Vibe             | Editorial, refined, nighttime   | Whiteboard, sketchy, daytime       |
