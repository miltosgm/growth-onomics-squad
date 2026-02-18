# Growth-onomics Reporting System — Master Template

**Cadence:** Bi-weekly  
**Delivery:** Email (client portal TBD — Phase 2)  
**Length:** 2-3 pages  
**Audience:** Mix of CEOs (want "so what") + Marketing Managers (want data)  
**Tool:** Looker Studio (live dashboard) + AI-generated narrative summary

---

## REPORT STRUCTURE (Universal Template)

### PAGE 1 — Executive Summary
*For the CEO. 30-second read.*

**[CLIENT NAME] — Performance Snapshot**  
*Period: [DATE RANGE]*

> **In plain English:** [2-3 sentence summary of what happened this period. Was it good? Why? What's the one thing to know?]

| KPI | This Period | Last Period | Change |
|-----|-------------|-------------|--------|
| [Primary metric 1] | | | ↑/↓ % |
| [Primary metric 2] | | | ↑/↓ % |
| [Primary metric 3] | | | ↑/↓ % |

**Top Win:** [The single best result from this period]  
**Watch:** [One thing to monitor — not alarming, just flagged]  
**Next 2 Weeks:** [3 bullet points of what we're doing next]

---

### PAGE 2 — Channel Performance
*For the Marketing Manager. Metrics with context.*

#### SEO Performance (if applicable)
- **Organic Sessions:** [#] vs [# last period] ([+/-]%)
- **Keyword Rankings:** [# keywords in top 3 / top 10 / top 20]
- **Top Gaining Keywords:** [List top 3-5 with position movement]
- **Top Losing Keywords:** [List any significant drops]
- **Impressions (GSC):** [#] | **Clicks:** [#] | **CTR:** [%]
- **New Content Published:** [List titles]
- **Technical Fixes Implemented:** [If any]

#### Paid Ads Performance (if applicable)
- **Total Spend:** [£/$/€]
- **Impressions:** [#] | **Clicks:** [#] | **CTR:** [%]
- **CPC:** [avg] | **CPA:** [avg] | **ROAS:** [x]
- **Conversions:** [#] — [Type: leads/sales/signups]
- **Top Performing Ad/Campaign:** [Name + why it worked]
- **Paused/Adjusted:** [What we stopped or changed + why]

#### AEO Performance (if applicable)
- **AI Mentions / Featured Snippets:** [#]
- **Answer Engine Presence:** [Which queries we're appearing for]
- **Content Optimized for AEO:** [What was updated]

---

### PAGE 3 — Deliverables & Next Steps
*Accountability layer. What was done, what's coming.*

#### Completed This Period
- [ ] [Deliverable 1] — [Brief description]
- [ ] [Deliverable 2]
- [ ] [Deliverable 3]

#### In Progress
- [ ] [Item] — [Expected completion]

#### Planned Next Period
- [ ] [Item 1]
- [ ] [Item 2]
- [ ] [Item 3]

#### Open Questions / Client Actions Required
- [Anything the client needs to provide, approve, or decide]

---

## SERVICE-SPECIFIC VARIANTS

### SEO-Only Report (Karma Developers, ThePayStubs)
Focus Page 2 on:
- Organic traffic trends
- Keyword ranking movements (target buyer-intent keywords)
- Content performance
- Backlink acquisition (if active)
- Local SEO signals (for Karma — Google Business Profile, local rankings)

**Karma-specific KPIs:** Rankings for property-type + location keywords, organic leads from property pages  
**ThePayStubs-specific KPIs:** Rankings for "pay stub generator" cluster, organic traffic volume, free tool conversions

---

### SEO + Paid Ads Report (CDMA)
Page 2 split evenly between SEO and Paid.  
**CDMA-specific KPIs:** Cost per B2B lead, lead quality indicators, branded vs non-branded search share

---

### Full-Service Report (Hola Prime — SEO + AEO + Paid Ads)
Longest report — may run 3 pages comfortably.  
Add AEO section to Page 2.  
**Hola Prime-specific KPIs:** Prop firm comparison keyword rankings, trust signal content performance, trader acquisition cost, AI mention/featured snippet count

---

## EMAIL DELIVERY TEMPLATE

**Subject:** [Client Name] — Growth-onomics Performance Report | [Date Range]

---

Hi [Name],

Here's your bi-weekly performance update for [period].

**The short version:** [1-2 sentences — mirror the executive summary]

Full report attached / [Looker Studio Dashboard Link]

Happy to jump on a quick call if anything needs context. Otherwise, we're already moving on [next priority].

Talk soon,  
[Team member name]  
Growth-onomics

---

## PRODUCTION PROCESS (How to Generate Each Report)

1. **Data pull** (15 min): Export from GSC, GA4, Google Ads, Looker Studio for the period
2. **AI narrative** (10 min): Feed data to Claude with this prompt:
   > *"Here is performance data for [Client] for [period]. Write a 2-3 sentence executive summary in plain English for a CEO audience. Highlight the top win and one thing to watch. Be direct, not corporate."*
3. **Complete template** (10 min): Fill in the numbers, paste the narrative
4. **Miltos review** (5 min): Quick sanity check before send
5. **Send** (2 min): Email with Looker Studio link

**Target: Each report takes <45 minutes to produce.**

---

## REPORTING CALENDAR

| Client | Service | Report Due | Sent By |
|--------|---------|------------|---------|
| Karma Developers | SEO/AEO | Every 2nd Monday | [Team member] |
| CDMA | SEO + Paid | Every 2nd Monday | [Team member] |
| Hola Prime | SEO/AEO/Paid | Every 2nd Monday | [Team member] |
| ThePayStubs | SEO | Every 2nd Monday | [Team member] |

*All reports sent same day = consistent client expectation, easy to batch.*

---

## LOOKER STUDIO SETUP RECOMMENDATIONS

**One dashboard per client.** Each should include:
- Date range selector (default: last 14 days for bi-weekly)
- Traffic overview (GA4 connector)
- Search Console data (impressions, clicks, CTR, position)
- Google Ads data (if applicable)
- Custom KPI scorecard at the top

**Share settings:** View-only link per client. No login required for client to view.

**Pro tip:** Build one master template dashboard in Looker, then clone it per client and reconnect data sources. Saves 80% of setup time.
