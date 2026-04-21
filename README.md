# Handoff: Spending Pulse Website Redesign

## Overview
Full redesign of the three-page Spending Pulse marketing website (`index.html`, `privacy.html`, `terms.html`). The original site was a minimal legal-doc hub. The redesign turns `index.html` into a proper product marketing page and polishes the legal pages.

## About the Design Files
The files bundled in this folder are **HTML design references** — prototypes showing the intended look and behavior. Your task is to **recreate these designs in the existing `duy-a/SpendingPulse-Website` repo**, replacing the three HTML files (and adding `legal.css`). The repo is plain HTML/CSS — no framework — so ship them as-is. The prototypes are production-ready enough to deploy directly; just verify on real devices and update the App Store URL placeholder if needed.

## Fidelity
**High-fidelity.** Pixel-accurate final designs with exact colors, typography, spacing, and layout. Ship the files as provided.

---

## Pages

### 1. `index.html` — Marketing landing page

**Purpose:** Convert app-store visitors; explain the product; link to App Store.

**Sections (top → bottom):**

#### Sticky nav
- Height: 64px, `position: sticky; top: 0; z-index: 100`
- Background: `rgba(255,255,255,0.80)` + `backdrop-filter: blur(20px) saturate(160%)`
- Border-bottom: `0.5px solid rgba(16,24,40,0.07)`
- Left: logo img (`assets/logo-icon.png`, 32×32, `border-radius:7px`) + wordmark "Spending Pulse" (18px, 800 weight, `letter-spacing:-0.03em`)
- Right: nav links (Terms, Privacy, Support) + "Download" pill CTA (`background:#101828; color:#fff; border-radius:999px; padding:9px 18px`)
- App Store link: `https://apps.apple.com/app/apple-store/id6759994055?pt=125941816&ct=Website&mt=8`

#### Hero
- Grid: `1fr 380px`, gap 60px, `max-width:1160px`, `padding:80px 40px`
- Left: `<h1>` 62px / 900 weight / `letter-spacing:-0.04em` — first two words in `#4BC8F5` (brand cyan), rest `#101828`. Sub-text 19px / `color:#667085`. App Store button (dark pill).
- Right: real device screenshot `assets/device-screenshot.png`, width 300px, `filter: drop-shadow(0 40px 60px rgba(0,0,0,.18))`

#### Features grid
- Section label: 13px / 700 / uppercase / `#1177FF`; headline: 42px / 800
- Grid: `repeat(3,1fr)`, gap 20px
- Each card: glass card (see Design Tokens), 48×48 icon tile (`border-radius:14px`), h3 18px/700, p 15px/`#667085`

#### Signal section ("Four states")
- Grid: `1fr 1fr`, gap 24px, `align-items:center`, `padding:80px 40px`
- Left: section label + headline + two paragraphs
- Right: 4 status cards stacked, each with a 10px coloured dot + h4 + p
  - Safe: `#34C759`, Close: `#FF9500`, At the limit: `#FF3B30`, Overspent: `#FF3B30` (60% opacity dot)

#### Privacy promise
- Single glass card, inner grid `1fr 1fr`, `align-items:center`, `padding:80px 40px`
- Left: badge pill + h2 28px/800 + body copy
- Right: 4 `prow` tiles (icon + h4 + p), each on a thin-glass background, `border-radius:14px`

#### CTA (dark)
- `background:#101828`, `border-radius:32px`, flex row space-between
- Left: headline (42px/900, accent word in `#4BC8F5`) + subtext
- Right: App Store button (semi-transparent dark variant) + fine print

#### Footer
- `border-top:0.5px solid rgba(16,24,40,.08)`; flex row: brand wordmark · nav links · copyright

---

### 2. `privacy.html` — Privacy Policy

**Purpose:** Legal requirement; linked from app and footer.

- Same sticky nav (logo img, Home back-link, Terms/Privacy links)
- Full-width single-column layout (`max-width:1160px`)
- Hero card: h1 "Privacy Policy", lead sentence, last-updated date
- 13 section cards, each with a numbered badge (`border-radius:8px; background:rgba(17,119,255,.09); color:#1177FF`) + h2 + body copy
- Footer identical to index

**Content:** Identical to the existing `privacy.html` in the repo — do not alter legal text.

---

### 3. `terms.html` — Terms & Conditions

**Purpose:** Legal requirement.

- Same structure as `privacy.html`
- 15 sections
- Hero: "Terms & Conditions"

**Content:** Identical to existing `terms.html` in the repo — do not alter legal text.

---

## Design Tokens

### Colors
| Token | Value | Use |
|---|---|---|
| `--accent` | `#1177FF` | Buttons, links, badges, chart fills |
| `--cyan` | `#4BC8F5` | Hero headline accent word, logo |
| `--ink1` | `#101828` | Primary text, CTA background |
| `--ink2` | `#344054` | Body text |
| `--ink3` | `#667085` | Muted / secondary text |
| `--ink4` | `#98A2B3` | Placeholder / footer |
| `--safe` | `#34C759` | Safe status |
| `--close` | `#FF9500` | Close-to-limit status |
| `--red` | `#FF3B30` | At limit / Overspent |
| `--card` | `rgba(255,255,255,0.84)` | Glass card fill |
| `--card-thin` | `rgba(255,255,255,0.64)` | Inner tile fill |

### Background (canvas)
```css
background:
  radial-gradient(780px 480px at 18% 0%, rgba(17,119,255,.08), transparent 60%),
  radial-gradient(600px 400px at 88% 0%, rgba(0,199,190,.09), transparent 60%),
  linear-gradient(158deg, #EEF3FF 0%, #E8FBF5 100%);
```

### Glass card
```css
background: rgba(255,255,255,0.84);
backdrop-filter: blur(16px) saturate(160%);
border-radius: 20–28px;           /* 20 inner cards, 28 hero/privacy */
box-shadow: inset 0 0 0 1px rgba(255,255,255,0.65),
            0 18px 50px rgba(16,24,40,0.07);
```

### Typography
- Font: `"Inter"` from Google Fonts (weights 400–900), fallback `-apple-system`
- Nav brand: 18px / 800 / `letter-spacing:-0.03em`
- Hero h1: clamp(40px, 4.5vw, 62px) / 900 / `letter-spacing:-0.04em`
- Section headline: clamp(28px, 3vw, 42px) / 800 / `letter-spacing:-0.03em`
- Body: 16–19px / 400 / `line-height:1.65–1.75` / `#344054`
- Caption/muted: 13–15px / `#667085`

### Spacing
- Section padding: `80px 40px` (desktop), `40px 20px` (≤900px)
- Card padding: `28–44px`
- Grid gap: `20–60px`

### Radii
- Pill: `999px`
- Nav CTA / buttons: `14px` (rect), `999px` (pill)
- Cards: `20px` standard, `24–28px` hero/privacy card
- Inner tiles: `14px`

### Breakpoints
- `≤900px`: single-column hero; signal grid collapses; privacy inner grid collapses; CTA stacks
- `≤560px`: features grid single column; some nav links hidden

---

## Interactions
- Nav Download CTA → App Store link (same tab)
- Hero App Store button → same link
- CTA App Store button → same link
- App Store URL: `https://apps.apple.com/app/apple-store/id6759994055?pt=125941816&ct=Website&mt=8`
- Hover: opacity `0.85` on buttons; `color:#101828` on nav links
- Nav is sticky; scrolls with page but stays at top

---

## Assets
| File | Use |
|---|---|
| `assets/logo-icon.png` | App icon in nav (all 3 pages) |
| `assets/device-screenshot.png` | Hero phone mockup on index.html |

Both files live in `assets/` relative to the project root. In the website repo they sit one level up from the HTML files, so the paths are `../assets/logo-icon.png` etc.

---

## Files in this bundle
| File | Description |
|---|---|
| `index.html` | Marketing landing page |
| `privacy.html` | Privacy Policy (legal content unchanged) |
| `terms.html` | Terms & Conditions (legal content unchanged) |
| `legal.css` | Shared stylesheet for privacy + terms pages |
| `assets/logo-icon.png` | App icon |
| `assets/device-screenshot.png` | Hero device photo |

---

## How to deploy
1. Copy all files into the root of `duy-a/SpendingPulse-Website`
2. Copy `assets/` folder alongside the HTML files (or adjust relative paths if your repo structure differs)
3. Commit and push — the site is static HTML, no build step needed
4. Create a PR: `redesign` → `main`
