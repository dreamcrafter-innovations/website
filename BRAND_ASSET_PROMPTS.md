# DreamCrafter Innovations — brand asset generation prompts
**Paste into ChatGPT (image generation), Gemini/Imagen, Muse, or any other image model. All three prompts describe one consistent mark so the favicon, icon, and banner read as the same brand at any size.**

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
