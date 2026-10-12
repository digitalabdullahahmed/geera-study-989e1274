# 08 — Egyptian Market Size & Digital Readiness (TAM / SAM / SOM)

**Research angle:** How big is the Egyptian opportunity for (a) a free, building/compound resident app (Amarati / Imarti / Saknna style) and (b) a later home-services marketplace that monetizes the installed base by acting as an intermediary?
**Date of research:** 2026-10-12
**Exchange rate used throughout:** **1 USD ≈ 50 EGP** (30rates showed 50.20 on 2026-08-28; 2026 range was ~49–55, peak 54.85 on 31-Mar-2026) — [30rates](https://30rates.com/usd-to-egp-today-forecast-dollar-to-egyptian-pound), [PoundSterlingLive](https://www.poundsterlinglive.com/history/USD-EGP-2026)
**Convention:** Every number has a source URL. Anything I calculated or assumed is labelled **ESTIMATE** with its reasoning. Where I could not find data, I say so.

---

## 0. Executive summary (the 12 numbers that matter)

| # | Metric | Value | Source / status |
|---|---|---|---|
| 1 | Households in Egypt (1 Jan 2025) | **26.5 M** (11.8 M urban, 14.7 M rural) | CAPMAS via [CairoScene](https://cairoscene.com/buzz/over-half-of-egyptian-households-live-in-rural-areas) |
| 2 | Domestic population | **~108.6–109 M** (CAPMAS, 2026) | [Ahram/CAPMAS](https://english.ahram.org.eg/News/575154.aspx), [Trading Economics](https://tradingeconomics.com/egypt/population/forecast) |
| 3 | Housing units (2017 census) | **42.97 M** total units; **22.97 M** ordinary residential units | [Ahram Gate](https://gate.ahram.org.eg/News/5240877.aspx), [Amwal Al Ghad](https://amwalalghad.com/ihtg) |
| 4 | Vacant + closed units (2017) | **12.5 M (29.1%)** | [Amwal Al Ghad](https://amwalalghad.com/ihtg) |
| 5 | Households living in an **apartment** | **75.7%** (census 10% microdata sample) → ≈ **20 M households** (ESTIMATE) | [ERF Data Portal](https://erfdataportal.com/index.php/catalog/248/variable/V2360) |
| 6 | Owner vs renter (2017) | **76% owned / 14% rented / 10% gifted**; Cairo renters **39%** | [Built Environment Observatory](https://marsadomran.info/en/2018/02/1410/) |
| 7 | Internet users (end-2025) | **98.2 M (82.7%)** | [DataReportal 2026](https://datareportal.com/reports/digital-2026-egypt) |
| 8 | Android share of mobile OS | **~83–91%** (Jun 2026 91.1%, Aug 88.0%, Sep 83.4%) [corrected] | [StatCounter](https://gs.statcounter.com/os-market-share/mobile/egypt) |
| 9 | Mobile-wallet accounts | **58.7 M** (Sep 2025) | CBE via [Arab Finance](https://arabfinance.com/ar/news/newdetails/ارتفاع-عدد-محافظ-الهواتف-المحمولة-إلى-أكثر-من-55-مليون-حساب-بنهاية-يونيو-2025) |
| 10 | InstaPay / IPN registered customers | **~22 M** (Q2 2026); 1.47 B txns worth EGP 4.33 T in the quarter | [Ahram Online](https://english.ahram.org.eg/News/577944.aspx) |
| 11 | Financial inclusion | **76.3%** of adults (Jun 2025), 53.8 M of 70.5 M adults | [Maspero/CBE](https://www.maspero.eg/economy/2025/09/03/887287/) |
| 12 | Our SAM (free app) | **≈ 7.5 M households / ≈ 650k buildings / ≈ 16 M users** | ESTIMATE (§7) |

**Bottom line**
- **Free app:** a realistic serviceable market is **~7.5 M urban apartment households in ~650k multi-unit buildings plus ~1,000+ compounds**. With zero marketing budget, a building-by-building viral loop can realistically reach **~35k buildings / ~450k households / ~1 M registered users by end of Year 3** (base case). The aggressive case is ~2.5 M users.
- **Marketplace:** the addressable spend on intermediated home services in the SAM is **~EGP 35–53 B/yr (≈ USD 0.7–1.06 B)**. At a 12–15% blended take rate the theoretical revenue pool is **EGP 4.2–8 B/yr**. The realistic Year-3 SOM is **~EGP 60–120 M revenue/yr (≈ USD 1.2–2.4 M)**.
- **The biggest money flow is not repairs. It is building fees.** Bawab, cleaning, elevator, and common-area electricity are paid monthly by almost every apartment household. Routing those payments through the app gives you payment volume, daily relevance, and the data to sell services. In the base case that is **≈ EGP 1.35 B/yr flowing through the app by Year 3** (≈ EGP 3.3 B in the aggressive case; ESTIMATE, §8.4).

---

## 1. Population & households

| Metric | Value | Date | Source |
|---|---|---|---|
| Domestic population | 107.5 M | Apr 2025 | [EgyptToday/CAPMAS](https://www.egypttoday.com/Article/1/139383/Egypt-s-Population-witness-500K-increase-in-5-months) |
| Domestic population | 108.6 M (start of 2026) | Jul 2026 report | [Ahram (CAPMAS)](https://english.ahram.org.eg/News/572647.aspx) |
| Domestic population | 109 M [unverified: the cited article has no population figure] | May 2026 | [Ahram](https://english.ahram.org.eg/News/575154.aspx) |
| Population (UN-based, DataReportal) | 119 M | Oct 2025 | [DataReportal 2026](https://datareportal.com/reports/digital-2026-egypt) |
| Households | **26.5 M** | 1 Jan 2025 | [CairoScene / CAPMAS](https://cairoscene.com/buzz/over-half-of-egyptian-households-live-in-rural-areas) |
| Urban households | 11.8 M (44.4%) | 1 Jan 2025 | same |
| Rural households | 14.7 M (55.6%) | 1 Jan 2025 | same |
| Age structure | 34.3% < 15; 26.8% 15–29; 35% 30–64; 3.9% 65+ | 2025 | same |
| Urbanisation | 43.5% urban | Oct 2025 | [DataReportal 2026](https://datareportal.com/reports/digital-2026-egypt) |
| Median age | 24.5 | Jan 2025 | [DataReportal 2025](https://datareportal.com/reports/digital-2025-egypt) |
| Cairo governorate | 10.4–10.5 M | 2025 | [cairo.gov.eg](https://cairo.gov.eg/en/Pages/Latestarticle.aspx?ArtID=8588) |
| Giza governorate | 9.8 M | 2025 | same |
| Alexandria governorate | 5.6 M | Apr 2025 | same |
| Greater Cairo (NPC projection) | > 23 M | 2025 | [Egypt Independent / NPC](https://egyptindependent.com/population-of-greater-cairo-tripled-since-1980-national-population-council/) |

**Note on the population gap (108.6 M vs 119 M).** CAPMAS counts the domestic resident population. DataReportal uses UN World Population Prospects, which differ in method. **For planning, use CAPMAS (≈109 M) and 26.5 M households.**

**Derived: average household size ≈ 107.5 M / 26.5 M ≈ 4.06 persons (ESTIMATE).** Adults (15+) = 65.7% of the population → **≈ 2.7 adults per household (ESTIMATE)**. The CBE counts **70.5 M adults** in its inclusion statistics ([Maspero](https://www.maspero.eg/economy/2025/09/03/887287/)).

> **Product implication:** each household holds roughly 2.7 adults, and most are smartphone/internet users (§4). The "every resident has an account" model therefore yields **~2–2.5 accounts per apartment** (ESTIMATE) instead of one account per unit. This roughly doubles the user count compared with competitors that register one owner per apartment.

---

## 2. Housing stock: buildings, units, vacancy, tenure

### 2.1 Buildings and units (2017 census — the latest full count)

| Metric | 2006 | 2017 | Source |
|---|---|---|---|
| Total buildings | 11.594 M | **16.185 M** (+39.5%) | [Amwal Al Ghad](https://amwalalghad.com/ihtg) |
| Ordinary residential buildings | 10.466 M | **13.466 M** (91.2% of buildings) | same |
| Work-only buildings | 531 k | 833 k | same |
| Total units (all uses) | 27.07 M | **42.97 M** | [Ahram Gate](https://gate.ahram.org.eg/News/5240877.aspx) |
| Ordinary residential units | — | **22.973 M** (52% of ordinary-building units) | [Amwal Al Ghad](https://amwalalghad.com/ihtg) |
| Old-rent units | 5.54 M (20%) [unverified: CAPMAS-cited press gives 15% for 2006] | **3.02 M (7%)** | [Ahram Gate](https://gate.ahram.org.eg/News/5240877.aspx) |

**Building condition (2017):** 75.2% need no repair, 14.7% need minor repair, 6.1% medium, 3.2% major, 0.8% demolition-due ([Amwal Al Ghad](https://amwalalghad.com/ihtg)). **That is ~3.4 M buildings that need some repair, which is direct demand for maintenance services.**

**Occupancy of completed residential buildings (2017):** 59.5% fully occupied, 22.1% partly occupied, 12.3% vacant, 4.2% under construction ([Amwal Al Ghad](https://amwalalghad.com/ihtg)).

### 2.2 Vacancy (2017)

| Category | Units | Share | Source |
|---|---|---|---|
| Vacant residential units (total) | 8.996 M | 20.9% of residential units | [Amwal Al Ghad](https://amwalalghad.com/ihtg) |
| — of which completed | 4.662 M | 10.8% | same |
| — of which unfinished | 4.334 M | 10.1% | same |
| Closed — family owns another home | 2.887 M | 6.7% | same |
| Closed — family lives abroad | 1.159 M | 2.7% | same |
| **Vacant + closed (all)** | **12.498 M** | **29.1% of all units** | same |

> **Product implication:** about 4 M units (2.9 M "second homes" plus 1.16 M "family abroad") are owned by people who do not live in them. That segment has a remote-owner need: someone has to pay the building fees, check the flat, fix leaks, and rent it out. **"Remote owner" is a monetizable persona** (paid inspections, key-holding, rent collection, cleaning before arrival). It is especially relevant for Egyptians abroad, who pay in hard currency.

### 2.3 Dwelling type — who lives in an apartment?

| Dwelling type (2017 census, 10% household sample) | Cases | % |
|---|---|---|
| **Apartment** | 1,979,476 | **75.7%** |
| House | 322,712 | 12.3% |
| Separate room(s) | 175,649 | 6.7% |
| Room(s) in a housing unit | 68,895 | 2.6% |
| One floor or more | 62,192 | 2.4% |
| Other | 5,657 | 0.2% |

Source: [ERF Data Portal — 2017 Census DWLTYP](https://erfdataportal.com/index.php/catalog/248/variable/V2360). ERF warns that microdata counts "cannot be interpreted as summary statistics" without weights, so treat 75.7% as indicative.

**ESTIMATE:** 26.5 M × 75.7% ≈ **20.1 M apartment households**. Many rural "apartments" sit in 2–4-unit family buildings with no shared management. This is why the SAM in §7 narrows to urban multi-unit buildings.

### 2.4 Tenure: owners vs renters (2017)

| Tenure | Households | Share | Source |
|---|---|---|---|
| Owned / bought / built / inherited | 17.8 M | **76%** | [BEO "State of Rent 2017"](https://marsadomran.info/en/2018/02/1410/) |
| Gifted | — | ~10% | same |
| Rented (total) | 3.3 M | **14%** | same |
| — Old rent | ~1.6 M | ~7% | same; [Ahram Gate](https://gate.ahram.org.eg/News/5240877.aspx) |
| — New rent | ~1.5 M | ~6.5% | same |
| Rent share in **Cairo** | — | **39%** (old rent 25.8%) | [BEO](https://marsadomran.info/en/2018/02/1410/) |

**Old-rent households by governorate (2017):** Cairo 670,857 (41%), Giza 308,091, Alexandria 213,147, Qalyubia 150,961. These four hold 82% ([Ahram Gate](https://gate.ahram.org.eg/News/5240877.aspx)).

**2025 regulatory shock:** Law 164/2025 (published 4 Aug 2025) ends old-rent contracts after a **7-year transition for residential units (to Aug 2032)**. Rents jump to 20× in prime areas (min EGP 1,000/month), 10× in middle areas (min EGP 400), and 10× in economic areas (min EGP 250), then rise 15% per year ([Egyptian Streets](https://egyptianstreets.com/2025/08/04/president-el-sisi-ratifies-amendments-ending-egypts-old-rent-arrangements/), [Egypt Independent](https://www.egyptindependent.com/egypt-mandates-15-increase-to-deregulate-old-rent-leases/)).

> **Product implications:**
> 1. Egypt is an **owner-occupier country (76%)**, so residents have long tenure and a strong incentive to maintain the building. That favours a building-community app.
> 2. In **Cairo, 39% are renters**. Your app needs separate **owner vs tenant roles**, which matches the "every resident has an account" idea.
> 3. The old-rent reform will create **~1.6 M landlord–tenant relationships that need rent recalculation, receipts, reminders, and possibly re-letting** over 2025–2032. That gives the app a **rent-collection/ledger feature** with a strong legal-change hook for virality, especially in downtown Cairo, Giza, and Alexandria.

### 2.5 New supply, new cities and compounds

| Metric | Value | Source |
|---|---|---|
| State housing executed/offered since 2014 (MHUC/NUCA) | ~1.15 M units (to Jun 2026) | [Akhbar El Yom](https://m.akhbarelyom.com/news/NewDetails/4844156/1/الإسكان-تنفيذ-وطرح-115-مليون-وحدة-سكنية-) |
| Broader state housing (all programs) | ~1.96 M executed/under way, 1.46 M completed | [Ahram Gate](https://gate.ahram.org.eg/News/5450774.aspx) |
| Social Housing Fund program | >790k delivered + 242k under construction; total program 1.72 M | [Hapi Journal (Jan 2026)](https://hapijournal.com/2026/01/13/مي-عبدالحميد-تنفيذ-1-72-مليون-وحدة-ضمن-برن/) |
| "Sakan Lekol El Masreyeen" (low income) | 642,610 completed; 188,532 under way | [Akhbar El Yom](https://m.akhbarelyom.com/news/NewDetails/4844156/1/الإسكان-تنفيذ-وطرح-115-مليون-وحدة-سكنية-) |
| JLL tracked modern residential stock, Greater Cairo | **~317,000 units** (Q3 2025); ~7,300–7,500 units delivered per quarter; +13,800 expected in Q4 2025 | [JLL Cairo Living Q3 2025](https://www.jll.com/content/dam/jllcom/en/us/documents/reports/research-reports/25-insights-cairo-living-market-dynamics-q3-2025.pdf) |
| Sale price growth YoY (Q3 2025) | 6th October +22.6%, New Cairo +18.5% | same |
| Rent growth YoY (Q3 2025) | 6th October +17.6%, New Cairo +16.9% | same |
| Gated communities in Greater Cairo | > 466 by 2010; ~500 by 2013 | Ibrahim et al. 2011; Metwally & Abdalla 2013, cited in [Benha Univ. publication](https://bu.edu.eg/staff/islamalsayed3-publications/31822) |
| Madinaty (TMG) | Planned for 600k people in 120k units (other source: 600k residents in 80k units) | [Aqarmap](https://aqarmap.com.eg/en/advice/talaat-mostafa-group/) |
| Al Rehab | Designed for ~120k residents | [Aqarmap](https://aqarmap.com.eg/en/advice/talaat-mostafa-group/) |
| New Administrative Capital residents | ~30k people, expected 50–60k by year-end (date of report unclear); 1,000 families in Jun 2024 | [Asharq Al-Awsat](https://english.aawsat.com/arab-world/5296623-egypt%E2%80%99s-new-administrative-capital-gains-official-momentum-residential-occupancy) |

**Not found:** an official 2025 count of compounds in Egypt, total compound units, or current population of each new city (New Cairo, 6th October, Sheikh Zayed). ECES published a July 2026 population-performance analysis of new cities ([ECES](https://eces.org.eg/wp-content/uploads/2026/07/ECONOMIC-LENS-Issue-20-Ar.pdf)), but the extract I retrieved had no figures.

**ESTIMATE: compounds today.** About 500 gated communities existed in Greater Cairo by 2013. Since then, delivery has run at ~25–30k "modern" units a year in Cairo alone (JLL), and state "gated" housing such as Sakan Masr, Dar Misr, and Jannah has been added (≈140k units in 2020 alone, per Reda et al. 2022 cited in the same review). **I estimate 1,000–1,500 gated compounds nationwide (Greater Cairo, Alexandria, North Coast, Red Sea), with roughly 600k–1 M units delivered.** Occupancy in many new-city compounds is low, so expect **~350–600k occupied compound households** (ESTIMATE, wide error bars).

> **Product implication:** compounds are few but concentrated. Each one is a single sales/onboarding unit with 300–20,000 households, an existing management company, and high spending power. **They are the best beachhead for monetization.** Ordinary city buildings (~650k) are the volume and dominance play.

---

## 3. Building governance: the "اتحاد الشاغلين" (occupants' union) market

- **Law 119/2008 (Unified Building Law), Part 4** governs occupants' unions. Art. 72 requires a union for buildings with **≥ 5 units**. A union **exists by force of law whether registered or not**, and every occupant, owner or tenant, is a member (Ministerial Decree 144/2009) ([Mobtada](https://www.mobtada.com/print/944602), [Youm7 Aug 2026](https://www.youm7.com/story/2026/8/3/%D9%82%D8%A7%D9%86%D9%88%D9%86-%D8%A7%D9%84%D8%A8%D9%86%D8%A7%D8%A1-%D9%8A%D9%86%D8%B8%D9%85-%D8%A5%D9%86%D8%B4%D8%A7%D8%A1-%D8%A7%D8%AA%D8%AD%D8%A7%D8%AF%D8%A7%D8%AA-%D8%A7%D9%84%D8%B4%D8%A7%D8%BA%D9%84%D9%8A%D9%86-%D9%81%D9%89-%D8%A7%D9%84%D8%B9%D9%82%D8%A7%D8%B1%D8%A7%D8%AA-%D9%88%D9%8A%D9%85%D9%86%D8%AD%D9%87%D8%A7-3/7499429)).
- Registration is handled at the district (حي) technology centres in Cairo and Giza ([Youm7](https://www.youm7.com/story/2023/2/4/%D8%A5%D8%AC%D8%B1%D8%A7%D8%A1%D8%A7%D8%AA-%D9%88%D9%85%D8%B3%D8%AA%D9%86%D8%AF%D8%A7%D8%AA-%D8%B7%D9%84%D8%A8-%D9%82%D9%8A%D8%AF-%D8%A7%D8%AA%D8%AD%D8%A7%D8%AF-%D8%B4%D8%A7%D8%BA%D9%84%D9%89-%D8%A7%D9%84%D8%B9%D9%82%D8%A7%D8%B1%D8%A7%D8%AA-%D9%81%D9%89-%D8%A7%D9%84%D8%A3%D8%AD%D9%8A%D8%A7%D8%A1-%D8%A7%D8%B9%D8%B1%D9%81/6058053)). Districts such as Nasr City, Maadi, and West Cairo have run union-activation initiatives ([El Watan](https://www.elwatannews.com/news/details/8193631)).
- The law lets the union earn income from advertising licences and mobile antennas on the roof to fund maintenance ([Youm7](https://www.youm7.com/story/2023/10/26/%D8%A7%D8%AA%D8%AD%D8%A7%D8%AF-%D8%A7%D9%84%D8%B4%D8%A7%D8%BA%D9%84%D9%8A%D9%86-%D9%8A%D8%AD%D9%85%D9%89-%D8%A7%D9%84%D8%B9%D9%82%D8%A7%D8%B1%D8%A7%D8%AA-%D9%85%D9%86-%D8%A7%D9%84%D8%B3%D9%82%D9%88%D8%B7-%D9%88%D9%8A%D8%AD%D9%82-%D9%84%D9%87-%D8%A7%D9%84%D8%AD%D8%B5%D9%88%D9%84-%D8%B9%D9%84%D9%89/6352079)).
- Former Speaker Ali Abdel Aal called for **obliging unions to contract specialised property-management companies** ([Youm7 2020](https://www.youm7.com/story/2020/3/9/عبد-العال-يجب-إلزام-اتحادات-الشاغلين-بالتعاقد-مع-شركات-مُتخصصة/4664251)). A proposed amendment would let the administrative authority **appoint a management company where no union exists** ([Mobtada](https://www.mobtada.com/print/944602)).
- **Not found:** the number of registered occupants' unions in Egypt. I searched in both Arabic and English and found no official figure.

> **Product implications:**
> - Treasurers and union heads keep the union's legal duties (accounts, general assembly, minutes, fees) on paper or in WhatsApp. **An app that produces law-compliant union records (members list, budget, minutes, votes, receipts) has a legal "reason to adopt".**
> - If the law moves toward mandatory professional management, **the app becomes the operating system for small property-management companies.** That is a B2B channel that brings hundreds of buildings per signup.

---

## 4. Digital readiness

### 4.1 Connectivity

| Metric | Value | Date | Source |
|---|---|---|---|
| Internet users | **98.2 M (82.7%)** | Oct/Dec 2025 | [DataReportal 2026](https://datareportal.com/reports/digital-2026-egypt) |
| Internet users | 96.3 M (81.9%) | Jan 2025 | [DataReportal 2025](https://datareportal.com/reports/digital-2025-egypt) |
| Cellular connections (GSMA) | 121 M (102% of pop.) | late 2025 | DataReportal 2026 |
| Mobile connections that are 3G/4G/5G | 95.4% | late 2025 | same |
| Mobile subscriptions (MCIT) | **126.91 M** | May 2026 | [Ahram / MCIT](https://english.ahram.org.eg/News/575154.aspx) |
| Mobile subscriptions per 100 inhabitants | 113.42 [corrected] | May 2026 | same |
| Active mobile broadband (voice+data) | **96.26 M** [corrected] (+4.05 M data-only) | May 2026 | same |
| Fixed broadband subscriptions | 13.13 M | May 2026 | same |
| Mobile internet users (IDC) | 92.6 M | Dec 2025 | [MEA Tech Watch](https://meatechwatch.com/?p=50695) |
| Household internet penetration (Household ICT survey) | 72.2% (male 79.3%, female 65.2%) [unverified: not in the cited article] | 2022/23 | [Ahram / MCIT](https://english.ahram.org.eg/News/575154.aspx) |
| Median mobile download speed | 56.45 Mbps | late 2025 | DataReportal 2026 |
| Median fixed download speed | 89.84 Mbps | late 2025 | same |
| Mobile OS share | **Android 83–91%, iOS 9–17%** [corrected] (Sep 2026: Android 83.4%, iOS 16.6%) | Jun–Sep 2026 | [StatCounter](https://gs.statcounter.com/os-market-share/mobile/egypt) |
| Smartphone shipments | Egypt was Africa's fastest-growing market (+21% YoY Q2 2025; +34% Q1 2025 in North Africa) | 2025 | [Business Today Egypt / Canalys](https://www.businesstodayegypt.com/amp/4/6653/Egypt-emerges-as-Africa’s-top-smartphone-market-as-region-defies) |

**Not found:** an official smartphone-ownership percentage for 2025/26 (GSMA's Egypt-specific figure is not public). **ESTIMATE:** with 96.3 M active mobile-broadband subscriptions (May 2026) [corrected] and 98 M internet users, adult smartphone ownership in **urban** Egypt is likely **> 90%**.

> **Product implications:** build **Android-first** (≈ 8.5–9 of 10 users; iOS share rose to ~17% in Sep 2026, so iOS cannot be an afterthought) [corrected]. Make the APK small, keep it working on low-end devices, and offer a PWA/web fallback, as Saknna does with its no-store install. 4G is near-universal and speeds are adequate, so media-rich features (photos of defects, voice notes) are fine.

### 4.2 Social & messaging platforms (ad-audience reach, not MAU)

| Platform | Ad reach | % of pop. | YoY change | Source |
|---|---|---|---|---|
| Facebook | **51.6 M** | 43.4% | +10.6% | [DataReportal 2026](https://datareportal.com/reports/digital-2026-egypt) |
| YouTube | 49.3 M | 41.5% | −2.8% | same |
| TikTok (18+) | **48.8 M** | — | **+25.2%** | same |
| Messenger | 37.0 M | 31.1% | +6.0% | same |
| Instagram | 21.7 M | 18.2% | +13.9% | same |
| LinkedIn (members) | 15.0 M | 12.6% | +25% | same |
| X | 4.64 M | 3.9% | −15.4% | same |
| **WhatsApp** | **No official figure.** Vendor estimate ~52 M users, ~76% of smartphone users (unverified) | — | — | [ChatDaddy blog](https://chatdaddy.tech/blog/whatsapp-business-api-egypt) |

Other WhatsApp evidence: a 2020 academic survey (n=400) found **98% of respondents use WhatsApp and 90% use it daily** ([SJOCS](https://sjocs.journals.ekb.eg/article_154770.html)). WhatsApp is detected on 87.9% of Egyptian websites that embed a messaging widget ([wmtips](https://www.wmtips.com/technologies/instant-messaging/country/eg)). Meta does not publish WhatsApp country numbers; DataReportal's Egypt report does not cover it.

> **Product implications:**
> - **WhatsApp is the incumbent.** Every Egyptian building already has a WhatsApp group run by the treasurer or bawab. The founder's "WhatsApp bot in the building group" idea attacks the competitor that actually matters, the group itself. Join it, don't fight it.
> - **TikTok (+25% YoY, 48.8 M adults) and Facebook (51.6 M)** are the zero-budget distribution channels. Facebook neighbourhood and compound groups are the main organic acquisition route (detailed in the marketing research file).

### 4.3 Payments readiness

| Metric | Value | Date | Source |
|---|---|---|---|
| Financial inclusion (adults with active account) | **76.3%** (53.8 M of 70.5 M) | Jun 2025 | [Maspero / CBE](https://www.maspero.eg/economy/2025/09/03/887287/) |
| Financial inclusion (secondary report) | 77.6% (54.7 M) | Dec 2025 | [Hapi Journal](https://hapijournal.com/2026/02/17/البنك-المركزي-77-6-معدل-الشمول-المالي-في-م/) |
| Women's inclusion | 70% | Jun 2025 | Maspero / CBE |
| Mobile-wallet accounts | 55.8 M (Jun 2025) → **58.7 M (Sep 2025)**; ~60 M wallets cited for 2025 | 2025 | [Arab Finance](https://arabfinance.com/ar/news/newdetails/ارتفاع-عدد-محافظ-الهواتف-المحمولة-إلى-أكثر-من-55-مليون-حساب-بنهاية-يونيو-2025), [Bankygate](https://www.bankygate.com/72177) |
| Wallet transactions | ~801 M txns, EGP 1.1 T in Q3 2025; FY Jul-24–Jun-25: 2.5 B txns, EGP 3.4 T | 2025 | same |
| Wallet market share (by count) | Vodafone Cash 53%, e& cash 23%, Orange Cash 20% | 2025 | NTRA via [Bankygate](https://www.bankygate.com/72177), [NTRA Q1-2025 report](https://www.tra.gov.eg/wp-content/uploads/2025/05/الجهاز-القومي-لتنظيم-الاتصالات-يصدر-تقرير-مؤشرات-استخدام-المحافظ-الإلكترونية-التابعة-لشركات-الاتصالات-للربع-الأول-لعام-2025-تقرير-1.pdf) |
| InstaPay / IPN registered customers | 11.5 M (Nov 2024) → **~22 M (Q2 2026)** | 2026 | [Ahram Online](https://english.ahram.org.eg/News/577944.aspx), [Sharikat Mubasher](https://www.sharikatmubasher.com/media-hub/news/21451621/egypt-to-enable-gulf-remittances-via-instapay-in-2-months) |
| IPN volume | 1.47 B txns, EGP 4.33 T in Q2 2026 | Q2 2026 | [Ahram Online](https://english.ahram.org.eg/News/577944.aspx) |
| Fawry FY2025 | Revenue EGP 8.65 B (+57%); processed value EGP 943.6 B; myFawry app 24.2 M downloads | FY2025 | [Zawya](https://www.zawya.com/en/press-release/companies-news/fawry-releases-fy2025-results-356861), [MEA Tech Watch](https://meatechwatch.com/?p=48097) |
| Fawry network | >300k service points; 54.1 M users (Q2 2025, last reported) | 2025 | [TechCabal](https://techcabal.com/2026/04/20/how-fawry-built-a-profitable-fintech/) |
| E-commerce cash-on-delivery share | ~45% of value (2024); 55–70% of shoppers prefer COD (single publisher) | 2024 | [P&S Intelligence](https://www.psmarketresearch.com/market-analysis/egypt-e-commerce-market) |

> **Product implications:**
> - **InstaPay plus wallets are now mainstream** (22 M IPN users, ~59 M wallet accounts). Collecting building fees by **InstaPay link / Vodafone Cash / Fawry reference** is realistic today. Saknna already accepts InstaPay, Vodafone Cash, and bank transfer ([saknna.com](https://saknna.com)).
> - Cash is still large. The app must **record cash payments to the bawab or treasurer** (digital receipt for cash) and should not force digital payment on day one.

---

## 5. Household spending capacity

### 5.1 Household Income, Expenditure & Consumption Survey (HIECS)

| Metric | Value | Survey round | Source |
|---|---|---|---|
| Mean annual household expenditure | **EGP 72,396** | 2021 (HIECS 2021/22 microdata, n=12,463) | [CAPMAS census-info](https://censusinfo.capmas.gov.eg/metadata-en-v4.2/index.php/catalog/747/datafile/F34/V6142) |
| Mean annual "housing & utilities" spend | EGP 16,880 (incl. imputed rent, water, electricity, gas) | 2021/22 | [ERF](https://erfdataportal.com/index.php/catalog/309/variable/V1606) |
| Housing & utilities share | ≈ 23% (ratio of the two means; ESTIMATE) | 2021/22 | derived |
| Housing & supplies, published | EGP 11.9k/yr; 19.2% of spend (urban 20.4%) | 2019/20 | [Amwal Al Ghad / CAPMAS](https://amwalalghad.com/atkm) |

**Inflation adjustment (ESTIMATE):** Egyptian CPI has risen sharply since 2021 (urban inflation peaked above 30% in 2023; it was still **14.5% urban / 12.7% national in Aug 2026** — [Ahram](https://english.ahram.org.eg/News/576399.aspx), [Enterprise](https://enterpriseam.com/egypt/2026/09/13/urban-inflation-unexpectedly-slowed-to-14-5-in-august/)). I assume a cumulative **~2.5–2.8× price level since 2021**. On that basis the **mean household now spends ~EGP 180–200k/yr**, and urban households spend more (ESTIMATE).

**Wages context:** private-sector minimum wage EGP 7,000/month since Mar 2025. A rise to EGP 8,000 from Jul 2026 was announced, though sources disagree on whether it covers the private sector ([Egyptian Streets](https://egyptianstreets.com/2026/04/02/egypt-raises-minimum-wage-to-8000-egp-from-july-2026/), [Trading Economics](https://tradingeconomics.com/egypt/minimum-wages)).

### 5.2 Typical building & compound fees

Good public price data is scarce. The table lists what I found, with ages flagged, and my 2026 estimates.

| Item | Evidence found | 2026 working assumption (ESTIMATE) |
|---|---|---|
| Monthly building maintenance share (ordinary city building) | ~EGP 200/month per flat in a 10-flat building; some buildings collect up to EGP 500 (forum, **2021**) — [Egyptian Talks](https://www.egyptiantalks.org/invb/topic/165829-%D9%87%D9%84-%D8%AF%D9%81%D8%B9%D8%AA-%D9%85%D8%B3%D8%AA%D8%AD%D9%82%D8%A7%D8%AA-%D8%B5%D9%8A%D8%A7%D9%86%D8%A9-%D8%A7%D9%84%D8%B9%D9%85%D8%A7%D8%B1%D8%A9-%D8%9F/) | **EGP 400–1,200/month** per flat (×2–2.5 for inflation; mid-case **EGP 500**) |
| Bawab (doorman) pay | Abbasia residential building ad: EGP 6,000–7,000 basic + meals + housing ([Forasna](https://forasna.com/job/p/%D8%A8%D9%88%D8%A7%D8%A8-%D8%B9%D9%85%D8%A7%D8%B1%D8%A9-%D8%B3%D9%83%D9%86%D9%8A%D8%A9-%D9%85%D8%AC%D9%85%D9%88%D8%B9%D8%A9-6-%D8%A7%D9%83%D8%AA%D9%88%D8%A8%D8%B1-%D9%84%D9%84%D8%A7%D8%AF%D9%88%D8%A7%D8%AA-%D8%A7%D9%84%D9%85%D9%86%D8%B2%D9%84%D9%8A%D8%A9-%D9%85%D8%B5%D8%B1-%D8%A7%D9%84%D9%82%D8%A7%D9%87%D8%B1%D8%A9-441071)); a New Cairo security job from EGP 11,000 ([Dubizzle](https://www.dubizzle.com.eg/jobs/guards-security/q-new-cairo/)); a 2023 "bawab + family for EGP 24,000" villa ad went viral as unusually high ([Egypt Telegraph](https://www.egypttelegraph.com/article/4361/براتب-24-ألف-إعلان-عن-وظيفة-بواب)); many doormen get only a room plus tips ([Ahram Gate, May 2026](https://gate.ahram.org.eg/News/5608267.aspx)) | EGP 3,000–8,000/month per building, plus tips |
| Elevator | New 4–6-stop residential elevator EGP 180k–350k ([Hi-Lift blog, Dec 2025](https://www.egyptelevator.com/2025/12/Elevator%20installation%20cost.html?m=1)). **No public EGP monthly maintenance-contract price found.** | Maintenance contract EGP 1,000–3,000/month per elevator |
| Compound maintenance deposit | **8–10% of unit price** at handover is typical; some developers 4–10% ([Mudir](https://mudirapp.com/blog/%D9%83%D9%85%D8%A8%D9%88%D9%86%D8%AF%D8%A7%D8%AA-%D8%A7%D9%84%D8%B3%D8%A7%D8%AD%D9%84-%D8%A7%D9%84%D8%B4%D9%85%D8%A7%D9%84%D9%8A), [El Mohamy](https://elmo7amy.tv/%D9%88%D8%AF%D9%8A%D8%B9%D8%A9-%D8%A7%D9%84%D8%B5%D9%8A%D8%A7%D9%86%D8%A9/)); social housing 3–5% | — |
| State compound example | Jannah 2 (Sheikh Zayed): deposit ~EGP 100k per flat; residents complain that interest does not cover service contracts (Aug 2024) ([Egypt Telegraph](https://www.egypttelegraph.com/article/69216/)) | Deposit interest is not enough, so annual top-up fees ("فروق الصيانة") follow |
| Compound annual maintenance per m² | Rehab ~EGP 53/m², SODIC ~EGP 71/m² (after 10% rise, **~2021**) ([Dostor](https://www.dostor.org/3407360)); broker sites cite EGP 30–60/m² | **EGP 100–200/m²/yr** → a 150 m² unit pays **EGP 15k–30k/yr** |
| Compound conflict | Rehab residents accused the city authority of "إتاوات" and water cut-offs over maintenance differences ([Ahram Gate](https://gate.ahram.org.eg/News/1231089.aspx), [El Watan](https://www.elwatannews.com/news/details/1540532)) | Transparency of fees is a pain point → feature |

### 5.3 Home-service price points

**Little sourced 2025/26 EGP pricing is public.** Filkhedma does not publish prices on its homepage ([filkhedma.com](https://www.filkhedma.com/)). Expatistan lists hourly cleaning help in Cairo at **~EGP 161/hour** (6 data points, Jun 2025; low confidence) ([Expatistan](https://expatistan.com/price/cleaning-help/cairo/USD)).

**Working assumptions (ESTIMATE, Greater Cairo middle class, 2026). Validate with 30–50 calls to technicians before launch.**

| Service | Typical ticket (EGP) | Frequency / household / yr |
|---|---|---|
| Plumber / electrician visit + small job | 300–1,000 (+ parts) | 2–4 |
| AC cleaning / gas refill | 400–1,500 per unit | 1–2 (×1–3 units) |
| Deep cleaning (apartment) | 1,500–4,000 | 1–3 |
| Hourly cleaning | ~150–250/hour | variable |
| Pest control | 500–1,500 | 1–2 |
| Water-filter cartridge change | 500–1,500 | 1–2 |
| Appliance repair (washer, fridge) | 500–2,500 | 0.5–1 |
| Painting / renovation (project) | 10k–200k | 0.1–0.2 |
| Moving | 2,000–8,000 | 0.1 |

---

## 6. Third-party market sizes (top-down, for triangulation)

**Use with caution.** These are commercial research publishers with undisclosed methods, and their figures conflict.

| Market | Size | Growth | Source |
|---|---|---|---|
| Egypt facility management | USD 2.25 B (2024) → 3.6 B (2032) | 6.3% CAGR | [Verified Market Research](https://www.verifiedmarketresearch.com/product/egypt-facility-management-market/) |
| Egypt facility management | USD 2.4 B (2025) → 4.2 B (2034) | 6.1% | [IMARC](https://www.imarcgroup.com/egypt-facility-management-market) |
| Egypt facility management | USD 2.6 B (2025) → 4.6 B (2032) | 8.6% | [Ken Research](https://www.kenresearch.com/industry-reports/egypt-facility-management-market.md) |
| Egypt facility management (broad scope) | USD 7.2 B (2024) / 7.0 B (2025) | 8.5–11% | Data Bridge / Mordor ([summary](https://www.databridgemarketresearch.com/nucleus/egypt-facility-management-market)) |
| **Egypt home services** | **USD 1.88 B (2025) → 5.11 B (2034)**; repair & maintenance is the largest category (~USD 0.92 B) | ~11.7% CAGR (implied) | [Deep Market Insights](https://deepmarketinsights.com/vista/insights/home-services-market/egypt) |
| Egypt cleaning services (all, incl. commercial) | USD 6.22 B (2025) → 11.03 B (2034) | 6.6% | [Deep Market Insights](https://deepmarketinsights.com/vista/insights/cleaning-services-market/egypt) |
| Middle East & Africa home services | USD 21.44 B (2025) → 57.14 B (2034) | — | [Deep Market Insights](https://deepmarketinsights.com/vista/insights/home-services-market/middle-east-and-africa) |
| Egypt residential construction | USD 18.8 B (2025) | — | [Mordor](https://www.mordorintelligence.com/industry-reports/egypt-residential-construction-market) |
| Egypt e-commerce | USD 9.1 B (2024, P&S); USD 10.2 B (2025) → 19.3 B (2030) | ~10–14% | [P&S](https://www.psmarketresearch.com/market-analysis/egypt-e-commerce-market), [MEA Tech Watch](https://meatechwatch.com/?p=31581) |

The FM market is mostly **commercial, institutional, and industrial**. IMARC's segmentation has no residential line, so FM figures overstate what a residential app can reach. The **USD 1.9 B "home services" figure (≈ EGP 94 B)** is the best top-down anchor for the marketplace TAM, and it agrees with the bottom-up model in §8.

---

## 7. TAM / SAM / SOM — (a) the FREE app (buildings, households, users)

### 7.1 Definitions
- **TAM:** every Egyptian household living in a multi-household residential building or compound. These households share walls, an entrance, utilities, and therefore costs.
- **SAM:** households in **urban and new-city multi-unit buildings (≥ 5 units, the legal threshold for an occupants' union) and compounds**, in governorates where smartphone, internet, and payments readiness is high and services can be delivered. For phase 1 that means Greater Cairo (Cairo, Giza, Qalyubia urban, new cities), Alexandria, Canal cities, Delta capitals, and Red Sea/North Coast compounds.
- **SOM:** what we can realistically capture in 36 months with **zero paid marketing**, using building-level viral loops (one champion invites the building).

### 7.2 Assumptions (all ESTIMATES unless sourced)

| ID | Assumption | Value | Reasoning |
|---|---|---|---|
| A1 | Households | 26.5 M | CAPMAS (sourced) |
| A2 | Share living in apartments | 75.7% | ERF census microdata (sourced, unweighted) |
| A3 | Share of apartment households in buildings with shared management needs (≥ ~4–5 units) | 65% | Many rural "apartments" are in 2–3-unit family houses; urban stock is mostly 5–30-unit walk-ups and towers |
| A4 | Urban households | 11.8 M | CAPMAS (sourced) |
| A5 | Share of urban households in ≥ 5-unit buildings or compounds | 65% | Urban Cairo/Giza/Alexandria are dominated by multi-storey blocks; informal areas (ashwa'iyyat) have many 4–8-floor family blocks |
| A6 | Units per multi-unit building (occupied) | 12 | Typical 5–6-floor block with 2–3 flats per floor; occupancy discounted per §2.1 (59.5% fully occupied, 22.1% partially) |
| A7 | Smartphone-using adults per household | 2.2 | 2.7 adults/household × ~82% internet penetration (higher in cities) |
| A8 | Compounds (households occupied) | 350k–600k | §2.5 |
| A9 | Other urban-like apartment households outside SAM (secondary cities, Upper Egypt capitals) | added to TAM only | — |

### 7.3 Results

| Tier | Households | Buildings (≈ households ÷ 12) | Users (× 2.2) | How computed |
|---|---|---|---|---|
| **TAM** | **≈ 13.0 M** | **≈ 1.1 M** multi-unit buildings + ~1,000–1,500 compounds | **≈ 28.6 M** | 26.5 M × 75.7% × 65% |
| **SAM** | **≈ 7.5 M** | **≈ 640k** buildings + ~1,000 compounds | **≈ 16.5 M** | 11.8 M urban × 65% (=7.7 M), minus ~0.2 M for non-target urban areas, plus compounds counted inside |
| **SOM — Year 1** | 25k–60k | 2k–5k | 55k–130k | §7.4 |
| **SOM — Year 2** | 120k–250k | 10k–20k | 0.26–0.55 M | §7.4 |
| **SOM — Year 3 (base)** | **≈ 450k** | **≈ 35k** (+ 40–80 compounds) | **≈ 1.0 M** | §7.4 |
| SOM — Year 3 (aggressive) | ≈ 1.1 M | ≈ 85k | ≈ 2.4 M | — |

```
FREE-APP FUNNEL (households)
TAM  ██████████████████████████████████████████████████  13.0 M
SAM  █████████████████████████████                        7.5 M
Y3   ██                                                   0.45 M (base) → 1.1 M (aggressive)
```

### 7.4 How the SOM was derived (bottom-up, zero-budget growth)

Unit of acquisition is the **building, not the person**. One "champion" (treasurer, union head, or bawab) onboards a building, then residents invite neighbours.

| Driver | Conservative | Base | Aggressive | Reasoning |
|---|---|---|---|---|
| Seed buildings (founder network, 3 districts, field reps of 1–2 people) | 300 | 500 | 1,000 | First 6 months, hand-held onboarding |
| Building-to-building K-factor per quarter (a resident's other building, family, compound-wide spread, treasurer referrals) | 0.25 | 0.35 | 0.5 | Comparable products spread through families: Egyptians often own or rent in two buildings (2.9 M "second home" units) |
| Compound deals (B2B, each 300–5,000 households) | 10 by Y3 | 40 | 80 | Sold via management companies |
| Activation (residents registered per building) | 50% | 65% | 80% | "Every resident has an account" requires a reason: fees and receipts, gate/visitors, alerts |
| Avg occupied units per building | 12 | 12 | 12 | A6 |

**Benchmarks:**
- **MyGate (India):** >27,000 communities and **5.7 M homes** (June 2026; self-reported, and MyGate's own 2026 blog says "4 M+ homes" — treat as an upper bound) after ~10 years, starting from 3.5 M homes / 25k societies in 2023 ([Entrepreneur India](https://india.entrepreneur.com/business-news/mygate-bags-inr-225-crore-from-dharana-capital), [Wikipedia](https://en.wikipedia.org/wiki/MyGate)). MyGate raised large VC rounds, including $56 M Series B ([Inc42](https://inc42.com/?p=174218)), so zero-budget Egypt should grow more slowly per year.
- **Saknna (Egypt/Gulf):** claims **"500+" buildings** on its site and charges **EGP 450/month (≤ 5 units), 900 (≤ 10), 2,200 (≤ 20), 7,500 (compounds)** ([saknna.com](https://saknna.com)). Paid SaaS with a 14-day trial grows slowly. **A free model can outgrow it quickly.**
- **Amarati / Imarti:** Play Store and AppBrain pages could not be fetched by my tools (403/truncated), so download counts are **not verified here**. See the competitor research files.

**Year-3 base check:** 35k buildings ÷ 640k SAM buildings ≈ **5.5% SAM building penetration**, and 450k ÷ 7.5 M ≈ **6% of SAM households**. That is ambitious but plausible for a free product with a WhatsApp-native growth loop. MyGate's India penetration of gated societies is in the same order of magnitude after a decade, with paid marketing.

> **Downloads forecast (ESTIMATE):** downloads ≈ users × 1.3 (reinstalls, multi-device, churned trials) → **Y1 ~0.1–0.15 M, Y2 ~0.4–0.6 M, Y3 ~1.3 M (base) / ~3 M (aggressive)**. If the WhatsApp bot lets passive residents interact without installing, "users" can exceed installs. Track **"reachable residents"** (bot + app) as the north-star metric, not downloads.

---

## 8. TAM / SAM / SOM — (b) the SERVICES MARKETPLACE (EGP & USD)

### 8.1 Spend categories the app can intermediate

| Bucket | Example services | Who pays | Notes |
|---|---|---|---|
| B1. **Building shared costs** | bawab salary, stair cleaning, elevator contract, common electricity & water pump, garbage, security, small repairs | Union/treasurer collects monthly from each flat | Recurring, near-universal, low margin. **Payments and float lever.** |
| B2. **In-home repair & maintenance** | plumbing, electrical, carpentry, AC, appliances, water heaters, aluminium | Household | Core "فني" marketplace (Filkhedma-like) |
| B3. **Cleaning & care** | hourly/deep cleaning, sofa/carpet cleaning, pest control | Household | Recurring |
| B4. **Utilities & consumables** | gas cylinders, water filters, drinking water, internet/mobile top-ups, electricity prepaid cards | Household | Payment/commission model (Fawry-like) |
| B5. **Bigger projects** | finishing, painting, renovation, elevator installation/modernisation, solar | Household or union | High ticket, lead-gen fees |
| B6. **Real-estate transactions** | rentals, resale, furnished short-stay, remote-owner services | Owner/tenant | Bawabs already act as informal brokers ([Ahram Gate, May 2026](https://gate.ahram.org.eg/News/5608267.aspx)) |
| B7. **Compound services** | annual maintenance fees, club, gate passes, landscaping | Owner → developer/FM | B2B SaaS + payments |

### 8.2 Per-household annual addressable spend (ESTIMATE, 2026 EGP)

| Bucket | SAM city-building household | Compound household | Reasoning |
|---|---|---|---|
| B1 Building shared costs | 6,000 (EGP 500/month) | 20,000 (≈150 m² × EGP 130) | §5.2 |
| B2 Repairs & maintenance | 3,000 | 6,000 | 3 visits × ~EGP 700 + parts; compounds more |
| B3 Cleaning & pest | 1,500 | 6,000 | Middle class: occasional deep clean; compounds: regular help |
| B4 Utilities & consumables (intermediable portion) | 1,500 | 2,500 | Filters, gas, top-ups. Excludes the electricity bill itself |
| B5 Projects (annualised) | 2,500 | 8,000 | ~EGP 20–60k once every ~10–15 years, plus finishing for new units |
| **Total (excl. B6)** | **≈ 14,500** | **≈ 42,500** | — |
| of which **marketplace-able** (B2+B3+B4+B5) | **≈ 8,500** | **≈ 22,500** | B1 is payments/SaaS, not a marketplace |

Cross-check: 14,500 ≈ **7–8% of an estimated EGP 180–200k annual household spend** (§5.1). That is consistent with the HIECS housing share (~19–23%, which also includes rent and utility bills). ✔︎

### 8.3 Market sizing

| Tier | Households | Total spend incl. B1 | Marketplace-able spend (B2–B5) | USD (marketplace-able) |
|---|---|---|---|---|
| **TAM** (13.0 M HH; 12.5 M city @ 14.5k ×0.8 for lower-income areas, 0.5 M compound @ 42.5k) | 13.0 M | ≈ EGP 166 B | ≈ EGP 96 B | **≈ USD 1.9 B** |
| **SAM** (7.5 M HH; 7.0 M city @ 14.5k, 0.5 M compound @ 42.5k) | 7.5 M | ≈ EGP 123 B | ≈ EGP 71 B | ≈ USD 1.4 B |
| **SAM, realistically intermediable** (online share 50–75% of marketplace-able; the rest stays with the neighbourhood "صنايعي" paid cash) | 7.5 M | — | **≈ EGP 35–53 B** | **≈ USD 0.7–1.06 B** |
| Revenue pool at 12–15% blended take | — | — | **≈ EGP 4.2–8 B/yr** | ≈ USD 85–160 M |

**Triangulation:** the bottom-up TAM of ≈ USD 1.9 B for marketplace-able home services matches **Deep Market Insights' USD 1.88 B (2025) Egypt home-services estimate** ([source](https://deepmarketinsights.com/vista/insights/home-services-market/egypt)). Two independent methods give the same order of magnitude. ✔︎

### 8.4 SOM — marketplace revenue by Year 3 (ESTIMATE)

| Driver | Conservative | **Base** | Aggressive |
|---|---|---|---|
| Households on platform (Y3) | 250k | **450k** | 1.1 M |
| % households transacting ≥ 1×/yr via app | 15% | **25%** | 35% |
| Orders per transacting household / yr | 3 | **4** | 5 |
| Average order value (EGP) | 700 | **800** | 900 |
| **Marketplace GMV** | EGP 79 M | **EGP 360 M** | EGP 1.73 B |
| Blended take rate | 12% | **15%** | 18% |
| **Marketplace revenue** | EGP 9.5 M | **EGP 54 M** | EGP 312 M |
| **Building-fee payment volume** through the app (B1; 50% of platform HH × EGP 6,000) | EGP 0.75 B | **EGP 1.35 B** | EGP 3.3 B |
| — convenience/processing margin 0.75% (net of PSP cost) | EGP 5.6 M | **EGP 10 M** | EGP 25 M |
| Compound/management SaaS (paid tier; Saknna-like pricing EGP 2–7.5k/month) | 20 × EGP 4k × 12 = EGP 1 M | 60 × 5k × 12 = **EGP 3.6 M** | 150 × 6k × 12 = EGP 11 M |
| Sponsored placements / local ads / B2B leads (finishing, real estate) | EGP 2 M | **EGP 10 M** | EGP 40 M |
| **Total revenue run-rate, Year 3** | **≈ EGP 18 M (≈ USD 0.36 M)** | **≈ EGP 78 M (≈ USD 1.6 M)** | **≈ EGP 390 M (≈ USD 7.8 M)** |

> The headline in §0 (≈ EGP 60–120 M) is the base case ± one band. Note how much more **payment volume** B1 creates than marketplace GMV. Collecting the monthly building fees inside the app is what makes people **open it every month**, and that is how a free app gets distribution it can sell services into later.

### 8.5 Longer-run upside (Year 5, ESTIMATE)
If penetration reaches **15% of SAM households (≈ 1.1 M HH)** and marketplace capture reaches **5% of that cohort's marketplace-able spend** (1.1 M × EGP 9,300 avg ≈ EGP 10 B → 5% ≈ EGP 0.5 B GMV), revenue would be **≈ EGP 75–100 M from marketplace + ≈ EGP 50 M from payments/SaaS/ads ≈ EGP 125–150 M/yr (≈ USD 2.5–3 M)** in today's money. Prices inflate ~12–15%/yr in EGP, so nominal EGP figures will be higher. **Adding real-estate transactions (B6)**, such as replacing the bawab's informal brokerage with in-building rental listings, and **remote-owner services for the ~1.16 M "family abroad" units paid in USD** are the two biggest upside levers.

---

## 9. Competitive capacity: can we win this market?

| Factor | Evidence | Read-out |
|---|---|---|
| Market fragmentation | No dominant building app found. Saknna claims "500+" buildings ([saknna.com](https://saknna.com)) vs ≈ 640k SAM buildings → **< 0.1% share** | **Wide open.** No incumbent above 1% of buildings (competitor download data still to be verified in the competitor files) |
| Real incumbent | WhatsApp groups + paper notebooks + bawab | Must be **WhatsApp-native** (bot inside the group) rather than replacing WhatsApp |
| Willingness to pay for SaaS | Saknna charges EGP 450–7,500/month | Small buildings may pay little. **Free for residents is right**; charge compounds and management firms |
| Service-marketplace players | Filkhedma (since 2014, several funding rounds — [Wamda](https://www.wamda.com/en/2017/09/egyptian-home-services-platform-filkhedma-closed-investment-round)), Fixawy (Alexandria, 2016 — [CB Insights](https://www.cbinsights.com/company/fixawy)), Sal7lyy (Upper Egypt — [Dealroom](https://app.dealroom.co/companies/sal7lyy)) | Supply exists. **Demand aggregation at building level is the moat they lack.** We can partner with them in phase 2 (they supply technicians, we take a commission) |
| Payments rails | InstaPay 22 M, wallets ~59 M, Fawry 300k points | Ready, with no need to build fintech |
| Regulation | Law 119/2008 occupants' unions; Law 164/2025 old-rent reform | Two legal hooks that create need |
| Trust gap | Bawab broker abuse ([Ahram Gate](https://gate.ahram.org.eg/News/5608267.aspx)); compound fee disputes ([Ahram Gate](https://gate.ahram.org.eg/News/1231089.aspx)) | **Transparency (ledger, receipts, votes) is the emotional selling point** |

**The cheapest way to beat competitors (market-size view):**
1. **Free for every resident, forever.** Monetize later through services, payments, compounds, and ads. Paid SaaS like Saknna's caps at the treasurer's willingness to pay.
2. **Win the treasurer (أمين الصندوق) first.** One person who collects ~EGP 6,000/yr from each of 12 flats (~EGP 72k/yr per building) brings 12 households with them.
3. **WhatsApp bot as acquisition.** Residents who never install still see receipts and reminders inside their group, then install to pay or see their history.
4. **Compound B2B** for revenue from month 6 to fund operations (60 compounds × EGP 5k/month ≈ EGP 3.6 M/yr in the base case).

---

## 10. Data gaps & what to validate next

| Gap | Why it matters | How to fill it (cheap) |
|---|---|---|
| Number of residential buildings by unit count (≥ 5 units) | Sharpens building TAM/SAM | CAPMAS 2017 census tables by governorate (paid request) or ERF microdata (building file) |
| Number of registered occupants' unions | Shows formal vs informal buildings | Ask Cairo/Giza governorate technology centres; FOI-style request |
| Current fee levels (2026) per flat / per m² | Drives B1 and payments revenue | 50 treasurer interviews across 5 districts; Facebook compound-group posts |
| Technician prices (2026) | Drives AOV | Mystery-shop 30 technicians plus the Filkhedma/Fixawy apps |
| Competitor install bases (Amarati, Imarti) | SOM benchmark | Play Store install bands via a browser; Sensor Tower free tier |
| New-city populations (New Cairo, 6th Oct, Zayed, NAC) | Geographic prioritisation | ECES Economic Lens #20; CAPMAS 2027 census (if held) |
| WhatsApp usage share | Bot strategy sizing | Meta does not publish it; run a 300-person survey in target districts |

---

## 11. Source list (main)

- CAPMAS households 2025 — https://cairoscene.com/buzz/over-half-of-egyptian-households-live-in-rural-areas
- CAPMAS population (Ahram) — https://english.ahram.org.eg/News/575154.aspx ; https://english.ahram.org.eg/News/572647.aspx ; https://www.egypttoday.com/Article/1/139383/Egypt-s-Population-witness-500K-increase-in-5-months
- 2017 census buildings/units/vacancy — https://amwalalghad.com/ihtg
- 2017 census units & old rent — https://gate.ahram.org.eg/News/5240877.aspx
- Dwelling type microdata — https://erfdataportal.com/index.php/catalog/248/variable/V2360
- Tenure (BEO State of Rent) — https://marsadomran.info/en/2018/02/1410/
- Old rent law 164/2025 — https://egyptianstreets.com/2025/08/04/president-el-sisi-ratifies-amendments-ending-egypts-old-rent-arrangements/ ; https://www.egyptindependent.com/egypt-mandates-15-increase-to-deregulate-old-rent-leases/
- Housing supply — https://gate.ahram.org.eg/News/5450774.aspx ; https://hapijournal.com/2026/01/13/مي-عبدالحميد-تنفيذ-1-72-مليون-وحدة-ضمن-برن/
- JLL Cairo Living Q3 2025 — https://www.jll.com/content/dam/jllcom/en/us/documents/reports/research-reports/25-insights-cairo-living-market-dynamics-q3-2025.pdf
- Gated communities count — https://bu.edu.eg/staff/islamalsayed3-publications/31822
- NAC occupancy — https://english.aawsat.com/arab-world/5296623
- DataReportal 2025/2026 — https://datareportal.com/reports/digital-2025-egypt ; https://datareportal.com/reports/digital-2026-egypt
- MCIT indicators (Ahram) — https://english.ahram.org.eg/News/575154.aspx
- StatCounter — https://gs.statcounter.com/os-market-share/mobile/egypt
- CBE financial inclusion — https://www.maspero.eg/economy/2025/09/03/887287/ ; https://hapijournal.com/2026/02/17/
- Mobile wallets — https://arabfinance.com/ar/news/newdetails/ارتفاع-عدد-محافظ-الهواتف-المحمولة-إلى-أكثر-من-55-مليون-حساب-بنهاية-يونيو-2025 ; https://www.bankygate.com/72177
- InstaPay/IPN — https://english.ahram.org.eg/News/577944.aspx
- Fawry — https://www.zawya.com/en/press-release/companies-news/fawry-releases-fy2025-results-356861 ; https://techcabal.com/2026/04/20/how-fawry-built-a-profitable-fintech/
- HIECS — https://censusinfo.capmas.gov.eg/metadata-en-v4.2/index.php/catalog/747/datafile/F34/V6142 ; https://erfdataportal.com/index.php/catalog/309/variable/V1606 ; https://amwalalghad.com/atkm
- Inflation Aug 2026 — https://english.ahram.org.eg/News/576399.aspx
- Minimum wage — https://egyptianstreets.com/2026/04/02/egypt-raises-minimum-wage-to-8000-egp-from-july-2026/
- Occupants' unions — https://www.mobtada.com/print/944602 ; https://www.youm7.com/story/2020/3/9/عبد-العال-يجب-إلزام-اتحادات-الشاغلين-بالتعاقد-مع-شركات-مُتخصصة/4664251
- Bawab as broker — https://gate.ahram.org.eg/News/5608267.aspx
- Maintenance deposits/fees — https://elmo7amy.tv/%D9%88%D8%AF%D9%8A%D8%B9%D8%A9-%D8%A7%D9%84%D8%B5%D9%8A%D8%A7%D9%86%D8%A9/ ; https://www.dostor.org/3407360 ; https://www.egypttelegraph.com/article/69216/
- FM market — https://www.imarcgroup.com/egypt-facility-management-market ; https://www.verifiedmarketresearch.com/product/egypt-facility-management-market/
- Home services market — https://deepmarketinsights.com/vista/insights/home-services-market/egypt
- Saknna — https://saknna.com
- MyGate benchmark — https://india.entrepreneur.com/business-news/mygate-bags-inr-225-crore-from-dharana-capital

---

## Verification log

Adversarial re-check on 2026-10-12. Fresh searches and fetches were run for each claim.

| # | Claim | Verdict | Evidence URL |
|---|---|---|---|
| 1 | 26.5 M households (11.8 M urban / 14.7 M rural), 1 Jan 2025 | confirmed (one secondary source only; consistent with CAPMAS's 24.3 M in 2019) | https://cairoscene.com/buzz/over-half-of-egyptian-households-live-in-rural-areas |
| 2 | Internet users 98.2 M (82.7%), Facebook 51.6 M, TikTok 18+ 48.8 M (+25.2%), YouTube 49.3 M, 121 M cellular connections, 43.5% urban | confirmed | https://datareportal.com/reports/digital-2026-egypt |
| 3 | Android 88–91% of mobile OS | corrected: 91.1% (Jun), 88.0% (Aug), **83.4% (Sep 2026)**; iOS up to 16.6% | https://gs.statcounter.com/os-market-share/mobile/egypt |
| 4 | MCIT 126.91 M mobile subscriptions; 13.13 M fixed broadband | confirmed (May 2026) | https://english.ahram.org.eg/News/575154.aspx |
| 5 | 97.68 M active mobile broadband, 114.15 per 100 (Jun 2026) | corrected: cited article gives 96.26 M and 113.42% for May 2026 | https://english.ahram.org.eg/News/575154.aspx |
| 6 | Household internet penetration 72.2% (2022/23) | unverified: not in the cited article | https://english.ahram.org.eg/News/575154.aspx |
| 7 | 58.7 M mobile-wallet accounts (Sep 2025); 801 M txns, EGP 1.1 T in Q3 2025 | confirmed | https://www.bankygate.com/75306 |
| 8 | IPN ~22 M registered customers; 1.47 B txns, EGP 4.33 T (Q2 2026) | confirmed (figure is for the IPN network, per the CBE governor) | https://english.ahram.org.eg/News/577944.aspx |
| 9 | Financial inclusion 76.3% (53.8 M of 70.5 M), Jun 2025; women 70% | confirmed | https://www.businesstodayegypt.com/Article/1/6685/Financial-inclusion-in-Egypt-reaches-76-3-by-June-2025 |
| 10 | 2017 census: 16.185 M buildings, 22.973 M residential units, 12.498 M vacant+closed (29.1%), 42.97 M total units, 3.02 M old-rent units (7%), ~1.64 M old-rent households | confirmed; the 2006 old-rent share (20%) is unverified (press cites 15%) | https://amwalalghad.com/ihtg ; https://almalnews.com/2013964/ |
| 11 | Law 164/2025: 7-year residential transition to Aug 2032; 20× (min EGP 1,000) / 10× (min 400) / 10× (min 250); +15%/yr | confirmed | https://www.parlmany.com/News/3/613091/ |
| 12 | Law 119/2008 Art. 72: union required for buildings with ≥ 5 units; exists by force of law (Decree 144/2009) | confirmed | https://www.mohamah.net/law/?p=178136 |
| 13 | Saknna: EGP 450 / 900 / 2,200 / 7,500 per month; "500+" buildings; 14-day trial; InstaPay, Vodafone Cash, bank transfer | confirmed (the live counter showed 0 in the scrape, so "500+" is a marketing claim) | https://saknna.com |
| 14 | Fawry FY2025 revenue EGP 8.65 B (+57%) | confirmed | https://meatechwatch.com/?p=48097 |
| 15 | MyGate: 27k communities, 5.7 M homes (Jun 2026) | confirmed as a company claim; the company's own blog says 4 M+, so the figure is inconsistent | https://india.entrepreneur.com/business-news/mygate-bags-inr-225-crore-from-dharana-capital |
| 16 | Deep Market Insights: Egypt home services USD 1.88 B (2025) → 5.11 B (2034); R&M USD 0.92 B | confirmed (stated CAGR 11.58%) | https://deepmarketinsights.com/vista/insights/home-services-market/egypt |
| 17 | Urban inflation 14.5% / national 12.7% (Aug 2026) | confirmed | https://www.dailynewsegypt.com/?p=853967 |
| 18 | Population 109 M (May 2026) cited to Ahram 575154 | unverified: that article reports only ICT indicators; 108.6 M from Ahram 572647 stands | https://english.ahram.org.eg/News/575154.aspx |
| 19 | WhatsApp ~52 M users | unverified (already flagged; vendor estimate only) | https://chatdaddy.tech/blog/whatsapp-business-api-egypt |

