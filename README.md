# Lapis

A parametric latex garment pattern generator — enter body measurements and latex-specific factors, get a live cutting pattern (SVG) with the actual math shown alongside it.

## Try it

Open `index.html` directly in a browser, or (once GitHub Pages is enabled for this repo) at the live site.

## What it does

Ten garment types, switchable via tabs at the top, sharing the same core latex-specific math and now including **curved seams, sleeves, a real multi-finger glove, and true 1:1 print export**.

**Curved seams (new):** side seams on Skirt/Top/Catsuit/Leotard curve outward instead of running dead straight, and Leggings/Catsuit have a genuine asymmetric crotch curve (concave inner seam, convex outer seam) instead of a mirrored straight block. The curve amount is adjustable via "Side-seam curve" in Latex-specific factors.

**Sleeves (new):** Top, Catsuit, and Leotard all have an "Include sleeves" toggle — when on, the bodice gets a real armhole cutout curve and a matching sleeve panel with a curved cap, sized by sleeve length and upper-arm circumference.

**Full-finger gloves (new):** the Gloves tab now defaults to a genuine multi-piece pattern — a palm plus four individually-sized fingers (proportional to your hand length) plus a separately-pieced thumb, rather than just a tapered sleeve. The old fingerless/arm-sleeve option is still there as a style choice.

**Hood improvements (new):** the crown now domes via a curve instead of meeting at a sharp point, and a face-opening curve is carved into the center-front edge. Still the least-solid garment here — see confidence note below.

**True 1:1 print export (new):** every garment has a "Print full-size (tiled)" button. It lays out the actual pattern pieces at real scale, slices them across A4 or US Letter pages with a 10mm margin, and adds corner registration marks so adjacent pages align when taped together. **This uses the exact same geometry functions as the on-screen preview** — there's no separate "print version" of the shapes that could quietly drift out of sync with what you see on screen; an automated test suite checks this equivalence directly.

Confidence tiers (shown live in the app via the colored banner above each pattern):

- **Solid:** Skirt, Top, Panties, Garters — straight-line construction (now with curves layered on top for the applicable ones) is a legitimate real-world choice
- **Simplified, with a clear caveat:** Leggings, Catsuit, Leotard — genuinely usable, curve-improved, but still approximations rather than measured/fitted curves
- **Rough starting blocks:** Bralette (triangle/no-underwire only), Hood (still fundamentally a 3D shape a flat pattern can only approximate) — marked with ▲ on the Hood tab

Shared across all ten: **Stretch reduction (%)** (latex is cut smaller than the body since it stretches to fit) and **glue overlap (mm)** (seams need overlap allowance, not a folded hem, since latex is bonded not sewn). A **cm/inch unit toggle** keeps all internal math in centimeters regardless of display unit. The formula panel shows the exact arithmetic live for whichever garment is selected.

## Known limitations (current state)

- **Curves are parametric approximations, not measured or draped curves.** They're a real improvement over straight lines, but a professional pattern-drafting system would derive curves from actual body scan data or draping — these are reasonable heuristic shapes, not that.
- **The full-finger glove has no fourchette side-strips** (the narrow strips real bespoke gloves use between fingers for a closer fit) — fingers are simple tapered tubes, pieced onto the palm rather than cut as one continuous silhouette.
- **Hood remains the least solid garment here** — a hood is inherently a 3D dome, and the face-opening/crown curves are single-edge approximations, not a properly drafted 3D-to-2D unwrap. Mock this up in cheap fabric before cutting latex.
- **Bralette is triangle/no-underwire only** — molded or underwire cups need darted, multi-panel construction this system doesn't attempt.
- **Sleeve cap and armhole curves are matched approximately**, not eased/notched to a precise seam-length match the way a professional pattern would be — expect to true up the cap by hand.
- **"Multiple types" for Garters/Panties/Gloves-length is still presets adjusting sliders**, not separate drafting algorithms.

## Roadmap ideas

- Fourchette side-strips for the glove, for a properly fitted 5-finger pattern
- A real 3D-to-2D hood unwrap (or at minimum, curves derived from actual head-scan proportions rather than heuristics)
- Darted/molded bra cup support
- Eased, notch-matched sleeve caps

## Testing

This isn't just "does it run" — there's an automated test suite (run via Node + jsdom, not committed to this repo but re-run before every push) that checks:
- Curve bulge directions are geometrically correct (outward curves actually curve outward, inward/concave curves actually curve inward) by sampling the resulting bezier control points, not just eyeballing the render
- Every garment generates valid SVG content with no `NaN` values, across all 10 tabs
- Toggling sleeves/glove-style actually changes the piece count as expected
- Print export runs without throwing and produces sane tile counts
- **Preview and print produce byte-for-byte identical geometry** for the same inputs — this is the check that matters most, since a mismatch here would mean what you see on screen doesn't match what you'd actually cut
