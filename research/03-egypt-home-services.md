# 03 — Egyptian Home Services and Adjacent Marketplaces (the Phase-2 Monetization Layer)

**Research angle:** Who the building/compound app will compete with or partner with when it starts selling services to residents as an intermediary in Phase 2.
**Market focus:** Egypt only. Gulf, Indian and US players are used as benchmarks.
**Date of research:** 2026-10-12
**Method:** About 55 web searches and page fetches in Arabic and English, covering news (Wamda, Enterprise, MENAbytes, Egyptian Streets, Masrawy, Amwal Al Ghad, Zawya), company investor relations (Fawry, Talabat, valU), regulators (NTRA, CBE via press), App Store pages, and AppGoblin (a third-party app-store index).

> **How to read this document**
> - Every fact has a source URL next to it.
> - **ESTIMATE** marks my own calculations. The reasoning is shown each time.
> - **NOT FOUND** means I searched and could not verify the item. Nothing in this document is invented.
> - AppGoblin install counts are third-party *estimates*. They are not the official Google Play install bands. Rating counts are more reliable.

---

## 0. Executive Summary (the 12 things the founder must know)

1. **No Egyptian home-services marketplace has reached scale. The category is fragmented and under-capitalised.** The best-known player, **FilKhedma** (founded 2014), raised about **US$1.2–1.25M** in total over 5 rounds [corrected: earlier draft said €1.2m; databases report USD] ([StartupList](https://startuplist.africa/startup/filkhedma/fundings), [CB Insights](https://www.cbinsights.com/company/filkhedma/financials)). It was sold to South Africa's **SweepSouth** in December 2021 for an undisclosed sum ([Wamda](https://www.wamda.com/en/2021/12/sweepsouth-fully-acquires-filkhedma)). Its Android app has about 1.4K ratings, a **3.72★** average and an estimated ~178K installs ([AppGoblin](https://appgoblin.info/apps/com.filkhedma.customer)). Its iOS app shows **3.2★** and was last updated in **November 2022** ([App Store EG](https://apps.apple.com/eg/app/filkhedma-home-services/id1473742608)). **Taskty** is at **3.39★**, with its last update in **December 2023** ([AppGoblin](https://appgoblin.info/apps/com.tasktyapp.taskty)). **Fixawy** shows an estimated ~11K installs ([AppGoblin](https://appgoblin.info/search/fixawy)). No player is dominant.
2. **The category's core problem is trust and execution, not demand.** The reviews I could verify complain about no-shows, last-minute cancellations, poor coordination and overpricing (FilKhedma iOS reviews: "service provider cancels at the last minute or simply fails to show up", "appalling coordination"; Fixawy: "services are over priced"). These problems are why horizontal on-demand marketplaces fail.
3. **Market size.** The only published Egypt-wide "home services" figure is **USD 1.88bn (2025) → USD 5.11bn (2034), 11.58% CAGR**. Repair & Maintenance is the largest segment at about **USD 0.92bn** ([Deep Market Insights](https://deepmarketinsights.com/vista/insights/home-services-market/egypt)). This is a low-transparency paywalled estimate. My bottom-up **ESTIMATE** for B2C paid home services among smartphone-using urban households is about **EGP 20–40bn/yr (~USD 0.4–0.8bn)**. Facility management (B2B, buildings and compounds) is a separate and larger pool: **USD 2.3–2.6bn** ([Ken Research](https://www.kenresearch.com/industry-reports/egypt-facility-management-market.md), [IMARC](https://www.imarcgroup.com/egypt-facility-management-market)).
4. **The payment and utility rails are owned by giants, and they are partners, not competitors.** Fawry serves an **estimated 54.8M users monthly** [corrected: this is a press-release boilerplate estimate, not a reported 'active customer' KPI], has a network of 377K+ agents [corrected: reported as agents, not confirmed as POS terminals] and 24.2M cumulative myFawry downloads ([Zawya FY2025](https://www.zawya.com/en/press-release/companies-news/fawry-releases-fy2025-results-356861)). Vodafone Cash holds about 55% of wallets ([NTRA Q2-2025 via MEA Tech Watch](https://meatechwatch.com/2025/09/16/egypts-mobile-wallet-transactions-surge-72-in-q2-2025-to-egp-943-4-billion/)). InstaPay had **~11.5M registered users** by Nov–Dec 2024 [corrected: CBE figure was 11.5M, not 12M+] ([Egyptian Streets](https://egyptianstreets.com/2024/11/19/central-bank-of-egypt-to-allow-gulf-remittances-via-instapay-by-years-end/)) and processed 263M transactions in Q1-2025 ([Zawya](https://www.zawya.com/en/economy/north-africa/egypt-instapay-turns-profitable-a-year-after-transfer-fee-rollout-rt18pyrt), [PhotonPay summary of CBE](https://www.photonpay.com/hk/blog/article/instapay-egypt)). Sahl (bill payments, NFC electricity-card charging) has an estimated 5.2M Android installs and 298K ratings ([AppGoblin](https://appgoblin.info/search/sahl)). **Do not try to become a biller. Integrate with one** (Fawry, Sahl or Khales).
5. **Grocery and quick-commerce are taken.** Breadfast has $150M+ ARR (2024), about 1M orders/month, 30+ fulfilment centres and a valuation near $400M ([Egyptian Streets](https://egyptianstreets.com/2025/08/02/breadfast-attracts-ebrd-investment-of-10-million/), [Daba Finance](https://dabafinance.com/en/news/breadfast-ebrd-series-b2-funding-egypt)). Talabat has the largest market share in Egypt [unverified: not independently re-checked] ([Enterprise, Nov 2025](https://enterpriseam.com/logistics/2025/11/11/talabat-flynas-saudi-ground-services-see-bottom-line-top-line-growth-in-3q-2025/)). Rabbit says it is profitable in Egypt, with 1.4M customers ([Wamda](https://www.wamda.com/en/2025/04/rabbit-enters-saudi-market-backed-major-regional-investors)). **Do not build grocery.** Earn affiliate or referral fees, or run building-level group drops.
6. **Commission benchmarks.** Egyptian maintenance startups self-report **20–25%** (Khidmitty, [Gust](https://gust.com/companies/Khidmitty-s-startup-2/financials)) and **30–50%** of labour (Sal7lyy, [Gust](https://gust.com/companies/%D8%B5%D9%84%D8%AD%D9%84%D9%8A)). Talabat averages **14–15% overall and 17–18% for restaurants** (group-wide MENA figure; FAB does not isolate Egypt) ([FAB Securities](https://fabsresearch.bankfab.com/ResearchPortal/Download/Index/961)). Urban Company (India) has a take rate of about **26%**, an unverified figure ([IPO Market](https://www.ipomarket.in/news/urban-company-ipo-listing-performance)). A realistic blended Egyptian take rate is **12–20%** on labour-heavy jobs and **5–10%** on product-heavy jobs (ESTIMATE).
7. **Your unfair advantage is the building, not the individual.** Building-level, recurring and committee-approved services have high frequency, low customer acquisition cost and low leakage. They are paid from the building fund that your Phase-1 app will already manage. Examples are elevator maintenance contracts, water-tank cleaning, pest control for common areas, stairwell cleaning, pump and generator maintenance, building insurance and facility management. Incumbents here are offline FM firms. For example, Egypro FME manages 800 buildings (CEO interview, company self-reported) with 1,500+ staff and no resident app mentioned ([Amwal Al Ghad](https://amwalalghad.com/2025/10/21/%D8%B4%D8%B1%D9%83%D8%A9-egypro-fme-%D8%AA%D8%AF%D9%8A%D8%B1-800-%D9%85%D8%A8%D9%86%D9%89-%D8%A8%D9%85%D8%B3%D8%A7%D8%AD%D8%A9-%D8%A5%D8%AC%D9%85%D8%A7%D9%84%D9%8A%D8%A9-3-5-%D9%85%D9%84/)).
8. **Highest-scoring categories for a building-centric intermediary** (Section 7): (1) AC service, a seasonal mass event; (2) pest control, building plus unit, recurring; (3) plumbing and electrical handyman under a building-wide "approved technician"; (4) water-tank cleaning, elevator and pump AMC (B2B); (5) home cleaning and deep-cleaning subscriptions; (6) utility and building-fee payments, low margin but daily habit and data; (7) home insurance and BNPL referrals, high margin, no operations; (8) laundry pickup per building.
9. **The leakage lesson.** Homejoy (US) died partly because good cleaners took clients offline ([TechCrunch](https://techcrunch.com/2015/07/31/why-homejoy-failed-and-the-future-of-the-on-demand-economy)). In Egypt, where cash and WhatsApp dominate, leakage will be worse. Design for it: warranty only through the app, building-level contracts, wallet credits, technician subscription tiers instead of pure commission, and price-transparency features that technicians cannot replicate offline.
10. **The community-app monetization lesson.** India's MyGate (a gated-community app) ended free services in February 2023, made layoffs, and now earns about **65–70% of revenue from advertising** [corrected] rather than from service commissions ([Inc42](https://inc42.com/?p=471555), [SaaSRise](https://www.saasrise.com/deals/mygate-raises-225-crore-from-dharana-capital-72817b60-56dc-41fb-8149-9bffef4de1b1)). NoBrokerHood mixes ads, store commissions and home-services commissions ([NextLeap case](https://assets.nextleap.app/submissions/NLNoBrokerHood-2bb55e05-6d75-437c-a46b-3687a1e141f1.pdf)). US Amenify shares service revenue with property managers ([Amenify](https://www.amenify.com/blog/how-does-amenify-work-a-step-by-step-look-at-the-resident-services-app-changing-apartment-living)). **Plan for three revenue engines, not one:** (a) brand and local-merchant ads aimed at verified building residents, (b) service commissions, (c) building-fund payment and SaaS fees.
11. **Several names in the brief could not be verified as Egyptian home-services players.** "Elmohandes" (no maintenance app found), "Sallah" (most likely *Salahly / Sal7lyy*, an Assiut startup), "Mrs. Clean" (no Egyptian company found), and "Movers" (no single brand; the closest are Winch, an old app-based moving service, and Homzmart's 2025 spin-off **Lifters** for bulky logistics). Justlife and Washmen operate in the UAE, not Egypt. Rizek (UAE) entered Egypt in 2021 as a third-party super-app aggregator ([Enterprise](https://enterpriseam.com/egypt/2021/08/09/uae-super-app-rizek-launches-in-egypt/)).
12. **Zero-marketing-budget implication.** In Phase 2, supply (technicians) must come at no cost. Recruit from the bawab and the building's existing trusted technicians: every building already has a plumber and an electrician it calls. Formalising *them* in the app ("the building's technician") turns leakage into lock-in. This idea is my synthesis, not a sourced fact.

---

## 1. Market Sizing

### 1.1 Published top-down figures

| Market | Value | Year | Growth | Source | Reliability note |
|---|---|---|---|---|---|
| Egypt home services (total) | **USD 1.88bn** | 2025 | 11.58% CAGR to USD 5.11bn by 2034 | [Deep Market Insights](https://deepmarketinsights.com/vista/insights/home-services-market/egypt) | Paywalled. Segment values masked except Repair & Maintenance (USD 0.92bn, ~49%). Last updated June 2026. |
| Egypt home painting services | USD 1.09bn | 2025 | n/a | [Deep Market Insights](https://deepmarketinsights.com/vista/insights/home-painting-service-market/egypt) | Larger than half of "total home services", so the definitions are inconsistent. Treat as indicative only. |
| Egypt facility management | USD 2.6bn → 4.6bn | 2025 → 2032 | 8.6% CAGR | [Ken Research](https://www.kenresearch.com/industry-reports/egypt-facility-management-market.md) | B2B, includes commercial |
| Egypt facility management | USD 2.3bn → 4.1bn | 2024 → 2033 | 6.37% CAGR | [IMARC](https://www.imarcgroup.com/egypt-facility-management-market) | |
| Egypt facility management (broad) | USD 7.0bn → 13.1bn | 2025 → 2031 | 11.05% CAGR | [Mordor](https://www.mordorintelligence.com/industry-reports/egypt-facility-management-market) | Much broader definition. Mordor's *integrated* FM report says USD 1.63bn. |
| Egypt home healthcare | USD 1.015bn → 2.08bn | 2022 → 2030 | | [Insights10](https://insights10.com/product/egypt-home-healthcare-market-analysis/) | Adjacent vertical |
| Egypt home appliances (goods) | USD 6.85bn | 2024 | | [IMARC](https://www.imarcgroup.com/egypt-home-appliances-market) | Goods, not services. Drives install and repair demand. |
| Egypt e-commerce | USD 10.24bn → 19.28bn | 2025 → 2030 | 13.49% CAGR | Mordor via [Zawya](https://www.zawya.com/en/economy/north-africa/how-egypt-is-redefining-online-shopping-geq8k83m) | 72.7% of 2024 e-com sales on smartphones |
| Egypt BNPL volume | USD 1.67bn | 2025 | ~33% YoY | [ResearchAndMarkets / BusinessWire](https://www.businesswire.com/news/home/20250305099643/en/Egypt-Buy-Now-Pay-Later-Business-and-Investment-Report-2025) | |
| Mobile-wallet transactions | EGP 943.4bn per quarter | Q2-2025 | +72% YoY | NTRA via [MEA Tech Watch](https://meatechwatch.com/2025/09/16/egypts-mobile-wallet-transactions-surge-72-in-q2-2025-to-egp-943-4-billion/) | 46.3M active wallets |

### 1.2 Demographic and housing base (Egypt)

| Indicator | Value | Source |
|---|---|---|
| Households | ~25.5M (2022, CAPMAS) | [Amwal Al Ghad / CAPMAS](https://amwalalghad.com/mw4m) |
| Urban households | ~11.5M (44.6%). Rural ~14.3M (55.4%) | Same CAPMAS-based reporting ([Amwal Al Ghad](https://amwalalghad.com/trbh)) |
| Buildings (2017 census) | 16.18M buildings, 43.2M units | [Invest-Gate](https://invest-gate.me/news/egypts-capmas-reveals-latest-population-housing-census/) |
| Vacant units (2017) | 12.8M (Cairo: 22.7% of 4.7M units vacant) | [Egypt Independent](https://egyptindependent.com/total-number-vacant-housing-units-egypt-12-8-mn-capmas/) |
| Internet users | 96.3M (81.9%), early 2025 | DataReportal via [Zawya](https://www.zawya.com/en/economy/north-africa/how-egypt-is-redefining-online-shopping-geq8k83m) |
| Electricity subscribers | target 47.14M for FY2026/27 | Electricity Holding Co. via [Amwal Al Ghad](https://amwalalghad.com/iqi5) |
| Informal workers | 18.7M of 29.2M employed (~60%), Q1-2024 | CAPMAS via [Cairo Governorate](https://www.cairo.gov.eg/en/news/news-eng/2024/edd26a9969d44378be5c315c024dc05d) |
| Household spend on "housing & its requirements" | 18.7% of spending (HIECS 2017/18) | [El Watan](https://www.elwatannews.com/news/details/5092762) (press summary; verify with CAPMAS) |

### 1.3 Bottom-up ESTIMATE of the addressable B2C home-services pool

**ESTIMATE.** Every input below is an assumption and should be validated by survey.

| Input | Assumption | Reasoning |
|---|---|---|
| Target households (urban + new cities, apartment, smartphone, middle income and above) | 5–7M | ~11.5M urban households (CAPMAS), minus low-income and non-apartment households. Internet penetration is ~82%. |
| Paid home-service spend per household per year | EGP 4,000–6,000 | e.g. 3–4 handyman visits at EGP 150–500 ([Khidhma price list](https://www.khidhma.com/)), 1–2 AC services at about EGP 450 per unit ([B.TECH](https://btech.com/p/air-conditioner-maintenance-service-1-device)), 1 pest treatment, occasional deep cleaning. Excludes finishing and renovation and full-time domestic help. |
| Pool | **EGP 20–42bn/yr** (≈ USD 0.4–0.85bn at ~EGP 48–50/USD, an assumed rate to verify) | 5M × 4,000 to 7M × 6,000 |
| Online/app-intermediated today | <5% | No player has more than ~200K installs (Section 2). Most demand goes through the bawab, word of mouth, Facebook groups and WhatsApp. |
| Building-level (common area) services, separate pool | Part of the USD 2.3–2.6bn FM market | Elevators, tanks, cleaning, security, gardens. Mostly compounds and commercial buildings. |

**Interpretation.** The Deep Market Insights USD 1.88bn figure is plausible as an *all-in* number that includes B2B and informal labour. The share that is *already digital* is tiny. That means the opportunity is converting the offline trust network (bawab, union head, residents' WhatsApp group). It is not taking share from existing apps.

---

## 2. Competitor and Partner Landscape: Home Maintenance and Handyman

### 2.1 Master table

| Player | Model | Coverage | Traction (latest verified) | Funding | Ratings / app health | Status |
|---|---|---|---|---|---|---|
| **FilKhedma (فى الخدمة)** | Managed marketplace: pre-set prices, background-checked technicians, 1-month warranty, multiple services per visit. In 2019 it charged per hour and paid technicians a salary plus bonus ([Gust/StartupList summary](https://www.startuplist.africa/startups/filkhedma)). Also offers cleaning and in-home beauty (Velvet Unit) | 20+ areas in Cairo, Giza, North Coast ([App Store](https://apps.apple.com/app/id1473742608)) | 2019: 500 technicians, target 1,000; ~60 staff; business volume ×5 in 2018 ([Daily News Egypt](https://www.dailynewsegypt.com/2019/10/01/filkhedma-new-app-provides-home-maintenance-services-through-1000-handyworkers/)). 2021: ~2,000 providers ([Business Today Egypt](https://businesstodayegypt.com/amp/4/1199/Egyptian-home-services-platform-Filkhedma-acquired-by-SA’s-SweepSouth)) | KiAngel (2016), Algebra + Glint (2017, $300K + $800K per DNE), Cairo Angels (Dec 2021) ([Wamda](https://www.wamda.com/en/2021/12/filkhedma-receives-new-investment-cairo-angels)). **Acquired 100% by SweepSouth, Dec 2021** ([Wamda](https://www.wamda.com/en/2021/12/sweepsouth-fully-acquires-filkhedma)) | Android 3.72★, ~1.4K ratings, ~178K installs (est.), updated Aug 2025 ([AppGoblin](https://appgoblin.info/apps/com.filkhedma.customer)). iOS 3.2★ / 2.1K ratings, last version Nov 2022 ([App Store EG](https://apps.apple.com/eg/app/filkhedma-home-services/id1473742608)) | Operating. SweepSouth exited Nigeria in Nov 2022 but kept Egypt ([Nairametrics](https://nairametrics.com/2022/11/23/south-african-cleaning-services-startup-sweepsouth-quits-nigeria/)). No post-2022 Egypt growth news found. |
| **Taskty** | Marketplace for cleaning, pest control, plumbing, carpentry, electrical, AC, moving | Greater Cairo | "Proudly serving 20,000 customers" (listing). Older claim of 500 active suppliers in 2 cities ([MIT Solve via search](https://vc4a.com/ventures/taskty-com)) | ~$140K seed ([CB Insights](https://www.cbinsights.com/company/taskty)) | Android 3.39★, 658 ratings, ~168K installs (est.), **last update Dec 2023** ([AppGoblin](https://appgoblin.info/apps/com.tasktyapp.taskty)) | Probably dormant or low activity (ESTIMATE based on the update gap) |
| **Fixawy (فكساوي)** | Started as a directory (pick an area and trade, call the craftsman directly, rate them). A 2024 app version auto-matches technicians, lists 250+ services, accepts cash, wallet or card ([AppGoblin](https://appgoblin.info/apps/com.fixawy.servicebooking)). Ran video-guided DIY repair during COVID ([Daily News Egypt](https://www.dailynewsegypt.com/?p=727734)) | Alexandria origin, national claim | Starting price EGP 50 (older roundup, [Cairoscene](https://cairoscene.com/lifestyle/you-ll-never-have-to-do-housework-again-with-these-4-egyptian-apps)) | NOT FOUND | iOS 4.2★ / 124 ratings, v9.2.1 Sep 2025 ([App Store](https://apps.apple.com/app/id1071671875)). New Android app ~11K installs (est.) | Operating, small |
| **Salahly / Sal7lyy (صلحلي)**, probably the "Sallah" in the brief | Tech-enabled maintenance with vetted technicians, 1-month guarantee, own technician academy, parts store, free inspection, fixed price | Assiut, Sohag, New Valley (Upper Egypt) ([Dealroom](https://app.dealroom.co/companies/sal7lyy)) | NOT FOUND | Athar accelerator, TIEC incubation ([careers site](https://sites.google.com/view/salahly-career/home)) | NOT FOUND | Commission self-reported at **30–50% of labour** ([Gust](https://gust.com/companies/%D8%B5%D9%84%D8%AD%D9%84%D9%8A)) |
| **Khidhma** | Fixed-price marketplace (cleaning, maintenance, AC, finishing, waterproofing, car repair) | Cairo (Al Rehab listed) | Self-claims 100K+ bookings, 5K+ pros, 4.9 rating (unverified) | NOT FOUND | Web only. "App coming soon" ([khidhma.com](https://www.khidhma.com/)) | New or early. Prices: cleaning EGP 99–199, plumbing EGP 150, electrical EGP 175 |
| **Khidmitty** | Marketplace, **20–25% commission on labour** | Cairo (founded Dec 2016) | NOT FOUND | Gust profile only ([Gust](https://gust.com/companies/Khidmitty-s-startup-2/financials)) | NOT FOUND | Unknown |
| **Osta (Alexandria)** | Commission from technicians plus customer order fees | Alexandria | NOT FOUND | NOT FOUND ([Gust](https://gust.com/companies/osta0)) | NOT FOUND | Unknown |
| **FIXIT Egypt** | Scheduled maintenance (book ≥6 h ahead). EGP 100 (router) to EGP 15.1K (painting) | "All Egypt" | NOT FOUND | NOT FOUND | NOT FOUND | Listed in 2024 ([Enterprise](https://enterpriseam.com/egypt/2024/08/30/leave-home-maintenance-to-the-pros/)) |
| **Aamel** | "Instant maintenance": electrical, plumbing, AC, pest, **tank cleaning, insulation**, furniture moving | NOT FOUND | NOT FOUND | NOT FOUND | iOS and Android per Enterprise | Listed in 2024 ([Enterprise](https://enterpriseam.com/egypt/2024/08/30/leave-home-maintenance-to-the-pros/)) |
| **Edara** | Plumbing, electrical, pest, pool maintenance **plus property management**, from EGP 4/m² | Cairo | NOT FOUND | NOT FOUND | NOT FOUND | Closest to a building-management competitor ([Enterprise](https://enterpriseam.com/egypt/2024/08/30/leave-home-maintenance-to-the-pros/)) |
| **BusyBees (Handyman)** | Cleaning, post-construction, pest, holiday-home services | Cairo, Sahel, Sokhna | NOT FOUND | NOT FOUND | NOT FOUND | [busybeesgroup.com](https://busybeesgroup.com/egypt/handyman-services/) |
| **Shoghlana (شغلانة)** | Craftsmen register, upload work photos, set availability. Claims no intermediary fees | Egypt | NOT FOUND (not indexed by AppGoblin) | NOT FOUND | iOS listing ([mwm.ai](https://mwm.ai/apps/shoglana/6744296451)) | New (2025 App Store ID range) |
| **Rizek (UAE)** | "Super app" aggregating third-party home-service apps | UAE, KSA, Egypt (launched in Egypt Aug 2021) | NOT FOUND for Egypt | $10M Series A (2021). Acquired by Astra Tech (2022) ([Khaleej Times](https://www.khaleejtimes.com/kt-network/astra-tech-acquires-rizek-to-move-closer-to-delivering-ultra-platform-to-customers?amp=1)) | NOT FOUND | Egypt activity unclear |
| **"Elmohandes"** | **NOT FOUND** as a home-maintenance app. The closest match is a real-estate app, "Abo Hamza El Mohandes" | | | | | |
| **Dubizzle Egypt (Services)** | Classifieds: individual electricians list at EGP 55–200 | National | n/a | n/a | n/a | Main informal discovery channel ([Dubizzle](https://www.dubizzle.com.eg/en/services/maintenance/dokki/q-electric-services-services/)) |

### 2.2 What this tells us

- **No category leader with a strong brand.** The largest specialist, FilKhedma, has an estimated ~178K Android installs after 11 years. For comparison, Breadfast has ~5.2M (est.) and Sahl ~5.2M (est.) ([AppGoblin](https://appgoblin.info/search/breadfast)). Home services in Egypt has not produced an app that people open every month.
- **Why.** (a) Visits are infrequent per household, so customer acquisition cost is high and retention low. (b) Trust and quality are hard to control with an informal workforce. (c) Leakage: after one good visit, the customer keeps the technician's WhatsApp number. (d) Price sensitivity and cash. Every one of these improves when you **own the building relationship** first. This is the strategic logic of the founder's Phase-1 then Phase-2 plan.
- **Three operating models exist:**
  1. **Directory / lead-gen.** Fixawy (old), Shoghlana, Dubizzle. Low operations, low trust, low monetization.
  2. **Commission marketplace.** Khidmitty 20–25%, Sal7lyy 30–50%, Osta.
  3. **Managed service with employed or salaried technicians.** FilKhedma's 2019 model with 12 direct technicians. Highest quality, but slow and hard to scale.
- **Recommended Phase-2 model:** a hybrid. Run a commission marketplace for long-tail trades, plus a managed "building technician" programme. Building-level contracts can be white-labelled from FM firms.

---

## 3. Cleaning, Laundry, Pest Control, Gas and Water

| Category | Egyptian players found | Price points found | Notes |
|---|---|---|---|
| **Home cleaning** | Jinni (Cairo, 2016, residential + corporate) ([TechCabal](https://techcabal.com/2019/12/18/my-life-in-tech-this-egyptian-couples-got-a-genie-full-of-housekeepers-jinni/)); Kheddma (deep cleaning, min. EGP 300, older) ([Cairoscene](https://cairoscene.com/buzz/kheddma-on-demand-cleaning-app)); Mermaid (subscriptions) ([Gust](https://gust.com/companies/mermaid-getamermaid-com)); RE-BEYT (Cairo, EGP 100/h commercial); Hestia (staffing agency, 240 customers claimed) ([hestia-egypt.com](https://hestia-egypt.com/)); HLPR (domestic helpers) ([Dealroom](https://app.dealroom.co/companies/hlpr)); FilKhedma and Taskty also offer cleaning | Cleaning help ~EGP 161/h in Cairo (6 data points, weak) ([Expatistan](https://expatistan.com/price/cleaning-help/cairo/USD)); Khidhma cleaning EGP 99–199 | **"Mrs. Clean": NOT FOUND in Egypt.** **Justlife (ex-JustMop) is UAE-only** ([CB Insights](https://www.cbinsights.com/company/just-mop/financials)). There is no scaled Egyptian cleaning brand, so this is an open lane. Cleaning is the most subscription-friendly category. |
| **Laundry / dry cleaning** | **Laverie** (Cairo, 2018). Six-figure seed from A15 (Apr 2021). 4,000 users and 60K items by 2021. 25% MoM growth claimed ([Wamda](https://www.wamda.com/en/2021/04/laverie-raises-figure-funding-round)). ~17K installs (est.) ([AppGoblin](https://appgoblin.info/search/laverie)). Kleen and Aghsilini (cities unconfirmed) | NOT FOUND | **Washmen is UAE-only.** No large Egyptian player. Per-building pickup routes (one driver, 30 flats) fix laundry's main unit-economics problem, last-mile cost. Strong fit for a building-centric app. |
| **Pest control** | SWF (since 1999; rats whole house EGP 1.55K, bed bugs 3 rooms EGP 2.3K, +EGP 125–135 per room) ([Enterprise](https://enterpriseam.com/egypt/2024/08/30/leave-home-maintenance-to-the-pros/)); Maadi firm with 5-yr written warranty ([Yellow Pages](https://yellowpages.com.eg/ar/keyword/pest-control)); Dubizzle listings EGP 50–70 ([Dubizzle](https://www.dubizzle.com.eg/services/maintenance/dokki/q-pest-control-services/)) | EGP 50 → 2,300 | **A building-wide treatment is the ideal group-buy.** Pests move between flats, so treating one flat alone fails. The building app can sell "whole-building spraying" with per-flat cost split. Licensing is required ([projectsegy](https://projectsegy.com/what-licensing-pest-control-egypt/)). |
| **Gas cylinders (بوتاجاز)** | Quick Gas (iOS 1.6★ / ~106 ratings), Gazna, Qannina. Egyptian coverage unconfirmed | Official 12.5 kg cylinder: EGP 200 (Apr 2025) → 225 (Oct 2025) → **275 (Mar 2026, single report)** ([Masrawy](https://www.masrawy.com/news/news_economy/details/2026/7/23/3022188/بكم-يشتري-المواطن-أسطوانة-البوتاجاز-)) | Price is regulated, so margin comes only from a delivery fee. High frequency in non-piped areas. Piped natural gas bills (Petrotrade, Town Gas) are payable through Sahl and Fawry. **Low-margin utility. Treat as a habit feature, not a profit centre.** |
| **Drinking water (gallons)** | H2U (Cairo, ~2018, status unknown) ([Cairoscene](https://cairoscene.com/buzz/http-www-cairoscene-com-buzz-h2u-water-delivery-app)) | NOT FOUND | Breadfast and Talabat sell water. Building-level standing order could work. |
| **Water-tank cleaning (خزانات)** | Aamel lists it ([Enterprise](https://enterpriseam.com/egypt/2024/08/30/leave-home-maintenance-to-the-pros/)). Otherwise informal | Dubizzle Alexandria shows EGP 10K–100K listings, scope unclear ([Dubizzle](https://www.dubizzle.com.eg/services/maintenance/bolkly/q-housekeeping-services/)) | **Building-only service, paid from the building fund.** Recurring (1–2×/yr recommended). Under-digitised. |
| **Elevator maintenance (الأسانسير)** | Offline: OEMs and local firms | **NOT FOUND (no reliable 2025 EGP price).** Only Saudi comparables (~SAR 1,000/yr, 12 visits) ([OpenSooq](https://sa.opensooq.com/ar/search/280846358)) | Highest-value recurring building contract. The app can host the logbook, visit check-ins and breakdown tickets, and later broker the annual maintenance contract (AMC). |

---

## 4. Grocery and Quick Commerce (adjacent, do not compete)

| Player | Key facts | Source | Relevance to the building app |
|---|---|---|---|
| **Breadfast** | $150M+ ARR (2024, company-reported); ~1M orders/month (company claim); 300K+ active users; 30+ fulfilment centres; >80% retention; $10M from EBRD (Series B2, 2025); ~$382–400M valuation. Super-app expansion: restaurants, Chef on-Demand, travel, Breadfast Card/Pay. iOS 4.8★ / 153K ratings; Android ~5.2M installs (est.) / 91K ratings | [Egyptian Streets](https://egyptianstreets.com/2025/08/02/breadfast-attracts-ebrd-investment-of-10-million/), [MENAbytes](https://www.menabytes.com/breadfast-10m-series-b2/), [App Store](https://apps.apple.com/eg/app/id1288436997), [AppGoblin](https://appgoblin.info/search/breadfast) | Likely to add services eventually. Partner for building-level group orders or affiliate. iOS complaints centre on contact and complaint channels ("there's no other way of reaching you"). |
| **Rabbit** | Founded Oct 2021; $11M pre-seed (record for MEA); 40M+ items to 1.4M customers in Egypt; revenue ×8.5 in 2 years; **profitable in Egypt** (CEO claim); Saudi operations launched early 2024 in Riyadh [corrected: Apr 2025 was the funding/press announcement, not the market entry] | [Wamda](https://www.wamda.com/en/2025/04/rabbit-enters-saudi-market-backed-major-regional-investors), [Arab News](https://www.arabnews.com/node/2603775/amp), [MENAbytes](https://www.menabytes.com/rabbit-pre-seed/) | Same as above |
| **Talabat (Egypt)** | Largest market share in Egypt. Group 2025 GMV: food ~$6.7bn, grocery ~$3.5bn. talabat pro launched in Egypt in Q1-2025 ("most successful launch yet"). Group commission 14–15% overall, 17–18% restaurants (group-wide; commission rates compressed ~0.9pp in 4Q25 per FAB). Older Egypt figure: 15–25% [unverified for 2025] | [Talabat IR May 2026](https://ir.talabat.com/wp-content/uploads/2026/06/20260514_talabat-Investor-Presentation.pdf), [FAB Securities](https://fabsresearch.bankfab.com/ResearchPortal/Download/Index/961), [Enterprise 2021](https://enterpriseam.com/egypt/2021/10/13/are-restaurant-delivery-apps-a-modern-day-mafia-in-egypt-and-abroad/) | Commission benchmark. Talabat has no home-services vertical in Egypt (NOT FOUND). |
| **Online grocery overall** | Online share of food e-commerce 0–5%, ~$90M (ECDB) | [ECDB](https://ecdb.com/resources/sample-data/market/eg/food) | ECDB's $90M conflicts with Breadfast's $150M ARR alone, so third-party market sizes are unreliable. |

**Verdict:** Grocery is capital-intensive (dark stores, fleets) and owned by well-funded players. The building app should be a **demand aggregator**: a "building basket" or group order delivered once to the bawab. It should earn referral or affiliate revenue and never run inventory.

---

## 5. Payments, Bills and Financial Services (the rails)

| Player | Scale | Fees / model | Source | Integration angle |
|---|---|---|---|---|
| **Fawry** | FY2025 revenue EGP 8.65bn (+57%); net profit EGP 2.89bn; throughput EGP 943.6bn; **~54.8M estimated monthly users** [corrected: boilerplate estimate, not an active-customer KPI]; 377K+ agents [corrected: reported as agents]; **24.2M myFawry downloads**; ~6M transactions/day; 1.1M digital insurance policies | Utility subscribers historically paid EGP 1–5 commission per bill (old figure) | [Zawya](https://www.zawya.com/en/press-release/companies-news/fawry-releases-fy2025-results-356861), [Amwal Al Ghad (old)](https://en.amwalalghad.com/?p=26548) | Payment gateway (cards, wallets, valU, reference-code cash at 200K+ outlets). Collect building fees and service payments. Possible bill-payment API (developer terms NOT FOUND). |
| **Sahl (Delta Egypt Payments)** | ~5.2M Android installs (est.) / 298K ratings; 2024 claim: 12M customers monthly, 15M households; $6M seed + Series A (2024); NFC prepaid-electricity charging; electricity, water (NUCA), gas (Petrotrade), telecom, TV | [Wamda](https://www.wamda.com/en/2024/06/egypt-sahl-closes-dual-rounds-6-million), [LaunchBase](https://launchbaseafrica.com/2024/06/10/egyptian-fintech-startup-sahl-secures-6-million-in-funding-to-streamline-bill-payments/), [AppGoblin](https://appgoblin.info/search/sahl) | **The best-fit bill-payment partner.** New-city water (NUCA) matches the compound audience. Prepaid electricity cards can be charged by NFC on a phone ([Masrawy](https://www.masrawy.com/news/news_egypt/details/2025/1/22/2714129/-كيفية-شحن-كارت-الكهرباء-عبر-الموبايل-)). |
| **Khales (e-finance + Bee + E-Masary)** | Bill aggregator (electricity, telecom, government, charity) | | [Amwal Al Ghad](https://en.amwalalghad.com/?p=55404) | Alternative biller API |
| **Aman Holding** | 250K+ POS, 50M+ customers monthly (2024); CBE "Muyassir" payment-facilitator licence | | [Forbes ME](https://www.forbesmiddleeast.com/lists/the-middle-easts-fintech-50-2025/aman-holding/), [Al Mal](https://almalnews.com/781442/) | Cash-in network plus consumer finance |
| **Masary** | ~25K POS (undated) | | [e-masary](https://e-masary.yolasite.com) | Minor |
| **InstaPay (CBE / EBC)** | ~11.5M registered users Nov–Dec 2024 [corrected] (CBE); 263M transactions, EGP 1.2trn in Q1-2025; profitable after fees | **0.1% per transfer, min EGP 0.50, max EGP 20** (from 1 Apr 2025) | [Egyptian Streets](https://egyptianstreets.com/2025/04/03/instapay-now-charging-transfer-fees), [Zawya](https://www.zawya.com/en/economy/north-africa/egypt-instapay-turns-profitable-a-year-after-transfer-fee-rollout-rt18pyrt) | **Building-fee collection: residents already pay the union head by InstaPay.** The app should reconcile InstaPay transfers (screenshot OCR or IPN payment links) rather than replace them. |
| **Vodafone Cash** | 55% of wallets, 78% of transactions, 81% of value (Q2-2025); 12.6M active users H1-2025; prepaid-electricity card charging via Ana Vodafone (powered by Sahl) | | NTRA via [MEA Tech Watch](https://meatechwatch.com/2025/09/16/egypts-mobile-wallet-transactions-surge-72-in-q2-2025-to-egp-943-4-billion/), [Arab Finance](https://arabfinance.com/en/news/newdetails/vodafone-egypt-h1-2025-revenue), [Ahram Gate](https://gate.ahram.org.eg/News/5356365.aspx) | Wallet payment option. Bawab and technician payouts. |
| **valU (EFG)** | FY2025 revenue EGP 5.6bn (+71%); GMV EGP 24.5bn; 23% market share; 873K+ active users (9M-2025); BNPL up to 60 months; 8,500+ stores | | [bnok24](https://www.bnok24.com/?p=253864), [Techpoint](https://techpoint.africa/news/egyptian-fintech-valu-h1-results/), [Menastartup Digest](https://menastartupdigest.com/?p=22434) | Instalments for big-ticket jobs (AC purchase and install, finishing, elevator modernisation). Referral fees. |
| **Other BNPL** | Shahry and valU lead; MNT-Halan; Sympl ("save now pay later"); Contact; Souhoola (no data found) | | [BusinessWire](https://secure.businesswire.com/news/home/20251201749447/en/) | Multi-lender marketplace for building capex (e.g. elevator replacement financed per flat) |

**Key insight.** The money already flows. Egyptians pay utilities through Fawry, Sahl and wallets, and pay building fees by InstaPay or cash to the union treasurer. The building app's Phase-1 "fee collection and expense transparency" feature puts it on the **building's own cash flow**. That is the best launch point for Phase-2 services, because the building fund is the buyer for common-area services.

---

## 6. Insurance, Moving, Furniture and Finishing

| Player | Facts | Source | Phase-2 role |
|---|---|---|---|
| **Amenli (insurtech)** | Founded 2020. FRA-licensed broker for medical, car, **home** and business cover. $1M (Oct 2023, Alter Global, QIC DVP) + $2.3M (Nov 2024, EBRD VC, YC follow-on). App ~12K installs (est.) | [Wamda 2024](https://www.wamda.com/en/2024/11/amenli-cashes-new-investment-2-3-million), [Wamda 2023](https://www.wamda.com/en/2023/10/amenli-raises-1-million-equity-funding-round), [AppGoblin](https://appgoblin.info/search/amenli) | **Zero-operations, high-margin referral.** Building insurance (fire, elevator liability, third party) and per-flat home insurance. Insurance penetration in Egypt is <1% of GDP (Alter Global quote, [Beinsure](https://beinsure.com/news/insurtech-amenli-secured-funding/)). Fawry issued 1.1M digital policies in 2025, which shows digital distribution works. |
| **Homzmart** | Furniture and home marketplace; ~$39–40M raised ($15M Series A 2021, $23M pre-Series B 2022); KSA = 25–30% of volume (2022). Spun off **Lifters** (Apr 2025) for bulky logistics. Android ~2.3M installs (est.) / 4.5K ratings | [Enterprise](https://enterpriseam.com/egypt/2022/08/02/homzmart-closes-usd-23-mn-pre-series-b-round/), [MENAbytes](https://www.menabytes.com/homzmart-lifters/), [AppGoblin](https://appgoblin.info/search/homzmart) | Affiliate partner. Lifters as a moving and bulky-delivery partner for move-ins and move-outs (the app knows when residents move). |
| **Winch** | App-based goods and furniture moving; ~EGP 40M/month moved (2019); sought ~$1M | [Enterprise 2019](https://enterprise.press/?p=84404) | Status NOT FOUND. Moving is an event-driven, low-frequency, high-ticket referral. |
| **Trella** | Freight marketplace (B2B), not household | [GSMA](https://www.gsma.com/mobilefordevelopment/?p=47126) | Not relevant |
| **Shatablee** | Digital interior design and finishing, 3D design in <30 min, ~90-day delivery, targets **gated-community owners**, $1.2M (Mar 2022) | [Egypt Today](https://www.egypttoday.com/Article/3/113669/Shatablee-raises-1-2M-to-disrupt-Egypt’s-traditional-design-build) | High-ticket lead-gen. New compounds have many unfinished units: 4.3M units "need finishing" (2017 census) ([Egypt Independent](https://egyptindependent.com/total-number-vacant-housing-units-egypt-12-8-mn-capmas/)). |
| **Social Buildingz** | Matching designers and finishing companies (2017) | [Egyptian Streets](https://egyptianstreets.com/?p=54113) | Same |

---

## 7. Facility Management (FM): the hidden B2B competitor and partner

| Player | Facts | Source |
|---|---|---|
| **Egypro FME** | 800 buildings, 3.5M m², 21 governorates, 14 offices, 1,500+ staff, internal technician academy, 100+ clients over 22 years. **No app or digital platform mentioned.** CEO says there is no reliable FM market data | [Amwal Al Ghad, Oct 2025](https://amwalalghad.com/2025/10/21/%D8%B4%D8%B1%D9%83%D8%A9-egypro-fme-%D8%AA%D8%AF%D9%8A%D8%B1-800-%D9%85%D8%A8%D9%86%D9%89-%D8%A8%D9%85%D8%B3%D8%A7%D8%AD%D8%A9-%D8%A5%D8%AC%D9%85%D8%A7%D9%84%D9%8A%D8%A9-3-5-%D9%85%D9%84/) |
| **EFS Egypt / EFS Misr** | Since 2011. Exclusive FM for Palm Hills developments. MoU for ~1,230 units at Living Yards (New Cairo) | [Gulf News](https://gulfnews.com/business/property/efs-picks-up-a-major-fm-contract-in-egypt-1.1444594), [Invest-Gate](https://invest-gate.me/news/living-yard-partners-with-efs-misr-for-its-projects-management-at-nac/) |
| **Eden FM (Hassan Allam)** | Full FM at Katameya Plaza: operations, housekeeping, pest control, gardening, security | [Hassan Allam](https://hassanallam.com/news/eden-facility-management-offers-a-full-spectrum-of-facility-management-services-designed-to-enhance-the-living-experience-at-katameya-plaza) |
| **FilKhedma × EFS** | FilKhedma published an "EFS – FilKhedma" app for Katameya Plaza (last updated Mar 2021, removed from the US App Store). This suggests a past attempt at white-label compound services | [AppGoblin](https://appgoblin.info/apps/com.filkhedma.efs.katameyaplaza) |

**Implication.** In large compounds, the developer or its FM company controls services and often has its own app. In the **~16M ordinary buildings** (2017 census) there is no FM firm at all, only the bawab plus an informal union (اتحاد الشاغلين). The founder's beachhead should be **mid-size urban buildings and small compounds without professional FM**. Offer FM firms a white-label channel in big compounds instead of competing with them.

---

## 8. Commission and Take-Rate Benchmarks

| Platform | Market | Take rate / model | Source |
|---|---|---|---|
| Khidmitty | Egypt | 20–25% of labour | [Gust](https://gust.com/companies/Khidmitty-s-startup-2/financials) |
| Sal7lyy | Egypt (Upper) | 30–50% of labour (self-reported) | [Gust](https://gust.com/companies/%D8%B5%D9%84%D8%AD%D9%84%D9%8A) |
| Osta | Egypt (Alex) | Technician commission + customer order fee | [Gust](https://gust.com/companies/osta0) |
| FilKhedma (2019) | Egypt | Charges customer per hour; pays technician salary + bonus | [StartupList](https://www.startuplist.africa/startups/filkhedma) |
| Talabat | MENA incl. Egypt | 14–15% overall, 17–18% restaurants (2025) | [FAB Securities](https://fabsresearch.bankfab.com/ResearchPortal/Download/Index/961) |
| Urban Company | India | ~26% (unverified post-IPO figure) | [IPO Market](https://www.ipomarket.in/news/urban-company-ipo-listing-performance) |
| Amenify | USA | Revenue share to property managers; e.g. ~$50K/yr for 300 units (marketing claim) | [Amenify](https://www.amenify.com/blog/best-industry-value-proptech-amenify) |
| MyGate | India | ~65–70% advertising [corrected]; smart locks 8–9%; SaaS | [SaaSRise](https://www.saasrise.com/deals/mygate-raises-225-crore-from-dharana-capital-72817b60-56dc-41fb-8149-9bffef4de1b1) |
| InstaPay | Egypt | 0.1% (EGP 0.5–20 cap) | [Egyptian Streets](https://egyptianstreets.com/2025/04/03/instapay-now-charging-transfer-fees) |
| Fawry bills | Egypt | EGP 1–5 per bill to subscriber (old) | [Amwal Al Ghad](https://en.amwalalghad.com/?p=26548) |

**ESTIMATE for the founder's Phase-2 pricing:**
- Handyman and repair: 15% customer-side service fee, or a 10–15% technician commission. Do not exceed ~20% total in Egypt, or technicians will take jobs offline.
- Cleaning subscriptions: 15–20% margin over cleaner pay.
- Building-level contracts (pest, tank, elevator AMC): 8–12% broker fee paid by the vendor, plus a SaaS fee.
- Insurance and BNPL: referral commission. Rates are NOT FOUND publicly and must be negotiated.
- Bills and utilities: ~0 margin. Habit and data feature.

---

## 9. Failures, Shutdowns and Lessons

| Case | What happened | Lesson for the building app | Source |
|---|---|---|---|
| **Homejoy (US, 2015)** | Shut down. The CEO called worker-classification lawsuits the "deciding factor" (her own account; a former employee and later analyses also cite costly expansion, Handy competition and leakage). Best cleaners left with clients (leakage). $19 first-clean discounts attracted non-repeat customers. Fast multi-city expansion | Don't buy users with discounts. Engineer anti-leakage. Expand building by building. | [TechCrunch](https://techcrunch.com/2015/07/31/why-homejoy-failed-and-the-future-of-the-on-demand-economy), [Wikipedia](https://en.wikipedia.org/wiki/Homejoy) |
| **FilKhedma (Egypt)** | 7 years, about US$1.2–1.25M raised [corrected: USD, not EUR], then sold to SweepSouth. iOS app not updated since Nov 2022. Reviews cite no-shows and poor coordination | Under-capitalised horizontal on-demand services do not reach escape velocity in Egypt. Quality control is the product. | Sources in §2 |
| **Taskty (Egypt)** | ~$140K raised. Last Android update Dec 2023 | Same | [AppGoblin](https://appgoblin.info/apps/com.tasktyapp.taskty) |
| **SweepSouth (Nigeria exit, 2022)** | Exited Nigeria citing economic pressures. Kept Egypt | FX and inflation shocks kill marketplace unit economics. Keep costs in EGP and lean. | [Nairametrics](https://nairametrics.com/2022/11/23/south-african-cleaning-services-startup-sweepsouth-quits-nigeria/) |
| **Capiter (Egypt B2B e-com)** | $33M Series A. Growth at all costs. Founders ousted in 2022. Permanently closed about 2 years later | Don't burn on growth before unit economics. The founder's zero-marketing constraint is protective here. | [Wamda](https://www.wamda.com/en/2022/09/repercussions-capiters-downfall), [LaunchBase](https://launchbaseafrica.com/2024/12/17/battered-by-funding-crisis-egyptian-startups-plot-comeback) |
| **MyGate (India)** | Ended free services in Feb 2023, made two layoff rounds, pivoted to ads plus SaaS. Revenue reached ~₹187 cr in FY25 (single secondary report) | "Free for dominance" works only if a monetization engine exists. Ads to verified residents are the most proven engine for community apps. | [Inc42](https://inc42.com/?p=471555), [SaaSRise](https://www.saasrise.com/deals/mygate-raises-225-crore-from-dharana-capital-72817b60-56dc-41fb-8149-9bffef4de1b1) |
| **Laverie, H2U, Jinni, Kheddma, Winch** | Funded or launched 2016–2021. No later news found (status NOT FOUND) | Single-vertical home apps struggle with frequency. Bundling inside a daily-use building app fixes acquisition. | §3 sources |

---

## 10. Customer Pain Points (verified quotes only)

I collected verbatim review quotes where I could verify them. **Google Play review text could not be fetched** (the page truncates). The Facebook, X and Reddit searches returned no Egypt-specific threads I could cite. **This section is thin and should be strengthened with manual scraping of Play Store reviews.**

| App | Quote (verbatim) | Date | Theme | Source |
|---|---|---|---|---|
| FilKhedma (iOS) | "when a service provider cancels at the last minute or simply fails to show up at the agreed time" | 5 Sep (year not shown) | No-show / reliability | [App Store EG](https://apps.apple.com/eg/app/filkhedma-home-services/id1473742608) |
| FilKhedma (iOS) | "Lousy customer service, appalling coordination of work internally." | 20/07/2024 | Operations | same |
| FilKhedma (iOS) | "They are liars, dishonest and unprofessional!Not recommended at all!!" | 5 Apr | Trust | same |
| FilKhedma (iOS) | "This is a company that has made my life easier." | 09/02/2021 | Positive | same |
| Fixawy (iOS) | "THe services are over priced the plumber cam for 2 hours" | 10/03/2018 | Price transparency | [App Store](https://apps.apple.com/app/id1071671875) |
| Fixawy (iOS) | "one was excellent while the other was bad" | 03/02/2021 | Inconsistent quality | same |
| Fixawy (iOS) | "Excellent app idea. Can't live without it" | 02/03/2020 | Positive | same |
| Breadfast (iOS) | "there's no other way of reaching you and it's very frustrating" | 01/08/2024 | Support access | [App Store EG](https://apps.apple.com/eg/app/id1288436997) |
| Breadfast (iOS) | "there is no one to contact or complain for." | 03/11/2021 | Support access | same |
| Quick Gas (iOS) | Overall 1.6★ on ~106 ratings | n/a | Reliability | search result summary |

**Synthesised pain map (ESTIMATE from the above plus category structure):**
1. **Reliability and no-shows.** Fix: SLA with automatic compensation credit, live technician tracking, "building technician" with a reputation inside the building.
2. **Price opacity and overcharging.** Fix: fixed-price menu (Khidhma-style), AI photo-based quote before the visit, materials pass-through with receipt photo.
3. **Inconsistent quality.** Fix: building-level ratings visible to neighbours, warranty (1 month is the market norm at FilKhedma and Sal7lyy; offer 3 months), re-do guarantee.
4. **Can't reach support.** Fix: WhatsApp-native support plus an AI agent with human escalation. This links to the founder's WhatsApp-bot idea.
5. **Trust and safety of strangers at home.** Fix: ID-verified technicians, bawab check-in or check-out logged in the app.

---

## 11. Category Scoring for a Building-Centric Intermediary

Scoring is 1–5, where 5 is best. **ESTIMATE.** The reasoning uses the frequency, price-point and structure evidence above.

| Category | Frequency per household | Avg ticket (EGP) | Margin potential | Building-level leverage (group/common area) | Leakage risk (5 = low) | Ops complexity (5 = easy) | **Total /30** | Priority |
|---|---|---|---|---|---|---|---|---|
| AC service and cleaning (seasonal campaign) | 1–2/yr per unit, many units | 450/unit | 4 | 5 (book whole building in one day) | 4 | 4 | **26** | ★ Launch |
| Pest control (building + flats) | 1–4/yr | 50–2,300 | 4 | 5 | 4 | 4 | **26** | ★ Launch |
| Water-tank cleaning, pumps, generators (B2B, building fund) | 1–2/yr per building | 1,000s+ | 4 | 5 | 5 | 3 | **26** | ★ Launch with Phase-1 fund feature |
| Plumbing and electrical handyman | 3–4/yr | 150–500 | 3 | 4 ("building technician") | 2 | 3 | **21** | Core, with anti-leakage design |
| Home cleaning (subscription) | weekly to monthly | ~160/h | 4 | 3 | 2 | 3 | **20** | Phase 2b |
| Elevator AMC, brokered | monthly contract | high | 4 | 5 | 5 | 2 | **22** | Phase 2b (needs vendor network) |
| Laundry pickup per building | weekly | 100–300 | 3 | 5 (one route per building) | 4 | 2 | **21** | Partner-run |
| Building and home insurance (Amenli etc.) | annual | 500–5,000 | 5 | 4 | 5 | 5 | **26** | ★ Referral, zero ops |
| BNPL for big-ticket (valU etc.) | rare | 10K+ | 4 | 3 | 5 | 5 | **23** | Referral |
| Utility bills and prepaid electricity (Sahl, Fawry) | monthly+ | 100s | 1 | 3 | 5 | 4 | **19** | Habit and data, not profit |
| Grocery and water group orders | weekly | 300–1,000 | 2 | 4 | 4 | 4 | **19** | Affiliate only |
| Gas cylinders | monthly (non-piped) | 225–275 + delivery | 1 | 3 | 3 | 3 | **14** | Skip or partner |
| Moving (Lifters, etc.) | rare (event) | 1,000s | 3 | 2 | 4 | 4 | **18** | Referral on move-in/move-out events |
| Finishing and renovation (Shatablee-like) | rare, huge ticket | 100K+ | 5 | 2 | 3 | 1 | **17** | Lead-gen only |
| Domestic staff, nanny, elderly care | ongoing | high | 3 | 2 | 2 | 1 | **13** | Later or partner (Hestia-type) |

**Top 5 for Phase 2 launch:** AC campaign, building pest control, tank and pump and generator maintenance from the building fund, insurance referral, and plumbing and electrical through "building technicians".

---

## 12. Strategic Recommendations for Phase 2 (synthesised from the evidence)

### 12.1 Partner vs build matrix

| Layer | Recommendation | Who |
|---|---|---|
| Payments and bills | **Integrate, never build** | Fawry or Paymob gateway; Sahl or Khales for bills; InstaPay payment links; Vodafone Cash payouts |
| Grocery, water, food | **Affiliate or group-buy** | Breadfast, Rabbit, Talabat (affiliate links, building group drops) |
| Insurance | **Referral** | Amenli (FRA-licensed broker); Fawry digital insurance |
| BNPL | **Referral or embedded** | valU, Shahry, MNT-Halan, Sympl |
| Furniture and moving | **Affiliate** | Homzmart, Lifters |
| Pest control, tank cleaning | **Curated vendor marketplace** (licensed SMEs) | SWF-type firms, local licensed operators |
| Handyman | **Own marketplace** with "building technician" programme | Recruit existing building technicians plus the bawab's network |
| Cleaning | **Own or partner** | Hestia, HLPR-type agencies at first |
| Big compounds | **White-label** | EFS, Eden, Egypro (sell them the resident app instead of competing) |

### 12.2 Anti-leakage toolkit (critical for Egypt)

1. **Warranty only through the app** (≥3 months, beating the 1-month market norm).
2. **Building-level pricing.** A pre-negotiated building rate is cheaper than what the technician would charge privately.
3. **Technician subscription tier.** Technicians pay a flat monthly fee for priority leads in "their" buildings instead of per-job commission. This removes the incentive to go offline. It is a common answer to Homejoy-type leakage; the approach is my synthesis.
4. **Payment through the building wallet.** Common-area jobs are paid from the union fund inside the app, with neighbour visibility.
5. **Public building reputation.** A technician's rating inside a building of 40 flats is worth more than one customer's WhatsApp contact.

### 12.3 Revenue scenarios (ESTIMATE)

Assumptions: average order value EGP 600 (mix of handyman, AC and pest); blended take 15%; building-level contract broker fee 10%; currency at an assumed EGP 48–50/USD.

| Scenario (Phase 2, year 1 after monetization) | Active households | Orders/household/yr | GMV (EGP) | Service revenue (EGP) | + Building contracts (EGP) | + Ads and referrals (EGP) | **Total (EGP)** | ≈ USD |
|---|---|---|---|---|---|---|---|---|
| Conservative | 50,000 | 2 | 60M | 9M | 2,000 buildings × 10K × 10% = 2M | 3M | **14M** | ~0.28M |
| Base | 200,000 | 3 | 360M | 54M | 8,000 × 15K × 10% = 12M | 15M | **81M** | ~1.6M |
| Aggressive | 600,000 | 4 | 1.44bn | 216M | 25,000 × 20K × 10% = 50M | 60M | **326M** | ~6.5M |

These numbers depend on Phase 1 reaching that household count organically. Other research files cover that.

### 12.4 Sequencing

1. **Phase 1 (free):** run building fees, expenses, maintenance tickets and the bawab inside the app. This creates the "building fund" buyer and a service-demand log (every ticket shows what services are needed).
2. **Phase 1.5:** "Approved vendors" directory per building, voted by residents. Free, used to recruit supply.
3. **Phase 2a:** seasonal campaigns (AC in April and May, pest in spring, tank cleaning twice a year) plus insurance referral.
4. **Phase 2b:** handyman marketplace with building technicians; cleaning subscriptions; laundry route partners.
5. **Phase 2c:** ads to verified residents (the MyGate lesson), elevator AMC brokerage, BNPL for building capex.

---

## 13. Gaps and items NOT FOUND (for follow-up)

- Google Play review texts for FilKhedma, Taskty and Fixawy (Play page truncated in the fetch tool). Manual scraping is recommended.
- Reddit, X and Facebook complaint threads specific to Egyptian home-service apps: none surfaced in searches.
- Current EGP pricing for elevator AMCs, water-tank cleaning, and freon recharge.
- Fawry, Sahl and Khales biller-API commercial terms for third-party apps.
- Commission rates paid by Amenli and valU to referral partners.
- Whether Justlife, Washmen or Urban Company have any plan to enter Egypt (no evidence found).
- Exact 2025 count of prepaid electricity meters (only partial: 1.7M installed during 2022; [Amwal Al Ghad](https://amwalalghad.com/iqi5)).
- Operating status of Laverie, H2U, Jinni, Kheddma, Winch, Khidmitty, Osta.
- The brief's names "Elmohandes", "Mrs. Clean", "Movers" and "Sallah" could not be matched to Egyptian home-services companies. "Sallah" is most likely Salahly/Sal7lyy.

---

## 14. Source List (main)

- Deep Market Insights, Egypt Home Services: https://deepmarketinsights.com/vista/insights/home-services-market/egypt
- Ken Research, Egypt FM: https://www.kenresearch.com/industry-reports/egypt-facility-management-market.md
- IMARC, Egypt FM: https://www.imarcgroup.com/egypt-facility-management-market
- Mordor, Egypt FM: https://www.mordorintelligence.com/industry-reports/egypt-facility-management-market
- Wamda, SweepSouth acquires FilKhedma: https://www.wamda.com/en/2021/12/sweepsouth-fully-acquires-filkhedma
- Daily News Egypt, FilKhedma 2019: https://www.dailynewsegypt.com/2019/10/01/filkhedma-new-app-provides-home-maintenance-services-through-1000-handyworkers/
- AppGoblin, FilKhedma: https://appgoblin.info/apps/com.filkhedma.customer
- App Store EG, FilKhedma: https://apps.apple.com/eg/app/filkhedma-home-services/id1473742608
- AppGoblin, Taskty: https://appgoblin.info/apps/com.tasktyapp.taskty
- App Store, Fixawy: https://apps.apple.com/app/id1071671875
- Enterprise, home maintenance roundup 2024: https://enterpriseam.com/egypt/2024/08/30/leave-home-maintenance-to-the-pros/
- Khidhma: https://www.khidhma.com/
- Gust, Khidmitty: https://gust.com/companies/Khidmitty-s-startup-2/financials
- Gust, Sal7lyy: https://gust.com/companies/%D8%B5%D9%84%D8%AD%D9%84%D9%8A
- Wamda, Laverie: https://www.wamda.com/en/2021/04/laverie-raises-figure-funding-round
- Egyptian Streets, Breadfast EBRD: https://egyptianstreets.com/2025/08/02/breadfast-attracts-ebrd-investment-of-10-million/
- Wamda, Rabbit KSA: https://www.wamda.com/en/2025/04/rabbit-enters-saudi-market-backed-major-regional-investors
- Talabat IR: https://ir.talabat.com/wp-content/uploads/2026/06/20260514_talabat-Investor-Presentation.pdf
- FAB Securities, Talabat: https://fabsresearch.bankfab.com/ResearchPortal/Download/Index/961
- Zawya, Fawry FY2025: https://www.zawya.com/en/press-release/companies-news/fawry-releases-fy2025-results-356861
- Wamda, Sahl: https://www.wamda.com/en/2024/06/egypt-sahl-closes-dual-rounds-6-million
- MEA Tech Watch, NTRA wallets: https://meatechwatch.com/2025/09/16/egypts-mobile-wallet-transactions-surge-72-in-q2-2025-to-egp-943-4-billion/
- Egyptian Streets, InstaPay fees: https://egyptianstreets.com/2025/04/03/instapay-now-charging-transfer-fees
- bnok24, valU FY2025: https://www.bnok24.com/?p=253864
- Wamda, Amenli: https://www.wamda.com/en/2024/11/amenli-cashes-new-investment-2-3-million
- Enterprise, Homzmart: https://enterpriseam.com/egypt/2022/08/02/homzmart-closes-usd-23-mn-pre-series-b-round/
- MENAbytes, Lifters: https://www.menabytes.com/homzmart-lifters/
- Egypt Today, Shatablee: https://www.egypttoday.com/Article/3/113669/Shatablee-raises-1-2M-to-disrupt-Egypt’s-traditional-design-build
- Amwal Al Ghad, Egypro FME: https://amwalalghad.com/2025/10/21/%D8%B4%D8%B1%D9%83%D8%A9-egypro-fme-%D8%AA%D8%AF%D9%8A%D8%B1-800-%D9%85%D8%A8%D9%86%D9%89-%D8%A8%D9%85%D8%B3%D8%A7%D8%AD%D8%A9-%D8%A5%D8%AC%D9%85%D8%A7%D9%84%D9%8A%D8%A9-3-5-%D9%85%D9%84/
- TechCrunch, Homejoy: https://techcrunch.com/2015/07/31/why-homejoy-failed-and-the-future-of-the-on-demand-economy
- Inc42, MyGate: https://inc42.com/?p=471555
- Amenify: https://www.amenify.com/blog/how-does-amenify-work-a-step-by-step-look-at-the-resident-services-app-changing-apartment-living
- Masrawy, gas cylinder price: https://www.masrawy.com/news/news_economy/details/2026/7/23/3022188/
- Masrawy, NFC electricity charging: https://www.masrawy.com/news/news_egypt/details/2025/1/22/2714129/
- Invest-Gate, CAPMAS census: https://invest-gate.me/news/egypts-capmas-reveals-latest-population-housing-census/
- Egypt Independent, vacant units: https://egyptindependent.com/total-number-vacant-housing-units-egypt-12-8-mn-capmas/

---

## Verification log

Adversarial re-check performed 2026-10-12 with fresh web searches and fetches. Claims are tagged inline as [corrected] or [unverified] where they changed.

| Claim | Verdict | Evidence URL |
|---|---|---|
| SweepSouth acquired 100% of FilKhedma in Dec 2021, price undisclosed | confirmed | https://www.naspers.com/news-insights/group-updates/2021/sweepsouth-acquires-egyptian-startup-filkhedma |
| FilKhedma raised "about €1.2m" in total | corrected (≈US$1.2–1.25M over 5 rounds; currency was wrong) | https://startuplist.africa/startup/filkhedma/fundings |
| FilKhedma Android 3.72★, ~1.4K ratings, ~178K installs (est.), updated Aug 2025 | confirmed (AppGoblin estimate) | https://appgoblin.info/apps/com.filkhedma.customer |
| Taskty 3.39★, 658 ratings, ~168K installs, last update Dec 2023 | confirmed (last update 11 Dec 2023) | https://appgoblin.info/apps/com.tasktyapp.taskty |
| Egypt home services USD 1.88bn (2025) → 5.11bn (2034), 11.58% CAGR; R&M USD 0.92bn | confirmed as published (single paywalled vendor estimate; low reliability) | https://deepmarketinsights.com/vista/insights/home-services-market/egypt |
| Fawry FY2025: revenue EGP 8.65bn, net profit EGP 2.89bn, throughput EGP 943.6bn, 24.2M myFawry downloads | confirmed | https://www.fawry.com/wp-content/uploads/2026/03/Fawry-Earnings-Presentation-4Q2025-Final.pdf |
| Fawry "54.8M active network customers" and "377K POS" | corrected (54.8M is a boilerplate monthly-user estimate; 377K reported as agents) | https://www.zawya.com/en/press-release/companies-news/fawry-releases-fy2025-results-356861 |
| InstaPay "12M+ users end-2024" | corrected (CBE: ~11.5M registered users, Nov–Dec 2024) | https://egyptianstreets.com/2024/11/19/central-bank-of-egypt-to-allow-gulf-remittances-via-instapay-by-years-end/ |
| InstaPay Q1-2025: 263M transactions, >EGP 1.2trn | confirmed (CBE Financial Stability report via Arab Finance) | https://www.zawya.com/en/economy/north-africa/egypt-instapay-turns-profitable-a-year-after-transfer-fee-rollout-rt18pyrt |
| InstaPay fee 0.1%, min EGP 0.50, max EGP 20, from 1 Apr 2025 | confirmed (one outlet says min EGP 1; majority say 0.50) | https://egyptianstreets.com/2025/04/03/instapay-now-charging-transfer-fees |
| NTRA Q2-2025: 46.3M active wallets, EGP 943.4bn; Vodafone Cash 55% wallets / 78% txns / 81% value | confirmed | https://www.tra.gov.eg/en/ntra-issues-q2-2025-report-on-the-usage-indicators-of-mobile-wallets-operated-by-telecom-companies/ |
| Breadfast $150M+ ARR (2024), ~1M orders/mo, 30+ FCs, $10M EBRD, ~$382–400M valuation | confirmed (ARR and orders are company-reported) | https://launchbaseafrica.com/2025/08/01/ebrd-puts-10m-into-breadfast-as-the-egyptian-grocery-startups-valuation-nears-400m/ |
| Rabbit: 1.4M customers in Egypt, profitable in Egypt (CEO claim) | confirmed as company claim | https://www.arabnews.com/node/2603775/amp |
| Rabbit "Saudi expansion Apr 2025" | corrected (Saudi launch early 2024 in Riyadh) | https://www.arabnews.com/node/2603775/amp |
| Talabat commission 14–15% overall, 17–18% restaurants | confirmed for group (not Egypt-specific); 4Q25 compressed ~0.9pp | https://fabsresearch.bankfab.com/ResearchPortal/Download/Index/961 |
| Talabat has the largest market share in Egypt | unverified (not re-checked independently) | https://enterpriseam.com/logistics/2025/11/11/talabat-flynas-saudi-ground-services-see-bottom-line-top-line-growth-in-3q-2025/ |
| MyGate ended free services, layoffs (Dec 2022 + Feb 2023), ~70% ad revenue | corrected (ads = 65–70%; layoffs confirmed) | https://inc42.com/?p=471555 |
| CAPMAS 2017: 16.18M buildings, 43.2M units, 12.8M vacant, 4.3M need finishing | confirmed | https://egyptindependent.com/total-number-vacant-housing-units-egypt-12-8-mn-capmas/ |
| Butane cylinder EGP 200 (Apr 2025) → 225 (Oct 2025) → 275 (Mar 2026) | confirmed (multiple 2026 reports; no newer official rise found as of Oct 2026) | https://www.masrawy.com/news/news_economy/details/2026/7/23/3022188/ |
| valU FY2025 revenue EGP 5.6bn (+71%), GMV EGP 24.5bn, 23% share | confirmed | https://decypha.com/en/news/details/Valu-closes-2025-with-81--higher-net-income--revenues-hit-EGP-5-6bn/21539339?L=EN |
| Sahl $6M seed + Series A (Jun 2024); 12M customers monthly, 15M households | confirmed (company claim for usage figures) | https://www.wamda.com/en/2024/06/egypt-sahl-closes-dual-rounds-6-million |
| Amenli $2.3M (Nov 2024, EBRD VC + YC) after $1M (Oct 2023) | confirmed | https://english.ahram.org.eg/News/535455.aspx |
| Homzmart ~$40M raised; Lifters launched Apr 2025 | confirmed (MENAbytes, 26 Apr 2025) | https://www.menabytes.com/homzmart-lifters/ |
| Egypro FME manages 800 buildings / 3.5M m² | confirmed as CEO self-report only | https://amwalalghad.com/2025/10/21/%D8%B4%D8%B1%D9%83%D8%A9-egypro-fme-%D8%AA%D8%AF%D9%8A%D8%B1-800-%D9%85%D8%A8%D9%86%D9%89-%D8%A8%D9%85%D8%B3%D8%A7%D8%AD%D8%A9-%D8%A5%D8%AC%D9%85%D8%A7%D9%84%D9%8A%D8%A9-3-5-%D9%85%D9%84/ |
| Homejoy: worker-classification lawsuits were the "deciding factor" | corrected (CEO's own account; contested by ex-employee and analysts) | https://www.entrepreneur.com/article/248579 |
