# DreamCrafter Innovations — brand asset generation prompts
**All three prompts describe one consistent mark so the favicon, icon, and banner read as the same brand at any size.** Each asset now carries a shared prompt (works in ChatGPT / GPT Image and Gemini / Imagen) plus a dedicated **Meta Muse Image** brief.

Which engine to reach for:

- **ChatGPT (GPT Image)** — dense keyword prompts; exclusions must live inside the prompt body.
- **Gemini (Imagen / Nano Banana)** — natural-language description; ignores negative lists; weakest at typography, so keep text out of its frames.
- **Meta Muse Image** — agentic: it reasons, writes and executes code to place exact geometry, and self-refines. **This is the right engine for these particular assets**, because the mark is defined by exact facet angles and six beams at specific colours, and because the banner's beam count and colour order are the whole concept. Muse will place that geometry with code rather than approximating it. Give it hard numeric specs and close with a self-check instruction.

Muse Image embeds an invisible **Content Seal** provenance watermark. That is fine for a website hero and social preview; if you need a demonstrably unwatermarked master for a press kit, generate that version elsewhere.

---

## The concept (why these prompts look like this)

One mark, not a literal collage of a game controller + dollar sign + graduation cap: a **faceted gold gem/prism** on near-black, refracting into thin beams tinted to the six portfolio categories already used across the site's card glows. It reads as "one company, many focused facets" — accurate to the portfolio (13 apps, 6 categories) without depicting any single app's actual icon or trademark.

Brand colors (use exactly):
- Background: `#08060a` (near-black)
- Gem / primary accent: `#ffd21f` (gold)
- Text-safe cream (if any text appears): `#fff8e8`
- Category beam colors: Gaming `#6fe86f` · Finance `#2fd9b0` · Education `#5b9bff` · Family & Kids `#ffb15b` · Lifestyle `#d97fd9` · Utility & Safety `#5fd6e8`

Style throughout: flat vector / geometric illustration, Swiss-modernist precision, hard clean edges on the gem facets, no photorealism, no drop shadows or lens-flare clichés, no readable text baked into any image unless a prompt says otherwise.

---

## 1. Favicon

```
Design a minimal app favicon mark: a single faceted gem/diamond shape, flat vector geometric
style, centered on a square canvas with generous padding on all sides. Background solid
near-black (#08060a). The gem is solid gold (#ffd21f) with 4-6 flat angular facet lines in a
slightly darker gold (#b3810a) to suggest depth without any gradient blur or drop shadow. No
text, no letters, no other elements. Bold and high-contrast enough to stay legible when
shrunk to 16x16 and 32x32 pixels. Square canvas, 512x512px, flat design, sharp vector edges,
no photorealism, no glow, no lens flare.
```

**Meta Muse Image prompt:**

```
Design a favicon mark for "DreamCrafter Innovations," a studio publishing a
portfolio of 13 mobile apps across 6 categories.

Hard specs: 512x512, square, full-bleed background #08060a.

Single centred subject: a faceted gem drawn as a hexagon, point-up and
point-down, 62% of canvas height and 46% of canvas width, filled solid
#ffd21f. Overlay exactly 5 facet lines in #b3810a, stroke 2.5% of canvas
width, hard-edged with no blur: one horizontal line across the gem's widest
point (the girdle), and four lines running from the top point down to the
four girdle vertices. Place the geometry with code so the hexagon is
symmetric about the vertical axis and the four crown facets are equal.

Nothing within 16% of any edge. Absolutely flat: no gradient, no blur, no
glow, no lens flare, no drop shadow. No text, letters or numerals.

Before returning, downscale to 16x16 and confirm the gem still reads as a
faceted gem rather than a solid yellow blob — at least the girdle line must
remain visible. If it does not, reduce to 3 facet lines and thicken them,
then regenerate.
```

**Export:** 512x512 master → downscale to 32x32 and 16x16 for `.ico`, plus a 180x180 PNG for Apple touch icon. Save the master as `/assets/favicon-512.png` and the multi-size `.ico` as `/assets/favicon.ico`.

---

## 2. App / brand icon (the main mark)

```
Design an app icon: the same faceted gold gem/diamond mark as a favicon, but with more
polish and dimension — subtle flat-shaded facets in three tones of gold (#ffee9e highlight,
#ffd21f base, #b3810a shadow facet), still flat vector illustration, no soft gradients, no
photorealistic glass or realistic lighting. Centered on a solid near-black (#08060a) square
canvas with even padding on all sides so it reads correctly when the platform applies a
rounded-square mask. No text, no wordmark, no other icons or objects in the frame. Clean,
premium, geometric, confident — like a fintech or design-tool app icon, not a cartoon gem
or jewelry photo. Square canvas, 1024x1024px.
```

**Meta Muse Image prompt:**

```
Design the primary brand icon for "DreamCrafter Innovations," a studio
publishing 13 mobile apps across 6 categories.

Hard specs: 1024x1024, square, full-bleed background #08060a.

Single centred subject: the same faceted gem as the favicon — a point-up,
point-down hexagon, 62% of canvas height and 46% of canvas width — but with
flat-shaded facets instead of a single fill. Divide the gem into exactly 7
flat polygonal facets with hard edges and no blur between them: the top
crown facet in #ffee9e (highlight), the two upper side facets in #ffd21f
(base), the two lower side facets in #ffd21f darkened slightly, and the two
pavilion facets meeting at the bottom point in #b3810a (shadow). Every facet
boundary is a hard vector edge — no soft gradient, no glass refraction, no
photorealistic lighting.

Place the geometry with code so the gem is symmetric about the vertical axis
and the facet boundaries meet cleanly at shared vertices with no gaps or
overlaps.

Nothing within 15% of any edge so a platform rounded-square mask cannot clip
the gem. No text, no wordmark, no other objects. No glow, no lens flare, no
drop shadow, no noise.

Reference: this should read like a fintech or design-tool app icon —
confident, geometric, Swiss-modernist — never a cartoon gem, a jewellery
photograph, or a sparkle-emoji diamond.

Before returning, confirm the gem has exactly 7 facets with clean shared
vertices, confirm all three golds are distinguishable from one another, and
downscale to 48x48 to confirm the facet structure survives.
```

**Export:** 1024x1024 master PNG, no transparency needed (background is intentionally solid). Save as `/assets/icon-mark.png` (site nav mark — also export a transparent-background SVG/PNG trace if your tool supports vectorizing, as `/assets/icon-mark.svg`, since the site CSS is already wired to look for that file in the header).

---

## 3. Site banner / social preview image

```
Design a wide brand banner. Solid near-black background (#08060a). On the left third, the
same faceted gold gem/diamond mark (flat vector, 3-tone gold shading as above), positioned
at roughly 40% height. From the gem, six thin flat light beams radiate outward toward the
right side of the frame, fanning out and fading in opacity as they extend — each beam a
different solid color: #6fe86f, #2fd9b0, #5b9bff, #ffb15b, #d97fd9, #5fd6e8. The beams should
feel like refracted light splitting from the gem, not like a rainbow gradient — keep each
beam a distinct flat color with a soft fade-to-transparent only at its far tip. Leave the
right half of the frame mostly empty near-black negative space for text to be added
separately — do not render any text, words, or logotype in the image itself. Flat vector
illustration style, no photorealism, no lens flare, no noise/grain. Landscape, 1920x640px.
```

**Meta Muse Image prompt:**

```
Design a wide brand banner for "DreamCrafter Innovations," a studio
publishing 13 mobile apps across 6 categories.

Hard specs: 1920x640, landscape, flat #08060a background, no gradient or
vignette, no noise or grain.

Left region: the 7-facet gold gem mark (point-up, point-down hexagon,
flat-shaded facets in #ffee9e / #ffd21f / #b3810a, hard vector edges),
280px tall, centred at approximately (x=420, y=256).

From the gem's right edge, exactly SIX straight flat beams radiate outward
and to the right, fanning across an 80-degree spread centred on the
horizontal. Each beam is a long thin triangle originating at the gem and
widening as it extends, reaching between 700px and 1000px in length at
varying angles. Each beam is one distinct flat colour with no gradient along
its body, fading to fully transparent only across the final 20% of its
length. The six colours, in order from the topmost beam to the bottommost:
#6fe86f, #2fd9b0, #5b9bff, #ffb15b, #d97fd9, #5fd6e8. Beams may overlap
slightly but each must remain individually identifiable by colour — this is
refracted light splitting into six discrete facets, NOT a rainbow gradient
and NOT a blended spectrum.

Keep the right third of the frame (x > 1280) mostly empty near-black
negative space, since site copy is overlaid there. Do not render any text,
words or logotype.

Place the geometry with code so the six beams share a common origin point at
the gem and the angular spread between adjacent beams is even.

Before returning: count the beams and confirm there are exactly six; confirm
each is a distinct flat colour matching the hex list in the stated top-to-
bottom order; confirm no beam has blended into its neighbour to form a
gradient; and confirm the right third is clear enough for overlaid text.
```

**Export:** 1920x640 (site hero banner — the CSS is already wired to show this at `/assets/banner.jpg` on the right side of the homepage hero, so keep the gem + beams positioned so the *left* portion of the image is the busiest, since that's what stays visible after the crop). Also export a 1200x630 crop of the same artwork (centered on the gem) as `/assets/og-image.png` for social link previews — the current placeholder is an SVG which most platforms won't render, so this raster export is the one that actually needs to replace it.

---

## Where these go once generated

| File | Save as | Already wired up? |
|---|---|---|
| Favicon | `website/assets/favicon.ico` | Update the `<link rel="icon">` line in every page's `<head>` (currently pointing at the temporary `/favicon.svg`) |
| Brand mark | `website/assets/icon-mark.svg` (or `.png`) | Yes — `style.css` `.brand::before` already looks for this file in the nav; it'll appear next to "DreamCrafter" automatically once the file exists |
| Banner | `website/assets/banner.jpg` | Yes — `style.css` `.hero` already looks for this file; it'll appear as the right-side hero backdrop automatically once the file exists |
| OG/social image | `website/assets/og-image.png` | No — swap the `<meta property="og:image">` line in `index.html` from `/og-image.svg` to `/assets/og-image.png` once generated |

Drop the generated files into an `assets/` folder at the website root and most of this activates with no further code changes — send them back here and I'll wire the two remaining meta-tag swaps.

---

## Production notes

- **Count the beams every time.** The banner's whole idea is "one company, six focused facets," mapped to the six category colours already used in the site's card glows. Five beams or seven breaks the mapping, and blending them into a rainbow gradient breaks it worse — a spectrum says "generic tech," six discrete flat beams say "six deliberate categories." This is the most common failure across all three engines, which is why the Muse brief specifies the count, the angles and the exact colour order, and asks the model to verify.
- **Generate the favicon first, then chain.** Muse Image composes from multiple input references, so produce the 512px favicon gem, confirm it survives a 16×16 downscale, then attach it as a reference image when generating the 1024px icon and the banner. That keeps the gem's proportions and facet structure identical across all three assets far more reliably than re-describing the geometry each time.
- **The 16×16 test is the real constraint on the favicon.** A seven-facet gem is beautiful at 512px and mud at 16px. If the girdle line disappears, drop to three facet lines and thicken them — a legible simple gem beats an illegible detailed one, and the favicon is the only asset in this set that has to work at that size.
- **Colour drift.** All three engines pull `#ffd21f` toward orange and `#08060a` toward pure black. Sample and correct against the hex list above, since these values are already in the site CSS and a mismatch will be visible where the banner meets the page background.
- **The OG image is the one that actually matters right now.** The current `/og-image.svg` placeholder won't render on most social platforms, so the 1200×630 raster crop is the export to prioritise — it's the asset a shared link actually shows.
