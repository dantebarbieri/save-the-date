# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A static "Save the Date" wedding website. No build tools — plain HTML/CSS/JS served via GitHub Pages under a custom domain.

## Development

Open `index.html` in a browser, or serve locally:

```
python3 -m http.server 8000
```

No build step, no dependencies, no tests. Deployment is automatic via GitHub Pages on push to main.

## Design Intent

The design is inspired by a Save the Date card from The Knot (screenshot was in `inspo.png`, may be deleted). Key layout from the inspiration:

- **Full-bleed background photo** — the image fills the entire viewport (no centered card on a gray background; avoid empty space around the photo)
- **"SAVE" and "DATE"** in large vertical serif lettering, positioned on the left side of the viewport
- **"the"** in a cursive/script font, placed between "SAVE" and "DATE"
- **Wedding details** (names, date, venue, city) in smaller serif text, positioned bottom-right

### Fonts

The Knot original uses "The Seasons" (for SAVE/DATE) and "Mrs Eaves" (for wedding details). Both are paid/licensed fonts. Use similar free alternatives:

- **SAVE / DATE text**: Use a elegant thin serif like Cormorant Garamond, Playfair Display, or similar Google Font that evokes "The Seasons"
- **"the" script**: Use a cursive Google Font (e.g., Great Vibes, Tangerine, or similar)
- **Wedding info**: Use a readable serif like EB Garamond or Libre Baskerville to evoke "Mrs Eaves" — ensure sufficient contrast and legibility (the original was hard to read)

### Responsive Background Images

Two versions of the same photo exist:

- `background-wide.jpg` — landscape crop for wide screens
- `background-vertical.jpg` — portrait crop (AI-extended) for narrow/mobile screens

Behavior: On wide displays, use `background-wide.jpg` and crop it (via `background-size: cover` or similar) to fit the viewport. As the viewport narrows and the wide image would be too aggressively cropped, switch to `background-vertical.jpg`. The switch should happen at a natural breakpoint where the vertical image looks better than an over-cropped wide image (experiment around 768px or wherever the aspect ratio transition feels right).

### Accessibility

- Text overlaid on the photo must have sufficient visual contrast (use text-shadow, a semi-transparent overlay, or gradient scrim behind text)
- Use semantic HTML and appropriate ARIA attributes
- Ensure the page is usable with screen readers (meaningful heading structure, alt text considerations for decorative background)

## Hosting

GitHub Pages with a custom domain. Requires a `CNAME` file in the repo root with the domain name.
