# Lapis

A parametric latex garment pattern generator — enter body measurements and latex-specific factors, get a live cutting pattern (SVG) with the actual math shown alongside it.

## Try it

Open `index.html` directly in a browser, or (once GitHub Pages is enabled for this repo) at the live site.

## What it does

Ten garment types, switchable via tabs at the top, sharing the same core latex-specific math. Each carries an honest confidence level shown right in the app — not every shape reduces cleanly to straight lines, and I'd rather flag that than hand you a pattern that looks equally trustworthy across the board when it isn't.

**Solid — straight lines are a genuinely reasonable choice for these:**
- **Skirt** — front + back trapezoid panels + waistband
- **Top** — sleeveless bodice block
- **Panties** — front/back/gusset, a real common construction method
- **Garters** — belt + straps, just strips of material

**Simplified, with a clear caveat — usable, but expect to true up by hand:**
- **Leggings** — waist→hip→ankle taper, no crotch curve
- **Catsuit** — one continuous bodice+leg panel per side, no crotch curve, no sleeves
- **Leotard** — solid bodice + simple rectangular gusset, no curved leg-opening binding

**Rough starting blocks only — genuinely need curves/darts this system can't produce:**
- **Gloves** — fingerless/arm-sleeve style only; individual finger stalls need different construction entirely and are out of scope
- **Bralette** — triangle-cup, no-underwire style only; molded/underwire cups need curved, darted pieces
- **Hood** — a hood is inherently a 3D dome; this gives you a starting silhouette only, strongly recommend a fabric mockup before cutting latex

Shared across all ten:

- **Stretch reduction (%)** — latex is cut *smaller* than the body since it stretches to fit; applied before any panel geometry is computed
- **Glue overlap (mm)** — seams need overlap allowance rather than a folded hem, since latex is bonded, not sewn

A **cm / inch unit toggle** sits in the header — all internal math always runs in centimeters regardless of which unit is displayed. The formula panel below the pattern preview shows the exact arithmetic live for whichever garment is selected, so the math is never a black box.

## Known limitations (current state)

- **Straight-line panels only, everywhere** — no curved seams anywhere yet, including any crotch curves
- **On-screen scale only** — no 1:1 physical-size print/PDF export with page tiling yet
- **"Multiple types" is implemented via presets/parameters, not separate algorithms** — e.g. Garters' strap count, Gloves' length presets (wrist/elbow/shoulder), Panties' rise presets (low/mid/high) all just adjust existing sliders rather than switching to a genuinely different pattern-drafting method

## Roadmap ideas

- Curved seam support (side seams, crotch curve, cup shaping) — the single biggest upgrade across nearly every garment here
- Multi-page 1:1 scale PDF export (tiled across printable sheets)
- Sleeves and armhole shaping for Top/Catsuit/Leotard
- A real 5-finger glove pattern (genuinely different construction from the current fingerless block)
- Face-opening drafting for the Hood, once curved-seam support exists
