# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A static "Save the Date" wedding website for Dante & Anjali. No build tools — plain HTML/CSS served via GitHub Pages under a custom domain. No JavaScript.

## Development

Open `index.html` in a browser, or serve locally:

```
python3 -m http.server 8000
```

No build step, no dependencies, no tests. Deployment is automatic via GitHub Pages on push to main.

## File Structure

```
index.html            — page markup and responsive <picture> elements
styles.css            — all styling (layout, typography, responsive breakpoints)
CNAME                 — custom domain (savethedate.danteandanjali.com)
assets/img/           — optimized images in AVIF, WebP, and JPG at multiple resolutions
  wide-{640..3840}.*  — landscape crop for wide viewports
  vertical-{640..1920}.* — portrait crop for narrow/mobile viewports
.originals/           — unoptimized source images (not deployed)
background-wide.jpg   — original wide photo (source for optimized assets)
background-vertical.jpg — original vertical photo (AI-extended portrait crop)
```

## Design

### Layout

- **Full-bleed background photo** fills the entire viewport (`object-fit: cover`)
- **"SAVE the DATE"** in large vertical text, rotated −90° on the left side of the viewport
- **Wedding details** (names, date, venue, city) in smaller serif text, positioned bottom-right
- Gradient scrim overlays (horizontal from left, vertical from bottom) ensure text readability over the photo

### Fonts (Google Fonts)

- **Cormorant Garamond 300** — SAVE / DATE display text (elegant thin serif)
- **Great Vibes** — "the" script accent between SAVE and DATE
- **Libre Baskerville** — wedding details (readable serif)

### Colors

- Text: `#f5f0e8` (cream) with `#e8e0d0` for detail text
- Theme color: `#3d3529`

### Responsive Images

Two art-directed crops of the same photo:

- `wide-*` — landscape crop for viewports >768px
- `vertical-*` — portrait crop for viewports ≤768px

Served via `<picture>` with `<source>` elements providing AVIF → WebP → JPG fallback at resolutions from 640px to 3840px. Font sizes use `clamp()` for fluid scaling across breakpoints.

### Responsive Breakpoints

- **≤768px**: switches to vertical image, adjusts text positioning
- **≤480px**: tighter padding and constrained font sizes
- **≤500px height (landscape)**: minimal font sizes for short viewports
- **≥2000px**: caps font sizes and centers content (max-width 2200px)

## Metadata

- Open Graph and Twitter Card tags for rich link previews
- Canonical URL: `https://savethedate.danteandanjali.com/`
- OG image points to `background-wide.jpg`

## Accessibility

- Screen-reader-only `<h1>` via `.sr-only` class
- `aria-hidden="true"` on decorative visual text
- `aria-label` on main content landmark
- `role="presentation"` on background image
- Text contrast ensured via text-shadow and gradient scrim overlays

## Hosting

GitHub Pages with a custom domain. The `CNAME` file in the repo root contains `savethedate.danteandanjali.com`.
