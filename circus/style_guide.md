# Circus — Style Guide

A big-top design system with velvet-dark backgrounds, crimson and gold accents, bold slab-serif headings, playbill programs, admission tickets, tent-stripe dividers, and the dramatic energy of a three-ring show. Intended for event programs, creative briefs, showmanship-forward documents, and anything that should feel like stepping under the big top.

---

## Color Palette

### Velvet Dark (Backgrounds)

| Token          | Hex       | Usage                                  |
|----------------|-----------|----------------------------------------|
| `--bg`         | `#0c0a10` | Page background (deep warm purple-black)|
| `--surface`    | `#141118` | Cards, panels, playbill rows           |
| `--surface-2`  | `#1e1a24` | Nested surfaces, ticket backgrounds    |
| `--border`     | `#2c2634` | Borders, dividers                      |
| `--border-light` | `#3c3448` | Lighter borders for emphasis         |

### Text — Warm Cream

| Token          | Hex       | Usage                                  |
|----------------|-----------|----------------------------------------|
| `--text`       | `#f0e6d8` | Primary — headings, act names          |
| `--text-dim`   | `#908498` | Body paragraphs, descriptions          |
| `--text-faint` | `#584c64` | Labels, ring numbers, metadata         |

### Crimson (Primary Accent)

| Token           | Hex       | Usage                                   |
|-----------------|-----------|------------------------------------------|
| `--crimson`     | `#e82030` | H2 headings, danger spotlight, primary accent |
| `--crimson-dim` | `#8a1420` | Muted crimson, list numbers, dim labels |
| `--crimson-fill`| `rgba(232,32,48,0.07)` | Spotlight/tag backgrounds  |

### Gold (Secondary Accent)

| Token           | Hex       | Usage                                   |
|-----------------|-----------|------------------------------------------|
| `--gold`        | `#f0b020` | H3 headings, playbill header, spotlight default |
| `--gold-dim`    | `#8a6614` | Muted gold, hero label, star dividers   |
| `--gold-fill`   | `rgba(240,176,32,0.07)` | Spotlight/tag backgrounds  |

### Supporting Cast

Each has full, dim, and fill (7% opacity) variants.

| Token     | Hex       | Role              | Typical Use              |
|-----------|-----------|-------------------|--------------------------|
| `--teal`  | `#2abfb0` | Standing ovation  | Success, positive        |
| `--royal` | `#4466cc` | Program note      | Info, references         |
| `--violet`| `#a855cc` | Mystery           | Magic, special           |

---

## Typography

### Font Stack

| Role      | Family          | Google Fonts Import                              |
|-----------|-----------------|--------------------------------------------------|
| Headings  | Alfa Slab One   | `Alfa+Slab+One`                                 |
| Body      | Lato            | `Lato:ital,wght@0,300;0,400;0,700;0,900;1,300;1,400` |
| Mono      | Roboto Mono     | `Roboto+Mono:wght@400;500;600`                  |

```html
<link href="https://fonts.googleapis.com/css2?family=Alfa+Slab+One&family=Lato:ital,wght@0,300;0,400;0,700;0,900;1,300;1,400&family=Roboto+Mono:wght@400;500;600&display=swap" rel="stylesheet">
```

**Key convention:** Alfa Slab One is the heaviest heading font in any system — it only ships at weight 400 but renders like 800+. Use it only for display text. H3 subsections use Lato at weight 900 (the "black" weight) in uppercase gold for a poster-style sub-heading.

### Type Scale

| Element        | Family          | Size                          | Weight | Notes                         |
|----------------|-----------------|-------------------------------|--------|-------------------------------|
| Hero h1        | Alfa Slab One   | `clamp(2.8rem, 7vw, 5rem)`   | 400    |                               |
| Section h2     | Alfa Slab One   | `1.8rem`                      | 400    | Color: `--crimson`            |
| Subsection h3  | Lato            | `0.85rem`                     | 900    | Uppercase, `letter-spacing: 0.15em`, color: `--gold` |
| Card title h4  | Lato            | `0.88rem`                     | 700    |                               |
| Body           | Lato            | `0.92rem`                     | 400    | Color: `--text-dim`           |
| Ring number    | Alfa Slab One   | `1.3rem`                      | 400    | Color: `--text-faint`         |
| Section label  | Roboto Mono     | `0.62rem`                     | 400    | Uppercase, `letter-spacing: 0.2em` |
| Tag            | Roboto Mono     | `0.6rem`                      | 400    | Uppercase, `letter-spacing: 0.08em` |

---

## Layout

- **Container:** max-width 880px, centered, 2rem horizontal padding
- **Sections:** 5rem vertical padding, `1px solid var(--border)` top divider
- **Border radius:** 0 everywhere — sharp poster edges
- **No shadows** — depth from surface colour layering
- **Full-bleed:** max-width 1040px for diagram containers

---

## Hero Section

- Full viewport, flex-centered, velvet-dark background
- Dual radial gradient glow (crimson + gold, very subtle)
- Accent `<span>` in `--gold`
- Hero label: Lato weight 900, uppercase, ultra-wide tracking (0.45em), `--gold-dim` — the "Ladies & Gentlemen" announcer style
- Staggered fade-up animation with longer delays for drama

---

## Components

### Playbill (Program)

The signature unique component — a show program listing.

- **Header:** `--surface-2` background, Lato weight 900 uppercase, `--gold` text, showtime in Roboto Mono
- **Rows:** CSS Grid with 4 columns (`70px 1fr 120px 80px`), `--surface` background
- **Act type classes:** `.acrobat` (crimson), `.comedy` (gold), `.magic` (violet), `.animal` (teal)
- **Responsive:** Ring column hides at 640px

### Grand Parade (Pipeline)

Sequence of acts with star connectors.

- Flex row of parade-act cells, connected by `★` characters via `::after`
- Act names in Alfa Slab One, `--crimson`
- Roman numeral markers (I, II, III, IV) in Roboto Mono
- Crimson top accent bar (3px)

### Admission Ticket

- `inline-flex` layout, `--surface-2` background, `1px` border
- Punched holes: 12px circles via `::before`/`::after`
- Show/Seat sections with tiny Roboto Mono label and Lato name
- Star (★) divider in `--gold-dim`
- "ADMIT ONE" badge: Alfa Slab One, `--crimson`, border-left separated

### Act Cards (2-Column Grid)

- **Grid:** 2 columns, `1.25rem` gap
- **Card:** `--surface` bg, `1px` border, sharp corners, `1.5rem` padding
- **Top accent bar:** 3px, colour from class (`crimson`, `gold`, `teal`, `royal`, `violet`)
- **Ring number:** Alfa Slab One, `1.3rem`, `--text-faint`, Roman numerals

### Spotlight Callouts

| Variant   | Class               | Border Colour | Background       |
|-----------|---------------------|---------------|------------------|
| Default   | `.spotlight`        | `--gold`      | `--gold-fill`    |
| Danger    | `.spotlight.danger` | `--crimson`   | `--crimson-fill` |
| Ovation   | `.spotlight.ovation`| `--teal`      | `--teal-fill`    |
| Note      | `.spotlight.note`   | `--royal`     | `--royal-fill`   |

Structure: `1px` border, `3px` coloured left border, matching fill background.

### Tent Stripe

- Diagonal crimson stripe gradient: `repeating-linear-gradient(-45deg, ...)`
- Default: 8px tall. `.thin` variant: 4px tall
- Use as a decorative section divider evoking circus tent canvas

### Numbered List

- Vertical stack with shared borders (zero gap)
- Numbers: Alfa Slab One, `1.4rem`, `--crimson-dim`
- Sharp corners throughout

### Tags

- Roboto Mono, `0.6rem`, uppercase, letter-spaced
- Bordered with `1px` solid dim colour, fill background, sharp corners
- Prefix: `t-` (e.g., `t-crimson`, `t-gold`, `t-teal`)

### Tables

- Full width, collapsed borders
- **Headers:** Roboto Mono, uppercase, `0.62rem`, letter-spaced, `--text-faint`
- **Cells:** `0.88rem`, `--text-dim`, `1px` bottom border
- **First column:** `--text`, weight 700

### Star Ornament

- Centred decorative divider: `★ ★ ★`
- `--gold-dim` colour, wide letter-spacing (0.5em)

### Diagram Container

- `--surface` background, `1px` border, sharp corners
- Label in Roboto Mono, small uppercase
- SVG text in Lato

---

## Section Label Convention

Sections use three-ring circus numbering:

```
Ring 01 — Palette
Ring 02 — Typography
Ring 03 — Layout
```

Cards use Roman numerals: I, II, III, IV, V.

---

## Comparison with All Systems

| Aspect          | Vesper            | Excalidraw        | Engineer            | Mathematician       | Physicist            | Train Station         | Terminal              | Circus                |
|-----------------|-------------------|-------------------|---------------------|---------------------|----------------------|-----------------------|-----------------------|-----------------------|
| Theme           | Dark (purple)     | Light (white)     | Dark (navy)         | Dark (green)        | Dark (void/black)    | Dark (warm brown)     | Dark (pure black)     | Dark (velvet plum)    |
| Background      | Flat              | Flat              | Grid overlay        | Flat                | Flat                 | Flat                  | Scanlines + vignette  | Flat                  |
| Border radius   | 10–16px           | 8px               | 0                   | 0                   | 4px                  | 0                     | 0                     | 0                     |
| Heading font    | DM Serif Display  | Caveat            | Barlow Condensed    | EB Garamond         | Space Grotesk        | Stint Ultra Expanded  | VT323                 | Alfa Slab One         |
| Body font       | DM Sans           | Nunito            | IBM Plex Sans       | Source Serif 4      | Inter                | Libre Franklin        | Fira Code             | Lato                  |
| Mono font       | JetBrains Mono    | Fira Code         | IBM Plex Mono       | JetBrains Mono      | Space Mono           | Inconsolata           | Share Tech Mono       | Roboto Mono           |
| Letter-spacing  | Normal            | Normal            | Positive (wide)     | Normal              | Negative (tight)     | Natural (expanded)    | Normal                | Normal                |
| Primary accent  | Purple #c4a0ff    | (multi-color)     | Cyan #4fc3f7        | Yellow #f0d060      | Cyan #22d3ee         | Brass #c8a84c         | Green #33ff33         | Crimson #e82030       |
| Color model     | 4 semantic        | 8 stroke + fill   | 1 + 4 status        | 5 chalk             | 1 primary + 5 spectrum| 2 material + 3 signal | 1 primary + 5 ANSI   | 2 headliner + 3 cast  |
| Unique elements | —                 | Sticky notes      | Stamps, title block | Theorem/proof, QED  | Readout panel, spectrum bar | Departures board, ticket stub | Process table, progress bar | Playbill, tent stripe |
| Vibe            | Editorial         | Whiteboard        | Technical           | Academic            | Laboratory           | Railway               | Console               | Showtime              |
