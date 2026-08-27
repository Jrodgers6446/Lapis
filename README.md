# Lapis

A parametric latex garment pattern generator — enter body measurements and latex-specific factors, get a live cutting pattern (SVG) with the actual math shown alongside it.

## Try it

Open `index.html` directly in a browser, or (once GitHub Pages is enabled for this repo) at the live site.

## What it does

Three garment types, switchable via tabs at the top, sharing the same core latex-specific math:

- **Skirt** — front + back trapezoid panels + waistband, optional back zip allowance
- **Top** — sleeveless bodice block, bust-to-waist trapezoid panels, optional back zip allowance
- **Leggings** — simplified single-leg block per panel (waist → hip → ankle taper), straight-line only, no crotch curve yet

Shared across all three:

- **Stretch reduction (%)** — latex is cut *smaller* than the body since it stretches to fit; this is the core latex-specific calculation, applied before any panel geometry is computed
- **Glue overlap (mm)** — latex garments are bonded with rubber cement, not sewn, so seams need overlap allowance rather than a folded hem

A **cm / inch unit toggle** sits in the header — all internal math always runs in centimeters regardless of which unit is displayed, so switching units never drifts or rounds the underlying values.

The formula panel below the pattern preview shows the exact arithmetic live, with your actual entered numbers plugged in, so the math is never a black box.

## Known limitations (current state)

- **Straight-line panels only, for every garment** — no curved seams anywhere yet, including the Leggings crotch curve, which real fitted leggings/catsuit bottoms need. The Leggings tab explicitly calls this out in its formula panel.
- **Top is a sleeveless block** — no sleeves, armhole shaping, or bust darts modeled yet
- **On-screen scale only** — no 1:1 physical-size print/PDF export with page tiling yet
- **Leggings' hip placement is an approximation** (18% of inseam length down from the waist), not a measured rise — adjust by hand if that doesn't match your actual proportions

## Roadmap ideas

- Curved side-seam and crotch-curve shaping for genuinely fitted silhouettes
- Multi-page 1:1 scale PDF export (tiled across printable sheets)
- Sleeves and armhole shaping for the Top block
- A full catsuit combining the Top and Leggings blocks into one connected garment
- Per-body-region ease presets (chest vs. ankle stretch differently)
