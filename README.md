# Lapis

A parametric latex garment pattern generator — enter body measurements and latex-specific factors, get a live cutting pattern (SVG) with the actual math shown alongside it.

## Try it

Open `index.html` directly in a browser, or (once GitHub Pages is enabled for this repo) at the live site.

## What it does

Currently generates a two-panel latex skirt pattern (front + back + waistband), driven by:

- **Body measurements** — waist, hip, skirt length
- **Stretch reduction (%)** — latex is cut *smaller* than the body since it stretches to fit; this is the core latex-specific calculation, applied before any panel geometry is computed
- **Glue overlap (mm)** — latex garments are bonded with rubber cement, not sewn, so seams need overlap allowance rather than a folded hem
- **Hem flare (cm)** — additive width for an A-line silhouette
- **Waistband height**
- **Back zip toggle** — switches the center-back edge between a plain fold and an overlap allowance for a zip flap

A **cm / inch unit toggle** sits in the header — all internal math always runs in centimeters regardless of which unit is displayed, so switching units never drifts or rounds the underlying values.

The formula panel below the pattern preview shows the exact arithmetic live, with your actual entered numbers plugged in, so the math is never a black box.

## Known limitations (current state)

- **Straight-line panels only** — no curved side seams yet, so it's closer to a flared cut than a truly fitted silhouette
- **On-screen scale only** — no 1:1 physical-size print/PDF export with page tiling yet
- **One garment type** — just the skirt. The `generate()` function structure is meant to make adding a top or catsuit straightforward, sharing the same ease/overlap logic, but that's not built yet

## Roadmap ideas

- Curved side-seam shaping for a true A-line/fitted cut
- Multi-page 1:1 scale PDF export (tiled across printable sheets)
- Additional garment types (top, catsuit) reusing the existing stretch/overlap math
- Per-body-region ease presets (chest vs. ankle stretch differently)
