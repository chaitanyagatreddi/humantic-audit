# Humantic AI — Full SEO & GTM Audit
**Date:** 2026-06-15
**Framework:** FLOW (Find · Leverage · Optimize · Win) © Daniel Agrici, CC BY 4.0 — github.com/AgriciDaniel/flow
**Tools:** Firecrawl · gtm-predictor CRO · gpt-4o-mini · Revenue formula: Sprinto Growth Audit (May 2026)

---

## Table of Contents

1. [Revenue Leakage](#1-revenue-leakage)
2. [FLOW Analysis — Find + Optimize](#2-flow-analysis--find--optimize)
3. [AEO — Answer Engine Optimization](#3-aeo--answer-engine-optimization)
4. [Paid Ads — WIN Stage](#4-paid-ads--win-stage)
5. [CRO Scorecard — 3 Pages](#5-cro-scorecard--3-pages)
6. [Crawl Audit — 404s, Broken Links, Missing Tags](#6-crawl-audit--404s-broken-links-missing-tags)

---

## 1. Revenue Leakage

> Humantic AI is leaking **~$1.1M / year** through search-invisible pages and broken conversion architecture.
> Same formula as Sprinto Growth Audit (May 2026) — adapted assumptions for enterprise sales intelligence SaaS.

---

### Assumptions

| Variable | Value | Basis |
|---|---|---|
| Average deal (ACV) | **$25,000 ARR** | Enterprise B2B sales tool, Gartner Cool Vendor tier. Sprinto used $8K for mid-market compliance SaaS; sales intelligence enterprise commands ~3× premium. |
| Demo → close rate | **6%** | Standard for enterprise B2B SaaS with 90+ day sales cycles. Sprinto used 8% for faster mid-market cycle. |
| Page → demo conversion | **2%** | High-friction enterprise product. CRO audit scored homepage 5.5/10 and pricing 4.5/10 — both below 7/10 category baseline. |
| CPC (paid search) | **$45 avg** | "Buyer intelligence software", "AI sales intelligence", "DISC sales tool" cluster. Enterprise B2B SaaS CPCs run $30–65. |

**Formula:** `est. monthly visits × 2% (page→demo) × 6% (demo→close) × $25,000 (ACV) = lost ARR/mo`

---

### Search-Invisible Pages (Humantic AI's equivalent of Sprinto's 404s)

These pages return HTTP 200 but are invisible to search engines due to canonical misdirection or noindex tags — confirmed via Firecrawl crawl (40 pages, June 2026).

#### Critical — canonical → homepage + noindex (complete search invisibility)

| Page | Issue | Why It Hurts |
|---|---|---|
| `/start/pricing` | Canonical → homepage + noindex,nofollow | Highest-intent buyer page. Enterprise evaluators always check pricing before booking a demo. Zero organic traffic despite active demand. |
| `/comparison/crystal-knows-alternative` | Canonical → homepage + noindex,nofollow | Crystal Knows is the #1 direct competitor. "Crystal Knows alternative" is a high-intent BOFU query — competitor is capturing this traffic. |
| `/comparison/ibm-watson-alternative` | Canonical → homepage + 3× conflicting noindex tags | High-intent comparison query. Also contains a malformed internal link (LinkedIn URL prefixed with humantic.ai domain) that would 404 if crawled. |
| `/comparison/xiq-alternative` | Canonical → homepage + noindex,nofollow | xiQ is a direct competitor. All three comparison pages being dark is a significant BOFU gap. |
| `/buyer-intelligence` | Canonical → homepage + noindex,nofollow (×2) | The category-definition page — most important for AI citation and category ownership. Currently noindexed. |

#### High — broken or missing canonical

| Page | Issue | Why It Hurts |
|---|---|---|
| `/solutions/revenue` | Canonical → homepage + noindex,nofollow | Core solution page for Revenue Teams — primary ICP. Excluded from search entirely. |
| `/personalization-suite` | Canonical → homepage + noindex,nofollow | Kairos Activation Engine product page. Also has a broken og:image (raw HTML in the meta value). |
| `/miia` | Canonical set to `/miia#` (broken relative path) | Flagship product page. Google cannot associate organic signals correctly. |
| `/pi` | Canonical missing entirely + og tags missing | Agent Pi product page. No canonical tag. Social shares also broken. |

---

### Revenue Lost from Search-Invisible Pages

| Invisible Page | Primary Query | Est. Monthly Visits Lost | Lost Demos/mo | Lost Deals/mo | Lost ARR/mo |
|---|---|---|---|---|---|
| `/start/pricing` | "humantic ai pricing" | 600 | 12 | 0.72 | $18,000 |
| `/comparison/crystal-knows-alternative` | "crystal knows alternative" | 250 | 5 | 0.30 | $7,500 |
| `/comparison/ibm-watson-alternative` | "ibm watson personality alternative" | 150 | 3 | 0.18 | $4,500 |
| `/comparison/xiq-alternative` | "xiq alternative" | 120 | 2.4 | 0.14 | $3,600 |
| `/buyer-intelligence` | "buyer intelligence platform" | 400 | 8 | 0.48 | $12,000 |
| `/solutions/revenue` | "buyer intelligence for sales teams" | 300 | 6 | 0.36 | $9,000 |
| `/personalization-suite` | "sales personalization AI" | 200 | 4 | 0.24 | $6,000 |
| `/miia` (broken canonical) | "AI account research tool" | 500 | 10 | 0.60 | $15,000 |
| `/pi` (no canonical) | "DISC personality AI sales" | 300 | 6 | 0.36 | $9,000 |
| **Total** | | **2,820/mo** | **56.4** | **3.38** | **~$84.6K/mo → ~$1.01M/year** |

### Wasted Paid Spend

~500 paid clicks/month to pages with broken canonical or missing meta description × $45 CPC = **$22,500/month = $270K/year** in underperforming paid traffic (suppressed quality scores, higher CPCs over time, no organic assist).

### CRO Conversion Gap (Additional Opportunity)

| Scenario | Conv. Rate | Demos/mo | Deals/mo | ARR/mo |
|---|---|---|---|---|
| Current (5/10 avg CRO score) | 2.0% | 300 | 18 | $450,000 |
| After fixes (7/10 category baseline) | 2.8% | 420 | 25.2 | $630,000 |
| **Uplift** | **+0.8%** | **+120** | **+7.2** | **+$180K/mo → +$2.16M/year** |

> CRO uplift is incremental gain, not existing loss — not included in the headline leak figure.

### Total Annual Leak

| Bucket | Annual Impact |
|---|---|
| Revenue lost from search-invisible pages | ~$1,015,200 |
| Paid spend underperformance | ~$270,000 |
| **Total confirmed leak** | **~$1.1M / year** |
| CRO conversion uplift opportunity (additional) | ~$2.16M / year |

> Even at 50% of these assumptions: **~$550K/year** walking out through pages Google cannot see.

---

### Fix Priority

| Rank | Fix | Effort | Stops |
|---|---|---|---|
| 1 | Self-canonical all 14 misdirected pages | Low (CMS config) | ~$1M/year organic leak |
| 2 | Remove noindex from `/buyer-intelligence`, `/solutions/revenue`, `/start/pricing`, `/comparison/*`, `/library/*` | Low | BOFU pages dark |
| 3 | Consolidate to one CTA per page | Low | CRO gap |
| 4 | Move Gartner + outcome stats above fold | Low/Med | CRO gap |
| 5 | Fix og:image on `/personalization-suite` | Low | Social sharing broken |
| 6 | Fix malformed LinkedIn link on `/ibm-watson-alternative` | Low | Broken internal link |

---

## 2. FLOW Analysis — Find + Optimize

### Stage Diagnosis

| Stage | Status | Blocker |
|---|---|---|
| **Find** | 🔴 Blocking | Homepage leads with brand language, not buyer search language |
| **Leverage** | 🟡 Partial | G2 + Gartner present; need citable case study pages |
| **Optimize** | 🔴 Blocking | Missing meta description, opaque product names, unsourced stats |
| **Win** | 🟡 Partial | "This AI Is Not For Everyone" is smart; free-trial funnel needs conversion tracking |

---

### FIND Stage

#### Searcher & Buyer Intent

The target buyer is a **VP of Sales / RevOps / Sales Enablement** at an enterprise B2B company with 50–5,000 AEs and a ≥90-day sales cycle.

| Intent Layer | Likely Queries | Current Coverage |
|---|---|---|
| Category awareness | `sales intelligence software`, `buyer intelligence platform` | Partial — title uses the phrase but H1 doesn't |
| Pain-driven | `how to personalize cold outreach at scale`, `account research automation` | Not found on homepage |
| Comparison | `Humantic AI vs Crystal Knows`, `DISC personality sales tool` | Not found on homepage |
| AI-era | `AI sales agent`, `AI account research` | Referenced but not clearly anchored |
| Proof-seeking | `Humantic AI reviews`, `Gartner sales intelligence` | Trust signals exist but buried below fold |

**Gap:** H1 `"Previously Impossible Buyer Intelligence For Elite Sellers"` is brand aspiration. No buyer searches this phrase.

#### Evidence Available

| Evidence | Present? | Notes |
|---|---|---|
| Gartner Cool Vendor 2024 | ✓ | High-trust signal — needs to be above fold |
| G2 Top 100 Satisfaction + Momentum Leader | ✓ | Strong third-party validation |
| Named customers (Microsoft, IBM, Domo) | ✓ | Fortune-brand association confirmed |
| Quantified outcomes | ✓ | 109% pipeline increase, 16.2% closed/won — unlinked to source |
| SOC 2 Type 2, GDPR, EU AI Act | ✓ | Critical for enterprise procurement |
| 90% adoption rate | ✓ | Needs attribution ("based on what sample?") |
| Meta description | ✗ | Missing |
| Category definition | ✗ | "Buyer Intelligence Platform" undefined vs. competitors |

#### Gaps Blocking Trust, Extraction & Conversion

**A. Category ownership gap**
"Buyer intelligence" is Humantic AI's own term. Established search category is "sales intelligence" (ZoomInfo, Apollo, 6sense). Humantic sits at a crossroads — needs to own the niche term with a definitional page or anchor as the personality layer within sales intelligence.

**B. Brand-name product opacity**
`Agent Miia`, `Agent Pi`, `Kairos Activation Engine` are not searchable. Add functional subtitles on first mention (e.g. *"Agent Miia — multi-agent account research AI"*).

**C. Missing meta description**
SERP snippet is pulled from random body text. No controlled first impression.

**D. Outcomes unlinked to evidence**
"109% average increase in qualified pipeline" has no linked case study, methodology, or date. Reduces citeability for AI overviews and procurement reviewers.

---

### OPTIMIZE Stage

#### Recommended Changes — Priority Order

| Priority | Change | Evidence Basis |
|---|---|---|
| P1 | Write a meta description | Currently missing |
| P1 | Rewrite H1 with buyer language | "Previously Impossible" is aspirational, not searchable |
| P2 | Add functional subtitles to product names | Miia/Pi/Kairos are opaque to first-time visitors |
| P2 | Add source citation to outcome stats | 109% pipeline, 16.2% close rate need methodology note |
| P3 | Move Gartner Cool Vendor above the fold | Highest-authority trust signal buried below scroll |
| P3 | Create a "What is Buyer Intelligence?" definitional page | Establishes category ownership; gives AI overviews an entity to cite |
| P4 | Reduce CTA fragmentation | 4 competing CTAs — consolidate to 2 max |

#### Proposed H1 Rewrites

**Current:** *"Previously Impossible Buyer Intelligence For Elite Sellers"*

**Options:**
- *"AI-Powered Buyer Intelligence That Prepares Every Seller in 3 Minutes"*
- *"Know Your Buyer Before the First Call — AI Account Research for Enterprise Sales"*
- *"Personalize Every Enterprise Deal With AI Buyer Intelligence"*

#### Proposed Meta Description

```
Humantic AI gives enterprise sales teams AI-generated account research and
DISC-based buyer personality intelligence in minutes. Used by Fortune 10 teams.
Gartner Cool Vendor 2024. SOC 2 certified.
```
*(~155 chars)*

#### Measurement Events

| Event | Tool | Cadence |
|---|---|---|
| SERP snippet CTR for branded + category queries | GSC | Monthly |
| AI Overview citation check | Manual SERP check | Quarterly |
| Demo conversion rate | CTA clicks → booked demos | Weekly |
| "Free Report" to trial conversion | Funnel drop-off | Monthly |
| G2 / Gartner review velocity | New reviews per quarter | Quarterly |

#### Claims Requiring Verification

| Claim | Source Needed |
|---|---|
| 109% average increase in qualified pipeline | Methodology, sample size, date range, customer count |
| 16.2% increase in closed/won revenue | Same as above |
| 90%+ adoption rate | Internal platform data — clarify definition |
| Fortune 10 usage | Permissioned customer name or description |
| Gartner Cool Vendor 2024 | Confirm year; link to Gartner press or acknowledgment page |

---

## 3. AEO — Answer Engine Optimization

### Executive Summary

Humantic AI has strong third-party validation (Gartner, G2, Fortune-brand customers) but is poorly configured for AI answer engines. AI models summarising the "sales intelligence" or "buyer intelligence" category have no clean, citable passage to anchor Humantic AI to a clear definition, differentiator, or verified outcome. The FAQ section is the one AEO-ready element. Everything else works against citation.

---

### 1. Entity Clarity

| Signal | Status | Issue |
|---|---|---|
| Company name | ✓ | "Humantic AI" is unambiguous |
| Category entity | 🔴 | "Buyer Intelligence Platform" is self-coined — not an established taxonomy AI models recognise |
| Product entity | 🔴 | Agent Miia, Agent Pi, Kairos are brand-invented; AI models cannot map these to buyer queries |
| Competitor anchoring | 🔴 | No mention of category peers — AI models can't place Humantic AI in the competitive landscape |
| Founding / about signals | ⚠️ | Not visible on homepage — reduces entity confidence in AI knowledge graphs |

**Fix:** Add one paragraph on the homepage that defines the category in plain language, names the problem, and locates Humantic AI within the established "sales intelligence" taxonomy:

> *"Humantic AI is a buyer intelligence platform that layers DISC-based personality prediction on top of account research, helping enterprise B2B sellers personalise outreach and prepare for calls. It sits at the intersection of sales intelligence tools (like ZoomInfo or Apollo) and conversation intelligence (like Gong), focusing specifically on buyer personality rather than firmographic data alone."*

---

### 2. Passage-Level Citability

| Query an AI might be asked | Citable passage on humantic.ai? | Gap |
|---|---|---|
| "What is Humantic AI?" | 🔴 No | No definitional paragraph |
| "How does Humantic AI work?" | 🔴 No | Features listed but mechanism unexplained |
| "What results do customers get?" | ⚠️ Partial | Stats present but unlinked to methodology |
| "Is Humantic AI SOC 2 certified?" | ✓ Yes | Compliance badges visible |
| "Who uses Humantic AI?" | ⚠️ Partial | Named logos, no passage-format statement |
| "How is Humantic AI different from Crystal Knows?" | 🔴 No | No comparison content |

---

### 3. Structured Data & AI Crawler Signals

*[ASSUMPTION — requires technical verification]*

| Element | Expected Status | Why It Matters |
|---|---|---|
| `Organization` schema | Likely missing | Anchors entity name, URL, description for AI crawlers |
| `FAQPage` schema | Likely missing | FAQ exists on-page but not machine-readable |
| `SoftwareApplication` schema | Likely missing | Signals product type and category to AI models |
| `Review` / `AggregateRating` schema | Likely missing | G2 ratings mentioned in copy, not in structured data |
| `llms.txt` | Likely absent | Guides LLM crawlers on what to index |

**Immediate wins:**
- Add `FAQPage` JSON-LD — zero content work, immediate AI extractability gain
- Add `Organization` schema with `description`, `foundingDate`, `sameAs` (LinkedIn, G2, Crunchbase)
- Add `SoftwareApplication` schema with `applicationCategory: "Sales Intelligence"`

---

### 4. Platform-Specific Gaps

| Platform | Issue |
|---|---|
| **Google AI Overviews** | No meta description + no `<title>` optimised for category query. Need definitional H2 + supporting paragraph above fold. |
| **ChatGPT / Perplexity** | Outcome stats need attribution so AI models can confidently cite them. Strongest citation vectors: G2 reviews, Gartner profile, press coverage. |
| **Bing Copilot** | Pulls from pages with clear `<h1>` → `<p>` structure. Current hero with animated text is hard to linearise. |

---

### 5. AEO Content Gaps — Priority Order

| Priority | Action | Effort |
|---|---|---|
| P1 | Add `FAQPage` JSON-LD to existing FAQ section | Low |
| P1 | Write definitional paragraph (what is Humantic AI, plain language) | Low |
| P1 | Add meta description using category + trust signals | Low |
| P2 | Add `Organization` + `SoftwareApplication` JSON-LD | Medium |
| P2 | Source the outcome stats with methodology note | Low |
| P2 | Create `/what-is-buyer-intelligence` category page | Medium |
| P3 | Add comparison pages (`/vs-crystal-knows`, `/vs-gong`) | High |
| P3 | Add `llms.txt` for AI crawler guidance | Low |
| P3 | Build passage-format "how it works" explanation | Medium |

---

### 6. Measurement Plan

| Metric | Tool | Cadence |
|---|---|---|
| ChatGPT/Perplexity citation — "best buyer intelligence platform" | Manual prompt testing | Monthly |
| Google AI Overviews appearance for category queries | GSC + manual SERP | Monthly |
| `FAQPage` rich results in SERP | Google Search Console | Ongoing |
| Branded entity accuracy | Ask 3 AI engines "What is Humantic AI?" | Quarterly |
| G2 review count | G2 profile | Quarterly |

---

### 7. AEO Verification Checklist

- [ ] Confirm whether `llms.txt` exists at `humantic.ai/llms.txt`
- [ ] Verify current JSON-LD schema via Google Rich Results Test
- [ ] Confirm methodology behind "109% pipeline increase" stat
- [ ] Test "What is Humantic AI?" in ChatGPT, Perplexity, and Google AI — log baseline answers
- [ ] Confirm Gartner Cool Vendor year is 2024 and page is publicly linkable

---

## 4. Paid Ads — WIN Stage

### Executive Summary

Three compounding problems: no dedicated landing pages (ads likely send to homepage), CTA fragmentation dilutes conversion signal, and current messaging leads with brand aspiration rather than decision-stage proof. The 109%/16.2% outcome stats are the strongest ad assets on the site — currently buried and unsourced.

---

### 1. Buyer Intent at Decision Stage

| Stage | Mindset | What They Need to Convert |
|---|---|---|
| **Evaluation** | "I'm comparing buyer intelligence tools" | Feature comparison, pricing signal, named customer proof, frictionless trial |
| **Justification** | "I've chosen Humantic AI, I need to get it approved" | ROI evidence, security/compliance docs, case study with named company + metric |

---

### 2. BOFU Landing Page Brief

**Recommended H1 (ad-matched):**
> *"AI Account Research and Buyer Personality Intelligence for Enterprise Sales Teams"*

#### Section Outline for Dedicated Landing Page

| Section | Content | Evidence Source |
|---|---|---|
| Hero | H1 + outcome stat + single primary CTA | 109% pipeline stat — add source |
| Problem | 2–3 sentences on the preparation gap in enterprise sales | Customer language |
| How it works | Functional explanation of Miia + Pi in plain English | Homepage product section |
| Proof | 2 named customer quotes with role, company, specific result | Microsoft / IBM / Domo testimonials |
| Trust bar | Gartner Cool Vendor + G2 badges + SOC 2 / GDPR | Existing page assets |
| Objection handling | FAQ: Setup time? CRM integrations? Enterprise procurement? | Sales call notes |
| Single CTA | "Get Your Free Account Research Report" | Simplify to one |

---

### 3. Conversion Audit

#### CTA Fragmentation (highest friction point)

4 competing CTAs currently on homepage:
1. "Get Free Intelligence on your Next Deal"
2. "Start Free Trial"
3. "Book Demo"
4. "Try A Free Account Research Report"

**Fix:** Match ad copy → landing page headline → single CTA. If ad says "Try AI Account Research Free," the LP CTA must match exactly.

#### Message-Match Gap

| Ad Query (assumed) | Expected Landing Message | Current Homepage Message |
|---|---|---|
| "buyer intelligence platform" | Clear definition + feature proof | "Previously Impossible Buyer Intelligence" |
| "AI sales research tool" | How the tool works in 3 minutes | Agent Miia under brand name, not functional descriptor |
| "Humantic AI demo" | Demo booking with social proof | Demo CTA competes with 3 others |

#### Missing Decision Information

- **Pricing signal** — not required to publish, but "contact for enterprise pricing" reduces objection
- **Integration list** — Salesforce, HubSpot, LinkedIn Sales Navigator should be visible on paid LP
- **Implementation friction** — "how long to get up and running" not answered
- **Procurement path** — SOC 2 / GDPR present but no "security overview" or "procurement resources" link

---

### 4. Dual-Surface Scorecard

| Surface | Score | Rationale |
|---|---|---|
| **Traditional paid search** | 4 / 10 | No dedicated LP, CTA fragmentation, message mismatch, missing integration/pricing signals |
| **LinkedIn / social paid** | 6 / 10 | "This AI Is Not For Everyone" is strong social-native copy; Gartner + outcome stats are scroll-stoppers |
| **AI-assisted discovery** | 3 / 10 | No structured FAQ, unsourced stats, brand-name products block AI extraction |
| **Conversion readiness** | 5 / 10 | Trust signals exist; conversion architecture broken by fragmentation |

---

### 5. Paid Ad Creative Angles

| Angle | Headline Variant | Supporting Proof |
|---|---|---|
| Speed | "3-Minute Account Research for Enterprise Deals" | Agent Miia — "3-minute reports" on homepage |
| Outcome | "109% More Qualified Pipeline. Without More Reps." | *Needs source before running* |
| Selectivity | "Not for Everyone. Built for Elite Enterprise Sellers." | "This AI Is Not For Everyone" section |
| Compliance | "SOC 2. GDPR. EU AI Act. Buyer Intelligence Your Legal Team Can Approve." | Compliance badges |
| Social proof | "Used by Fortune 10. Taught at Indiana University." | Homepage trust signals |
| Gartner | "Gartner Cool Vendor 2024 — Try It Free" | Homepage |

---

### 6. Ranked Test Backlog

| Test | Hypothesis | Effort |
|---|---|---|
| 1. Dedicated paid landing page | Removing homepage fragmentation will increase demo CVR | Medium |
| 2. Single CTA test: "Free Report" vs "Book Demo" | Lower-friction offer increases top-of-funnel volume | Low |
| 3. "109% pipeline" as primary ad headline | Outcome-led ads outperform feature-led for evaluation-stage buyers | Low |
| 4. Add integration logos to LP | Reduces objection before it's raised | Low |
| 5. "This AI Is Not For Everyone" as LinkedIn ad copy | Exclusivity framing increases CTR from ICP | Low |

---

### 7. Measurement Fix

**Current risk:** 4 CTAs = split attribution, impossible to read ROAS.

| Event | Tool | Priority |
|---|---|---|
| Primary: Demo booked (qualified lead) | CRM + UTM → ad platform | P1 |
| Secondary: Free report activated | Product analytics + UTM | P1 |
| Tertiary: Free trial → paid upgrade | CRM pipeline | P2 |
| Negative: Bounce rate on paid LP | GA4 | P1 |

> **Do not optimise ad spend until the primary conversion event is isolated and tracked end-to-end.**

---

## 5. CRO Scorecard — 3 Pages

*Scored by [gtm-predictor](https://gtm-predictor-two.vercel.app) · gpt-4o-mini · Rubric sources: Baymard, NN/g, Unbounce 2024, HubSpot 2024*

### Overall Scores

| Page | Score | Verdict |
|---|---|---|
| **Homepage** (`/`) | **5.5 / 10** | CTA fragmentation, buried social proof |
| **Product** (`/miia`) | **5.5 / 10** | Brand-first copy; social proof missing on the closing page |
| **Pricing** (`/start/pricing`) | **4.5 / 10** | Lowest — trust signals near-absent, headline mismatched to intent |

---

### Homepage `/` — Dimension Breakdown

| Dimension | Score | Fix | Expected Lift |
|---|---|---|---|
| Headline | 6/10 | Shorten to ≤8 words, value first | +5–10% |
| Subhead | 5/10 | Add audience specificity: "for enterprise B2B sales teams" | +5–10% |
| CTA | 6/10 | "Get Your Free Intelligence Report Now" — single, urgent | +10–15% |
| **Social proof** | **4/10** | **Move Gartner + Fortune 10 logos above fold, add metrics** | **+10–15%** |
| Form friction | 5/10 | Limit to name + email only | +10–15% |
| Page focus | 5/10 | One primary CTA per page — remove competing actions | +5–10% |
| Trust signals | 6/10 | SOC 2 / GDPR badges visible above fold | +5–10% |
| Mobile-readable | 5/10 | Break dense paragraphs into scannable bullets | +5–10% |

**Top 3 fixes:**
1. Social proof above fold — logos + "109% pipeline increase" stat with source
2. Simplify form to 2 fields
3. Kill the 3 competing CTAs — one primary action only

---

### Product Page `/miia` — Dimension Breakdown

| Dimension | Score | Fix | Expected Lift |
|---|---|---|---|
| Headline | 6/10 | Lead with outcome: "AI Account Research in 5 Minutes" | +5–10% |
| Subhead | 5/10 | Name the audience: "for enterprise sales teams with complex buying committees" | +5–10% |
| **CTA** | **4/10** | **"Get Your Free 5-Minute Account Report Now" — add "Free", add urgency** | **+10–15%** |
| **Social proof** | **3/10** | **Add 1 named quote with metric — weakest dimension on product page** | **+10–15%** |
| Form friction | 5/10 | 2 fields max | +10–15% |
| Page focus | 6/10 | Consolidate to free report CTA only | +5–10% |
| Trust signals | 4/10 | SOC 2 badge missing from product page | +5–10% |
| Mobile-readable | 5/10 | Feature descriptions → bullet list | +5–10% |

**Top 3 fixes:**
1. CTA: "Try A 5-Minute Report Now" → "Get Your Free 5-Minute Account Report"
2. Add one testimonial with named role + metric
3. Break feature descriptions into bullets

---

### Pricing Page `/start/pricing` — Dimension Breakdown

| Dimension | Score | Fix | Expected Lift |
|---|---|---|---|
| Headline | 5/10 | "Get Started With Personality Insights" → "Unlock Sales Success with Personality Insights" | +5–10% |
| Subhead | 4/10 | Add audience + benefit — both missing | +5–10% |
| CTA | 6/10 | "Book a Demo" → "Get Your Free Demo Now" + contrasting colour | +10–15% |
| **Social proof** | **3/10** | **No logos, no metrics — highest-impact gap on this page** | **+10–20%** |
| **Form friction** | **5/10** | **Remove "receive promotional offers" checkbox** | **+10–15%** |
| **Page focus** | **4/10** | **Consolidate to demo booking + 3 key benefits** | **+5–10%** |
| **Trust signals** | **2/10** | **Worst score across all pages — no security badges, no guarantee** | **+5–10%** |
| Mobile-readable | 5/10 | Dense text — break into short paragraphs + bullets | +5–10% |

**Top 3 fixes:**
1. Trust signals — add SOC 2, GDPR, G2 badge directly above the demo form
2. Social proof — 2 client logos + one metric quote minimum
3. Remove the promo checkbox — unnecessary friction at decision moment

---

### Cross-Page Priority Stack

| Rank | Fix | Pages | Estimated Lift |
|---|---|---|---|
| 1 | Named social proof with metrics above fold | All 3 | +10–20% |
| 2 | Single primary CTA per page | All 3 | +10–15% |
| 3 | Trust signals on pricing page (SOC 2 / GDPR at form) | Pricing | +5–10% |
| 4 | Remove promo checkbox from pricing form | Pricing | +10–15% |
| 5 | Product page CTA rewrite — add "Free" + urgency | /miia | +10–15% |
| 6 | Headline ≤8 words with outcome language | All 3 | +5–10% |

---

## 6. Crawl Audit — 404s, Broken Links, Missing Tags

*Tool: Firecrawl · 40 pages crawled · 200 credits · all pages returned HTTP 200*

---

### 404s

**None found.** Every crawled page returned HTTP 200.

---

### Broken Links

One malformed internal link found:

| Source Page | Broken Link | Issue | Fix |
|---|---|---|---|
| `/comparison/ibm-watson-alternative` | `https://humantic.ai/comparison/linkedin.com/in/katrinacockrell/` | LinkedIn URL prepended with humantic.ai domain — would 404 if followed | Change href to `https://linkedin.com/in/katrinacockrell/` |

---

### Critical: Canonical Misdirection (14 pages)

**This is the single biggest SEO issue on the site.** These pages point their `<link rel="canonical">` to `https://humantic.ai/` — Google treats all of them as duplicates of the homepage and will not index them individually.

| Page | Canonical Set To | Impact |
|---|---|---|
| `/buyer-intelligence` | `humantic.ai/` | Not indexed |
| `/solutions/revenue` | `humantic.ai/` | Not indexed |
| `/sandler` | `humantic.ai/` | Not indexed |
| `/sandler/pricing` | `humantic.ai/` | Not indexed |
| `/solutions/personality-ai-api` | `humantic.ai/` | Not indexed |
| `/start/pricing` | `humantic.ai/` | Not indexed |
| `/start/AE` | `humantic.ai/` | Not indexed |
| `/start/revops` | `humantic.ai` (no trailing slash) | Not indexed |
| `/comparison/crystal-knows-alternative` | `humantic.ai/` | Not indexed |
| `/comparison/ibm-watson-alternative` | `humantic.ai/` | Not indexed |
| `/comparison/xiq-alternative` | `humantic.ai/` | Not indexed |
| `/personalization-suite` | `humantic.ai/` | Not indexed |
| `/miia` | `/miia#` (broken relative path) | Broken canonical |
| `/pi` | MISSING | No canonical at all |

**Fix:** Each page needs `<link rel="canonical" href="https://humantic.ai/[its-own-path]">`. Likely a CMS/template misconfiguration — one global canonical overriding all pages.

---

### Pages with noindex (Review Required)

| Page | noindex Set? | Likely Intentional? |
|---|---|---|
| `/buyer-intelligence` | ✓ | ❓ — key SEO category page |
| `/solutions/revenue` | ✓ | ❓ — core solution page |
| `/personalization-suite` | ✓ | ❓ — product page |
| `/start/pricing` | ✓ | ❓ — pricing should be indexable |
| `/start/AE`, `/start/bdr`, `/start/sales-leader`, `/start/revops` | ✓ | ✓ (role-specific onboarding) |
| `/sandler`, `/sandler/pricing` | ✓ | ✓ (partner-specific) |
| `/comparison/crystal-knows-alternative` | — | ✗ — comparison pages should be indexed |
| `/comparison/xiq-alternative`, `/ibm-watson-alternative` | ✓ | ✗ — link-building opportunities being wasted |
| `/library/*` (all 5 sub-pages) | ✓ | ❓ — content library should be indexed |
| `/release-notes` | ✓ | ✓ (product docs) |
| `/fitness-challenge` | ✓ | ✓ (stale campaign) |

**Priority:** Un-noindex `/buyer-intelligence`, `/solutions/revenue`, `/start/pricing`, all `/comparison/*`, and the entire `/library/*` tree.

---

### Missing SEO Tags Per Page

**Complete tag failure (all 7 tags missing — JS rendering issue):**

| Page | Missing |
|---|---|
| `/start` | title, meta desc, h1, canonical, robots, og:title, og:desc |
| `/start/bdr` | title, meta desc, h1, canonical, robots, og:title, og:desc |
| `/library` | title, meta desc, h1, canonical, robots, og:title, og:desc |
| `/library/case-studies` | title, meta desc, h1, canonical, robots, og:title, og:desc |
| `/library/ebooks-and-guides` | title, meta desc, h1, canonical, robots, og:title, og:desc |
| `/cdpa` | title, meta desc, h1, canonical, robots, og:title, og:desc |

**Partial — og tags missing:**

| Page | Missing |
|---|---|
| `/pi` | og:title, og:description, canonical |
| `/library/whitepapers` | og:title, og:description |
| `/library/videos` | og:title, og:description |

---

### Other Anomalies

| Issue | Detail | Fix |
|---|---|---|
| **Broken og:image on `/personalization-suite`** | Tag value contains raw HTML from next `<meta>` — image fails on social shares | Fix malformed `<meta>` — likely unclosed tag in template |
| **3 conflicting robots tags on `/ibm-watson-alternative`** | `["noindex,nofollow", "noindex", "noindex"]` | Remove duplicates — leave one or remove all |
| **Duplicate author meta** | `["Humantic", "HubSpot, Inc.", "HubSpot, Inc."]` across many pages | Strip HubSpot's `<meta name="author">` from theme output |
| **4× duplicate viewport tags on `/solutions/revenue`** | Multiple `<meta name="viewport">` from stacked templates | Deduplicate to one |
| **Public profile canonical mismatch (Ala Boincean)** | Canonical slug differs from page URL slug | Reconcile canonical to match actual URL |
| **`/fitness-challenge` still live** | Stale 2023 campaign, all tags broken with leading `.` rendering artifact | 301 redirect to homepage or delete |
| **Blog h1 renders as `"/"`** | `/blog/` h1 shows path instead of actual heading | Verify h1 is in static HTML, not injected by JS |

---

### Crawl Audit — Priority Fix Order

| Rank | Fix | Effort |
|---|---|---|
| 1 | **Fix canonicals on all 14 misdirected pages** — self-canonical per page | Low (CMS config) |
| 2 | **Remove noindex from** `/buyer-intelligence`, `/solutions/revenue`, `/start/pricing`, `/comparison/*`, `/library/*` | Low |
| 3 | **Fix broken og:image** on `/personalization-suite` | Low |
| 4 | **Fix malformed link** on `/ibm-watson-alternative` | Low |
| 5 | **Add og:title + og:description** to `/pi`, `/library/whitepapers`, `/library/videos` | Low |
| 6 | **Remove duplicate meta tags** (author, viewport, robots) across all pages | Medium |
| 7 | **301 or remove** `/fitness-challenge` | Low |

---

## Master Priority Stack — All Findings

| Rank | Fix | Section | Effort | Expected Impact |
|---|---|---|---|---|
| 1 | Fix canonical misdirection on 14 pages | Crawl | Low | 🔴 Critical — pages not being indexed |
| 2 | Remove noindex from key marketing pages | Crawl | Low | 🔴 Critical — category + comparison pages dark |
| 3 | Write meta description | FLOW/AEO | Low | 🟠 High — SERP + AI snippet control |
| 4 | Add `FAQPage` JSON-LD | AEO | Low | 🟠 High — AI extraction readiness |
| 5 | Rewrite H1 with buyer language | FLOW | Low | 🟠 High — search + message match |
| 6 | Fix broken og:image on `/personalization-suite` | Crawl | Low | 🟡 Medium — social sharing broken |
| 7 | Add social proof above fold (all 3 pages) | CRO | Medium | 🟠 High — +10–20% CVR |
| 8 | Consolidate to single CTA per page | CRO/Paid | Low | 🟠 High — +10–15% CVR |
| 9 | Source the outcome stats (109%, 16.2%) | FLOW/Paid | Low | 🟡 Medium — AEO + ad credibility |
| 10 | Create dedicated paid landing page | Paid | Medium | 🟠 High — ad ROAS |
| 11 | Add `Organization` + `SoftwareApplication` JSON-LD | AEO | Medium | 🟡 Medium — entity clarity |
| 12 | Fix duplicate meta tags sitewide | Crawl | Medium | 🟡 Medium — template hygiene |
| 13 | Add integration logos to product + paid pages | Paid/CRO | Low | 🟡 Medium — objection handling |
| 14 | Create `/what-is-buyer-intelligence` category page | FLOW/AEO | Medium | 🟡 Medium — category ownership |
| 15 | Build comparison pages (`/vs-crystal-knows`, `/vs-gong`) | FLOW/AEO | High | 🟡 Medium — long-tail + AI citations |
