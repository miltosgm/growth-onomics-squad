# AI Design Workflow — Growth-onomics
**Author:** Iris, Creative & Design Strategist
**Date:** February 2026
**Status:** Active — Version 1.0

> This document defines Growth-onomics' end-to-end AI design workflow for producing client visual assets in-house. It covers tool selection, asset-type workflows, brand consistency protocols, per-client prompt templates, and QC standards.

---

## 1. AI Design Tool Stack — Recommended

### Overview

| Tool | Best For | Pricing (approx.) | Agency Score |
|---|---|---|---|
| **Midjourney** | Hero imagery, lifestyle, brand visuals | $30–96/mo | ⭐⭐⭐⭐⭐ |
| **Adobe Firefly** | Brand-safe edits, inpainting, stock integration | Included in Creative Cloud | ⭐⭐⭐⭐ |
| **Ideogram** | Typography-heavy graphics, text-on-image | $8–25/mo | ⭐⭐⭐⭐ |
| **Canva AI** | Social templates, quick turnarounds, team collab | $15/mo/seat | ⭐⭐⭐⭐ |
| **DALL-E 3** | Conceptual/illustrative work, ChatGPT integration | Included w/ GPT-4 | ⭐⭐⭐ |

**Estimated monthly cost for 4-client agency:** ~$120–180/mo (Midjourney Pro + Canva Teams + Ideogram Creator + Firefly via CC)

---

## 2. Asset-Type Workflows

### 2A. Social Media Graphics
**Tools:** Midjourney → Ideogram → Canva AI

1. **Brief** — Platform, format, message, CTA, client brand
2. **Image Generation (Midjourney)** — Generate 4 variants using client prompt template. Select best 1–2, upscale. Export PNG.
3. **Text & Layout (Ideogram or Canva)** — If text is part of image: use Ideogram. If text overlays: import to Canva, apply brand fonts/colours.
4. **Resize & Export** — Canva Magic Resize for all required formats. PNG for organic, JPG for paid.
5. **QC** — Run checklist (Section 5)

### 2B. Blog Headers
**Tools:** Ideogram or Midjourney → Canva AI

1. **Topic brief** — Headline text, article topic, client brand
2. **Generate base image** — Ideogram for text-forward. Midjourney for photographic/lifestyle. Target: 1200×630px
3. **Overlay in Canva** — Client logo, headline, brand colour accents
4. **Export** — PNG or JPG at 72dpi, compressed under 200KB

### 2C. Ad Creatives
**Tools:** Midjourney → Adobe Firefly → Canva AI

1. **Ad brief** — Objective, audience, platform, format specs, offer/CTA
2. **Hero image (Midjourney)** — 4–6 variants, select top 2
3. **Compositing (Firefly or Canva)** — Background removal, inpainting
4. **Ad layout (Canva)** — Apply brand template, 3–5 size variants
5. **A/B variants** — Minimum 2 creative variants per ad set
6. **QC** — Verify no text cut-off, safe zones respected

### 2D. Report Covers
**Tools:** Midjourney or Firefly → Canva AI

1. **Cover brief** — Title, client name, reporting period, brand palette
2. **Cover imagery** — Midjourney for aspirational. Firefly for conservative/B2B.
3. **Layout in Canva** — Full bleed image, gradient overlay, report title, logos
4. **Export** — PDF (print quality) + PNG thumbnail

---

## 3. Brand Consistency Protocol

### 3A. Client Brand File Structure
```
/brand-assets/
  [ClientName]/
    brand-kit.json         ← HEX codes, font names
    logo-primary.svg
    logo-white.svg
    logo-dark.svg
    style-reference.png    ← Midjourney --sref image
    approved-images/       ← Bank of approved AI outputs
    prompt-library.md      ← Master prompts (see Section 4)
```

### 3B. Canva Brand Kit Setup (per client)
- ✅ Upload all logo variations
- ✅ Set primary + secondary colour palettes (HEX exact)
- ✅ Set brand fonts
- ✅ Lock brand elements
- ✅ Create 3–5 master templates per asset type

### 3C. Midjourney Style Anchoring
Use `--sref` (Style Reference) parameter to lock visual style across sessions:
1. Generate an approved "anchor image" for the client's visual identity
2. All future generations include: `--sref [anchor-image-URL] --sw 100`
3. Use `--cref` for character/person consistency

### 3D. Colour Accuracy Rule
- **Never rely on AI for brand colour accuracy in generated images**
- Apply brand colours in Canva or Photoshop as overlays/UI elements
- AI-generated images = backgrounds/hero imagery only

### 3E. Version Control
- Save approved assets: `/brand-assets/[ClientName]/approved/`
- Naming: `[ClientName]_[AssetType]_[Platform]_[Date]_v[N].png`
- Example: `KarmaDev_InstagramPost_1080x1080_2026-02-18_v2.png`

---

## 4. Prompt Templates — Per Client

### Client 1: Karma Developers (Real Estate, East Cyprus)
**Brand Personality:** Aspirational, trustworthy, Mediterranean luxury, lifestyle-forward

```
[KARMA DEVELOPERS — MASTER PROMPT]

Base style: Luxury real estate lifestyle photography, golden hour lighting, 
Mediterranean setting, East Cyprus coast and landscape. 
Aspirational but authentic.

Colour temperature: Warm golds, deep blues, sandy whites.
Mood: Premium, serene, attainable luxury.

PROPERTY EXTERIOR:
"Luxury modern villa with clean Mediterranean architecture, limestone facade, 
infinity pool overlooking turquoise sea, East Cyprus coastline, golden hour, 
professional real estate photography, warm tones --ar 16:9 --style raw --v 6.1"

LIFESTYLE HERO:
"Happy professional couple on a sun-drenched terrace of a modern Cyprus villa, 
morning coffee, sea view in background, aspirational Mediterranean lifestyle, 
warm golden light --ar 16:9 --v 6.1"
```

### Client 2: CDMA (B2B IT Services, Cyprus)
**Brand Personality:** Professional, technically credible, reliable, enterprise-grade

```
[CDMA — MASTER PROMPT]

Base style: Corporate B2B technology photography. Clean, professional, trustworthy.
Colour temperature: Cool blues, greys, whites.

TECH INFRASTRUCTURE:
"Modern enterprise data centre, server racks with blue LED lighting, 
clean and organised, professional photography, cool blue tones --ar 16:9 --style raw --v 6.1"

TEAM/PEOPLE:
"Confident IT professional in business casual attire working at multi-monitor 
setup in modern office, Mediterranean light, credible and professional --ar 3:2 --style raw --v 6.1"
```

### Client 3: Hola Prime (Prop Trading / Forex, Global)
**Brand Personality:** High-energy, fintech confidence, global reach, trust signals

```
[HOLA PRIME — MASTER PROMPT]

Base style: High-energy fintech photography. Trading charts, financial dashboards, global city skylines.
Colour temperature: Deep blacks, electric greens, gold accents.

TRADING HERO:
"Confident professional trader at dual-monitor setup showing live forex charts, 
dramatic lighting, dark office environment, green trading data, cinematic style --ar 16:9 --style raw --v 6.1"

PAYOUT/PERFORMANCE:
"Successful moment — trader celebrating at desk, charts showing upward trend, 
laptop with green P&L, modern home office, aspirational but believable --ar 4:3 --style raw --v 6.1"
```

### Client 4: ThePayStubs (US SaaS, Paystub Generator)
**Brand Personality:** Simple, clean, functional, friendly, US-market SaaS

```
[THESTUBS — MASTER PROMPT]

Base style: Clean SaaS product photography. Friendly, approachable, American small business context.
Colour temperature: Clean whites, light blues, friendly greens.

HERO / PRODUCT:
"Clean white laptop screen showing a pay stub generator web app interface, 
bright natural light, American home office or small business setting --ar 16:9 --style raw --v 6.1"

PEOPLE / USE CASE:
"Friendly small business owner reviewing documents at desk, laptop open, 
American office setting, natural light, approachable and diverse --ar 3:2 --style raw --v 6.1"
```

---

## 5. Quality Control Checklist

### ✅ Brand Compliance
- [ ] Brand colours match client HEX values
- [ ] Correct logo version used
- [ ] Brand-approved fonts applied
- [ ] Tone matches client personality

### ✅ Visual Quality
- [ ] Resolution sufficient (min 72dpi web, 300dpi print)
- [ ] No AI artefacts (distorted hands, garbled text)
- [ ] No watermarks
- [ ] Balanced composition

### ✅ Text & Copy
- [ ] All text legible at intended display size
- [ ] No spelling errors
- [ ] CTA clear and prominent (for ads)
- [ ] Text contrast passes WCAG AA (4.5:1 ratio)

### ✅ Technical Specs
- [ ] Correct dimensions for platform
- [ ] File size within limits
- [ ] Correct format (PNG/JPG/PDF)
- [ ] Safe zones respected (no critical content in outer 10%)

### ✅ Legal & Compliance
- [ ] No identifiable real people without consent framework
- [ ] No competitor logos or trademarks in AI output
- [ ] For Hola Prime: no misleading financial claims
- [ ] For Karma: no inaccurate property representations

### ✅ Platform Specs

| Platform | Format | Dimensions | Max File Size |
|---|---|---|---|
| Instagram Feed | Square | 1080×1080 | 8MB |
| Instagram Story | Vertical | 1080×1920 | 8MB |
| Meta Feed Ad | Landscape | 1200×628 | 30MB |
| LinkedIn Post | Landscape | 1200×627 | 5MB |
| Blog Header | Landscape | 1600×900 | 200KB (web) |
| Google Display | Various | 300×250, 728×90 | 150KB |
| Report Cover | Portrait | A4 / 2480×3508 | PDF |

---

## 6. Getting Started — Team Onboarding Steps

1. **Set up Canva Teams** — invite all team members, create Brand Kit per client
2. **Subscribe to Midjourney Pro** — minimum 1 seat, share via Discord server
3. **Subscribe to Ideogram Creator** — for text-on-image work
4. **Connect Adobe Firefly** via existing CC subscription
5. **Create shared folder structure** in Google Drive
6. **Load prompt templates** into shared Notion or Google Doc
7. **Run 1 test asset per client** using templates before going live

---
*Document maintained by: Iris, Creative & Design Strategist*
*Next review: Q2 2026*
