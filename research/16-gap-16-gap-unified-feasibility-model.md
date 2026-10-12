# 16 — Unified Feasibility Model: Downloads, P&L, Break-even, Funding and Expansion Costs (Egypt)

> **Purpose.** Files 08, 13 and 14 contain three forecast models that disagree with each other, and files 03, 10 and 11 add further conflicting building-size and cost assumptions. This file replaces all of them with **one reconciled 36-month monthly model** with three scenarios. It is the feasibility study (دراسة جدوى) the founder asked for.
> **Research date:** 2026-10-12. **Model month M1 = November 2026.** Build runs M1–M4, the pilot runs M5–M6, and scale-up starts at M7.
> **Convention:** Every sourced number carries a URL. Every model input I chose is marked **ESTIMATE** and has its reasoning beside it. Where I could not find something, I say so.
> **Machine-readable model:** `research/data/16-model.csv` (3 scenarios × 36 months × 47 columns). The generator script is `research/data/16-model.py`, so you can re-run it with different inputs.

---

## 0. Executive summary

**The verdict in one paragraph.** The idea is feasible, but it is **slower and smaller in the first 36 months than files 08, 13 and 14 claimed**. Under the founder's constraints (zero paid marketing, a budget for development and operations only), the base case reaches **~11,100 Live buildings plus 60 compounds, ~92,600 active households, ~154,000 accounts and ~167,000 cumulative app downloads by month 36 (Oct 2029)**. Monthly revenue at M36 is **EGP 1.90 M (~USD 31.6k)**. The base case **does not break even inside 36 months**. It turns operationally profitable around **M45 (Jul 2030) at ~135k active households**, and the **peak cumulative funding need is ~USD 570k**. The founder's own budget realistically covers **M1–M12 (~USD 105k)**. After that, a **pre-seed raise of USD 400–600k around M10–M14** is needed unless the aggressive-case traction metrics appear. The two biggest swing factors are **marketplace booking frequency and ads yield**, not the viral K-factor. The single biggest cost trap is **running the WhatsApp assistant for every resident**: at 3× the planned WhatsApp volume, the base case never breaks even.

### 0.1 Headline numbers (all ESTIMATES from this model)

| Metric | Conservative | **Base** | Aggressive |
|---|---|---|---|
| Live buildings M12 / M24 / M36 | 208 / 1,021 / 2,286 | **636 / 4,188 / 11,069** | 1,614 / 12,793 / 36,369 |
| Compounds onboarded by M36 | 20 | **60** | 120 |
| Active households M12 / M24 / M36 | 859 / 7,200 / 16,059 | **5,167 / 38,788 / 92,601** | 18,432 / 136,656 / 350,280 |
| Accounts M12 / M24 / M36 | 1,212 / 10,668 / 23,743 | **8,652 / 65,185 / 154,063** | 33,975 / 250,601 / 638,947 |
| MAU at M36 | 10,684 | **84,735** | 396,147 |
| WhatsApp-reachable residents at M36 (non-installers) | 18,150 | **80,528** | 244,654 |
| Cumulative downloads M12 / M24 / M36 | 780 / 8,891 / 22,894 | **6,762 / 61,190 / 166,581** | 28,992 / 247,513 / 719,687 |
| Revenue in year 1 / year 2 / year 3 (EGP M) | 0.00 / 0.18 / 1.19 | **0.01 / 2.28 / 13.43** | 0.20 / 13.97 / 83.36 |
| Costs in year 1 / year 2 / year 3 (EGP M) | 4.85 / 9.01 / 12.79 | **5.60 / 14.03 / 26.04** | 6.99 / 24.58 / 50.91 |
| Monthly revenue at M36 | EGP 167k (~$2.8k) | **EGP 1,897k (~$31.6k)** | EGP 11,962k (~$199.4k) |
| Monthly operating result at M36 | EGP -925k | **EGP -643k** | EGP +6,658k |
| Break-even month (sustained) | none by M48 | **M45 (Jul 2030)** | **M26 (Dec 2028)** |
| Cumulative cash at M12 / M24 / M36 (USD k) | -90 / -247 / -444 | **-104 / -313 / -528** | -126 / -315 / +231 |
| Peak funding need (USD, through M48) | ~647k and still burning | **~568k** | ~320k |

### 0.2 Seven conclusions the founder should act on

1. **Plan on 90–100k households by month 36, not 450k (08) or 235k (13) or 200k (14).** Those files combined a too-large building size, generous activation and, in 08's case, a K-factor that compounds every quarter. All three overstated households per building or growth per building (§1, §3).
2. **The ordinary Egyptian building is smaller than all prior files assumed.** The 2017 census gives **5.3 units per urban building nationally and 8.05 in Cairo**, and only **~55% of urban apartments are occupied** (§3). The reconciled planning value is **10 occupied households per target building**, and with 60% activation that means **6 active households per Live building**.
3. **Break-even needs about 130–170k active households**, not 100–120k (14). The exact figure depends on the size of the team you carry. Monetization per household is ~EGP 20/month at M36 in the base case (§9).
4. **The founder's budget funds the first 12 months**, about USD 105k cumulative burn, which matches 14's estimate. **The raise decision comes at M10–M14** and depends on hitting the gates in §13.
5. **Field champions are the growth engine and the largest variable cost.** A full-cost Live building costs **~EGP 1,200 (USD ~22) across all channels**, or **~EGP 2,700 (USD ~49) when sourced by a field champion**. Each new city costs about **EGP 1.8 M (~USD 34k) in its first year** (§10).
6. **WhatsApp is the cost line to police, not AI.** Over 36 months the base case spends EGP 3.2 M on WhatsApp and SMS against EGP 1.0 M on AI. Giving every resident the 1:1 WhatsApp assistant (3× volume) pushes break-even beyond M60 (§11).
7. **Marketplace frequency and ads yield decide profitability.** Bookings per household per month (2.5% vs 6%) move break-even from M53 to M40. Take rate and AOV matter less (§11).

---

## 1. What this file supersedes

The table lists every conflicting number in earlier files that this model replaces. **Treat the earlier values as obsolete.** The narrative, competitor and UX findings in those files still stand.

| File & section | Old number | Problem | Superseded by (this file) |
|---|---|---|---|
| 08 §7.2 A6 | 12 occupied units per building | Census: 5.3 units per urban building, 8.05 in Cairo; ~55% urban apartment occupancy | **10 occupied HH** per target city building (9 / 10 / 11 by scenario), §3 |
| 08 §7.2 A7 | 2.2 users per household | Counts every smartphone adult, not accounts actually created | **1.6 accounts per active HH** (1.4 / 1.6 / 1.8); 1.8 in compounds |
| 08 §7.4 | K = 0.25 / 0.35 / 0.5 **per quarter** on the building stock | Applied to the stock, this compounds about 10% a month forever. 13 defines K as lifetime (×1/(1−K)) | **Lifetime K = 0.30 / 0.45 / 0.65**, realised over 6 months after activation |
| 08 §0, §7.3 | Y3 base ≈ 35k buildings, 450k HH, 1.0 M users; aggressive 2.4 M | Driven by the stock-compounding K and 12 HH/building | Base M36: **11,069 Live buildings + 60 compounds, 92,601 HH, 154,063 accounts**. Aggressive: 350,280 HH |
| 08 §7.4 | Downloads Y1 0.10–0.15 M, Y2 0.4–0.6 M, Y3 1.3 M (base) | Users × 1.3 on inflated users | Cumulative downloads **6,762 / 61,190 / 166,581** (base) |
| 08 §8.4 | Y3 revenue run-rate EGP 78 M base | 450k HH × 25% transacting × 4 orders | Base M36 run-rate **EGP 22.8 M/yr** |
| 08 §7.4, §9 | Amarati and Imarti install counts "not verified" | 01 and 12 had already verified them | **Re-verified 2026-10-12: Amarati 1K+ (4.7★), Imarti 100+** (Play Store, §12) |
| 08 header, 11 §3.3, 03 §12.3 | FX ≈ 48–50 EGP/USD | Stale | **52.5 at M1** (CBE 52.32/52.46 on 7 Oct 2026), ESTIMATE path to **60 at M36** |
| 13 §11.1 | 18 units per building × 60–65% join, no vacancy discount | ~1.8× the census-consistent value | 10 occupied HH × 60% activation (= 6 active HH per Live building) |
| 13 §11.2 | Base M12: 2,000 buildings, 41k accounts, 55k downloads; M36: 400k accounts | Assumes scale from month 1; ignores the 4-month build and pilot | Base M12: **636 Live, 8,652 accounts, 6,762 downloads**; M36 **154,063** accounts |
| 13 §11.3 | AOV EGP 900, take 12%, EGP 18–21 M/yr at M36 | Conflicts with 14 | AOV **EGP 750** (Oct-2026 prices, indexed at 1%/month), take **15%**; M36 run-rate EGP 22.8 M/yr from all lines |
| 13 §6.4, 14 §3.3, 10 §9 | 18 / 30 / 30 HH per building in WhatsApp cost models | Building size inconsistent | WhatsApp cost modelled per account and per Live building (§4, row C9) |
| 14 §7.3 | Base 200k active HH at M36, AOV 700, take 18%, revenue $74.3k/month | Household count far above the reconciled funnel | Base **92,601 HH, $31.6k/month**. 200k HH is reached only in the aggressive case (~M28) |
| 14 §7.3 | Break-even at 100–120k active HH | Leaves out field ops and the salary step-ups | **~135k HH** (base cost base, M45); **~165k** (aggressive cost base, M26) |
| 14 §8 | 24-month cost ≈ USD 400k | No field-ops ramp per city; FX flat at 52.5 | 24-month cost **EGP 19.6 M (≈ USD 353k)**; 24-month net burn **USD 313k** |
| 14 §1.1 | FX 52.5 flat | OK as a starting point | 52.5 → 60 path; FX sensitivity in §11 |
| 03 §12.3 | 200k HH base, AOV 600, revenue EGP 81 M | "Year 1 after monetization", no time axis | Superseded by §7 monthly P&L |
| 10 §9 | 1,000 buildings × 30 flats × 1.5 = 45k users | Building size | 1,000 Live buildings ≈ 6,000 active HH ≈ 9,600 accounts |
| 11 §3.3 | 25 units per building; AI ≈ $0.20–0.35 per building per month | Building size and FX | AI = **$0.015 per MAU + $0.02 per Live building per month** (≈ $0.10 per building) |

---

## 2. Verified macro inputs (October 2026)

| Input | Value used | Evidence (live check, Oct 2026) | Status |
|---|---|---|---|
| USD/EGP (CBE) | **52.5 at M1** | CBE official rate **52.3204 buy / 52.4600 sell on Wed 7 Oct 2026** ([Al Mal News](https://almalnews.com/2139951/)); 52.22/52.36 on 4 Oct ([Al Mal News](https://almalnews.com/2139292/)); XE 52.58 on 11 Oct (file 14) | **Confirmed** (2 sources) |
| FX path M1→M36 | 52.5 → 60.0 (≈ 4.5%/yr) | **ESTIMATE.** The 2026 range was ~49–55 (file 08). I assume mild depreciation, roughly half the inflation differential. Tested 54 and 66 in §11 | Estimate |
| Urban CPI (Sep 2026) | 13.9% y/y; monthly +1.3% | CAPMAS via [Daily News Egypt, 10 Oct 2026](https://www.dailynewsegypt.com/2026/10/10/egypts-annual-urban-inflation-eases-to-13-9-in-september/); national 12.8% ([Egyptian Streets](https://egyptianstreets.com/2026/10/11/egypts-annual-inflation-rises-to-12-8-percent-in-september-as-food-prices-increase/)) | **Confirmed** (2 sources) |
| Price index in model | **+1.0%/month (≈12.7%/yr)** on EGP prices (AOV, fees, bonuses) | ESTIMATE. CBE targets 7% ±2pp by H2 2027 ([Rio Times](https://www.riotimesonline.com/egypt-urban-inflation-13-9-percent-september-2026/), file 14), so 12.7% is a conservative blend | Estimate |
| Salary index | **+15% step every 12 months** | File 14 recommends +12–20%/yr to retain developers | Estimate |
| Private-sector minimum wage | EGP 7,000/month (from Mar 2025). I found **no confirmation of an 8,000 private-sector rise**; 8,000 is for the public sector from Jul 2026 | [CairoScene](https://cairoscene.com/buzz/minimum-wage-for-private-sector-in-egypt-raised-to-egp-7-000); search summary of secondary sources | Partly confirmed |
| Android / iOS share | StatCounter **Sep 2026: Android 83.4%, iOS 16.58%** (Jun 91.1%, Aug 88.0%) | [StatCounter](https://gs.statcounter.com/os-market-share/mobile/egypt) (re-fetched); vendor shares Sep 2026 Samsung 23.9%, Oppo 17.1%, Apple 16.6% ([StatCounter vendors](https://gs.statcounter.com/vendor-market-share/mobile-device/egypt)) | Confirmed. Web-traffic share is volatile month to month |
| Download split used | City buildings **88% Android / 12% iOS**; compounds **70 / 30** | ESTIMATE. Middle of the Jun–Sep range for city stock; compounds skew to iPhone owners (higher income) | Estimate |
| WhatsApp Egypt rates | Marketing $0.0644; utility, authentication and service $0.0036; service messages free for the first 1,000 per number per month from 1 Oct 2026; +14% VAT | [ChatMaxima](https://chatmaxima.com/whatsapp-api-pricing/egypt/) (re-fetched 12 Oct 2026); files 10 and 14 | Confirmed (BSP; Meta CSV not parsed) |
| LLM prices | Gemini 2.5 Flash-Lite $0.10 / $0.40 per 1M tokens; Gemini 2.5 Flash $0.30 / $2.50; newer 3.x Flash models $0.25–0.75 input | [Google pricing](https://ai.google.dev/gemini-api/docs/pricing) (re-fetched) | Confirmed. The model uses $0.015/MAU, which leaves headroom for moving to 3.x models |
| Field rep pay benchmark | Outside sales representative average **EGP 144k/yr** (~12k/month); retail sales median EGP 33k/yr | [Payscale Egypt 2026](https://www.payscale.com/research/EG/Job=Outside_Sales_Representative/Salary) | Indicative (aggregator) |

---

## 3. Settling "12 vs 18 units per building": what the census says

### 3.1 Census 2017 data (CAPMAS, Statistical Yearbook 2025, tables 7-10, 7-11, 7-12)

I downloaded the CAPMAS-sourced **Statistical Yearbook 2025, Part 2** ([MoSS PDF](https://www.moss.gov.eg/media/iuxiwrsi/الكتاب-الإحصائي-السنوي-_-2025_الجزء-الثاني.pdf)) and extracted the 2017 census tables. Building counts are regular buildings for housing and work (table 7-10, connected + not connected to sewage). Unit counts come from table 7-11.

| Governorate (urban) | Regular buildings | All units | Residential units | Apartments | **Units / building** | **Residential units / building** | Apartments / building |
|---|---|---|---|---|---|---|---|
| **Cairo** | 591,428 | 4,762,446 | 4,169,574 | 3,885,318 | **8.05** | **7.05** | 6.57 |
| **Giza (urban)** | 474,744 | 3,149,100 | 2,789,212 | 2,599,519 | **6.63** | 5.88 | 5.48 |
| **Alexandria (urban)** | 424,012 | 3,026,955 | 2,638,351 | 2,409,197 | **7.14** | 6.22 | 5.68 |
| Port Said | 40,694 | 282,740 | 243,613 | 220,203 | 6.95 | 5.99 | 5.41 |
| Qalyubia (urban) | 220,052 | 1,318,489 | 1,140,017 | 1,084,975 | 5.99 | 5.18 | 4.93 |
| Gharbia (urban) | 158,266 | 769,342 | 636,515 | 599,780 | 4.86 | 4.02 | 3.79 |
| Dakahlia (urban) | 225,373 | 1,054,820 | 847,223 | 779,866 | 4.68 | 3.76 | 3.46 |
| Sharkia (urban) | 239,724 | 981,730 | 808,854 | 712,977 | 4.10 | 3.37 | 2.97 |
| **Egypt urban total** | **4,077,580** | **21,643,979** | **18,624,236** | **16,759,256** | **5.31** | **4.57** | 4.11 |

*Derived ratios are my arithmetic on the CAPMAS figures. CEIC reports 688,001 urban buildings in Cairo (all building types; [CEIC](https://www.ceicdata.com/en/egypt/number-of-buildings-census-by-region/no-of-buildings-census-urban-cairo), page blocked, figure from the search snippet). That would lower Cairo's ratio to ~6.9.*

**Occupancy (table 7-12, urban apartments, 2017):** of 16,759,256 urban apartments, **9,165,143 (54.7%) were used for housing**. Of the rest, 2,474,632 were vacant and completed, 1,852,730 were vacant (other), 1,811,203 were closed because the family has another home, and 715,993 were closed because the family lives abroad. This matches the national 29% vacant-plus-closed figure in file 08.

### 3.2 Reconciliation

| Step | Value | Reasoning |
|---|---|---|
| Census mean, residential units per urban building | 4.6 (Cairo 7.05) | The mean includes 1–3-unit family houses, which are outside the SAM |
| Typical **target** building (≥5 units, has a treasurer or union) | **~14 residential units** (ESTIMATE) | The dominant "classical informal" and middle-class walk-up is 1–7 floors ([Cities Alliance / Sims](https://www.citiesalliance.org/sites/default/files/2019-07/CairosInformalAreas_fulltext.pdf)), with 1–2 small flats per floor and up to 3–4 in some cases ([ETH Zurich case study](https://ethz.ch/content/dam/ethz/special-interest/conference-websites-dam/no-cost-housing-dam/documents/Barthes_final.pdf)). Ground floors are often commercial ([MDPI 2023](https://www.mdpi.com/2075-5309/13/5/1263)). Mix: ~70% walk-ups at ~11 flats and ~30% towers (Nasr City, Maadi, Heliopolis, New Cairo) at ~22 flats → ~14 |
| Occupancy in target districts | **~72%** (ESTIMATE) | The urban average is 54.7%, but that includes new cities and unfinished stock. Established districts with a working committee are fuller |
| **Occupied households per target building** | **≈ 10** (conservative 9, aggressive 11) | 14 × 72% ≈ 10 |
| Activation (share of occupied HH with an account at maturity) | 50% / **60%** / 70% | 60% matches the "Live = ≥40%" threshold in 13 §3.2, with room above it |
| **Active HH per Live building** | 4.5 / **6.0** / 7.7 | Product of the two rows above |

**Verdict:** File 08's "12 occupied" is ~20% too high for the average target building. File 13's "18 units × 60% join" implies 10.8 active HH per building, about **1.8× the census-consistent value**, because it applied the join rate to total units with no vacancy discount. Eighteen units *is* realistic in New Cairo, Nasr City towers and 6th of October blocks. Use it as the aggressive district mix, not as the national planning value. **Validate in the pilot:** record units, occupied units and joined households for the first 100 buildings.

---

## 4. The reconciled assumption table

Values are listed as Conservative / **Base** / Aggressive. "Source" means a sourced figure; "ESTIMATE" means a model choice with the reasoning shown.

### 4.1 Growth engine

| # | Assumption | Cons / **Base** / Aggr | Source or reasoning |
|---|---|---|---|
| G1 | Timeline | Build M1–M4; pilot M5–M6; scale from M7 | 14 §8 (Option A team, 6-month MVP+pilot) |
| G2 | Founder-seeded Live buildings in the pilot (M5, M6) | 10+15 / **15+25** / 20+35 | ESTIMATE; 13 §12 targets 10 → 100 in 90 days |
| G3 | Field champions (headcount schedule) | 1→8 / **2→22** / 3→32 | ESTIMATE; one city wave adds 3–6 (§10) |
| G4 | Buildings seeded per champion per month | 18 / **25** / 32 | ESTIMATE: ~3 treasurer meetings a day × 20 days × ~40% agree to seed |
| G5 | Seeded → Live (field) | 45% / **55%** / 62% | 13 §13 targets ≥50% (M6) and ≥60% (M12) |
| G6 | Self-serve seeds per month by M36 (TikTok, SEO, captains), linear from M7 | 150 / **350** / 900 | ESTIMATE; 13 §7–8 content engine |
| G7 | Self-serve seed → Live | 25% / **30%** / 35% | ESTIMATE: lower intent than field seeds |
| G8 | Partner-channel seeds per month by M36 (elevator, tank, FM, suppliers), from M13 | 50 / **150** / 400 | ESTIMATE; 13 §5.2-E |
| G9 | Partner seed → Live | 40% (all) | ESTIMATE |
| G10 | **Lifetime inter-building K** (new Live per Live building, spread over 6 months) | 0.30 / **0.45** / 0.65 | 13 §4.2 target 0.3–0.4 with "great" at 0.4 ([Saxifrage](https://www.saxifrage.xyz/post/k-factor-benchmarks)); replaces 08's per-quarter K |
| G11 | Live-building churn per month | 2.5% / **1.5%** / 1.0% | ESTIMATE; 13 targets admin M3 retention ≥80% |
| G12 | Occupied HH per city building | 9 / **10** / 11 | §3 |
| G13 | Activation at maturity (ramp 50% → 80% → 100% over months 0–2) | 50% / **60%** / 70% | §3 |
| G14 | Accounts per active HH (city) | 1.4 / **1.6** / 1.8 | 13 (1.5–1.7); 08 (2.7 adults/HH) is the ceiling |
| G15 | Compounds onboarded by M36 (linear from start month) | 20 from M12 / **60 from M9** / 120 from M8 | 08 §7.4 (10/40/80) and 13 (80) |
| G16 | Occupied HH per compound | 1,000 / **1,200** / 1,400 | 13 §11.1 (1,000–1,500 units, 40–50% adoption); new-city occupancy is low (08 §2.5) |
| G17 | Compound activation (6-month ramp) | 35% / **45%** / 55% | 13 §11.1 |
| G18 | Accounts per compound HH | 1.6 / **1.8** / 1.9 | ESTIMATE: larger, younger families |
| G19 | MAU / accounts | 45% / **55%** / 62% | ESTIMATE: monthly dues cycle; 13 targets WAU/MAU ≥35% |
| G20 | App-install share of accounts (rest are WhatsApp/web-only), M5 → M36 | 45→65% / **50→75%** / 55→80%; compounds +15pp | 10 §9 assumes 50% WhatsApp-only in year 1 |
| G21 | Downloads | 1.25 × net new installers + 1% of installers a month (device changes) | ESTIMATE; 08 and 13 used 1.3 × users |
| G22 | WhatsApp-reachable residents | WhatsApp-only accounts + 70% of non-registered adults (1.5 per HH) in Live buildings | ESTIMATE: they see the shared cards in the building group |

### 4.2 Revenue (EGP prices are Oct-2026 and indexed at +1%/month)

| # | Line | Start month | Cons / **Base** / Aggr | Source or reasoning |
|---|---|---|---|---|
| R1 | Payment convenience fee: share of HH paying dues in-app with a fee (ramps to M36) | M12 / **M10** / M9 | 3→20% / **5→30%** / 8→40% | 14 §7.3 (20/30/40%) |
| R2 | Net margin per fee-bearing payment | — | EGP 3 / **5** / 6 | 14 §7.1: PSP pass-through + EGP 3–5 |
| R3 | Compound SaaS: paying share of compounds (after a 3-month free pilot) × flat monthly price | M12 / **M9** / M8 | 40% × 4,000 / **50% × 6,000** / 60% × 9,000 | Undercuts Saknna's compound plan at EGP 7,500/month ([saknna.com](https://saknna.com)) |
| R4 | "Pro" plan for large buildings and FM firms (share of Live buildings × price) | M18 / **M15** / M12 | 0.3% × 200 / **0.5% × 250** / 0.8% × 300 | ESTIMATE, anchored under Saknna's EGP 450 for 5 units |
| R5 | Marketplace bookings per active HH per month (ramps to M36) | M16 / **M13** / M11 | 0.5→2.5% / **1→4%** / 1.5→6% | 14 §7.3 (3/5/7% at M36), cut because density is lower; 03 §2: 3–4 handyman visits/HH/yr in total spend |
| R6 | AOV | — | 650 / **750** / 900 | 14 (700), 13 (900), 03 (600), 08 (700–900); Khidhma visits EGP 150–175 ([khidhma.com](https://www.khidhma.com/)) + AC/pest/cleaning tickets |
| R7 | Take rate | — | 12% / **15%** / 18% | 03 §8: Egyptian peers 20–25% (Khidmitty) and 30–50% (Sal7lyy) self-reported; Talabat 14–15% group-wide; "do not exceed ~20%" |
| R8 | Building contracts (elevator AMC, tanks, pest): share of Live buildings × EGP 12,000/yr × 10% fee | from R5 start | 0→8% / **0→15%** / 0→22% | 13 §10.3 (20% of Live buildings) |
| R9 | Ads and sponsorship (USD per active HH per year, ramps to M36) | M18 / **M15** / M13 | 0.4 / **1.0** / 1.5 | 14 §6.3 ($0.5–1.5); MyGate ~$2.6–2.8 in India, 65–70% of its revenue ([Inc42](https://inc42.com/buzz/mygate-trims-fy25-loss-by-61-to-₹15-4-cr/)) |
| R10 | Referrals (BNPL, insurance, ISP): EGP per active HH per year | M24 / **M18** / M15 | 5 / **15** / 30 | ESTIMATE; 14 §6.2 says fees are private, so this is upside only |
| R11 | Payment float | — | **0** | 14 §3.5: no published terms; holding funds needs a CBE licence |

### 4.3 Costs

| # | Line | Cons / **Base** / Aggr | Source or reasoning |
|---|---|---|---|
| C1 | Team, loaded EGP/month at Oct-2026 prices (M1–6 / M7–12 / M13–24 / M25–36) + 15% step each year | 265k / 380k / 420k / 460k; **265k / 440k / 500k / 650k**; 265k / 500k / 700k / 950k | 14 §2.3: Option A EGP 265k, Option B EGP 440k; M13–24 base ≈ 14's $11k after the step |
| C2 | Field champion, loaded + transport/phone | EGP 18,700/month (+ salary step) | 14 §2.2: EGP 9–12k net × 1.35 + EGP 2.5k transport; Payscale outside sales ~12k/month |
| C3 | Per new Live building: bawab or captain bonus + printed QR kit | EGP 150 (indexed) | 13 §5.2-C: EGP 50–100 bawab bonus; 14 §9: posters ≈ EGP 5 each |
| C4 | City lead per non-Cairo wave | EGP 35,000/month | ESTIMATE: senior field manager |
| C5 | City launch one-off per new wave | EGP 250,000 (indexed) | §10.2 breakdown (ESTIMATE) |
| C6 | Support agents | 1 per 30k MAU (min 1 from M5) × EGP 15k loaded | 14 §2.4: 1 per 25–40k MAU with AI triage; Wuzzuf EGP 10–14k |
| C7 | Infrastructure | $150 + $0.025/MAU per month | 14 §4: ≈ $0.03–0.05/MAU including messaging |
| C8 | AI | $0.015/MAU + $0.02 per Live building per month | 14 §3.4 ($0.01–0.015/MAU); 11 §3.3; headroom for 3.x model prices |
| C9 | WhatsApp | (4 utility/month per WhatsApp-only account + 0.5 per installer) + service (30% of accounts × 6 replies + 60 admin replies per Live building + 200 per compound − 3,000 free) + OTP (1.3 per new account + 2%/month re-login) × $0.0036 × 1.14 VAT; SMS fallback 5% of OTPs at $0.015 | 10 §9; ChatMaxima rates |
| C10 | Legal, accounting, tools | EGP 60k setup + EGP 20k/month; DPO EGP 15k/month from M10 | 14 §3.7 (EGP 25–60k formation; 3–8k accounting) |
| C11 | PDPL licence | EGP 150k when passing 100k records, then yearly (300k above 1 M) | ESTIMATE between 14's "≤100k exempt" and "max EGP 666,666 >5 M" ([Tamimi](https://www.tamimi.com/law_update_articles/from-policy-to-practice-egypt-issues-executive-regulations-of-the-personal-data-protection-law/)); intermediate tiers not found |
| C12 | Paid marketing | **0** | Founder constraint |

---

## 5. Model mechanics (so anyone can audit it)

- **New Live buildings** = (champions × G4 × G5) + pilot + (self-serve seeds × G7) + (partner seeds × G9) + **viral**, where viral = K/6 × (new Live buildings in the previous 6 months).
- **Live stock** = previous stock × (1 − churn) + new Live.
- **Active HH (city)** = Σ over cohorts of surviving buildings × G12 × G13 × age ramp (50%, 80%, 100%).
- **Active HH (compounds)** = compounds onboarded so far × G16 × G17 × 6-month ramp.
- **Accounts** = HH × G14 (city) or G18 (compound). **MAU** = accounts × G19. **Installers** = accounts × G20. **WhatsApp-only** = accounts − installers.
- **Revenue** follows R1–R10 from each start month. Ads convert at the month's FX.
- **Costs** follow C1–C11. USD lines (infra, AI, WhatsApp) convert at the month's FX.
- **Break-even month** is the first month from which the operating result stays ≥ 0 for the rest of a 48-month run.
- Operating result excludes tax. Under the Law 6/2025 SME regime (turnover ≤ EGP 20 M) tax is ~0.4–1.5% of revenue, which is immaterial here (14 §3.7).

---

## 6. Scenario logic in plain words

| | Conservative | **Base** | Aggressive |
|---|---|---|---|
| Story | The product works, but treasurers adopt slowly and the founder can fund only 1–4 champions. Giza starts at M16 and Alexandria at M28 | Cairo-East pilot, then **Giza and 6th of October/Zayed at M13, Alexandria at M19, Delta and new cities at M25**. Viral loops work at the 13 design target | Strong dues-in-app "aha" and WhatsApp share cards; a pre-seed raise at ~M10 funds 30+ champions; four waves by M21 |
| What has to be true | — | Seeded → Live ≥55%, K ≥0.45, 6 active HH per building, marketplace live by M13 | 7.7 active HH per building, K 0.65, 120 compounds, 6% booking rate |
| Is it plausible? | Floor if the product is good | Central, with zero marketing | Requires funding plus excellent execution, and still far below MyGate's VC-funded ramp (§12) |

---

## 7. 36-month monthly model

### 7.1 Base case — growth (monthly)

| M | Month | Champ. | New Live | Live bldgs | Compounds | Active HH | Accounts | MAU | App installers | WA-reachable residents | Downloads (Android / iOS) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | Nov-26 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 (0 / 0) |
| 2 | Dec-26 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 (0 / 0) |
| 3 | Jan-27 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 (0 / 0) |
| 4 | Feb-27 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 (0 / 0) |
| 5 | Mar-27 | 2 | 42 | 42 | 0 | 128 | 204 | 112 | 102 | 414 | 128 (112 / 15) |
| 6 | Apr-27 | 2 | 56 | 98 | 0 | 368 | 589 | 324 | 299 | 928 | 247 (218 / 30) |
| 7 | May-27 | 3 | 54 | 150 | 0 | 672 | 1,076 | 592 | 555 | 1,389 | 323 (284 / 39) |
| 8 | Jun-27 | 3 | 61 | 209 | 0 | 1,007 | 1,611 | 886 | 844 | 1,904 | 367 (323 / 44) |
| 9 | Jul-27 | 4 | 83 | 289 | 2 | 1,605 | 2,607 | 1,434 | 1,440 | 2,719 | 753 (640 / 113) |
| 10 | Aug-27 | 4 | 93 | 378 | 4 | 2,467 | 4,063 | 2,235 | 2,351 | 3,692 | 1,154 (952 / 202) |
| 11 | Sep-27 | 6 | 131 | 503 | 6 | 3,671 | 6,105 | 3,357 | 3,660 | 5,082 | 1,659 (1,341 / 318) |
| 12 | Oct-27 | 6 | 141 | 636 | 9 | 5,167 | 8,652 | 4,759 | 5,335 | 6,593 | 2,131 (1,699 / 432) |
| 13 | Nov-27 | 8 | 184 | 810 | 11 | 7,036 | 11,837 | 6,510 | 7,463 | 8,532 | 2,713 (2,144 / 569) |
| 14 | Dec-27 | 8 | 200 | 998 | 13 | 9,220 | 15,563 | 8,559 | 10,004 | 10,606 | 3,251 (2,553 / 698) |
| 15 | Jan-28 | 8 | 216 | 1,199 | 15 | 11,516 | 19,467 | 10,707 | 12,709 | 12,719 | 3,481 (2,726 / 755) |
| 16 | Feb-28 | 10 | 259 | 1,440 | 17 | 13,970 | 23,625 | 12,994 | 15,627 | 15,129 | 3,774 (2,954 / 821) |
| 17 | Mar-28 | 10 | 277 | 1,695 | 19 | 16,556 | 27,994 | 15,396 | 18,737 | 17,573 | 4,043 (3,166 / 878) |
| 18 | Apr-28 | 10 | 294 | 1,964 | 21 | 19,253 | 32,540 | 17,897 | 22,025 | 20,035 | 4,298 (3,368 / 930) |
| 19 | May-28 | 13 | 353 | 2,287 | 24 | 22,153 | 37,413 | 20,577 | 25,586 | 22,909 | 4,672 (3,667 / 1,005) |
| 20 | Jun-28 | 13 | 371 | 2,624 | 26 | 25,206 | 42,529 | 23,391 | 29,377 | 25,779 | 4,995 (3,929 / 1,066) |
| 21 | Jul-28 | 13 | 390 | 2,974 | 28 | 28,388 | 47,850 | 26,318 | 33,380 | 28,650 | 5,297 (4,175 / 1,122) |
| 22 | Aug-28 | 15 | 436 | 3,366 | 30 | 31,732 | 53,433 | 29,388 | 37,635 | 31,791 | 5,652 (4,465 / 1,188) |
| 23 | Sep-28 | 15 | 455 | 3,770 | 32 | 35,205 | 59,221 | 32,571 | 42,112 | 34,918 | 5,973 (4,728 / 1,245) |
| 24 | Oct-28 | 15 | 474 | 4,188 | 34 | 38,788 | 65,185 | 35,852 | 46,798 | 38,034 | 6,279 (4,980 / 1,299) |
| 25 | Nov-28 | 19 | 548 | 4,673 | 36 | 42,614 | 71,537 | 39,346 | 51,837 | 41,645 | 6,767 (5,379 / 1,388) |
| 26 | Dec-28 | 19 | 569 | 5,172 | 39 | 46,615 | 78,171 | 42,994 | 57,166 | 45,201 | 7,180 (5,720 / 1,460) |
| 27 | Jan-29 | 19 | 590 | 5,684 | 41 | 50,758 | 85,031 | 46,767 | 62,757 | 48,712 | 7,559 (6,036 / 1,524) |
| 28 | Feb-29 | 19 | 610 | 6,209 | 43 | 54,979 | 92,016 | 50,609 | 68,543 | 52,207 | 7,860 (6,289 / 1,572) |
| 29 | Mar-29 | 19 | 629 | 6,746 | 45 | 59,271 | 99,116 | 54,514 | 74,521 | 55,665 | 8,158 (6,539 / 1,620) |
| 30 | Apr-29 | 22 | 689 | 7,334 | 47 | 63,755 | 106,520 | 58,586 | 80,829 | 59,446 | 8,629 (6,929 / 1,700) |
| 31 | May-29 | 22 | 711 | 7,935 | 49 | 68,383 | 114,156 | 62,786 | 87,419 | 63,160 | 9,046 (7,277 / 1,769) |
| 32 | Jun-29 | 22 | 729 | 8,545 | 51 | 73,121 | 121,970 | 67,083 | 94,260 | 66,779 | 9,425 (7,595 / 1,830) |
| 33 | Jul-29 | 22 | 747 | 9,164 | 54 | 77,917 | 129,874 | 71,431 | 101,293 | 70,329 | 9,734 (7,856 / 1,878) |
| 34 | Aug-29 | 22 | 765 | 9,791 | 56 | 82,764 | 137,860 | 75,823 | 108,514 | 73,806 | 10,038 (8,113 / 1,925) |
| 35 | Sep-29 | 22 | 782 | 10,426 | 58 | 87,659 | 145,924 | 80,258 | 115,921 | 77,207 | 10,344 (8,372 / 1,972) |
| 36 | Oct-29 | 22 | 799 | 11,069 | 60 | 92,601 | 154,063 | 84,735 | 123,514 | 80,528 | 10,651 (8,631 / 2,020) |

### 7.2 Base case — P&L (EGP thousands, nominal)

| M | Payments | SaaS | Market-place | Ads | Referrals | **Revenue** | Team | Field ops | Support | Infra + AI | WhatsApp + SMS | Legal/PDPL | **Cost** | **Op. result** | Cum. cash (EGP k) | Cum. cash (USD k) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 0 | 0 | 0 | 0 | 0 | **0** | 265 | 0 | 0 | 3 | 0 | 80 | **348** | **-348** | -348 | -7 |
| 2 | 0 | 0 | 0 | 0 | 0 | **0** | 265 | 0 | 0 | 3 | 0 | 20 | **288** | **-288** | -635 | -12 |
| 3 | 0 | 0 | 0 | 0 | 0 | **0** | 265 | 0 | 0 | 8 | 0 | 20 | **293** | **-293** | -928 | -18 |
| 4 | 0 | 0 | 0 | 0 | 0 | **0** | 265 | 0 | 0 | 8 | 0 | 20 | **293** | **-293** | -1,221 | -23 |
| 5 | 0 | 0 | 0 | 0 | 0 | **0** | 265 | 106 | 15 | 8 | 0 | 20 | **415** | **-415** | -1,636 | -31 |
| 6 | 0 | 0 | 0 | 0 | 0 | **0** | 265 | 46 | 15 | 9 | 1 | 20 | **356** | **-356** | -1,992 | -38 |
| 7 | 0 | 0 | 0 | 0 | 0 | **0** | 440 | 65 | 15 | 10 | 2 | 20 | **552** | **-552** | -2,544 | -48 |
| 8 | 0 | 0 | 0 | 0 | 0 | **0** | 440 | 66 | 15 | 10 | 4 | 20 | **555** | **-555** | -3,099 | -58 |
| 9 | 0 | 0 | 0 | 0 | 0 | **0** | 440 | 88 | 15 | 12 | 6 | 20 | **581** | **-581** | -3,680 | -69 |
| 10 | 1 | 0 | 0 | 0 | 0 | **1** | 440 | 90 | 15 | 13 | 9 | 35 | **602** | **-601** | -4,281 | -80 |
| 11 | 1 | 0 | 0 | 0 | 0 | **1** | 440 | 134 | 15 | 16 | 12 | 35 | **652** | **-651** | -4,932 | -92 |
| 12 | 2 | 7 | 0 | 0 | 0 | **9** | 440 | 136 | 15 | 19 | 16 | 35 | **661** | **-652** | -5,584 | -104 |
| 13 | 3 | 14 | 9 | 0 | 0 | **27** | 575 | 525 | 17 | 23 | 22 | 40 | **1,203** | **-1,176** | -6,760 | -125 |
| 14 | 5 | 22 | 14 | 0 | 0 | **41** | 575 | 246 | 17 | 28 | 27 | 40 | **935** | **-894** | -7,654 | -141 |
| 15 | 6 | 31 | 21 | 5 | 0 | **64** | 575 | 249 | 17 | 33 | 33 | 40 | **949** | **-885** | -8,539 | -157 |
| 16 | 9 | 39 | 29 | 9 | 0 | **86** | 575 | 300 | 17 | 39 | 40 | 40 | **1,012** | **-926** | -9,465 | -174 |
| 17 | 11 | 48 | 38 | 14 | 0 | **112** | 575 | 304 | 17 | 45 | 47 | 40 | **1,029** | **-917** | -10,382 | -190 |
| 18 | 14 | 56 | 50 | 21 | 3 | **144** | 575 | 308 | 17 | 51 | 55 | 40 | **1,046** | **-902** | -11,284 | -206 |
| 19 | 18 | 65 | 64 | 28 | 5 | **180** | 575 | 722 | 17 | 57 | 64 | 40 | **1,476** | **-1,296** | -12,580 | -229 |
| 20 | 22 | 74 | 80 | 37 | 8 | **221** | 575 | 427 | 17 | 64 | 73 | 40 | **1,197** | **-976** | -13,556 | -246 |
| 21 | 27 | 83 | 99 | 48 | 11 | **267** | 575 | 431 | 17 | 72 | 82 | 40 | **1,217** | **-950** | -14,506 | -263 |
| 22 | 32 | 92 | 120 | 60 | 15 | **320** | 575 | 484 | 17 | 79 | 92 | 40 | **1,287** | **-968** | -15,473 | -280 |
| 23 | 38 | 102 | 144 | 74 | 19 | **378** | 575 | 488 | 34 | 87 | 102 | 40 | **1,328** | **-950** | -16,423 | -297 |
| 24 | 45 | 112 | 171 | 90 | 24 | **443** | 575 | 492 | 34 | 96 | 113 | 40 | **1,351** | **-909** | -17,332 | -313 |
| 25 | 53 | 122 | 203 | 108 | 30 | **515** | 860 | 1,031 | 40 | 105 | 125 | 46 | **2,206** | **-1,691** | -19,023 | -342 |
| 26 | 61 | 132 | 238 | 128 | 37 | **596** | 860 | 718 | 40 | 114 | 138 | 46 | **1,916** | **-1,320** | -20,342 | -365 |
| 27 | 70 | 142 | 276 | 151 | 45 | **685** | 860 | 723 | 40 | 124 | 151 | 46 | **1,944** | **-1,259** | -21,601 | -386 |
| 28 | 80 | 153 | 319 | 175 | 54 | **781** | 860 | 729 | 40 | 134 | 164 | 46 | **1,972** | **-1,190** | -22,791 | -407 |
| 29 | 91 | 164 | 365 | 202 | 64 | **886** | 860 | 733 | 40 | 144 | 177 | 46 | **2,000** | **-1,114** | -23,906 | -426 |
| 30 | 103 | 175 | 416 | 232 | 74 | **1,001** | 860 | 821 | 40 | 155 | 192 | 246 | **2,313** | **-1,312** | -25,218 | -448 |
| 31 | 116 | 187 | 473 | 264 | 86 | **1,126** | 860 | 827 | 60 | 166 | 206 | 46 | **2,165** | **-1,039** | -26,257 | -466 |
| 32 | 130 | 198 | 534 | 299 | 100 | **1,260** | 860 | 832 | 60 | 178 | 221 | 46 | **2,196** | **-936** | -27,193 | -482 |
| 33 | 145 | 210 | 599 | 336 | 114 | **1,404** | 860 | 837 | 60 | 189 | 237 | 46 | **2,228** | **-824** | -28,017 | -496 |
| 34 | 161 | 222 | 670 | 376 | 129 | **1,558** | 860 | 842 | 60 | 201 | 252 | 46 | **2,261** | **-703** | -28,720 | -507 |
| 35 | 179 | 235 | 745 | 418 | 146 | **1,722** | 860 | 847 | 60 | 213 | 268 | 46 | **2,294** | **-572** | -29,292 | -517 |
| 36 | 197 | 247 | 826 | 463 | 164 | **1,897** | 860 | 853 | 60 | 226 | 283 | 259 | **2,540** | **-643** | -29,935 | -528 |

### 7.3 Conservative case — growth (monthly)

| M | Month | Champ. | New Live | Live bldgs | Compounds | Active HH | Accounts | MAU | App installers | WA-reachable residents | Downloads (Android / iOS) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | Nov-26 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 (0 / 0) |
| 2 | Dec-26 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 (0 / 0) |
| 3 | Jan-27 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 (0 / 0) |
| 4 | Feb-27 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 (0 / 0) |
| 5 | Mar-27 | 1 | 18 | 18 | 0 | 41 | 57 | 26 | 26 | 160 | 32 (28 / 4) |
| 6 | Apr-27 | 1 | 24 | 42 | 0 | 118 | 165 | 74 | 75 | 360 | 62 (55 / 7) |
| 7 | May-27 | 2 | 20 | 61 | 0 | 207 | 290 | 130 | 134 | 513 | 75 (66 / 9) |
| 8 | Jun-27 | 2 | 22 | 82 | 0 | 299 | 419 | 189 | 197 | 680 | 80 (70 / 10) |
| 9 | Jul-27 | 2 | 25 | 104 | 0 | 394 | 552 | 249 | 263 | 862 | 84 (74 / 10) |
| 10 | Aug-27 | 3 | 35 | 137 | 0 | 516 | 722 | 325 | 348 | 1,128 | 110 (96 / 13) |
| 11 | Sep-27 | 3 | 38 | 172 | 0 | 657 | 920 | 414 | 449 | 1,406 | 130 (114 / 16) |
| 12 | Oct-27 | 3 | 41 | 208 | 1 | 859 | 1,212 | 545 | 611 | 1,716 | 207 (179 / 28) |
| 13 | Nov-27 | 4 | 51 | 254 | 2 | 1,132 | 1,613 | 726 | 843 | 2,127 | 296 (251 / 45) |
| 14 | Dec-27 | 4 | 53 | 301 | 2 | 1,469 | 2,113 | 951 | 1,141 | 2,568 | 381 (317 / 63) |
| 15 | Jan-28 | 4 | 56 | 350 | 3 | 1,867 | 2,707 | 1,218 | 1,505 | 3,037 | 466 (383 / 84) |
| 16 | Feb-28 | 5 | 69 | 410 | 4 | 2,341 | 3,417 | 1,538 | 1,948 | 3,622 | 569 (461 / 108) |
| 17 | Mar-28 | 5 | 73 | 473 | 5 | 2,883 | 4,232 | 1,904 | 2,467 | 4,235 | 669 (537 / 132) |
| 18 | Apr-28 | 5 | 77 | 538 | 6 | 3,444 | 5,073 | 2,283 | 3,011 | 4,853 | 704 (561 / 142) |
| 19 | May-28 | 6 | 89 | 613 | 6 | 4,033 | 5,954 | 2,679 | 3,586 | 5,546 | 750 (596 / 154) |
| 20 | Jun-28 | 6 | 93 | 691 | 7 | 4,642 | 6,863 | 3,088 | 4,189 | 6,240 | 789 (626 / 164) |
| 21 | Jul-28 | 6 | 97 | 771 | 8 | 5,268 | 7,795 | 3,508 | 4,817 | 6,935 | 826 (654 / 172) |
| 22 | Aug-28 | 6 | 101 | 853 | 9 | 5,904 | 8,741 | 3,934 | 5,464 | 7,635 | 857 (678 / 179) |
| 23 | Sep-28 | 6 | 105 | 936 | 10 | 6,548 | 9,699 | 4,365 | 6,129 | 8,335 | 887 (701 / 186) |
| 24 | Oct-28 | 6 | 109 | 1,021 | 10 | 7,200 | 10,668 | 4,801 | 6,814 | 9,034 | 917 (725 / 192) |
| 25 | Nov-28 | 6 | 112 | 1,108 | 11 | 7,859 | 11,647 | 5,241 | 7,517 | 9,732 | 947 (748 / 199) |
| 26 | Dec-28 | 6 | 116 | 1,196 | 12 | 8,524 | 12,634 | 5,685 | 8,237 | 10,426 | 976 (771 / 205) |
| 27 | Jan-29 | 6 | 119 | 1,285 | 13 | 9,195 | 13,628 | 6,133 | 8,974 | 11,115 | 1,004 (793 / 211) |
| 28 | Feb-29 | 8 | 138 | 1,392 | 14 | 9,906 | 14,681 | 6,606 | 9,759 | 11,933 | 1,071 (846 / 224) |
| 29 | Mar-29 | 8 | 142 | 1,499 | 14 | 10,644 | 15,770 | 7,096 | 10,580 | 12,737 | 1,123 (888 / 235) |
| 30 | Apr-29 | 8 | 146 | 1,608 | 15 | 11,401 | 16,886 | 7,599 | 11,431 | 13,529 | 1,170 (926 / 244) |
| 31 | May-29 | 8 | 150 | 1,718 | 16 | 12,165 | 18,011 | 8,105 | 12,302 | 14,317 | 1,203 (953 / 250) |
| 32 | Jun-29 | 8 | 154 | 1,830 | 17 | 12,934 | 19,143 | 8,614 | 13,192 | 15,099 | 1,236 (979 / 256) |
| 33 | Jul-29 | 8 | 158 | 1,942 | 18 | 13,708 | 20,283 | 9,127 | 14,102 | 15,875 | 1,269 (1,006 / 263) |
| 34 | Aug-29 | 8 | 163 | 2,056 | 18 | 14,488 | 21,432 | 9,644 | 15,032 | 16,646 | 1,303 (1,034 / 269) |
| 35 | Sep-29 | 8 | 166 | 2,171 | 19 | 15,272 | 22,585 | 10,163 | 15,980 | 17,404 | 1,335 (1,060 / 275) |
| 36 | Oct-29 | 8 | 169 | 2,286 | 20 | 16,059 | 23,743 | 10,684 | 16,945 | 18,150 | 1,366 (1,085 / 281) |

### 7.4 Conservative case — P&L (EGP thousands)

| M | Payments | SaaS | Market-place | Ads | Referrals | **Revenue** | Team | Field ops | Support | Infra + AI | WhatsApp + SMS | Legal/PDPL | **Cost** | **Op. result** | Cum. cash (EGP k) | Cum. cash (USD k) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 0 | 0 | 0 | 0 | 0 | **0** | 265 | 0 | 0 | 3 | 0 | 80 | **348** | **-348** | -348 | -7 |
| 2 | 0 | 0 | 0 | 0 | 0 | **0** | 265 | 0 | 0 | 3 | 0 | 20 | **288** | **-288** | -635 | -12 |
| 3 | 0 | 0 | 0 | 0 | 0 | **0** | 265 | 0 | 0 | 8 | 0 | 20 | **293** | **-293** | -928 | -18 |
| 4 | 0 | 0 | 0 | 0 | 0 | **0** | 265 | 0 | 0 | 8 | 0 | 20 | **293** | **-293** | -1,221 | -23 |
| 5 | 0 | 0 | 0 | 0 | 0 | **0** | 265 | 84 | 15 | 8 | 0 | 20 | **392** | **-392** | -1,613 | -30 |
| 6 | 0 | 0 | 0 | 0 | 0 | **0** | 265 | 22 | 15 | 8 | 0 | 20 | **331** | **-331** | -1,944 | -37 |
| 7 | 0 | 0 | 0 | 0 | 0 | **0** | 380 | 41 | 15 | 8 | 0 | 20 | **464** | **-464** | -2,409 | -45 |
| 8 | 0 | 0 | 0 | 0 | 0 | **0** | 380 | 41 | 15 | 9 | 1 | 20 | **465** | **-465** | -2,874 | -54 |
| 9 | 0 | 0 | 0 | 0 | 0 | **0** | 380 | 41 | 15 | 9 | 1 | 20 | **466** | **-466** | -3,341 | -63 |
| 10 | 0 | 0 | 0 | 0 | 0 | **0** | 380 | 62 | 15 | 9 | 2 | 35 | **503** | **-503** | -3,843 | -72 |
| 11 | 0 | 0 | 0 | 0 | 0 | **0** | 380 | 62 | 15 | 9 | 3 | 35 | **504** | **-504** | -4,348 | -81 |
| 12 | 0 | 0 | 0 | 0 | 0 | **0** | 380 | 63 | 15 | 10 | 3 | 35 | **506** | **-506** | -4,853 | -90 |
| 13 | 0 | 0 | 0 | 0 | 0 | **0** | 483 | 95 | 17 | 10 | 4 | 40 | **650** | **-650** | -5,503 | -102 |
| 14 | 0 | 0 | 0 | 0 | 0 | **0** | 483 | 95 | 17 | 11 | 6 | 40 | **652** | **-652** | -6,155 | -114 |
| 15 | 0 | 1 | 0 | 0 | 0 | **2** | 483 | 96 | 17 | 11 | 7 | 40 | **654** | **-653** | -6,807 | -126 |
| 16 | 0 | 3 | 1 | 0 | 0 | **5** | 483 | 450 | 17 | 12 | 8 | 40 | **1,011** | **-1,007** | -7,814 | -144 |
| 17 | 1 | 5 | 2 | 0 | 0 | **7** | 483 | 161 | 17 | 13 | 10 | 40 | **724** | **-717** | -8,531 | -156 |
| 18 | 1 | 6 | 3 | 1 | 0 | **11** | 483 | 161 | 17 | 14 | 12 | 40 | **728** | **-717** | -9,248 | -169 |
| 19 | 1 | 8 | 4 | 1 | 0 | **14** | 483 | 185 | 17 | 15 | 14 | 40 | **754** | **-740** | -9,989 | -182 |
| 20 | 1 | 10 | 5 | 2 | 0 | **18** | 483 | 186 | 17 | 16 | 15 | 40 | **758** | **-740** | -10,729 | -195 |
| 21 | 2 | 11 | 7 | 2 | 0 | **23** | 483 | 187 | 17 | 17 | 17 | 40 | **762** | **-740** | -11,468 | -208 |
| 22 | 2 | 13 | 9 | 3 | 0 | **28** | 483 | 188 | 17 | 18 | 19 | 40 | **766** | **-739** | -12,207 | -221 |
| 23 | 3 | 15 | 11 | 4 | 0 | **33** | 483 | 189 | 17 | 20 | 22 | 40 | **771** | **-738** | -12,945 | -234 |
| 24 | 3 | 17 | 13 | 6 | 0 | **39** | 483 | 190 | 17 | 21 | 24 | 40 | **775** | **-736** | -13,680 | -247 |
| 25 | 4 | 19 | 16 | 7 | 1 | **46** | 608 | 216 | 20 | 22 | 26 | 46 | **938** | **-892** | -14,573 | -263 |
| 26 | 4 | 21 | 19 | 8 | 1 | **53** | 608 | 217 | 20 | 23 | 28 | 46 | **943** | **-889** | -15,462 | -278 |
| 27 | 5 | 23 | 22 | 10 | 2 | **61** | 608 | 218 | 20 | 24 | 30 | 46 | **947** | **-886** | -16,348 | -293 |
| 28 | 6 | 25 | 26 | 12 | 2 | **70** | 608 | 645 | 20 | 26 | 33 | 46 | **1,377** | **-1,308** | -17,656 | -316 |
| 29 | 6 | 27 | 30 | 13 | 3 | **79** | 608 | 319 | 20 | 27 | 35 | 46 | **1,055** | **-976** | -18,632 | -332 |
| 30 | 7 | 29 | 35 | 16 | 3 | **89** | 608 | 320 | 20 | 29 | 38 | 46 | **1,060** | **-971** | -19,603 | -349 |
| 31 | 8 | 31 | 39 | 18 | 4 | **100** | 608 | 321 | 20 | 30 | 40 | 46 | **1,066** | **-965** | -20,568 | -365 |
| 32 | 9 | 33 | 45 | 20 | 5 | **112** | 608 | 322 | 20 | 31 | 43 | 46 | **1,071** | **-959** | -21,526 | -381 |
| 33 | 10 | 35 | 51 | 23 | 6 | **125** | 608 | 323 | 20 | 33 | 46 | 46 | **1,076** | **-951** | -22,478 | -397 |
| 34 | 11 | 37 | 57 | 26 | 7 | **138** | 608 | 324 | 20 | 34 | 48 | 46 | **1,082** | **-943** | -23,421 | -413 |
| 35 | 12 | 40 | 63 | 29 | 8 | **152** | 608 | 325 | 20 | 36 | 51 | 46 | **1,087** | **-934** | -24,356 | -429 |
| 36 | 14 | 42 | 70 | 32 | 9 | **167** | 608 | 326 | 20 | 37 | 54 | 46 | **1,092** | **-925** | -25,280 | -444 |

### 7.5 Aggressive case — growth (monthly)

| M | Month | Champ. | New Live | Live bldgs | Compounds | Active HH | Accounts | MAU | App installers | WA-reachable residents | Downloads (Android / iOS) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | Nov-26 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 (0 / 0) |
| 2 | Dec-26 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 (0 / 0) |
| 3 | Jan-27 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 (0 / 0) |
| 4 | Feb-27 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 (0 / 0) |
| 5 | Mar-27 | 3 | 80 | 80 | 0 | 306 | 551 | 342 | 303 | 845 | 379 (333 / 45) |
| 6 | Apr-27 | 3 | 103 | 182 | 0 | 882 | 1,588 | 984 | 886 | 1,876 | 732 (644 / 88) |
| 7 | May-27 | 5 | 135 | 315 | 0 | 1,748 | 3,146 | 1,951 | 1,781 | 3,165 | 1,128 (992 / 135) |
| 8 | Jun-27 | 5 | 160 | 471 | 4 | 3,340 | 6,065 | 3,760 | 3,634 | 4,925 | 2,334 (1,969 / 364) |
| 9 | Jul-27 | 5 | 187 | 654 | 8 | 5,663 | 10,353 | 6,419 | 6,482 | 7,149 | 3,597 (2,944 / 653) |
| 10 | Aug-27 | 8 | 277 | 925 | 12 | 8,953 | 16,434 | 10,189 | 10,609 | 10,450 | 5,224 (4,200 / 1,024) |
| 11 | Sep-27 | 8 | 334 | 1,249 | 17 | 13,221 | 24,329 | 15,084 | 16,072 | 14,379 | 6,934 (5,516 / 1,419) |
| 12 | Oct-27 | 8 | 377 | 1,614 | 21 | 18,432 | 33,975 | 21,064 | 22,874 | 18,753 | 8,664 (6,843 / 1,820) |
| 13 | Nov-27 | 12 | 503 | 2,101 | 25 | 24,815 | 45,783 | 28,385 | 31,313 | 24,384 | 10,777 (8,480 / 2,297) |
| 14 | Dec-27 | 12 | 558 | 2,638 | 29 | 31,734 | 58,555 | 36,304 | 40,541 | 30,216 | 11,849 (9,320 / 2,529) |
| 15 | Jan-28 | 15 | 677 | 3,289 | 33 | 39,389 | 72,653 | 45,045 | 50,813 | 36,868 | 13,245 (10,436 / 2,809) |
| 16 | Feb-28 | 15 | 746 | 4,002 | 37 | 47,622 | 87,791 | 54,431 | 61,976 | 43,786 | 14,462 (11,423 / 3,039) |
| 17 | Mar-28 | 15 | 813 | 4,776 | 41 | 56,400 | 103,909 | 64,424 | 74,017 | 50,923 | 15,671 (12,412 / 3,259) |
| 18 | Apr-28 | 15 | 881 | 5,609 | 46 | 65,641 | 120,862 | 74,934 | 86,864 | 58,299 | 16,799 (13,341 / 3,458) |
| 19 | May-28 | 18 | 1,012 | 6,565 | 50 | 75,579 | 139,069 | 86,223 | 100,816 | 66,500 | 18,309 (14,584 / 3,725) |
| 20 | Jun-28 | 18 | 1,083 | 7,582 | 54 | 86,124 | 158,369 | 98,189 | 115,795 | 74,841 | 19,732 (15,764 / 3,969) |
| 21 | Jul-28 | 24 | 1,275 | 8,781 | 58 | 97,694 | 179,514 | 111,299 | 132,338 | 84,487 | 21,837 (17,502 / 4,335) |
| 22 | Aug-28 | 24 | 1,355 | 10,048 | 62 | 110,038 | 202,051 | 125,272 | 150,179 | 94,209 | 23,625 (18,996 / 4,629) |
| 23 | Sep-28 | 24 | 1,438 | 11,385 | 66 | 123,080 | 225,846 | 140,024 | 169,258 | 104,019 | 25,350 (20,446 / 4,904) |
| 24 | Oct-28 | 24 | 1,521 | 12,793 | 70 | 136,656 | 250,601 | 155,373 | 189,396 | 113,983 | 26,865 (21,729 / 5,136) |
| 25 | Nov-28 | 28 | 1,686 | 14,351 | 74 | 151,077 | 276,878 | 171,664 | 211,016 | 124,839 | 28,919 (23,455 / 5,464) |
| 26 | Dec-28 | 28 | 1,775 | 15,983 | 79 | 166,233 | 304,476 | 188,775 | 234,010 | 135,721 | 30,853 (25,090 / 5,763) |
| 27 | Jan-29 | 28 | 1,866 | 17,689 | 83 | 182,072 | 333,305 | 206,649 | 258,344 | 146,639 | 32,758 (26,705 / 6,053) |
| 28 | Feb-29 | 28 | 1,946 | 19,458 | 87 | 198,436 | 363,079 | 225,109 | 283,838 | 157,520 | 34,451 (28,150 / 6,301) |
| 29 | Mar-29 | 28 | 2,026 | 21,290 | 91 | 215,297 | 393,748 | 244,124 | 310,478 | 168,349 | 36,138 (29,592 / 6,547) |
| 30 | Apr-29 | 32 | 2,186 | 23,263 | 95 | 232,939 | 425,822 | 264,010 | 338,669 | 179,840 | 38,343 (31,462 / 6,881) |
| 31 | May-29 | 32 | 2,274 | 25,304 | 99 | 251,260 | 459,119 | 284,654 | 368,306 | 191,184 | 40,433 (33,242 / 7,192) |
| 32 | Jun-29 | 32 | 2,354 | 27,405 | 103 | 270,179 | 493,492 | 305,965 | 399,306 | 202,298 | 42,433 (34,950 / 7,483) |
| 33 | Jul-29 | 32 | 2,432 | 29,563 | 108 | 289,559 | 528,694 | 327,790 | 431,504 | 213,227 | 44,241 (36,501 / 7,740) |
| 34 | Aug-29 | 32 | 2,510 | 31,777 | 112 | 309,376 | 564,683 | 350,103 | 464,886 | 223,944 | 46,042 (38,048 / 7,994) |
| 35 | Sep-29 | 32 | 2,587 | 34,046 | 116 | 329,619 | 601,438 | 372,892 | 499,456 | 234,427 | 47,862 (39,610 / 8,252) |
| 36 | Oct-29 | 32 | 2,664 | 36,369 | 120 | 350,280 | 638,947 | 396,147 | 535,221 | 244,654 | 49,701 (41,190 / 8,512) |

### 7.6 Aggressive case — P&L (EGP thousands)

| M | Payments | SaaS | Market-place | Ads | Referrals | **Revenue** | Team | Field ops | Support | Infra + AI | WhatsApp + SMS | Legal/PDPL | **Cost** | **Op. result** | Cum. cash (EGP k) | Cum. cash (USD k) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 0 | 0 | 0 | 0 | 0 | **0** | 265 | 0 | 0 | 3 | 0 | 80 | **348** | **-348** | -348 | -7 |
| 2 | 0 | 0 | 0 | 0 | 0 | **0** | 265 | 0 | 0 | 3 | 0 | 20 | **288** | **-288** | -635 | -12 |
| 3 | 0 | 0 | 0 | 0 | 0 | **0** | 265 | 0 | 0 | 8 | 0 | 20 | **293** | **-293** | -928 | -18 |
| 4 | 0 | 0 | 0 | 0 | 0 | **0** | 265 | 0 | 0 | 8 | 0 | 20 | **293** | **-293** | -1,221 | -23 |
| 5 | 0 | 0 | 0 | 0 | 0 | **0** | 265 | 131 | 15 | 9 | 1 | 20 | **441** | **-441** | -1,662 | -31 |
| 6 | 0 | 0 | 0 | 0 | 0 | **0** | 265 | 72 | 15 | 10 | 3 | 20 | **386** | **-386** | -2,048 | -39 |
| 7 | 0 | 0 | 0 | 0 | 0 | **0** | 500 | 115 | 15 | 13 | 7 | 20 | **669** | **-669** | -2,717 | -51 |
| 8 | 0 | 0 | 0 | 0 | 0 | **0** | 500 | 119 | 15 | 17 | 12 | 20 | **683** | **-683** | -3,400 | -64 |
| 9 | 3 | 0 | 0 | 0 | 0 | **3** | 500 | 124 | 15 | 23 | 18 | 20 | **700** | **-697** | -4,097 | -77 |
| 10 | 5 | 0 | 0 | 0 | 0 | **5** | 500 | 504 | 15 | 31 | 27 | 35 | **1,112** | **-1,107** | -5,204 | -97 |
| 11 | 9 | 25 | 35 | 0 | 0 | **69** | 500 | 240 | 15 | 43 | 39 | 35 | **871** | **-802** | -6,006 | -112 |
| 12 | 14 | 54 | 58 | 0 | 0 | **126** | 500 | 248 | 15 | 56 | 52 | 35 | **906** | **-780** | -6,786 | -126 |
| 13 | 21 | 81 | 88 | 17 | 0 | **208** | 805 | 383 | 17 | 73 | 69 | 40 | **1,387** | **-1,179** | -7,965 | -147 |
| 14 | 30 | 109 | 127 | 31 | 0 | **297** | 805 | 394 | 34 | 91 | 86 | 40 | **1,451** | **-1,154** | -9,119 | -168 |
| 15 | 41 | 137 | 176 | 49 | 11 | **415** | 805 | 807 | 34 | 112 | 107 | 40 | **1,906** | **-1,491** | -10,610 | -195 |
| 16 | 54 | 167 | 235 | 72 | 20 | **548** | 805 | 533 | 34 | 134 | 129 | 40 | **1,675** | **-1,127** | -11,737 | -215 |
| 17 | 69 | 197 | 306 | 101 | 31 | **704** | 805 | 546 | 52 | 158 | 152 | 216 | **1,929** | **-1,225** | -12,962 | -237 |
| 18 | 87 | 228 | 389 | 136 | 44 | **884** | 805 | 560 | 52 | 183 | 177 | 40 | **1,817** | **-933** | -13,895 | -254 |
| 19 | 108 | 259 | 486 | 178 | 61 | **1,093** | 805 | 649 | 52 | 210 | 205 | 40 | **1,961** | **-869** | -14,764 | -269 |
| 20 | 131 | 292 | 598 | 228 | 82 | **1,331** | 805 | 664 | 69 | 239 | 234 | 40 | **2,052** | **-720** | -15,484 | -282 |
| 21 | 159 | 326 | 732 | 286 | 106 | **1,609** | 805 | 1,175 | 69 | 271 | 268 | 40 | **2,629** | **-1,020** | -16,504 | -300 |
| 22 | 190 | 360 | 884 | 355 | 136 | **1,925** | 805 | 887 | 86 | 306 | 304 | 40 | **2,428** | **-503** | -17,007 | -309 |
| 23 | 226 | 396 | 1,058 | 432 | 170 | **2,282** | 805 | 905 | 86 | 342 | 341 | 40 | **2,520** | **-238** | -17,246 | -313 |
| 24 | 266 | 432 | 1,253 | 520 | 209 | **2,679** | 805 | 924 | 104 | 380 | 380 | 229 | **2,821** | **-142** | -17,388 | -315 |
| 25 | 310 | 469 | 1,474 | 620 | 253 | **3,127** | 1,256 | 1,152 | 119 | 421 | 423 | 46 | **3,418** | **-291** | -17,679 | -320 |
| 26 | 360 | 508 | 1,721 | 732 | 305 | **3,625** | 1,256 | 1,173 | 139 | 464 | 467 | 46 | **3,546** | **79** | -17,599 | -319 |
| 27 | 415 | 547 | 1,996 | 856 | 362 | **4,176** | 1,256 | 1,194 | 139 | 509 | 514 | 46 | **3,659** | **518** | -17,082 | -310 |
| 28 | 475 | 587 | 2,298 | 993 | 426 | **4,781** | 1,256 | 1,213 | 159 | 556 | 562 | 46 | **3,793** | **988** | -16,094 | -293 |
| 29 | 541 | 628 | 2,630 | 1,143 | 498 | **5,441** | 1,256 | 1,233 | 179 | 605 | 611 | 46 | **3,930** | **1,510** | -14,583 | -267 |
| 30 | 613 | 671 | 2,997 | 1,308 | 577 | **6,167** | 1,256 | 1,368 | 179 | 656 | 664 | 46 | **4,169** | **1,997** | -12,586 | -233 |
| 31 | 692 | 714 | 3,398 | 1,489 | 665 | **6,959** | 1,256 | 1,390 | 198 | 710 | 719 | 46 | **4,319** | **2,640** | -9,946 | -188 |
| 32 | 778 | 759 | 3,835 | 1,685 | 762 | **7,819** | 1,256 | 1,411 | 218 | 765 | 775 | 46 | **4,471** | **3,348** | -6,599 | -132 |
| 33 | 871 | 804 | 4,308 | 1,896 | 867 | **8,747** | 1,256 | 1,432 | 218 | 822 | 832 | 46 | **4,607** | **4,140** | -2,459 | -62 |
| 34 | 970 | 851 | 4,819 | 2,123 | 982 | **9,745** | 1,256 | 1,453 | 238 | 881 | 891 | 46 | **4,765** | **4,979** | 2,520 | 22 |
| 35 | 1,077 | 898 | 5,367 | 2,367 | 1,106 | **10,815** | 1,256 | 1,474 | 258 | 941 | 951 | 46 | **4,927** | **5,888** | 8,409 | 120 |
| 36 | 1,191 | 947 | 5,957 | 2,627 | 1,241 | **11,962** | 1,256 | 1,496 | 278 | 1,003 | 1,012 | 259 | **5,304** | **6,658** | 15,066 | 231 |

**Where the base-case Live buildings come from (36-month total of 12,738 new Live buildings, before churn):** field champions and pilot 5,768 (45%), viral K 4,518 (35%), self-serve content 1,654 (13%), partners 792 (6%).

**36-month base cost structure (EGP M):** team 21.4, field ops 15.5, WhatsApp + SMS 3.2, infrastructure 1.7, legal/PDPL/accounting 1.8, AI 1.0, support 1.0. **People (team + field + support) make up 83% of all costs**, so costs are mostly in EGP and a weaker pound *reduces* USD burn (§11).

---

## 8. Chart-ready data

### 8.1 Downloads curve (cumulative, quarterly points)

| Month | Conservative cum. downloads | Base cum. downloads | Aggressive cum. downloads |
|---|---|---|---|
| M3 (Jan-27) | 0 | 0 | 0 |
| M6 (Apr-27) | 94 | 375 | 1,111 |
| M9 (Jul-27) | 333 | 1,818 | 8,170 |
| M12 (Oct-27) | 780 | 6,762 | 28,992 |
| M15 (Jan-28) | 1,923 | 16,207 | 64,863 |
| M18 (Apr-28) | 3,865 | 28,322 | 111,795 |
| M21 (Jul-28) | 6,230 | 43,286 | 171,673 |
| M24 (Oct-28) | 8,891 | 61,190 | 247,513 |
| M27 (Jan-29) | 11,818 | 82,696 | 340,043 |
| M30 (Apr-29) | 15,182 | 107,343 | 448,975 |
| M33 (Jul-29) | 18,890 | 135,548 | 576,082 |
| M36 (Oct-29) | 22,894 | 166,581 | 719,687 |

### 8.2 Revenue stack — base (quarterly sums)

| Quarter | Payments | Compound/Pro SaaS | Marketplace | Ads & sponsorship | Referrals | Total (EGP k) | Total (USD k) |
|---|---|---|---|---|---|---|---|
| Q1 (M1–M3) | 0 | 0 | 0 | 0 | 0 | 0 | 0.0 |
| Q2 (M4–M6) | 0 | 0 | 0 | 0 | 0 | 0 | 0.0 |
| Q3 (M7–M9) | 0 | 0 | 0 | 0 | 0 | 0 | 0.0 |
| Q4 (M10–M12) | 4 | 7 | 0 | 0 | 0 | 11 | 0.2 |
| Q5 (M13–M15) | 14 | 68 | 44 | 5 | 0 | 131 | 2.4 |
| Q6 (M16–M18) | 35 | 143 | 117 | 44 | 3 | 342 | 6.1 |
| Q7 (M19–M21) | 67 | 222 | 242 | 114 | 23 | 668 | 11.8 |
| Q8 (M22–M24) | 116 | 306 | 436 | 225 | 58 | 1,140 | 19.9 |
| Q9 (M25–M27) | 184 | 396 | 716 | 388 | 113 | 1,797 | 31.0 |
| Q10 (M28–M30) | 274 | 492 | 1,100 | 609 | 192 | 2,668 | 45.6 |
| Q11 (M31–M33) | 392 | 595 | 1,606 | 898 | 300 | 3,790 | 64.1 |
| Q12 (M34–M36) | 537 | 704 | 2,240 | 1,257 | 439 | 5,177 | 86.6 |

### 8.3 Revenue stack — aggressive (quarterly sums)

| Quarter | Payments | Compound/Pro SaaS | Marketplace | Ads & sponsorship | Referrals | Total (EGP k) | Total (USD k) |
|---|---|---|---|---|---|---|---|
| Q1 (M1–M3) | 0 | 0 | 0 | 0 | 0 | 0 | 0.0 |
| Q2 (M4–M6) | 0 | 0 | 0 | 0 | 0 | 0 | 0.0 |
| Q3 (M7–M9) | 3 | 0 | 0 | 0 | 0 | 3 | 0.1 |
| Q4 (M10–M12) | 29 | 79 | 93 | 0 | 0 | 201 | 3.7 |
| Q5 (M13–M15) | 93 | 328 | 392 | 96 | 11 | 920 | 16.6 |
| Q6 (M16–M18) | 210 | 591 | 930 | 309 | 95 | 2,136 | 38.2 |
| Q7 (M19–M21) | 398 | 877 | 1,816 | 692 | 250 | 4,033 | 71.3 |
| Q8 (M22–M24) | 682 | 1,188 | 3,195 | 1,307 | 514 | 6,886 | 120.3 |
| Q9 (M25–M27) | 1,085 | 1,524 | 5,191 | 2,208 | 920 | 10,928 | 188.8 |
| Q10 (M28–M30) | 1,630 | 1,887 | 7,925 | 3,445 | 1,502 | 16,388 | 280.1 |
| Q11 (M31–M33) | 2,341 | 2,277 | 11,542 | 5,070 | 2,294 | 23,525 | 397.7 |
| Q12 (M34–M36) | 3,238 | 2,695 | 16,143 | 7,117 | 3,329 | 32,522 | 543.8 |

### 8.4 Revenue stack — conservative (quarterly sums)

| Quarter | Payments | Compound/Pro SaaS | Marketplace | Ads & sponsorship | Referrals | Total (EGP k) | Total (USD k) |
|---|---|---|---|---|---|---|---|
| Q1 (M1–M3) | 0 | 0 | 0 | 0 | 0 | 0 | 0.0 |
| Q2 (M4–M6) | 0 | 0 | 0 | 0 | 0 | 0 | 0.0 |
| Q3 (M7–M9) | 0 | 0 | 0 | 0 | 0 | 0 | 0.0 |
| Q4 (M10–M12) | 0 | 0 | 0 | 0 | 0 | 0 | 0.0 |
| Q5 (M13–M15) | 1 | 1 | 0 | 0 | 0 | 2 | 0.0 |
| Q6 (M16–M18) | 2 | 14 | 6 | 1 | 0 | 22 | 0.4 |
| Q7 (M19–M21) | 4 | 29 | 16 | 5 | 0 | 55 | 1.0 |
| Q8 (M22–M24) | 8 | 45 | 33 | 13 | 0 | 100 | 1.7 |
| Q9 (M25–M27) | 13 | 62 | 57 | 25 | 3 | 160 | 2.8 |
| Q10 (M28–M30) | 19 | 80 | 91 | 41 | 8 | 238 | 4.1 |
| Q11 (M31–M33) | 27 | 99 | 135 | 61 | 15 | 338 | 5.7 |
| Q12 (M34–M36) | 37 | 119 | 190 | 87 | 25 | 458 | 7.7 |

### 8.5 Cash curve (cumulative operating cash, USD thousands, extended to M48)

| Month | Conservative cum. cash (USD k) | Base cum. cash (USD k) | Aggressive cum. cash (USD k) | Base monthly op. result (USD k) |
|---|---|---|---|---|
| M3 (Jan-27) | -18 | -18 | -18 | -5.5 |
| M6 (Apr-27) | -37 | -38 | -39 | -6.7 |
| M9 (Jul-27) | -63 | -69 | -77 | -10.7 |
| M12 (Oct-27) | -90 | -104 | -126 | -11.9 |
| M15 (Jan-28) | -126 | -157 | -195 | -15.9 |
| M18 (Apr-28) | -169 | -206 | -254 | -16.1 |
| M21 (Jul-28) | -208 | -263 | -300 | -16.7 |
| M24 (Oct-28) | -247 | -313 | -315 | -15.8 |
| M27 (Jan-29) | -293 | -386 | -310 | -21.7 |
| M30 (Apr-29) | -349 | -448 | -233 | -22.4 |
| M33 (Jul-29) | -397 | -496 | -62 | -13.9 |
| M36 (Oct-29) | -444 | -528 | 231 | -10.7 |
| M39 (Jan-30) | -497 | -554 | 620 | -7.3 |
| M42 (Apr-30) | -548 | -567 | 1,107 | -2.8 |
| M45 (Jul-30) | -598 | -567 | 1,699 | 1.4 |
| M48 (Oct-30) | -647 | -557 | 2,393 | 2.2 |

*Suggested charts:* 8.1 as a 3-line chart; 8.2 as a stacked column; 8.5 as a 3-line chart with a zero line. The monthly series for all three scenarios are in the CSV, in the `cum_cash_egp`, `downloads` and `rev_*` columns.

---

## 9. Unit economics and break-even

| Metric (base, M36) | Value | Note |
|---|---|---|
| Revenue per active HH per month | **EGP 20.5** (~$0.34) | 14 implied ~EGP 19.5; MyGate ~$0.33/home/month ([Inc42](https://inc42.com/buzz/mygate-trims-fy25-loss-by-61-to-₹15-4-cr/)) |
| Cost per active HH per month | EGP 27.4 | Falls as fixed team cost is spread |
| Marketplace GMV per month | EGP 6.3 M | Includes building contracts |
| Break-even scale | **~135k active HH** (base, M45); ~165k (aggressive cost base, M26) | 14 said 100–120k |
| Field cost per new Live building (all channels) | **EGP 1,217 (~$22)** | 36-month field ops ÷ all new Live buildings |
| Field cost per field-sourced Live building | EGP 2,688 (~$49) | Excludes viral, self-serve and partner buildings |
| Field cost per active HH acquired | ~EGP 203 (~$3.7) | ÷ 6 active HH per Live building |
| Payback on a Live building | ≈ 10 months at M36 revenue per HH | Contribution excludes fixed team cost |

**Contribution of a single marketplace order** (14 §7.2, re-based): AOV 750 × 15% = EGP 112.5, minus PSP 2.75% + 3 on card orders (EGP 23.6), support (10) and guarantee reserve 3% (22.5) ≈ **EGP 56 per order (~$1.07)**. When the technician pays commission from a prepaid wallet and the customer pays in cash, the figure is ≈ EGP 80. **Design implication:** push cash/InstaPay customer payment with a technician-wallet commission, and keep card payment for BNPL and large tickets.

---

## 10. Expansion: district-by-district and city-by-city costs

### 10.1 Rollout sequence (base) and why

| Wave | Start (base / aggr / cons) | Districts | Why this order (evidence) | Champions added |
|---|---|---|---|---|
| 1 | M5 / M5 / M5 | **New Cairo (Tagamoa, Rehab, Madinaty fringe), Nasr City, Heliopolis, Maadi** | Cairo has the largest buildings (8.05 units/building) and 94% sewer connection (formal stock) (§3). Dense towers with active treasurers; Breadfast's beachhead was also New Cairo, Rehab and Madinaty (13 §2.1) | 2 → 6 |
| 2 | M13 / M10 / M16 | **Giza (Dokki, Mohandessin, Haram, Faisal) + 6th of October / Sheikh Zayed** | Giza urban has 474,744 buildings at 6.63 units/building. October/Zayed have compounds and new blocks; JLL rent growth of +17.6% creates landlord-tenant needs (08 §2.5) | +4 |
| 3 | M19 / M15 / M28 | **Alexandria (Smouha, Sporting, Miami, Sidi Bishr, Agami)** | 424,012 urban buildings at 7.14 units/building, the second-largest stock; Fixawy's origin city proves home-services demand (03) | +5 |
| 4 | M25 / M21 / — | **Delta capitals (Mansoura, Tanta, Zagazig) + new cities (Obour, Shorouk, 10th of Ramadan, New Capital)** | Delta buildings are small (4.1–4.9 units/building), so cost per household is higher. Enter there through partners (elevator/tank firms) and new-city handover deals | +7 |

### 10.2 Incremental cost of one new city wave (base, Oct-2026 prices, ESTIMATE)

| Item | One-off (EGP) | Monthly (EGP) | Reasoning |
|---|---|---|---|
| Launch: treasurer meet-ups and 2 cafe events | 60,000 | — | ~50 treasurers per event |
| Printed kits (5,000 QR posters and door hangers @ ~EGP 5) | 25,000 | — | 14 §9 |
| Supply onboarding: vet and onboard ~60 technicians (ID, references, test job) @ EGP 1,000 | 60,000 | — | Needed before the marketplace goes live in the city |
| City-lead recruitment and training | 30,000 | — | — |
| Founder travel and launch time | 40,000 | — | — |
| Local PR kit, legal templates (union minutes, consent forms) | 35,000 | — | — |
| **Launch subtotal** | **250,000 (~$4.8k)** | | |
| City lead | — | 35,000 | C4 |
| 4 field champions | — | 74,800 | C2 |
| Bawab/captain bonuses + kits (~90 new Live/month × 150) | — | 13,500 | C3 |
| Support share (~0.3 agent) | — | 4,500 | C6 |
| **Monthly run cost** | | **~127,800 (~$2.4k)** | |
| **First-year cost per city** | **≈ EGP 1.78 M (~USD 34k)** | | 250k + 12 × 127.8k |
| Expected Live buildings in the city's first 12 months | ≈ 950 | | Field 4 × 25 × 55% × 12 = 660; viral ~+210 within the year; self-serve/partners ~+80 |
| **Cost per activated building** | **≈ EGP 1,875 (~$36)** | | In Delta cities (≈7 occupied HH per building, K 0.35) ≈ EGP 2,600 (~$50) per building |
| Cost per active household | ≈ EGP 310 (~$6) | | ÷ 6 active HH |
| Cost per account | ≈ EGP 195 (~$3.7) | | ÷ 9.6 accounts |

**Whole-model check:** base field ops over 36 months = **EGP 15.5 M (~USD 268k)** for 12,738 new Live buildings, or EGP 1,217 per building across all channels.

### 10.3 Compound expansion (B2B)

| Item | Estimate | Reasoning |
|---|---|---|
| Sales cycle | 3–6 months per developer/FM company | 13 §5.1 rates it slow |
| BD effort | 0.5 FTE per 10 compounds a year (inside the team budget from M9) | ESTIMATE |
| Free pilot | 3 months, then EGP 6,000/month (base) | R3 |
| Cost per compound onboarded | ≈ EGP 25–40k (BD time, gate-device setup support, handover events) | ESTIMATE |
| Households per compound deal | ~540 active (1,200 × 45%) | G16 × G17 |
| Cost per active HH | **≈ EGP 50–75**, 4–6× cheaper than city buildings | That is why compounds go first for revenue, and city buildings for dominance |

### 10.4 Comparables for acquisition cost

| Comparable | Figure | Read-across |
|---|---|---|
| Paid mobile installs, Middle East (Egypt data below threshold) | **~$0.34 CPI** (AppsFlyer, 2023, one category) ([AppsFlyer](https://www.appsflyer.com/benchmarks/social-media/live-video-chat/live-video-chat---overall/android/egypt/2023-05-01/overall)) | At ~15% install-to-retained-account, ~9.6 accounts per building would cost ~$22 per building *if* ads could target one building, which they cannot. Field work buys **density**, and paid ads do not |
| Breadfast referral reward | 10% off up to EGP 50; referrer capped at 3 invites/month (13 §2.1) | Egyptian consumer incentives are small and capped. Our EGP 150 per building is in range |
| Bawab bonus proposal | EGP 50–100 when a building goes Live (13 §5.2-C) | Kept within C3 |
| MyGate burn (VC-funded) | Burned ~Rs 80 crore to earn Rs 15.4 crore in FY20 (Entrackr via 13 §2.2) | A paid-sales land grab is expensive. Zero budget means slower but cheaper growth |
| Field sales pay | Outside sales rep avg EGP 144k/yr ([Payscale](https://www.payscale.com/research/EG/Job=Outside_Sales_Representative/Salary)) | Supports C2 |

---

## 11. Sensitivity analysis (tornado; base case, one variable at a time)

Outputs: active HH at M36 · monthly revenue at M36 (EGP) · 36-month cumulative funding need (USD) · break-even month (60-month run). The base row is 92,601 HH · EGP 1,896,531 · $527,625 · M45.

| Driver | Low / High input | Active HH M36 | Revenue M36 (EGP) | 36-mo funding need (USD) | Break-even month |
|---|---|---|---|---|---|
| K (lifetime viral) | 0.3 / 0.6 | 82,885 / 106,066 | 1,708,526 / 2,157,341 | 532,707 / 522,156 | 50 / 42 |
| Activation per building | 0.5 / 0.7 | 82,085 / 103,116 | 1,735,954 / 2,057,109 | 540,732 / 515,179 | 50 / 43 |
| Occupied HH per building | 8 / 12 | 79,982 / 105,220 | 1,703,838 / 2,089,224 | 543,160 / 512,766 | 51 / 42 |
| Champion productivity | 18 / 32 | 80,213 / 104,989 | 1,657,471 / 2,135,591 | 534,534 / 521,391 | 50 / 43 |
| Take rate | 0.12 / 0.18 | 92,601 / 92,601 | 1,778,470 / 2,014,592 | 544,063 / 511,189 | 50 / 43 |
| AOV (EGP) | 600 / 900 | 92,601 / 92,601 | 1,778,470 / 2,014,592 | 544,063 / 511,189 | 50 / 43 |
| Bookings/HH/month at M36 | 0.025 / 0.06 | 92,601 / 92,601 | 1,675,167 / 2,191,683 | 555,283 / 490,748 | 53 / 40 |
| Ads $/HH/yr at M36 | 0.5 / 1.5 | 92,601 / 92,601 | 1,665,029 / 2,128,033 | 557,688 / 497,562 | 52 / 41 |
| FX at M36 (EGP/USD) | 66 / 54 | 92,601 / 92,601 | 1,942,832 / 1,850,231 | 501,224 / 557,971 | 45 / 45 |
| WhatsApp price multiplier | 2.0 / 0.5 | 92,601 / 92,601 | 1,896,531 / 1,896,531 | 582,559 / 500,164 | 53 / 42 |
| Building churn/month | 0.025 / 0.01 | 86,992 / 95,706 | 1,789,321 / 1,955,872 | 533,837 / 524,358 | 50 / 44 |

**Tornado ranking by effect on break-even month (widest first):**
1. **WhatsApp volume or price** (×0.5 → M42; ×2 → M53; **×3 "assistant for everyone" → no break-even by M60** and USD 0.9 M needed through M60)
2. Bookings per HH per month (M53 → M40)
3. Ads yield (M52 → M41)
4. Occupied HH per building, K, champion productivity, activation (each about ±4 months)
5. Take rate and AOV (M50 → M43)
6. Churn (M50 → M44)
7. **FX** changes the USD funding need (USD 501k at 66 vs USD 558k at 54) but **not** the break-even month, because costs and revenue are both mostly in EGP

**Lean-team variant:** freezing the team at EGP 400k / 440k / 520k (M7 / M13 / M25) instead of 440k / 500k / 650k moves break-even from M45 to **M42** and cuts the 36-month need to **~USD 473k**. This is the most controllable lever.

---

## 12. Sanity benchmarks

| Company | Market and model | Ramp evidence | Comparison with our base |
|---|---|---|---|
| **MyGate** | India, gated communities, VC-funded | 40 communities (2017) → **1,000+ within 18 months** of commercial launch (Oct 2018, Series A INR 65 cr) → **1.2 M homes / 11 cities (Oct 2019)**; 5,000+ communities (Dec 2019); 25,000 (2021); 27k / 5 M+ homes now ([Entrepreneur India](https://www.entrepreneur.com/article/343751), [MyGate Series A](https://mygate.com/blog/cooperative-housing-society/mygate-raises-inr-65-crore-in-series-a-to-fuel-rapid-growth-expansion-across-10-cities/), [MyGate about](https://mygate.com/about-us)) | Our base at M36 (92.6k HH) is **~8% of MyGate's homes at a similar age**, with no VC and no sales force. Our aggressive case (350k HH) is ~30% |
| **NoBrokerHood** | India, free society app funded by parent NoBroker | <1,000 → **4,500 societies in ~5 months (2020)** → 10,000 (2021) → 25,000+ (13 §2.1) | Shows the speed possible when the app is free *and* sales are funded |
| **Nextdoor** | USA, neighborhoods | **176 neighborhoods in year 1**; 100k by 2016 (13 §2.1) | Our base year 1 (636 small buildings) is similar in community units, with a smaller unit size |
| **InstaPay** | Egypt, CBE-backed, all banks | **2.16 M registered in year 1** (Mar 2022–Mar 2023; [Egypt Independent](https://egyptindependent.com/cbe-announces-that-instapay-transactions-total-le112-7-bn-in-year/), [Waya](https://waya.media/instapay-transactions-hit-112-7b-egp-within-one-year/)) → 11.5 M (Nov 2024) → ~22 M IPN (Q2 2026) | State-backed, universal need. Shows the **ceiling** for payment-led adoption in Egypt, not a comparable |
| **MoneyFellows** | Egypt, digital ROSCA (جمعية) | **1.6 M downloads / 173k active (Aug 2021)**; 8 M users / ~350k MAU (Oct 2025) ([Forbes ME via search](https://www.forbesmiddleeast.com/lists/?p=5044), [MEA Tech Watch](https://meatechwatch.com/2025/10/21/egypts-money-fellows-surpasses-1-5-billion-in-transactions-achieves-profitability/)) | Active/download ratio of 4–11%. Our building-led onboarding assumes ~55% MAU/accounts and ~1.1 downloads per account, which is **far more efficient per download** but **far fewer downloads** |
| **Breadfast** | Egypt, grocery; compound-cluster beachhead | 170k households (2021, ~4 yrs after 2017 seed) ([TechCrunch](https://techcrunch.com/2021/11/03/egypts-breadfast-wants-to-build-gopuff-for-africa-and-middle-east-gets-26m-backing)); ~1 M orders/month and 300k+ users (2025, search summary) | Our base reaches 92.6k HH in 3 years with no ad budget. Breadfast spent on delivery subsidies |
| **Swvl** | Egypt, mass transit | ~50,000 passengers about a year after its 2017 launch (Reuters via [Wikipedia](https://en.wikipedia.org/wiki/Swvl)); "over a million users" later ([SME10x](https://www.sme10x.com/entrepreneurship-2/the-meteoric-rise-of-swvl)) | A sharp price promise spreads; it was VC-funded |
| **MNT-Halan** | Egypt, ride-hailing → lending super-app | 4.2 M downloads (Dec 2023); 11.7 M downloads, ~2 M active (end-2024) ([Forbes ME](https://www.forbesmiddleeast.com/lists/the-middle-easts-fintech-50-2025/mnt-halan/)) | Mass-market and loan-led. Downloads far exceed actives |
| **Thndr** | Egypt, investing | 2.6 M downloads / 133.5k active (Dec 2023) (13 §2.1) | Again, actives are ~5% of downloads |
| **Egyptian building apps today** | Amarati, Imarti, etc. | **Amarati 1K+ installs (4.7★); Imarti 100+**, re-checked on Google Play (EG) on 2026-10-12 ([Play](https://play.google.com/store/apps/details?id=com.amarati.app), [Play](https://play.google.com/store/apps/details?id=com.craftfuture.imarti)); Lyve's white-label apps are 10K+ each (01) | **At M12 our base (~6.8k downloads) would already be ~5× the largest Egyptian building app.** By M24 (~61k) it would exceed every developer compound app found in file 01 |

**Sanity verdict:** the base case sits well below VC-funded ramps (MyGate, NoBrokerHood) and well above today's Egyptian building apps. That is where a zero-marketing product with a working viral loop should land. The aggressive case needs funding by ~M10 to be credible.

---

## 13. Funding recommendation

### 13.1 Bootstrapped runway

| Period | Base cumulative burn (USD) | What it buys |
|---|---|---|
| M1–M6 | **~38k** | MVP plus a 40-building pilot (Option A lean team) |
| M1–M12 | **~104k** | ~636 Live buildings, first compounds, payments live |
| M1–M18 | ~206k | Giza/October wave, marketplace starts |
| M1–M24 | ~313k | Alexandria wave, ads start |
| M1–M36 | ~528k | Four waves; ~92,601 HH |
| Peak (≈M44) | **~568k** | Break-even at M45 |

**Recommendation:**
1. **Self-fund M1–M12 (~USD 105k / EGP 5.5 M).** This is the founder's "development + operations" budget. Hold the field team to ≤6 champions in Cairo-East.
2. **Raise a pre-seed of USD 400–600k between M10 and M14**, but only when the gates below are met. That covers the base case to break-even with ~15% contingency. With an aggressive-case trajectory, raise USD 600k–1 M to fund 25–30 champions, because the aggressive case pays back earlier (peak need ~USD 320k, break-even M26).
3. **If the gates are missed at M12:** stay in Cairo-East, cap the team at Option A plus 2 champions, push compound SaaS (the cheapest households, §10.3), and re-test at M18. The conservative case never breaks even with a growing team, so **do not scale costs on conservative traction.**
4. **Non-dilutive options:** Flat6Labs-style accelerator packages (historically EGP 1.5 M cash and in-kind, follow-on up to EGP 3 M; [Entrepreneur ME](https://mena.entrepreneur.com/?p=19448), search summary), ITIDA/TIEC grants (not researched here), and **revenue-based financing against compound SaaS contracts** once ≥20 compounds are paying.

### 13.2 Gate metrics for the M10–M14 raise

| Metric | Gate | Why investors care |
|---|---|---|
| Live buildings (13 §3.2 definition) | **≥ 500**, growing ≥ 15% month on month | Scale proof |
| Seeded → Live within 30 days | ≥ 55% | Funnel efficiency |
| Household coverage in Live buildings | ≥ 60% of occupied units | Density = moat |
| Measured inter-building K (lifetime) | ≥ 0.4 | Organic growth |
| Admin (treasurer) M3 retention | ≥ 80% | Retention |
| Dues recorded in-app | ≥ 70% of units monthly | Habit and frequency |
| Field cost per Live building | ≤ EGP 2,000 | CAC discipline |
| Compounds | ≥ 5 pilots, ≥ 2 paying or with signed LOIs | Revenue path |
| Marketplace pilot | ≥ 300 orders, ≥ 25% repeat, ≤ 10% disputes | Monetization proof |
| Burn multiple (net burn ÷ net new ARR) | Trending below 3× by M18 | Capital efficiency |

### 13.3 What Egyptian investors are saying (2024–2026)

| Investor / source | Date | What they said or show | Relevance |
|---|---|---|---|
| **Algebra Ventures** (Karim Hussein, managing partner) | 27 May 2024 | Backs "potentially profitable business models". The era of "high growth at any cost" is over. Founders must ensure "every USD spent is spent towards improving profitability". Interested in AI only for "practical solutions to problems needed by the market" ([Enterprise](https://enterpriseam.com/egypt/?p=620791)) | Lead with unit economics (§9), not downloads |
| **A15** | 16 Jul 2025 | "Our bias remains toward the seed stage". Looks for teams that are "clear-eyed, data-driven, and execution-focused". First fund >10× DPI ([LaunchBase Africa](https://launchbaseafrica.com/?p=8485)) | Bring a metrics dashboard (the §13.2 gates) |
| **Sawari Ventures** | Oct 2024 | Launching Fund II, target **USD 200 M**, ~70% for Egypt; focus on fintech, edtech, health, green and deep tech ([Enterprise](https://enterpriseam.com/egypt/2024/10/22/sawari-ventures-is-launching-its-usd-200-mn-sawari-ventures-fund-ii/)) | Better at seed/Series A than pre-seed. Frame the payments and dues data as fintech |
| **Flat6Labs Cairo** | historical | EGP 1.5 M packages, follow-on up to EGP 3 M; sector-agnostic; takes idea-to-early-revenue stages ([Entrepreneur ME](https://mena.entrepreneur.com/?p=19448)) | Realistic first cheque or accelerator for M6–M12 |
| Market commentary (Arab Finance) | 23 Aug 2026 | Investors prefer startups with "market validation, revenue potential"; operators prioritise "unit economics, profitability, repeat purchasing" ([Arab Finance](https://arabfinance.com/en/news/newdetails/shifting-from-volume-to-value-egypt-startup-ecosystem)) | Show repeat behaviour (monthly dues) |
| Funding climate | H1 2026 | Egypt **USD 158.9 M across 29 deals, −11% y/y** (Wamda) ([Wamda](https://www.wamda.com/2026/07/mena-startup-investment-falls-1482-million-june-2026), [Arab Finance](https://arabfinance.com/en/news/newdetails/shifting-from-volume-to-value-egypt-startup-ecosystem)); USD 327 M including debt (Africa: The Big Deal). Tracxn: Egypt funding to July 2026 −62.76% vs 2025 (14 §7.3) | Capital is scarce and selective. Plan to bootstrap to the gates |

**Gap:** I found **no published pre-seed metric thresholds** from Algebra, Sawari, Flat6Labs or A15. The gate table in §13.2 is my synthesis of their stated priorities (profitability path, data-driven teams, validation and repeat use) plus category metrics from 13 §13.

---

## 14. Risks to the model and what the pilot must measure

| Assumption at risk | If wrong | Pilot measurement (M5–M8) |
|---|---|---|
| 10 occupied HH per building | ±1 HH moves break-even ~±4 months | Record units, occupied units and joined HH for the first 100 buildings |
| Seeded → Live 55% | −10pp ≈ −15% HH | Funnel by champion and by district |
| Lifetime K 0.45 | 0.30 → +5 months to break-even | Tag every building with the building that referred it |
| WhatsApp-only share 50% → 25% | More WhatsApp cost | Install share by age group; push opt-in rate |
| Bookings 4%/HH/month by M36 | 2.5% → break-even M53 | Ticket-to-booking conversion from maintenance tickets |
| Ads $1/HH/yr | $0.5 → +7 months | Pre-sell 3 sponsor pilots (ISP, water filters, pest control) in Cairo-East |
| PDPL fee tiers | Unknown mid-tier fees | Ask a privacy lawyer for the fee table before passing 100k records (base: ~M30) |
| FX | 66 at M36 cuts USD need by ~USD 25k | Keep USD costs (AI, WhatsApp, cloud) ≤ 15% of the total |

---

## 15. Sources

**Macro and census**
- CBE rate, 7 Oct 2026 — https://almalnews.com/2139951/ ; 4 Oct — https://almalnews.com/2139292/
- Urban CPI Sep 2026 — https://www.dailynewsegypt.com/2026/10/10/egypts-annual-urban-inflation-eases-to-13-9-in-september/ ; https://egyptianstreets.com/2026/10/11/egypts-annual-inflation-rises-to-12-8-percent-in-september-as-food-prices-increase/
- Statistical Yearbook 2025 Part 2 (2017 census tables 7-10, 7-11, 7-12) — https://www.moss.gov.eg/media/iuxiwrsi/الكتاب-الإحصائي-السنوي-_-2025_الجزء-الثاني.pdf
- CEIC Cairo urban buildings — https://www.ceicdata.com/en/egypt/number-of-buildings-census-by-region/no-of-buildings-census-urban-cairo
- 2017 census totals — https://amwalalghad.com/ihtg
- ERF census microdata (no floors variable) — https://erfdataportal.com/index.php/catalog/248/data-dictionary
- Cairo informal areas typology — https://www.citiesalliance.org/sites/default/files/2019-07/CairosInformalAreas_fulltext.pdf ; https://ethz.ch/content/dam/ethz/special-interest/conference-websites-dam/no-cost-housing-dam/documents/Barthes_final.pdf ; https://www.mdpi.com/2075-5309/13/5/1263
- Minimum wage — https://cairoscene.com/buzz/minimum-wage-for-private-sector-in-egypt-raised-to-egp-7-000
- StatCounter OS and vendors — https://gs.statcounter.com/os-market-share/mobile/egypt ; https://gs.statcounter.com/vendor-market-share/mobile-device/egypt

**Costs**
- WhatsApp Egypt rates — https://chatmaxima.com/whatsapp-api-pricing/egypt/
- Gemini pricing — https://ai.google.dev/gemini-api/docs/pricing
- Payscale field sales — https://www.payscale.com/research/EG/Job=Outside_Sales_Representative/Salary
- PDPL fees — https://www.tamimi.com/law_update_articles/from-policy-to-practice-egypt-issues-executive-regulations-of-the-personal-data-protection-law/
- AppsFlyer ME CPI — https://www.appsflyer.com/benchmarks/social-media/live-video-chat/live-video-chat---overall/android/egypt/2023-05-01/overall
- Saknna pricing — https://saknna.com
- Khidhma prices — https://www.khidhma.com/

**Benchmarks**
- MyGate — https://www.entrepreneur.com/article/343751 ; https://mygate.com/blog/cooperative-housing-society/mygate-raises-inr-65-crore-in-series-a-to-fuel-rapid-growth-expansion-across-10-cities/ ; https://mygate.com/about-us ; https://inc42.com/buzz/mygate-trims-fy25-loss-by-61-to-₹15-4-cr/
- InstaPay — https://egyptindependent.com/cbe-announces-that-instapay-transactions-total-le112-7-bn-in-year/ ; https://waya.media/instapay-transactions-hit-112-7b-egp-within-one-year/
- MoneyFellows — https://www.forbesmiddleeast.com/lists/?p=5044 ; https://meatechwatch.com/2025/10/21/egypts-money-fellows-surpasses-1-5-billion-in-transactions-achieves-profitability/
- Breadfast — https://techcrunch.com/2021/11/03/egypts-breadfast-wants-to-build-gopuff-for-africa-and-middle-east-gets-26m-backing ; https://sacra.com/c/breadfast
- Swvl — https://en.wikipedia.org/wiki/Swvl ; https://www.sme10x.com/entrepreneurship-2/the-meteoric-rise-of-swvl
- MNT-Halan — https://www.forbesmiddleeast.com/lists/the-middle-easts-fintech-50-2025/mnt-halan/ ; https://mena.entrepreneur.com/?p=3241
- Amarati / Imarti Play listings — https://play.google.com/store/apps/details?id=com.amarati.app ; https://play.google.com/store/apps/details?id=com.craftfuture.imarti

**Investors and funding**
- Algebra (Enterprise, May 2024) — https://enterpriseam.com/egypt/?p=620791
- A15 (LaunchBase, Jul 2025) — https://launchbaseafrica.com/?p=8485
- Sawari Fund II — https://enterpriseam.com/egypt/2024/10/22/sawari-ventures-is-launching-its-usd-200-mn-sawari-ventures-fund-ii/
- Flat6Labs Cairo fund — https://mena.entrepreneur.com/?p=19448
- Arab Finance, Aug 2026 — https://arabfinance.com/en/news/newdetails/shifting-from-volume-to-value-egypt-startup-ecosystem
- Wamda H1/June 2026 — https://www.wamda.com/2026/07/mena-startup-investment-falls-1482-million-june-2026

**Internal files reconciled:** 01, 03, 08, 10, 11, 12, 13, 14 in `research/`.

---

## 16. Verification log

| # | Claim | Check performed (2026-10-12) | Verdict |
|---|---|---|---|
| 1 | CBE USD/EGP ≈ 52.3–52.5 in early Oct 2026 | Al Mal News 7 Oct (52.3204/52.4600) and 4 Oct (52.22/52.36); file 14 XE 52.58 | **Confirmed** (two dates, two sources) |
| 2 | Urban CPI 13.9% (Sep 2026), national 12.8% | Daily News Egypt re-fetched; Egyptian Streets (file 14) | **Confirmed** |
| 3 | 2017 census: Cairo 591,428 regular buildings, 4,762,446 units | Extracted from the Yearbook PDF tables 7-10 and 7-11; CEIC snippet gives 688,001 for all urban building types | **Confirmed** (definition differs; both reported) |
| 4 | Urban apartments: 54.7% used for housing | Yearbook table 7-12 (9,165,143 of 16,759,256) | **Confirmed** (my ratio) |
| 5 | Floors-per-building distribution | Knoema (HTTP 530), CEIC (403), ERF microdata has no floors variable | **Not found.** Typical-building size is an ESTIMATE from typology studies |
| 6 | Android 83.4% / iOS 16.58% (Sep 2026) | StatCounter re-fetched; vendor page Apple 16.6% | **Confirmed**; volatile (Jun 91.1%) |
| 7 | WhatsApp Egypt $0.0644 / $0.0036; 1,000 free service messages from 1 Oct 2026; +14% VAT | ChatMaxima re-fetched; files 10 and 14 cite ArabyBot, YCloud, respond.io | **Confirmed** (BSP level; Meta CSV not parsed) |
| 8 | Gemini 2.5 Flash-Lite $0.10/$0.40; 2.5 Flash $0.30/$2.50 | Google pricing page re-fetched | **Confirmed**; newer 3.x models cost more, so the AI line has headroom |
| 9 | Amarati 1K+ (4.7★); Imarti 100+ | Raw Play Store HTML (gl=EG) fetched and parsed | **Confirmed.** Supersedes 08's "unverified" |
| 10 | MyGate 1,000+ communities within 18 months (Oct 2018); 1.2 M homes (Oct 2019) | MyGate Series A/B releases via search; Entrepreneur India | **Confirmed** (company-reported) |
| 11 | InstaPay 2.16 M registered in year 1 | Egypt Independent and Waya | **Confirmed** (registered, not active) |
| 12 | MoneyFellows 1.6 M downloads / 173k active (Aug 2021); 8 M users / 350k MAU (Oct 2025) | Forbes ME and MEA Tech Watch via search | **Partly confirmed**; the 2025 figures are company press releases |
| 13 | Halan 11.7 M downloads, 2 M active (end-2024) | Forbes ME via search; another entry says 10 M | **Conflicting** (definitions or dates); used only as order of magnitude |
| 14 | Algebra "growth at any cost" quote | Enterprise article fetched (27 May 2024) | **Confirmed**; older than 2025 |
| 15 | A15 "bias remains toward the seed stage" | LaunchBase Africa fetched (16 Jul 2025) | **Confirmed** |
| 16 | Egypt H1 2026 USD 158.9 M / 29 deals | Wamda via search and Arab Finance fetch | **Confirmed** |
| 17 | Private-sector minimum wage raised to EGP 8,000 (file 08) | Search found 8,000 only for the public sector | **Corrected**: private sector is still EGP 7,000 as far as I could find |
| 18 | Explicit pre-seed metric thresholds from Algebra, Sawari, Flat6Labs, A15 | Several searches | **Not found.** §13.2 gates are a synthesis |
| 19 | Egypt-specific CPI (cost per install) | AppsFlyer page shows ME data because Egypt is below threshold | **Weak** comparable only |
| 20 | Imarti developer origin (01: Saudi `.com.sa` policy; 12: Haram, Giza address) | Not re-checked | **Open conflict**; irrelevant to the model |
