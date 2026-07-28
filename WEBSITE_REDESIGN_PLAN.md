# DreamCrafter Website — Redesign Content & Theme Plan v2.0
**Purpose: make the website carry real weight in startup-credit applications (Microsoft Founders Hub, AWS Activate, and eventually the AI-specific programs), not just exist as a placeholder.**

*Companion to `dreamcrafter-startup-credits-plan.md`. Scope: content for `D:\Apps\dreamcrafters\website` and a visual redesign based on the Aurum design system in `D:\Apps\dreamcrafters\theme`.*

*v2 changes: portfolio is now organized by product category instead of a diaspora/geography-led pitch; every app gets its own privacy policy page; theme options swapped from Fizz/Aurum to Aurum/Currant (both from the newer `Aurum Premium Style Guide V1.zip`) after Fizz (navy) was ruled out.*

---

## 1. Why this matters for the credit applications

Every founder-tier infra program in the credits plan (§3, Tier A) lists "LLC + website" as its evidence bar — Microsoft Founders Hub and AWS Activate Founders both expect a real site behind the LLC, not just the entity paperwork. Right now the site is a single generic page: no product names, no founder background, no portfolio, a placeholder "coming soon" section, and a broken copyright glyph in the footer. It currently proves the LLC exists; it doesn't prove there's a real, active company behind it.

The redesign has one job: turn the site into the single best piece of evidence for every application in the tracker (§6 of the credits plan). A portfolio organized by product category (gaming, finance, education, and so on) also does real work here beyond aesthetics — it reads as a diversified software company building for six markets, which is a stronger signal to a reviewer than a single-market app studio, and it's the accurate framing: the 13 apps genuinely span unrelated categories, not variations on one theme.

---

## 2. Current-state audit

`index.html` — generic hero ("Innovative Mobile & Web Applications"), three static cards describing categories rather than products, a "Products Coming Soon" section with no names or dates, one `mailto:` CTA. No mention of Ruse, the LLC's actual apps, or the founder.
`privacy.html`, `terms`, `support` — one LLC-wide privacy policy exists; no per-app policies yet (see §3.5 — this is a gap worth closing regardless of the redesign, since app stores generally require a privacy policy URL per listing, not one shared page).
`style.css` — plain, unbranded; no relationship to the Aurum/Modernist system.
Footer — copyright symbol renders as `�` (mojibake) — a small but visible bug worth fixing regardless of the redesign.
No favicon/OG image referenced in `index.html`'s `<head>`.

---

## 3. Content plan, page by page

### 3.1 Home
- Hero: positioning built around the portfolio's actual breadth — a solo-founded Texas LLC building small, focused apps across several product categories, some on-device and some cloud-connected — not a single-market or single-culture pitch, and not limited to "offline-first" as the company's identity now that online apps are part of the roadmap. Lead with what the apps *do*, category-first.
- Category row: six short pills/tags (Gaming, Finance, Education, Family & Kids, Lifestyle, Utility & Safety) directly under the hero — gives a reviewer the shape of the company in one glance.
- Portfolio grid (centerpiece): one card per featured app — icon/art, a category badge, a stage badge, one honest line of description, and a "Privacy policy" link. Feature 6 apps spanning all 6 categories (one each) rather than defaulting to whichever are furthest along — breadth is the point of this section. Suggested picks: Ruse (Gaming), PerkVault (Finance), Ivy (Education), Little Keeps (Family & Kids), Temple Trails (Lifestyle), Safety 101 (Utility & Safety). Roll the remaining 7 into the full `/apps` page.
- Founder/About block: short, factual — professional software engineering background, Texas LLC in good standing, why a multi-category portfolio approach (small, sharp, single-purpose apps rather than one large product).
- Traction section: placeholder slot only, left empty until Ruse ships — per the credits plan's own principle (§7: "shipped evidence → application, never the reverse").
- Contact: keep the `mailto:` CTA, also show the address as visible text.

### 3.2 Apps (new page, linked from nav)
All 13 apps, grouped by category section (Gaming, Finance, Education, Family & Kids, Lifestyle, Utility & Safety — see §3.4 for the full mapping), each with its real name, one-line pitch, honest stage label, and its own privacy-policy link. This is the page to link directly from credit applications that ask for "your product" — it's also the strongest single artifact for demonstrating the "diversified software company" framing, since seeing six unrelated categories in one grid makes the point better than any sentence of copy could.

### 3.3 About (new page, or a deeper version of the home block)
Founder background, the LLC, and the actual reasoning behind the portfolio strategy (many small, focused apps across categories rather than one flagship product). Keep it short.

### 3.4 App category taxonomy
Neutral, function-first categories — no app's description leads with a geography or culture; where an app's subject matter is inherently specific (e.g. Temple Trails, Puja Checklist), the copy stays factual about what the app *does* rather than framing the whole company around one audience.

| Category | Apps | One-line function |
|---|---|---|
| Gaming | Ruse; Nightfall: Secret Roles | Pass-the-phone party / social-deduction games |
| Finance | PerkVault | Track and redeem credit card and loyalty perks before they expire |
| Education | DebateCraft; ScholarFind; Ivy | Debate practice & review; scholarship matching; college-admissions planning |
| Family & Kids | Little Keeps; Carpool | Private growth journaling; family carpool scheduling |
| Lifestyle | Puja Checklist; Temple Trails; Five Skies | Ritual-planning checklist; temple visit planning; multi-tradition astrology |
| Utility & Safety | Safety 101; DLS Calculator | Offline emergency reference; cricket match-scoring calculator |

DLS Calculator and Ivy currently have no bundle ID set yet (per `dreamcrafter-startup-credits-plan.md` §5) — list them as "Early concept" rather than "In development" until that changes.

### 3.5 Per-app privacy policies (new requirement)
Each app needs its own privacy policy page, not just a shared LLC-wide one — both because app store listings ask for a privacy policy URL per app (and the data an app actually collects differs a lot: Little Keeps touches a child's data and needs COPPA-conscious language, Carpool touches location, Ruse touches ad/tracking identifiers per its own `STORE_PUBLISH.md`, while apps like ScholarFind and Five Skies are genuinely on-device-only with nothing to disclose) — and because it's one more piece of evidence that the company is operating like a real, multi-product software business.

Proposed structure: `website/privacy-policy/[app-slug]/index.html` for each of the 13 apps, generated from one shared template with per-app data-collection specifics filled in, linked from every portfolio card and from the app's own store listing once published. Keep the existing top-level `privacy-policy/` page as the general LLC policy (data practices for the website itself, contact form, etc.), and cross-link it from each app-specific page rather than duplicating boilerplate.

### 3.6 Privacy / Terms / Support
Reskin onto the new visual system (nav, footer, typography, color tokens); no content changes beyond adding the per-app privacy pages above.

### 3.7 Footer (every page)
Fix the mojibake copyright character, add the LLC's registered name and state (Texas), keep contact + legal links.

---

## 4. Visual direction — Aurum vs Currant (Fizz/navy ruled out)

Both options below are exact palettes from the newer `theme/Aurum Premium Style Guide V1.zip` theme picker (same shared "Modernist" grid/type/component system as before, updated token values). A side-by-side mockup with the categorized, 6-app portfolio grid from §3.1 is saved at:

**`theme-comparison-mockup-v2.html`** (this session's outputs — open in a browser to compare)

The card treatment — dark ground, a color-matched glow behind each app's mark, a category badge, bold title, muted description, privacy-policy link — is still adapted from the FutureFuel reference: photographic/glowing product presentation on a dark ground, one accent color per item, applied to app icons instead of drink cans. Each card keeps its own accent glow color regardless of which base palette is chosen below, so Gaming/Finance/Education/etc. stay visually distinguishable at a glance in the grid — the category badge and the glow color are the same signal reinforced twice.

### Option A — Aurum (golden black) — recommended
| Token | Value |
|---|---|
| `--color-bg` | `#08060a` |
| `--color-surface` | `#171009` |
| `--color-text` | `#fff8e8` |
| `--color-accent` | `#ffd21f` |
| Neutral ramp (100→900) | `#fff8e8` `#efe3c0` `#d3c090` `#ab9a66` `#7d7048` `#544a2e` `#37301c` `#211c10` `#120f08` |
| Accent ramp (100→900) | `#fff8d8` `#ffee9e` `#ffe25c` `#ffd935` `#ffd21f` `#e0aa10` `#b3810a` `#805b06` `#4d3703` |
| Hero gradient | `linear-gradient(115deg, #ffee9e 0%, #ffd21f 45%, #b3810a 85%, #ffe25c 100%)` |

**Does gold make sense here?** Yes, more so than the other candidates. Gold reads as trust/value/achievement across all six categories at once — coins and rewards in Finance, honor-roll/achievement in Education, trophy/prize in Gaming, warmth in Family & Lifestyle, and it's simply a less common choice than blue for a software company, so it's memorable without needing an explanation. The V1 gold (`#ffd21f`) is more saturated than the earlier version pulled from the older zip (`#dba53f`) — brighter and more "gold" rather than "amber/bronze."

### Option B — Currant (blackcurrant / moody premium)
| Token | Value |
|---|---|
| `--color-bg` | `#0d0610` |
| `--color-surface` | `#1b0e20` |
| `--color-text` | `#f3e8f0` |
| `--color-accent` | `#9c2d78` |
| Neutral ramp (100→900) | `#f3e8f0` `#dfc7db` `#bb9ab6` `#94708f` `#6f4f6b` `#4d3549` `#33222f` `#1f151d` `#110b10` |
| Accent ramp (100→900) | `#f6dceb` `#eab8d8` `#d97fb8` `#c14f98` `#9c2d78` `#7a1d5e` `#5c1447` `#3f0d30` `#24071b` |
| Hero gradient | `linear-gradient(115deg, #eab8d8 0%, #9c2d78 45%, #5c1447 80%, #24071b 100%)` |

**Does currant make sense here?** Partially — it's genuinely elegant and more distinctive than gold (fewer companies use deep berry-magenta), but the design system's own framing for it is "for a premium wine, beauty or after-hours app," which doesn't map onto any of the six actual categories the way gold maps onto several of them. It would work fine as a one-off app's brand color (it'd suit Temple Trails or Five Skies well, for instance) but is a weaker fit as the *site-wide* identity for a multi-category portfolio, since it pulls the whole company toward a "beauty/nightlife" register that only one or two of the 13 apps are anywhere near.

**Recommendation:** Aurum (gold) for the site chrome. Keep Currant in reserve as a possible accent for an individual app card or a future "Lifestyle" section treatment rather than the whole site.

---

## 5. Foundations carried from the Modernist system

- Typography: Archivo throughout, weight 800 headings, 400 body.
- Spacing scale: 4 / 8 / 12 / 16 / 24 / 32px.
- Buttons: `.btn-primary` solid accent fill, `.btn-secondary` outlined, `.btn-ghost` text-only; states from the accent ramp, never a browser default focus ring.
- Cards, tags, nav, tables, dialogs: reusable component classes already defined in `theme/Aurum Premium Style Guide V1.zip` → `_ds/modernist-*/styles.css` — port these wholesale, then layer the chosen accent tokens (§4) on top.
- Departure from the base system: base Modernist calls for zero corner radius and no shadows/glow anywhere. Keep that flat, ruled treatment for the chrome (nav, footer, buttons, dividers) but allow soft radius + glow specifically on the portfolio cards, per §4.
- Icons: Lucide.

---

## 6. Implementation checklist

1. Confirm Aurum (gold) as the site theme — open `theme-comparison-mockup-v2.html` to sanity-check against Currant first.
2. Port `styles.css` tokens + component classes from `Aurum Premium Style Guide V1.zip` into `website/style.css`.
3. Rewrite `index.html` per §3.1 — category-first hero, 6-card portfolio grid, founder block, traction placeholder.
4. Build `/apps` with all 13 apps grouped by category (§3.4).
5. Add a short `/about` section or page.
6. Build the 13 per-app privacy policy pages from one template (§3.5); link each from its portfolio card and from the shared `/privacy-policy` page.
7. Reskin `terms/`, `support/`, and the existing `privacy-policy/` page onto the new nav/footer/typography.
8. Fix the footer copyright mojibake; add LLC name + state.
9. Add favicon and Open Graph meta tags.
10. Cross-check every "stage" label against `dreamcrafter-startup-credits-plan.md` §5 before publishing, and keep the two documents in sync as apps ship.
11. Once live, add the site URL to the Microsoft Founders Hub and AWS Activate applications in the credits tracker (§6 of the credits plan).
