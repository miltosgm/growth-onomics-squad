# Looker Studio Master Dashboard Spec
**Growth-onomics | Client Reporting Template**
Version 1.0 — February 2026

---

## 1. Overview & Purpose

This document defines the master Looker Studio dashboard template for Growth-onomics client reporting:
- Consistent, professional reporting experience across all clients
- **Mixed audience:** CEOs need the 30-second headline; marketing managers need the detail
- Default to **bi-weekly cadence** (last 14 days) with easy date overrides
- **Cloned per client** — one master, infinite instances

---

## 2. Page Layout

```
┌─────────────────────────────────────────────────────────┐
│  HEADER: Logo | Client Name | Date Range Selector        │
├─────────────────────────────────────────────────────────┤
│  SECTION 1: KPI Scorecard (always visible)              │
├─────────────────────────────────────────────────────────┤
│  SECTION 2: GA4 Traffic Overview                        │
├─────────────────────────────────────────────────────────┤
│  SECTION 3: Google Search Console                       │
├─────────────────────────────────────────────────────────┤
│  SECTION 4: Google Ads (conditional — paid clients)     │
├─────────────────────────────────────────────────────────┤
│  SECTION 5: AEO Performance (placeholder / emerging)    │
├─────────────────────────────────────────────────────────┤
│  FOOTER: Growth-onomics branding | Last Updated         │
└─────────────────────────────────────────────────────────┘
```

**Canvas Settings:**
- Page size: 1200 × 2800 px (portrait scroll — optimised for browser + PDF export)
- Grid: 12-column, 8px base unit
- Margins: 40px all sides

---

## 3. Header

| Element | Spec |
|---|---|
| Client logo | Top-left, 120×40px placeholder |
| Report title | "Performance Report — [Client Name]" |
| Date range control | Default: **Last 14 days** |
| Comparison toggle | vs. Previous period (on by default) |
| Last refreshed | Auto timestamp |

---

## 4. Section 1 — KPI Scorecard

**4 columns — CEOs stop here**

| KPI Card | Metric | Source |
|---|---|---|
| Card 1 | Organic Sessions | GA4 |
| Card 2 | Total Clicks (GSC) | Search Console |
| Card 3 | Conversions / Leads | GA4 |
| Card 4 | Cost per Lead *(paid clients)* | Google Ads |

**Spec:** 260×120px each | White background | 32px bold metric | Delta: ▲ green / ▼ red

---

## 5. Section 2 — GA4 Traffic Overview

**Data connector:** Google Analytics 4 (native)

- **Channel Breakdown:** Horizontal bar chart — Session default channel group × Sessions
- **Sessions Over Time:** Smooth line chart — Date × Sessions + Engaged sessions (14-day)
- **Top Landing Pages:** Table — Sessions, Engaged sessions, Engagement rate, Conversions (10 rows)
- **Device Split:** Donut chart — Device category × Sessions
- **Key Events:** Scorecard + table breakdown by event name

---

## 6. Section 3 — Google Search Console

**Data connector:** Google Search Console (native)

- **Impressions & Clicks Over Time:** Bar + line combo chart — dual Y-axis
- **CTR & Position Scorecard Row:** Total Impressions | Clicks | CTR | Avg Position
- **Top Queries Table:** Query × Impressions, Clicks, CTR, Position (15 rows, sorted by Clicks)
- **Top Pages by Impressions:** Landing Page × Impressions, Clicks, CTR, Position (10 rows)
- **Search Type Filter:** Web / Image / Video (default: Web)

**Note:** GSC has 2–3 day lag — include note on chart.

---

## 7. Section 4 — Google Ads (Conditional)

> **Only include for paid clients: Hola Prime ✓ | CDMA ✓ | TheStubs ✗ | Karma TBC**

**Data connector:** Google Ads (native)

- **Paid KPI Row:** Total Spend | Impressions | Clicks | CTR | Avg CPC | Conversions | CPL | ROAS
- **Spend Over Time:** Area chart with comparison period
- **Campaign Performance Table:** Campaign × Cost, Clicks, Conversions, CPL (conditional formatting: red if CPL > target)
- **Top Converting Keywords:** Active keywords with Conversions > 0

---

## 8. Section 5 — AEO Performance (Placeholder)

Current status: Manual tracking, full activation Q2 2026.

**Manual fields (Google Sheets connector):**
- AI Mentions this period
- Primary AI engine
- Brand cited in answer (Yes/No)

**Future metrics:** Brand mention frequency, query categories triggering citations, click-through from AI surfaces, Share of Voice vs competitors.

---

## 9. Data Connectors

| Connector | Purpose | Per-Client Config |
|---|---|---|
| Google Analytics 4 | Traffic, conversions | Per-client GA4 property |
| Google Search Console | Organic search | Per-client GSC property |
| Google Ads | Paid performance | Per-client account / MCC |
| Google Sheets | AEO data, targets, benchmarks | Shared Growth-onomics sheet |

---

## 10. Design System

### Colour Palette

| Role | Hex |
|---|---|
| Primary (Growth-onomics navy) | `#0F172A` |
| Accent / CTA | `#3B82F6` |
| Positive delta | `#10B981` |
| Negative delta | `#EF4444` |
| Background | `#F8FAFC` |
| Card background | `#FFFFFF` |
| Border | `#E5E7EB` |
| Body text | `#1F2937` |

### Typography
- Headers: Inter Bold, 18px
- Subheaders: Inter SemiBold, 14px
- Body: Inter Regular, 12px
- Metric values: Inter Bold, 28–32px

### Chart Rules
- ✅ Every chart has title and data source label
- ✅ Comparison period shown on all trend charts
- ❌ No 3D charts (ever)
- ❌ No more than 3 metrics per chart

---

## 11. Clone-Per-Client Workflow (9 Steps)

```
MASTER TEMPLATE (read-only)
  ↓ Clone
CLIENT INSTANCE
  ↓ Configure
```

1. **Duplicate master** → "Make a copy" in Looker Studio
2. **Rename:** `[Client Name] — Performance Dashboard`
3. **Reconnect data sources:** GA4 → client property | GSC → client domain | Ads → client account
4. **Update filters:** GSC branded query exclusion | GA4 goal events
5. **Customise header:** Client logo + report title
6. **Google Ads section:** Show (paid) or remove (organic-only)
7. **AEO section:** Connect client Google Sheet tab or leave placeholder
8. **Test & verify:** Date range = Last 14 days ✓ | Comparison period ✓ | PDF export ✓
9. **Share:** View-only link with client | Set up scheduled email delivery (optional)

### Naming Convention
| Asset | Convention |
|---|---|
| Master | `[MASTER] Growth-onomics Dashboard Template` |
| Client instance | `[CLIENT NAME] — Performance Dashboard v[X]` |
| Data sheet | `[CLIENT NAME] — AEO & Targets Data` |

### Access Control
| Role | Access |
|---|---|
| Growth-onomics internal | Edit |
| Client | View only (shared link) |

---

## 12. Client Configuration Notes

| Client | GA4 | GSC | Google Ads | Notes |
|---|---|---|---|---|
| Karma | ✓ | ✓ | TBC | Real estate, local SEO focus |
| CDMA | ✓ | ✓ | ✓ | B2B IT, Cyprus market |
| Hola Prime | ✓ | ✓ | ✓ | AEO priority — prop trading |
| TheStubs | ✓ | ✓ | ✗ | SEO only, US market |

---

## 13. Setup Checklists

### Pre-Clone
- [ ] GA4 property confirmed and data flowing
- [ ] GSC property verified (domain property preferred)
- [ ] Google Ads access confirmed (if applicable)
- [ ] Client Google Sheet created with AEO tab
- [ ] GA4 key events / goals verified

### Post-Clone
- [ ] All data sources reconnected
- [ ] Date range default = Last 14 days ✓
- [ ] Comparison period enabled ✓
- [ ] Client logo uploaded
- [ ] Branded terms filter set (GSC)
- [ ] Google Ads section: shown or hidden correctly
- [ ] PDF export tested
- [ ] Shared with client (view-only)
- [ ] Scheduled email delivery set up (optional)

---
*Prepared by Athena — Growth & AI Strategy Analyst, Growth-onomics*
*Template Version 1.0 | February 2026*
