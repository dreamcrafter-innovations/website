# DreamCrafter website — V2 Audit (static site)

*Run 21 Sep 2026. The `website/` repo is a static HTML site (no build step, no Expo). This pass checks internal links, page metadata, and whether each app's privacy page matches what the app does today. It did not load the live site.*

**Evidence key:** VERIFIED (read/run this pass) · PARTIAL · INFERRED · UNVERIFIED · N/A.

## 1. Executive Summary

- **Release classification: OK to publish, with owner items.** All internal links resolve; every listed app has a page and a privacy policy.
- **Fixed this pass (local commit only):**
  1. **Social preview image was an SVG.** `og:image` pointed at `/og-image.svg` with a relative path; Facebook, LinkedIn, X and most chat apps ignore SVG and need an absolute URL. Rendered `og-image.png` (1200 x 630, checked visually), pointed `og:image` at its absolute URL, and added the size and `twitter:card` tags.
  2. **Canonical links added to 49 pages** (`<link rel="canonical">`), so the `privacy.html` redirect stub, the `/apps/…` pages and the policies each name one preferred URL.
  3. **Little Keeps privacy page did not mention its optional iCloud / Google Drive backup.** Added one bullet (off unless turned on; copy goes to the user's own iCloud or Drive; we never receive it) and updated its date. This matches the app-side copy changes made in the Little Keeps V2 pass.
  4. Removed a stale HTML comment about a missing `assets/favicon.ico` (the only "broken link" the checker found was inside that comment).
- **Verified:** 0 broken internal `href` / `src` across all HTML pages; every page has a viewport meta; the site lists 21 apps and each has both `apps/<name>/` and `privacy-policy/<name>/` pages; support and terms pages exist; the only external link is the site's own domain.
- **Biggest open risk:** **policy pages must change before the app behaviour does.** Examples: the Ivy page says no third-party analytics are used, true today, but the app bundles PostHog and Sentry (dormant until keys are set), so that page must be updated before either key is configured. The Ruse, Perk Vault and Whistle Watch pages already disclose Firebase Analytics and Crashlytics, which matches those apps' build setup.
- **Next action:** owner deploys, then checks the social preview with a link-debugger and confirms each policy URL is entered in both store consoles.

## 2. Verification Results

| Check | Result | Evidence |
|---|---|---|
| Internal links (all `.html`) | 0 broken | VERIFIED |
| Viewport meta on every page | yes | VERIFIED |
| Canonical links | 49 added; none existed | VERIFIED |
| `og:image` | PNG, absolute URL | VERIFIED (file rendered and viewed; not tested in a link debugger) |
| Policy vs app behaviour | Little Keeps fixed; Ivy flagged; others spot-checked (Ruse, Perk Vault, Whistle Watch, Scholarfind, DLS, Safety 101) | PARTIAL |
| Live site, HTTPS, redirects, hosting | not checked | UNVERIFIED |
| Accessibility, mobile layout | not audited | UNVERIFIED |

## 3. Findings

### P1
- **No page for the newest app (AI Resilience)**, and it has no privacy or terms URL; its upgrade screen needs both before store submission. The pattern is one folder per app under `apps/` and `privacy-policy/`.
- **Policy dates are per page** (most say 24 Jul 2026; Align says 12 Sep). Keep them current when app behaviour changes.
- **No store links yet.** App pages carry no Play or App Store URLs (the apps are unreleased); add them at launch.

### P2
- `website.zip` (an April archive) and `BRAND_ASSET_PROMPTS.md` / `WEBSITE_REDESIGN_PLAN.md` are tracked in the site repo; they are served if the host publishes the repo root. Consider moving them out.
- The favicon is SVG-only; some older browsers and crawlers want `favicon.ico`.
- No sitemap or robots file.

## 4. Competitors
N/A (marketing site).

## 5. Backlog
| ID | Item | Pri | Owner |
|---|---|---|---|
| WS-1 | Add AI Resilience app and privacy pages | P1 | Dev |
| WS-2 | Update Ivy policy before any telemetry key is set | P1 | Owner |
| WS-3 | Add store links at launch | P1 | Owner |
| WS-4 | Move archives and planning docs out of the served root; add sitemap and robots | P2 | Dev |

## 6. Verification Appendix
Cloud copy of the repo: a Python link checker over all `.html` files, grep for metadata and privacy claims, Chromium screenshot of `og-image.svg` to `og-image.png`. Not run: live-site checks, link debuggers, accessibility tools.
