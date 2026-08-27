# Lapis

A parametric latex garment pattern generator — enter body measurements and latex-specific factors, get a live cutting pattern (SVG) with the actual math shown alongside it.

## Try it

Open `index.html` directly in a browser, or at the live GitHub Pages site if enabled for this repo.

## What it does

Ten garment types, switchable via tabs at the top, sharing the same core latex-specific math.

**Real upgrades in this version:**
- **Curved side seams** — every torso/leg shape now curves smoothly through its real measurement points (waist→hip→hem, bust→waist→hip→ankle, etc.) using an actual Catmull-Rom-to-Bezier spline, not a cosmetic effect. Straight top/bottom edges (where a waistband or hem attaches) stay straight on purpose.
- **True 1:1 scale print export** — "Print pattern (1:1, tiled)" renders every piece at genuine physical size and tiles it across US Letter or A4 pages with overlap margins for taping and a 1cm reference square on every sheet to verify your printer didn't rescale anything. Preview and print now share one geometry model, so what you see is what prints.
- **A real (if simplified) sleeve block** for Top/Catsuit/Leotard — a curved cap using a commonly-cited beginner drafting ratio (cap height ≈ armhole-depth × 0.6), with wrist/elbow/shoulder length presets.
- **A curved-base bralette cup** — a genuine soft-cup improvement over a hard triangle point.

**Confidence tiers**, shown live in the app via a colored banner on each tab:

**Solid:**
- **Skirt**, **Top**, **Panties**, **Garters**

**Simplified, with a clear caveat:**
- **Leggings**, **Catsuit**, **Leotard** — curved side seams now, but still no true crotch curve (front/back rise are treated as identical)

**Rough starting blocks — flagged with ▲ on their tabs:**
- **Gloves** — fingerless/arm-sleeve style only. A true 5-finger glove needs individual finger-length measurements and separate curved finger cones, which this tool doesn't collect yet — tell me your hand length and finger lengths and this becomes buildable properly.
- **Bralette** — triangle/no-underwire only. Molded or underwire cups need curved, darted pieces genuinely out of scope here.
- **Hood** — side panels curve now, but the face opening still isn't drafted at all — that needs face width/height measurements not yet collected. Strongly recommend a fabric mockup before cutting latex regardless, since a hood is inherently a 3D shape no flat pattern captures perfectly.

Shared across all ten:
- **Stretch reduction (%)** — latex is cut *smaller* than the body since it stretches to fit
- **Glue overlap (mm)** — seams need overlap allowance rather than a folded hem

A **cm / inch unit toggle** sits in the header — all internal math always runs in centimeters. The formula panel shows the exact arithmetic live for whichever garment is selected.

## Known limitations (current, honest state)

- **No true crotch curve** on Leggings/Catsuit — front and back rise are still treated as identical, which a real fitted pattern wouldn't do
- **Print page counts are large for a full garment** (often 15–30+ tiled pages) — this is inherent to printing real garment-sized panels on home-printer paper, not specific to this tool; real PDF sewing patterns commonly run this long for the same reason. A copy shop with large-format/plotter printing can output the same pattern on far fewer sheets.
- **Sleeves are a basic block** — no armhole-ease distribution or shoulder-slope adjustment; a muslin test is worthwhile before cutting latex
- **Gloves, Bralette, and Hood remain rough blocks on purpose** — each needs additional measurement inputs (finger lengths, cup volume data, face dimensions) that aren't collected yet; building those properly is the next real step rather than faking curves without the data to back them

## Roadmap ideas

- Per-finger measurement inputs + individual curved finger cones for a real 5-finger glove pattern
- Face width/height inputs + a real curved face-opening for the Hood
- True asymmetric front/back crotch curve for Leggings/Catsuit
- Armhole-ease distribution and shoulder-slope adjustment for a more refined sleeve
- Smarter page packing to reduce print page counts further where genuinely possible
