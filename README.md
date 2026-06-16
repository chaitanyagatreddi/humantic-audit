# Humantic AI — Full GTM & SEO Audit

Proof-of-work compiled June 2026. A complete growth audit of [humantic.ai](https://humantic.ai) across revenue leakage, SEO, AEO, paid ads, CRO, and crawl health.

---

## What's Inside

| Section | What it covers |
|---|---|
| **Revenue Leakage** | ~$1.1M/year leak from 14 canonically-misdirected and noindexed pages. Formula from [Sprinto Growth Audit](https://github.com/chaitanyagatreddi/sprinto), adapted for enterprise SaaS ($25K ACV, 6% demo→close, 2% page→demo). |
| **FLOW — Find** | Keyword intent gap analysis. H1 uses brand aspiration, not buyer search language. Product names (Miia, Pi, Kairos) are unsearchable. Category ("buyer intelligence") is self-coined and not indexed. |
| **FLOW — Optimize** | Missing meta description, unsourced outcome stats (109% pipeline, 16.2% close), 4 competing CTAs, no canonical page focus. |
| **AEO** | AI answer engine readiness: no FAQPage/Organization/SoftwareApplication schema, no llms.txt, no definitional paragraph for ChatGPT/Perplexity/Google AI Overviews to cite. |
| **Paid Ads** | No dedicated landing pages, message-match gap between ad copy and homepage H1, 4 CTAs creating attribution split. Creative angles from existing on-site evidence. |
| **CRO** | Three pages scored via [gtm-predictor](https://github.com/chaitanyagatreddi/gtm-predictor): Homepage 5.5/10, Product (/miia) 5.5/10, Pricing 4.5/10. Rubric: Baymard, NN/g, Unbounce 2024, HubSpot 2024. |
| **Crawl Audit** | Firecrawl crawl of 40 pages: 0 hard 404s, 1 malformed internal link, 14 pages with wrong canonical, 9 pages with noindex on revenue-critical URLs, broken og:image on /personalization-suite. |

---

## Headline Numbers

- **~$1.1M/year** confirmed revenue leak (canonical + noindex issues blocking organic traffic)
- **~$2.16M/year** additional CRO uplift opportunity (conversion rate 2.0% → 2.8% at category baseline)
- **14 pages** canonicalized to homepage — not independently indexed by Google
- **9 pages** with noindex including /start/pricing, /buyer-intelligence, all /comparison/* pages
- **CRO scores:** Homepage 5.5/10 · Product 5.5/10 · Pricing 4.5/10

---

## Top 5 Fixes (by revenue impact)

1. **Fix canonicals on 14 pages** — one CMS config change, recovers ~$1M/year organic pipeline
2. **Remove noindex from** `/buyer-intelligence`, `/solutions/revenue`, `/start/pricing`, `/comparison/*` — BOFU pages currently dark
3. **Add FAQPage + Organization + SoftwareApplication JSON-LD** — highest AEO ROI per engineering hour
4. **Consolidate to one CTA per page** — homepage runs 4 competing actions, +10–15% estimated CVR
5. **Source the outcome stats** — "109% pipeline increase" is unattributed; AI engines and enterprise procurement both need a methodology note

---

## Methodology

- **Revenue formula** — Sprinto Growth Audit (May 2026): `visits × page→demo% × demo→close% × ACV`
- **CRO scoring** — [gtm-predictor](https://github.com/chaitanyagatreddi/gtm-predictor) (gpt-4o-mini, Baymard/NN/g/Unbounce/HubSpot rubric)
- **Crawl** — Firecrawl, 40 pages, June 2026
- **Traffic estimates** are conservative proxies — validate against GSC actuals

---

## Files

| File | Description |
|---|---|
| `humantic-ai-seo-audit.md` | Full audit — all 6 sections |
| `README.md` | This file |

---

*Audit by [Chaitanya Gatreddi](https://github.com/chaitanyagatreddi) · June 2026*
