# 17. Gap-filling: 2026 Egyptian service prices, marketplace take rates, payment-rail fees and dues-collection legality

> Research date: 2026-10-12. Market: Egypt only. Arab and global players appear only as benchmarks.
> Fills the gaps listed in 03 §13, 08 §10, 09 §17 and 14 §10.
> **Rules used:** every number carries a source URL. **ESTIMATE** marks my own derivation, with the reasoning shown. **NOT FOUND** means I searched and found no public source.
> **Caveat on price sources:** Egypt has no official price list for home services. The best public 2026 evidence comes from three places: (a) **HomeRun Egypt** cost pages, which aggregate real executed requests with dates; (b) **Taskty's** published fixed-price menu; (c) vendor and company price explainers. Vendor pages are marketing material, and Taskty's menu shows signs of being only partly updated (it still lists COVID disinfection). I therefore give a **low / typical / high** band and name the source behind each value.

---

## 0. Executive summary (the 12 numbers that matter)

| # | Finding | Value | Confidence |
|---|---|---|---|
| 1 | Platform "inspection" or call-out fee is the norm in Egypt | **EGP 100–250** (Taskty 120 for most trades, 250 for AC, 100 for appliances) | High ([Taskty offers](https://taskty.com/Offers)) |
| 2 | Typical small plumbing or electrical fix (labour) | **EGP 250–900**; bigger jobs EGP 2,500–3,000 | Medium-high ([HomeRun plumber](https://homerun.com.eg/costs-prices/%D8%B3%D8%A8%D8%A7%D9%83_16342), [HomeRun electrical](https://homerun.com.eg/costs-prices/القاهرة-صيانة-كهرباء_42102_30098)) |
| 3 | AC freon refill | **EGP 1,000–1,300** typical (range 230–1,500) | High (3 sources) |
| 4 | AC installation, new unit | **EGP 850–1,400** (Cairo) | High (3 sources) |
| 5 | Pest control, standard apartment | **EGP 800–1,700** | High (3 sources) |
| 6 | Elevator maintenance contract, residential | **from EGP 350/month per lift** | Low-medium (1 vendor) |
| 7 | Egyptian home-services commission benchmarks | **20–25%** (Khidmitty), **30–50% of labour** (Sal7lyy), self-reported. **FilKhedma's 30% is NOT verified** | Low-medium |
| 8 | Card or wallet gateway, published rates | **Paymob 2.75% + EGP 3**; **Kashier 2.85% + EGP 3**; **FawryPay 2.75% + EGP 3 (cards and reference code), 1.5% + EGP 3 (wallet QR)**, with a EGP 999 setup fee and EGP 499 monthly minimum | High (official pages) |
| 9 | InstaPay person-to-person fee (paid by the sender) | **0.1%, min EGP 0.50, max EGP 20**, in force since 1 Apr 2025 | High (multiple outlets) |
| 10 | Can the union legally take digital dues? | **Yes.** A registered union (اتحاد الشاغلين) has legal personality and may open a bank account signed by its president and treasurer. Dues must be receipted | Medium (law-firm and press summaries of Law 119/2008 and its Executive Regulations) |
| 11 | Must the platform hold a CBE licence to pool and pay out funds? | **Effectively yes.** CBE PSP rules (June 2025; Category B needs EGP 10M capital) applied in full after June 2026. **Recommendation: never hold funds. Use the split and payout features of a licensed PSP** | High |
| 12 | AdMob in Egypt | **~US$0.29 blended eCPM** (weak source); tier-3 banner ≈ $0.07–0.14 | Low |

**Bottom line for phase 2:**
- A blended **12–15% take rate on labour**, plus a **flat EGP 15–25 customer service fee**, keeps the platform below the threshold at which technicians take jobs offline. It also yields about **EGP 80–125 contribution on a EGP 1,200 order** (ESTIMATE, §6).
- Dues collection is not a profit centre. Route dues **directly into the union's bank account** through InstaPay, or through Paymob or Fawry sub-accounts. Earn money from SaaS for the treasurer and from convenience fees, not from float.

---

## 1. Price table: 32 service types (EGP, 2025–2026)

"Low / typical / high" = the cheapest credible quote / the most frequent figure / the top of the normal range, excluding outliers. City: Greater Cairo unless noted. Labour only, unless the line says parts or materials are included.

| # | Service (Arabic) | Unit | Low | Typical | High | Date of evidence | Sources and notes |
|---|---|---|---|---|---|---|---|
| 1 | Plumber call-out / inspection (معاينة سباك) | visit | 100 | 120 | 250 | 2026 | Taskty 120 inspection ([Taskty](https://taskty.com/Offers)); HomeRun executed jobs at 250 ([HomeRun plumber](https://homerun.com.eg/costs-prices/%D8%B3%D8%A8%D8%A7%D9%83_16342)) |
| 2 | Small plumbing fix: drain unclog, valve, siphon (تسليك/تغيير محبس) | job | 250 | 300–900 | 2,500 | Feb–Oct 2026 | HomeRun executed jobs: valve 250 (Feb 2026), drain 250–300, siphon + shattaf 2,500 (Oct 2026) ([HomeRun](https://homerun.com.eg/costs-prices/%D8%B3%D8%A8%D8%A7%D9%83_16342)). Typical value is an ESTIMATE midpoint |
| 3 | Plumbing first-fix: 1 bathroom + 1 kitchen (تأسيس سباكة) | job | 3,000 | 3,500 | 4,200 | 2026 menu | Taskty 3,000–4,200 by configuration ([Taskty](https://taskty.com/Offers)) |
| 4 | Electrician call-out (معاينة كهربائي) | visit | 100 | 120 | 250 | 2026 | Taskty 120 ([Taskty](https://taskty.com/Offers)) |
| 5 | Electrical repair job (صيانة كهرباء) | job | 800 | 890–1,500 | 3,500 | Jan–Jun 2026 | HomeRun average 890–3,500; executed jobs 800 (May 2026), 888 (Jun 2026) and 1,500 (Jan 2026) ([HomeRun](https://homerun.com.eg/costs-prices/القاهرة-صيانة-كهرباء_42102_30098)) |
| 6 | AC inspection (معاينة تكييف) | visit | 250 | 250 | 250 | 2026 | Taskty ([Taskty](https://taskty.com/Offers)) |
| 7 | AC cleaning / summer service (غسيل وصيانة) | unit | 250 | 300 | 500 | Aug 2026 | Taskty 300; HomeRun jobs at 250 and range factor 250–500 ([HomeRun AC maintenance](https://homerun.com.eg/costs-prices/القاهرة-صيانة-تكييف_604_30098)) |
| 8 | AC freon refill (شحن فريون) | unit | 230 | 1,000–1,200 | 1,500 | 2026 | HomeRun 230–1,500 ([HomeRun freon](https://homerun.com.eg/costs-prices/القاهرة-شحن-فريون-التكييف_8238_30098)); Taskty 1,200; Dubizzle Suez listing 1,000 (search snippet, [Dubizzle](https://www.dubizzle.com.eg/services/suez-district/)); HomeRun job: 2–3 units 1,300 (Aug 2026) |
| 9 | AC repair, other faults | unit | 250 | 1,000 | 4,100 | Aug 2026 | HomeRun average 250–4,100; jobs 250 and 2,000 ([HomeRun](https://homerun.com.eg/costs-prices/القاهرة-صيانة-تكييف_604_30098)) |
| 10 | AC installation, new unit (تركيب) | unit | 650 | 850–1,100 | 1,400 | 2026 | HomeRun Cairo 850–1,400 ([HomeRun](https://homerun.com.eg/costs-prices/%D8%A7%D9%84%D9%82%D8%A7%D9%87%D8%B1%D8%A9-%D8%AA%D8%B1%D9%83%D9%8A%D8%A8-%D8%AA%D9%83%D9%8A%D9%8A%D9%81_40729_30098)); Misr Cool 800 (1.5 HP) to 1,400 (4–5 HP) ([airconditioningeg](https://airconditioningeg.com/%D8%A3%D8%B3%D8%B9%D8%A7%D8%B1-%D8%AA%D8%B1%D9%83%D9%8A%D8%A8-%D8%A7%D9%84%D8%AA%D9%83%D9%8A%D9%8A%D9%81-%D9%81%D9%8A-%D9%85%D8%B5%D8%B1/)); Carrier agent 650 ([carrier-egy](https://carrier-egy.net/Carrierairconditioninginstallationnumbers)) |
| 11 | AC dismantle and reinstall (فك وتركيب) | unit | 1,050 | 1,300 | 1,700 | 2026 | Taskty 1,300 (1.5 HP) to 1,700 (5 HP), plus 70 in Madinaty, Rehab, Shorouk and Obour ([Taskty offer](https://taskty.com/Offers/OfferDetails/2149)); Sharp 1,050 ([sharpegy](https://sharpegy.com/sharp-conditioning/)) |
| 12 | AC copper-pipe first-fix (تأسيس مواسير) | metre | 450 | 450 | n/a | 2026 | Vendor guide "from ~450/m" ([carrier-air-conditioning-maintenance](https://www.carrier-air-conditioning-maintenance.com/%D8%A7%D9%84%D9%85%D8%AF%D9%88%D9%86%D8%A9/%D8%AF%D9%84%D9%8A%D9%84-%D8%B4%D8%A7%D9%85%D9%84-%D8%B9%D9%86-%D8%B3%D8%B9%D8%B1-%D9%85%D8%AA%D8%B1-%D8%AA%D8%A3%D8%B3%D9%8A%D8%B3-%D9%85%D9%88%D8%A7%D8%B3%D9%8A%D8%B1-%D8%A7%D9%84%D8%AA%D9%83%D9%8A%D9%8A%D9%81-%D9%81%D9%8A-%D9%85%D8%B5%D8%B1-2026)). Single source |
| 13 | Carpenter job (نجار) | job | 500 | 1,000 | 2,500 | 2026 | HomeRun 500–2,500 (search summary of [HomeRun carpenter](https://homerun.com.eg/%D9%86%D8%AC%D8%A7%D8%B1)); Taskty inspection 120 |
| 14 | Painter labour, repaint (نقاشة تجديد) | m² | 25 | 40 | 50 | 2025–26 | Vendor explainers 25–50 ([hashmistone](https://hashmistone.com/1883/cost-meter-painting-today/), [buildora](https://buildora-group.com/%D8%B3%D8%B9%D8%B1-%D9%85%D8%AA%D8%B1-%D8%A7%D9%84%D9%86%D9%82%D8%A7%D8%B4%D9%87/)) |
| 15 | Painter labour, full finish (تشطيب نقاشة كامل) | m² | 40 | 70 | 100 | 2026 | Taskty 40 base coat, 70 full, 80 with decor ([Taskty](https://taskty.com/Offers)); vendors 40–100 |
| 16 | Painting a whole 100–120 m² flat | job | 8,000 | 15,000 | 25,000 | 2026 | 120 m²: 8–15k ([golden-view](https://golden-view-eg.com/%D8%AA%D9%83%D9%84%D9%81%D8%A9-%D9%86%D9%82%D8%A7%D8%B4%D8%A9-%D8%B4%D9%82%D8%A9-120-%D9%85%D8%AA%D8%B1/)); 100 m² incl. materials 15–25k ([kaydc](https://kaydc-eg.com/%D8%AA%D9%83%D9%84%D9%81%D8%A9-%D8%AF%D9%87%D8%A7%D9%86-%D8%B4%D9%82%D8%A9-100-%D9%85%D8%AA%D8%B1/)) |
| 17 | Pest control, standard flat (رش حشرات) | flat | 500 | 1,050–1,400 | 1,700 | 2026 | Taskty 1,050 kitchen and bathrooms, 1,400 small home, 1,700 large, 8-month warranty ([Taskty](https://taskty.com/Offers)); German Pest 800–1,200 for 2 rooms ([germanpest](https://www.germanpest.com/ar/%D8%A7%D8%B3%D8%B9%D8%A7%D8%B1-%D9%85%D9%83%D8%A7%D9%81%D8%AD%D8%A9-%D8%A7%D9%84%D8%AD%D8%B4%D8%B1%D8%A7%D8%AA-%D9%81%D9%8A-%D9%85%D8%B5%D8%B1/%D8%A7%D9%84%D8%A7%D8%B3%D8%B9%D8%A7%D8%B1/)); Falcon German 500–1,500 ([falcongerman](https://falcongerman.com/%D8%A7%D8%B1%D9%82%D8%A7%D9%85-%D8%B4%D8%B1%D9%83%D8%A7%D8%AA-%D8%B1%D8%B4-%D8%A7%D9%84%D8%AD%D8%B4%D8%B1%D8%A7%D8%AA)) |
| 18 | Bed-bug treatment (بق الفراش) | flat | 1,500 | 2,000 | 2,500 | 2026 | [insectscenter](https://insectscenter.com/%D8%A7%D8%B3%D8%B9%D8%A7%D8%B1-%D9%85%D9%83%D8%A7%D9%81%D8%AD%D8%A9-%D8%A7%D9%84%D8%AD%D8%B4%D8%B1%D8%A7%D8%AA-2026-%D8%A7%D9%84%D8%A3%D9%84%D9%85%D8%A7%D9%86%D9%8A%D8%A9-%D8%A7%D9%84%D8%A3/) |
| 19 | Rodent / gecko control | flat | 1,050 | 1,400 | 1,400 | 2026 | Taskty ([Taskty](https://taskty.com/Offers)) |
| 20 | Rooftop water-tank cleaning (غسيل خزان) | tank | 400 | 1,000 (ESTIMATE) | 3,000 | 2026 | City Clean 400–3,000 ([cityclean-eg](https://cityclean-eg.com/%D8%AA%D9%86%D8%B8%D9%8A%D9%81-%D9%88%D8%AA%D8%B7%D9%87%D9%8A%D8%B1-%D8%AE%D8%B2%D8%A7%D9%86%D8%A7%D8%AA-%D9%85%D9%8A%D8%A7%D9%87-%D8%A7%D9%84%D8%B4%D8%B1%D8%A8)); Taskty 120 inspection. Typical value is an ESTIMATE (mid-size concrete roof tank) |
| 21 | Elevator maintenance contract, residential (عقد صيانة أسانسير) | lift / month | 350 | 500–800 (ESTIMATE) | 3,000 | 2026 | Misr Elevator "from 350/month" ([misrelevator](https://misrelevator.com/%D8%AA%D9%83%D9%84%D9%81%D8%A9-%D8%B5%D9%8A%D8%A7%D9%86%D8%A9-%D8%A7%D9%84%D8%A7%D8%B3%D8%A7%D9%86%D8%B3%D9%8A%D8%B1/)); villa lifts 12–36k/yr = 1,000–3,000/month ([lec-egy](https://lec-egy.com/%D8%A3%D8%B3%D8%B9%D8%A7%D8%B1-%D9%85%D8%B5%D8%A7%D8%B9%D8%AF-%D8%A7%D9%84%D9%81%D9%84%D9%84/)). No Schindler, Kone or Otis Egypt AMC quote is public (NOT FOUND) |
| 22 | Elevator major parts (inverter / control) | part | 9,000 | 15,000 | 45,000 | 2026 | Inverter 9–22k, electrical parts 15–45k ([matrix-elevator](https://matrix-elevator.com/%D8%A7%D8%B3%D8%B9%D8%A7%D8%B1-%D9%82%D8%B7%D8%B9-%D8%BA%D9%8A%D8%A7%D8%B1-%D8%A7%D9%84%D9%85%D8%B5%D8%A7%D8%B9%D8%AF/)) |
| 23 | Satellite dish install / realign (تركيب دش) | job | 120 (inspection) | 300 (ESTIMATE) | 600 (ESTIMATE) | 2026 | Taskty inspection 120. Labour price NOT FOUND. Dish hardware 250–600 for 70–85 cm ([electro-eg](https://electro-eg.com/%D8%A7%D8%B3%D8%B9%D8%A7%D8%B1-%D8%A7%D8%B7%D8%A8%D8%A7%D9%82-%D8%A7%D9%84%D8%AF%D8%B4-%D9%81%D9%8A-%D9%85%D8%B5%D8%B1-2025-%D9%85%D8%B9-%D8%AF%D9%84%D9%8A%D9%84-%D8%B4%D8%A7%D9%85%D9%84-%D9%84%D9%84/)). ESTIMATE: labour ≈ 1–2 inspection fees, by analogy with other trades |
| 24 | Home internet / landline set-up (WE) | line | 194 + stamps | ~270 incl. VAT and stamps (ESTIMATE) | 1,400 (4G router) | 2021 / 2026 | Application fee 194 before VAT plus 8 stamps × 2.90 ([prices2day, old](https://www.prices2day.net/2021/04/landline-installation-prices.html)); WE 4G air router 1,400 ([mobilemasr](https://mobilemasr.com/blogs/we-air-router-without-a-landline-4g)); 2026 package increase of 9–15% ([elbalad](https://www.elbalad.news/6970319)). Installer is the telco, so this suits an affiliate model, not a marketplace |
| 25 | Standard flat cleaning (نظافة شقة) | visit | 520 | 650–750 | 1,000 | 2026 | Taskty 520 (≤170 m²), 750 comprehensive, 1,000 premium 8 h ([Taskty](https://taskty.com/Offers)); HomeRun job in New Cairo ≈650 ([HomeRun](https://homerun.com.eg/costs-prices/%D8%AA%D9%86%D8%B8%D9%8A%D9%81-%D8%B4%D9%82%D9%82_41862)) |
| 26 | Deep / post-renovation cleaning | m² or job | 20/m² | 2,000 (ESTIMATE, 100 m²) | 6,430 | 2026 | Taskty 20/m² ([Taskty](https://taskty.com/Offers)); HomeRun 550–6,430 ([HomeRun](https://homerun.com.eg/costs-prices/%D8%AA%D9%86%D8%B8%D9%8A%D9%81-%D8%B4%D9%82%D9%82_41862)) |
| 27 | Building staircase cleaning (نظافة سلم) | visit | 450 | 450 | 450 | 2026 | Taskty ([Taskty](https://taskty.com/Offers)). This is a building-level (union) purchase |
| 28 | Sofa / mattress / carpet cleaning | job | 570 | 720–1,100 | 1,350 | 2026 | Taskty: 3 mattresses 570; salon packages 570–1,350; carpets 20/m² ([Taskty](https://taskty.com/Offers)) |
| 29 | Moving, 3-bedroom flat within Cairo (نقل عفش) | job | 1,500 | 2,500–4,000 | 6,500 (with packing) | 2026 | Al-Haramain 2,500–4,000, or 4,000–6,500 with packing ([alharamain-afsh](https://alharamain-afsh.com/%D8%A7%D8%B3%D8%B9%D8%A7%D8%B1-%D9%86%D9%82%D9%84-%D8%A7%D9%84%D8%B9%D9%81%D8%B4-%D9%81%D9%8A-%D9%85%D8%B5%D8%B1/)); Naser Trans 1,500–2,800 ([nasertrans](https://nasertrans.com/%D8%A3%D8%B3%D8%B9%D8%A7%D8%B1-%D9%86%D9%82%D9%84-%D8%A7%D9%84%D8%B9%D9%81%D8%B4-%D9%81%D9%8A-%D9%85%D8%B5%D8%B1/)); HomeRun 2,000–15,000 ([HomeRun](https://homerun.com.eg/costs-prices/%D8%A7%D9%84%D9%82%D8%A7%D9%87%D8%B1%D8%A9-%D9%86%D9%82%D9%84-%D8%B9%D9%81%D8%B4_16341_30098)) |
| 30 | Moving, Cairo → Alexandria | job | 3,000 | 5,000 | 8,000 | 2026 | Naser Trans 3,000; El-Khabeer 4,000–8,000 ([el-khabeer](https://el-khabeer.com/%D8%A3%D8%B3%D8%B9%D8%A7%D8%B1-%D9%86%D9%82%D9%84-%D8%A7%D9%84%D8%A3%D8%AB%D8%A7%D8%AB-%D9%81%D9%8A-%D9%85%D8%B5%D8%B1-2026/)) |
| 31 | Home-appliance repair (washer, fridge) | job | 100 (inspection) | 500 (ESTIMATE) | 2,500 | 2026 | HomeRun 150–2,500 ([HomeRun](https://homerun.com.eg/costs-prices/القاهرة-صيانة-اجهزة-منزلية_36860_30098)); Taskty inspection 100 |
| 32 | Tiling / marble / parquet / plastering labour | m² | 30 (plaster) | 75 (ceramic) | 150 (marble epoxy) | 2026 | Taskty: plaster 30–55, ceramic from 75, marble polishing 120–150, parquet sanding 90–140 ([Taskty](https://taskty.com/Offers)) |
| 33 | Water-pump replacement for the building (موتور رفع) | pump hardware | 4,700 | 7,500 | 13,500 | 2026 | Chinese APT 1 HP 4,700; Pedrollo 7,500; Calpeda 13,500 ([waterinegypt](https://www.waterinegypt.com/%D8%A7%D9%81%D8%B6%D9%84-%D9%85%D9%88%D8%A7%D8%AA%D9%8A%D8%B1-%D8%A7%D9%84%D9%85%D9%8A%D8%A7%D9%87-%D8%A7%D9%84%D8%A7%D9%8A%D8%B7%D8%A7%D9%84%D9%8A-1-%D8%AD%D8%B5%D8%A7%D9%86/)). Install labour NOT FOUND; ESTIMATE 300–800 |
| 34 | CCTV 4-camera kit (hardware) | kit | 1,650 | n/a | n/a | dated | [pricesworld](https://www.pricesworld.net/?p=54191). The page mixes older data, so treat it as unreliable. Install labour NOT FOUND |
| 35 | Building guard / doorman (بواب) | month | 4,000 | 7,000 (ESTIMATE, wage floor) | 8,000 | 2024–26 | Private-sector minimum wage 7,000 since Mar 2025 ([banker.news](https://banker.news/144869)); older ad 4,000 ([mosta3ed](https://mosta3ed.com/?p=48920&post_type=jobs)); Ahram reports many guards earn below a living wage plus tips ([Ahram Gate](https://gate.ahram.org.eg/News/5608267.aspx)) |

**Historical anchor:** Fixawy charged a **EGP 50–100 inspection** fee, with minimums of 70 for plumbing and electrical work and 100 for appliances, in about 2019 ([Cairo360](https://www.cairo360.com/ar/article/%D8%AA%D8%B3%D9%88%D9%82/%D8%A3%D9%81%D8%B6%D9%84-3-%D8%AA%D8%B7%D8%A8%D9%8A%D9%82%D8%A7%D8%AA-%D8%AA%D8%B7%D9%84%D8%A8-%D9%85%D9%86%D9%87%D9%85-%D8%B5%D9%86%D8%A7%D9%8A%D8%B9%D9%8A-%D9%84%D8%A3%D8%B9%D8%B7%D8%A7%D9%84/)). Taskty's **120** in 2026 means the call-out fee has roughly doubled, which is in line with the EGP's fall from about 15.7 to about 47–50 per US$ (ESTIMATE).

### 1.1 What the price data tells product design

1. **The market already accepts fixed-menu pricing.** Taskty publishes 73 fixed-price offers, and FilKhedma advertises "pre-set prices to eliminate negotiations" ([Google Play](https://play.google.com/store/apps/details?id=com.filkhedma.customer&hl=en_US)). Copy the structure: **fixed menu for standard jobs** (AC service, freon, pest control, cleaning) and **inspection + quote** for open-ended jobs (plumbing, electrical, carpentry).
2. **The inspection fee of EGP 100–250 is the anchor.** Residents expect to pay it. Make it **refundable as credit when the job is booked through the app**. That gives the customer a reason to keep the transaction inside the app.
3. **Seasonality is extreme for AC.** Freon and cleaning cluster in May–August (HomeRun executed jobs are concentrated in August 2026). Pre-sell **"summer AC packs"** in April through the building group.
4. **Building-level (B2B) services are a separate, recurring revenue pool:** elevator AMC, tank cleaning, staircase cleaning, water pumps and the doorman. The union buys them, so the take is charged on recurring contracts, not one-off jobs.

### 1.2 Chart-ready data: typical price by category (EGP, labour)

```csv
service,low,typical,high
Plumber call-out,100,120,250
Small plumbing fix,250,600,2500
Electrical repair job,800,1200,3500
AC cleaning/service,250,300,500
AC freon refill,230,1100,1500
AC install (new),650,1000,1400
AC dismantle+reinstall,1050,1300,1700
Carpenter job,500,1000,2500
Pest control flat,500,1200,1700
Water-tank cleaning,400,1000,3000
Flat cleaning,520,700,1000
Moving 3BR in Cairo,1500,3000,6500
Appliance repair,100,500,2500
Elevator AMC per month,350,650,3000
```
Suggested chart: horizontal range bars (low–high) with a dot at the typical value, sorted by typical value. The typical values for small plumbing fixes, electrical jobs, water tanks, appliances and elevator AMC are ESTIMATE midpoints.

---

## 2. Commission and take-rate table

| Platform | Market | Model | Take rate / commission | Source | Status |
|---|---|---|---|---|---|
| **FilKhedma** | Egypt | Fixed-price marketplace, cash or card after job, 1-month guarantee | **~30% (claimed in the brief)** | No public source. Searched press, the App Store, Google Play, Wamda and Enterprise ([Wamda 2021](https://www.wamda.com/en/2021/12/filkhedma-receives-new-investment-cairo-angels), [Google Play](https://play.google.com/store/apps/details?id=com.filkhedma.customer&hl=en_US)) | **NOT VERIFIED** |
| **Sal7lyy (صلحلي)** | Upper Egypt | Vetted technicians, guarantee, parts store | **30–50% of labour** (self-reported) | [Gust](https://gust.com/companies/%D8%B5%D9%84%D8%AD%D9%84%D9%8A) (cited in file 03) | Self-reported, old |
| **Khidmitty** | Cairo | Marketplace | **20–25% of labour** (self-reported) | [Gust](https://gust.com/companies/Khidmitty-s-startup-2/financials) (cited in file 03; 403 on re-fetch today) | Self-reported, old |
| **Osta** | Alexandria | Technician commission + customer order fee | Not disclosed | [Gust](https://gust.com/companies/osta0) | NOT FOUND |
| **Fixawy** | Egypt | Inspection fee + job price; separate "Fixawy Fixer" technician app | Not disclosed | [APKPure technician app](https://apkpure.com/ar/%D9%81%D9%8A%D9%83%D8%B3%D8%A7%D9%88%D9%8A-%D9%84%D9%84%D8%B5%D9%86%D8%A7%D9%8A%D8%B9%D9%8A/com.fixawy.fixawyfixer) | NOT FOUND |
| **Taskty** | Egypt | Fixed menu + EGP 120 inspection | Not disclosed | [Taskty](https://taskty.com/Offers) | NOT FOUND |
| **Sanayeya (صنايعية)** | Egypt | Customer pays technician directly at the in-app agreed price | Not disclosed | [maashahir](https://maashahir.com/archives/1620) | NOT FOUND |
| **Bricole** | Egypt / MENA | Lead directory | **0% commission**, no subscription (advertised) | [bricoleapp](https://bricoleapp.com/ar/eg/) | Advertised |
| **HomeRun Egypt** | Egypt | 4 quotes per request (lead-gen) | Not disclosed; providers pay for leads (ESTIMATE, from the model) | [HomeRun](https://homerun.com.eg/costs-prices/%D8%B3%D8%A8%D8%A7%D9%83_16342) | NOT FOUND |
| **Uber Egypt** (gig-work anchor) | Egypt | Ride-hailing | **26.67%** (UberX), 15–17.5% (Saver), per 2022 driver strike reports | Search summary of [cairo24](https://www.cairo24.com/1619669) / [almalnews](https://almalnews.com/793679/«المال»-تنفرد-ببنود-العقد-المعدل-بين-أوبر/) | Old (2022) |
| **inDrive Egypt** (anchor) | Egypt | Ride-hailing | **≤9% (2021), 9.9% (2022)** | [Al Jazeera 2021](https://www.aljazeera.net/ebusiness/2021/9/2/منافسون-على-الطريق-هل-تنهي-إن-درايفر) | Old |
| **Talabat** (anchor) | MENA group | Delivery | **14–15% overall, 17–18% restaurants** | [FAB Securities](https://fabsresearch.bankfab.com/ResearchPortal/Download/Index/961) (file 03) | Confirmed, group level |
| **Urban Company** | India / UAE | Home services | Commission was **8.5–30%** by ticket size; beauty cut **30% → 25%** (2021); FY26 commission + fees = **28.3%** of pro earnings; forward take rate 22–23% | [Free Press Journal](https://www.freepressjournal.in/business/urban-company-cuts-commission-to-25-from-30-after-workers-protest), [Inc42](https://inc42.com/?p=571319), [S&P](https://www.spglobal.com/market-intelligence/en/news-insights/research/2026/04/urban-company-revenue-to-triple-by-2030-as-take-rates-and-platform-monetization-rise) | Confirmed |
| **ServiceMarket (e&)** / **Justlife** | UAE | Commissions from providers | Rate not disclosed | [CB Insights](https://www.cbinsights.com/compare/just-mop-vs-movesouq) | NOT FOUND |

**Reading:**
- Egyptian gig workers already accept **~10% (inDrive) to ~27% (Uber)**.
- Self-reported home-services commissions sit at **20–50%**. Those high figures belong to models that own the technician (training, guarantee, parts).
- **A pure marketplace with no guarantee can sustain only about 10–15%** before technicians take the work offline. The cash and WhatsApp economy makes leakage worse than anything Homejoy saw (see file 03, §1 item 9).
- No Egyptian platform publishes its technician terms. The only reliable way to get them is to **sign up as a technician on FilKhedma, Fixawy and Taskty and read the contract** (§9, action 1).

### 2.1 Chart-ready data: commission benchmarks (%)

```csv
platform,low,high,type
inDrive Egypt,9,9.9,ride-hailing
Talabat group,14,18,delivery
Uber Egypt,15,26.67,ride-hailing
Khidmitty,20,25,home services (self-reported)
Urban Company,22,28.3,home services
Sal7lyy,30,50,home services (self-reported)
Recommended (this app),10,15,home services
```

---

## 3. Payment-rail fee table (Egypt, October 2026)

| Rail / provider | Setup | Per-transaction fee | Settlement | Marketplace split / payouts | Notes and source |
|---|---|---|---|---|---|
| **Paymob**, standard (cards, wallets, BNPL, kiosk via one integration) | None, no monthly fee | **2.75% + EGP 3** per successful transaction (the "Local" rate); enterprise pricing is custom | **Weekly** per the pricing page; T+1 with optional **instant settlement** per Paymob's WooCommerce listing and [Digitology](https://digitology.co/payment-gateway-egypt/) | **Yes**: "MarketPlace" product for split payouts, plus mass payouts to bank, wallet and instant rails. Fees are by quote | [Paymob pricing](https://paymob.com/en/pricing), [Paymob marketplace](https://paymob.com:443/en/marketplace), [llms.txt](https://paymob.com/llms.txt), [WooCommerce](https://woocommerce.com/products/paymob/). Per-method rates (wallet, valU) are not published |
| **Kashier** | None | **2.85% + EGP 3** | Not stated | Payouts not documented publicly | [Kashier FAQ](https://kashier.io/en/faqs), [KrASIA](https://kr-asia.com/egyptian-payments-platform-kashier-raises-six-figure-seed), [Digitology](https://digitology.co/payment-gateway-egypt/) |
| **FawryPay** (online) | **EGP 999 one-time**; **EGP 499 monthly minimum processing fee** | Cards **2.75%**; **reference code (cash at 377k+ outlets) 2.75%**; **mobile wallet QR 1.5%**; all **+ EGP 3** processing; SMS EGP 0.16 | **Weekly** | **Sub-accounts**, payouts and cash disbursement, recurring payments, instalments | [atfawry pricing](https://atfawry.com/pricing). Through Flutterwave: 2.3% + EGP 1.5 + 14% VAT on the fee ([Flutterwave](https://flutterwave.com/gh/support/payments/fawry-pay-faq-egypt)). Reference codes are valid 30 days; about 80% get paid (third-party claim) |
| **Fawry biller listing** ("bill payment" for compounds) | By agreement | By agreement (NOT FOUND) | — | Owners pay dues in myFawry; the manager gets per-owner balance reports | [Fawry payment & collection](https://www.fawry.com/business/payment-and-collection/); Palm Hills, La Vista, Edara, Marina and 20+ compounds are already billers ([Fawry bill payment](https://www.fawry.com/consumer/bill-payment/)) |
| **Geidea** (pay-by-link, POS, SoftPOS) | Quote | **Not published**; negotiated MDR | Per contract | Not public | [Geidea pay-by-link](https://geidea.net/egypt/en/online-selling/pay-by-link) |
| **PayTabs Egypt** | Quote | Not published | Per market | Split payouts API exists | [PayTabs docs](https://docs.paytabs.com/PT2-API-Endpoints/Deposit-and-Payouts/Split-Payouts/Step-2-Initiating-Payout-Requests/Step-2-Initiating-Split-Payout-Request-Landing) |
| **InstaPay / IPN** (account-to-account, P2P) | Free (bank app) | **0.1% of value, min EGP 0.50, max EGP 20**, paid by the **sender**, since 1 Apr 2025. Some outlets say min EGP 1. 10 free balance checks, then 0.50 each | **Instant** | No split; payee is a bank account, wallet or IPA alias. No merchant MDR schedule is published | [Ahram Online](https://english.ahram.org.eg/NewsContent/1/2/543590/Egypt/Society/InstaPay-to-apply-charges-starting--April.aspx), [Egyptian Streets](https://egyptianstreets.com/2025/04/03/instapay-now-charging-transfer-fees), [Egypt Independent](https://www.egyptindependent.com/instapay-updates-fees-and-tariffs-for-money-transfers/). Limits: EGP 70k per transaction, 120k per day, 400k per month ([PhotonPay](https://www.photonpay.com/hk/blog/article/instapay-egypt?lang=en)). The 0.1% fee turned InstaPay profitable within a year ([EnterpriseAM, Apr 2026](https://enterpriseam.com/egypt/2026/04/06/instapay-hits-profitability-as-demand-keeps-up-one-year-into-0-1-transaction-fee/)) |
| **Vodafone Cash** (P2P) | Free | To a Vodafone wallet **EGP 1**; to another network's wallet **0.5% (min 1, max 15)**; cash-out ~1% (min 3) | Instant | Merchant rates **NOT FOUND** | [Vodafone money transfer](https://web.vodafone.com.eg/en/money-transfer), [MomoCalc](https://momocalc.com/egypt/en/vodafone-cash-fees) |
| **Meeza** | via PSP | Bundled in the PSP card rate (no separate public rate) | — | — | Accepted by Fawry and Paymob; separate MDR NOT FOUND |
| **BNPL** (valU, Souhoola, Halan, Contact, Sympl, Aman) via Paymob or Fawry | via PSP | **Merchant fee not published**. One guide cites ~7% for Egyptian BNPL (not attributed to a provider); globally 2–8% | — | — | [Digitology](https://digitology.co/payment-gateway-egypt/), Paymob BNPL list ([llms.txt](https://paymob.com/llms.txt)) |
| **Paystack Egypt** (benchmark) | None | 2.7% + EGP 2.5 (Visa / Mastercard), per search snippet | — | — | [Paystack support](https://support.paystack.com/hc/en-us/articles/360009882020-How-much-does-Paystack-charge-for-international-transactions-), ESTIMATE-grade (not re-fetched) |
| **Bank business account** for the platform or union | Banque Misr Digital Business Onboarding **EGP 1,200/yr**; **EGP 120 per account** for internet banking | Bank tariff | — | Bulk transfers by tariff | [Banque Misr corporate tariff](https://www.banquemisr.com/-/media/Corporate-Tarrif/Corporate-Tarrif--Eng.ashx) |

### 3.1 Effective cost at Egyptian ticket sizes (computed from the published rates)

| Ticket (EGP) | Paymob 2.75%+3 | Kashier 2.85%+3 | FawryPay card / ref 2.75%+3 | FawryPay wallet QR 1.5%+3 | InstaPay P2P 0.1% (sender pays) |
|---|---|---|---|---|---|
| 120 (inspection) | 6.30 (**5.25%**) | 6.42 (5.35%) | 6.30 (5.25%) | 4.80 (4.0%) | 0.50 (0.42%) |
| 300 | 11.25 (3.75%) | 11.55 (3.85%) | 11.25 (3.75%) | 7.50 (2.5%) | 0.50 (0.17%) |
| 600 (monthly dues) | 19.50 (3.25%) | 20.10 (3.35%) | 19.50 (3.25%) | 12.00 (2.0%) | 0.60 (0.1%) |
| 1,200 (typical job) | 36.00 (3.0%) | 37.20 (3.1%) | 36.00 (3.0%) | 21.00 (1.75%) | 1.20 (0.1%) |
| 3,000 (big job) | 85.50 (2.85%) | 88.50 (2.95%) | 85.50 (2.85%) | 48.00 (1.6%) | 3.00 (0.1%) |
| 20,000 (painting job) | 553 (2.77%) | 573 (2.87%) | 553 (2.77%) | 303 (1.52%) | 20.00 (cap, 0.1%) |

FawryPay also carries a EGP 499 monthly minimum, and prices may exclude 14% VAT on the fee; confirm this in the contract.
**Takeaways:**
- The **fixed EGP 3 fee dominates small tickets**. Never charge the EGP 120 inspection fee by card. Bundle it into the job or collect it in cash or by wallet.
- **Wallet QR through Fawry (1.5%) is about 45% cheaper than cards** for dues.
- **InstaPay is 30× cheaper than cards**, but it settles person-to-person with no API split. Reconciliation needs AI screenshot or SMS parsing, or bank statement matching (see file 11).

### 3.2 Chart-ready data: effective fee % by ticket

```csv
ticket_egp,paymob,kashier,fawry_card,fawry_wallet_qr,instapay
120,5.25,5.35,5.25,4.00,0.42
300,3.75,3.85,3.75,2.50,0.17
600,3.25,3.35,3.25,2.00,0.10
1200,3.00,3.10,3.00,1.75,0.10
3000,2.85,2.95,2.85,1.60,0.10
20000,2.77,2.87,2.77,1.52,0.10
```
Suggested chart: line chart, x = ticket on a log scale, y = effective %, five series.

---

## 4. Regulation: CBE rules on payment facilitators, collection on behalf of others, InstaPay

| Rule | What it says | Implication for the app | Source |
|---|---|---|---|
| **CBE Licensing and Registration Rules for PSOs and PSPs** (issued 19 Jun 2025 under Banking Law 194/2020, arts 184–200) | Licensed payment services include **electronic acceptance (payment technology, facilitation, cash collection)**, payment execution and transfers, e-money issuance, deposits and withdrawals, initiation and account information | A platform that **collects residents' money and pays it out** to technicians or unions performs a payment service | [Matouk Bassiouny](https://matoukbassiouny.com/egypts-central-bank-issues-the-licensing-framework-for-psos-and-psps/), [CBE rules PDF](https://www.cbe.org.eg/-/media/project/cbe/page-content/rich-text/payment-system/payment-systems-and-services-oversight/rules-for-licensing-and-registration-of-payment-system-operators.pdf), [Daily News Egypt](https://www.dailynewsegypt.com/2025/06/21/cbe-issues-new-licensing-framework-for-electronic-payment-service-providers/) |
| Capital | **Category B PSP EGP 10M** (monthly volume < EGP 750M); **Category A EGP 30M**; initiation and account information EGP 20M; PSO EGP 500M; must be an Egyptian joint-stock company with prior CBE approval | Out of reach for a bootstrapped founder | [Legal500](https://www.legal500.com/intelligence/egypt/finance-and-banking/fintech-license-in-egypt-cbe-fra-licensing-guide) |
| Transition | 12-month grace period for existing providers **ended June 2026**. Unlicensed operators are now exposed | Do not launch a wallet or pooled balance | [LaunchBase](https://launchbaseafrica.com/2025/06/19/egypts-fintech-firms-given-12-months-to-get-licensed-or-shut-down/), [Legal500](https://www.legal500.com/intelligence/egypt/finance-and-banking/fintech-license-in-egypt-cbe-fra-licensing-guide) |
| Partnering with a bank or PSP | "A common mistake is assuming that partnering with a bank automatically removes licensing questions". The test is **who holds customer funds and who issues the payment instrument** | Design so that the **PSP holds funds** and the platform is a **technology provider and merchant of record only for its own fee** | [Legal500](https://www.legal500.com/intelligence/egypt/finance-and-banking/fintech-license-in-egypt-cbe-fra-licensing-guide) |
| Governance and fit-and-proper rules (Sep 2025) | Additional rules for PSO and PSP officers | Applies only if the platform ever licenses | [CBE news](https://www.cbe.org.eg/en/news-publications/news/2025/09/01/13/10/payment-system-operators-and-payment-service-providers) |
| Sandbox | Does not replace a licence; testing for 6–12 months | A possible route for a future "building wallet" | [Legal500](https://www.legal500.com/intelligence/egypt/finance-and-banking/fintech-license-in-egypt-cbe-fra-licensing-guide) |
| InstaPay fees | 0.1% (min 0.50, max 20) since 1 Apr 2025. CBE had previously renewed fee waivers in 3-month blocks | P2P dues transfers cost the payer almost nothing | [Ahram](https://english.ahram.org.eg/NewsContent/1/2/543590/Egypt/Society/InstaPay-to-apply-charges-starting--April.aspx), [Amwal Al Ghad](https://en.amwalalghad.com/?p=187926) |
| Merchant QR on InstaPay | Announced (2024–25). No published merchant fee schedule found | Watch: if IPN merchant QR launches at ~0.1–0.5%, it becomes the best rail for dues | [Zawya](https://www.zawya.com/en/economy/north-africa/instapay-to-enable-qr-code-based-payments-between-individuals-within-days-in-egypt-gl4w462m), [Mordor](https://www.mordorintelligence.com/industry-reports/egypt-mobile-payment-market). **NOT FOUND** for fees |
| SoftPOS framework (2026) | CBE enabled phone-as-POS acceptance to cut acceptance costs | Technicians could accept cards on their phones through a PSP SoftPOS | [ME Observer](https://meobserver.news/?p=158523) |

**Compliant fund-flow architecture (recommended):**
1. **Marketplace order:** the customer pays → **Paymob MarketPlace (split)**. The technician's share is paid out to their wallet or bank. The platform's commission is settled to the platform's merchant account. The platform never holds the technician's money.
2. **Dues:**
   - **Option A (free):** InstaPay or wallet transfer **straight to the union's bank account or IPA**. The app only issues the request, reads the proof (AI on the screenshot or SMS) and issues the receipt.
   - **Option B (card / Fawry):** Paymob or Fawry **sub-merchant per union**, settled to the union's account.
3. **Cash with the technician:** the technician tops up a **prepaid commission balance** using InstaPay to the platform's account. The platform deducts its commission per job. This is the platform collecting **its own fee**, not third-party funds, so it falls outside the licensing perimeter. Lawyer confirmation is still needed (ESTIMATE / legal opinion required).

---

## 5. Can a union, treasurer or compound manager legally receive digital dues in 2026?

| Question | Answer | Evidence |
|---|---|---|
| Does an occupants' union have legal personality? | **Yes, from registration** with the local unit (الوحدة المحلية / الحي), under Building Law 119/2008. The article number differs by source (76 per Youm7; 204 of the Executive Regulations per a law firm) | [Youm7](https://www.youm7.com/story/2022/9/18/%D8%A7%D9%84%D9%82%D8%A7%D9%86%D9%88%D9%86-%D9%8A%D8%AD%D8%AF%D8%AF-%D9%85%D9%87%D8%A7%D9%85-%D8%A7%D8%AA%D8%AD%D8%A7%D8%AF-%D8%A7%D9%84%D8%B4%D8%A7%D8%BA%D9%84%D9%8A%D9%86-%D9%88%D9%8A%D9%85%D9%86%D8%AD%D9%87-%D8%A7%D9%84%D8%B4%D8%AE%D8%B5%D9%8A%D8%A9-%D8%A7%D9%84%D8%A7%D8%B9%D8%AA%D8%A8%D8%A7%D8%B1%D9%8A%D8%A9-%D8%A8%D9%85%D8%AC%D8%B1%D8%AF-%D9%82%D9%8A%D8%AF%D9%87/5910169), [Aziz Avocate](https://azizavocate.com/2024/06/%D8%A7%D9%84%D9%84%D8%A7%D8%A6%D8%AD%D8%A9-%D8%A7%D9%84%D8%AA%D9%86%D9%81%D9%8A%D8%B0%D9%8A%D8%A9-%D8%A7%D8%AA%D8%AD%D8%A7%D8%AF-%D8%A7%D9%84%D8%B4%D8%A7%D8%BA%D9%84%D9%8A%D9%86.html) |
| Can it open a bank account? | **Yes.** The Executive Regulations let the union open an account at a bank and notify the bank of the cheque signatories (president + treasurer) | [Aziz Avocate](https://azizavocate.com/2024/06/%D8%A7%D9%84%D9%84%D8%A7%D8%A6%D8%AD%D8%A9-%D8%A7%D9%84%D8%AA%D9%86%D9%81%D9%8A%D8%B0%D9%8A%D8%A9-%D8%A7%D8%AA%D8%AD%D8%A7%D8%AF-%D8%A7%D9%84%D8%B4%D8%A7%D8%BA%D9%84%D9%8A%D9%86.html); search summary of the published regulation text (Art. 222 per one site) |
| Who handles money? | The **treasurer** collects the financial obligations, deposits them in and withdraws them from banks, and prepares the budget and final accounts. Resources = obligations set by the General Assembly + investment returns + donations | Search summary of [mohamymasr](https://mohamymasr.com/%D8%A5%D8%AA%D8%AD%D8%A7%D8%AF-%D8%A7%D9%84%D8%B4%D8%A7%D8%BA%D9%84%D9%8A%D9%86-%D9%81%D9%89-%D8%A7%D9%84%D9%85%D8%A8%D8%A7%D9%86%D9%8A-%D8%A7%D9%84%D9%85%D8%B3%D8%AA%D8%A3%D8%AC%D8%B1%D8%A9-%D8%A7/) and [Shahid Law / shandpartners](https://www.shandpartners.com/maintenance-deposit-under-egyptian-laws/) |
| Receipts | **Amounts must be collected against receipts** (إيصالات) | [Aziz Avocate](https://azizavocate.com/%D9%84%D8%A7%D8%A6%D8%AD%D8%A9-%D9%82%D8%A7%D9%86%D9%88%D9%86-%D8%A7%D8%AA%D8%AD%D8%A7%D8%AF-%D8%A7%D9%84%D8%B4%D8%A7%D8%BA%D9%84%D9%8A%D9%86-%D8%B4%D8%B1%D8%AD-%D8%A7%D9%84%D9%85%D9%88%D8%A7%D8%AF/) |
| Can it contract maintenance companies? | Yes. Art. 76 lets the union contract maintenance firms registered with the Egyptian Federation for Construction and Building Contractors | [Youm7](https://www.youm7.com/story/2022/9/18/%D8%A7%D9%84%D9%82%D8%A7%D9%86%D9%88%D9%86-%D9%8A%D8%AD%D8%AF%D8%AF-%D9%85%D9%87%D8%A7%D9%85-%D8%A7%D8%AA%D8%AD%D8%A7%D8%AF-%D8%A7%D9%84%D8%B4%D8%A7%D8%BA%D9%84%D9%8A%D9%86-%D9%88%D9%8A%D9%85%D9%86%D8%AD%D9%87-%D8%A7%D9%84%D8%B4%D8%AE%D8%B5%D9%8A%D8%A9-%D8%A7%D9%84%D8%A7%D8%B9%D8%AA%D8%A8%D8%A7%D8%B1%D9%8A%D8%A9-%D8%A8%D9%85%D8%AC%D8%B1%D8%AF-%D9%82%D9%8A%D8%AF%D9%87/5910169) |
| Is there an Egyptian bank product called "اتحاد ملاك/شاغلين account"? | **NOT FOUND.** No NBE, Banque Misr, CIB or HDB product page names one. Unions open a standard **legal-entity current account** under the corporate tariff | Searches; [Banque Misr corporate tariff](https://www.banquemisr.com/-/media/Corporate-Tarrif/Corporate-Tarrif--Eng.ashx) |
| What about compounds run by a developer or a management company? | The management company is a normal company and collects through PSPs. **Fawry already lists 20+ compounds as billers**, and owners pay maintenance in myFawry. A **draft developers' law (Oct 2026)** would require per-project escrow accounts | [Fawry](https://www.fawry.com/business/payment-and-collection/), [Daily News Egypt](https://www.dailynewsegypt.com/2026/10/04/egypt-drafts-new-real-estate-developers-law-with-escrow-accounts-buyer-protection-funds/) |
| Unregistered building (most old Cairo buildings, informal "treasurer") | The informal treasurer receives money personally. That is legal as a private arrangement, but there is no legal personality, so all money sits in the treasurer's **personal** account | ESTIMATE / legal inference; consistent with file 09 |

**Product implication:**
1. Build a **"Register your union" wizard** (forms, General Assembly minutes template, a checklist for the district office). It is a moat feature: registered unions can then open a bank account and receive InstaPay to an **IPA such as `union-name@bank`**.
2. For unregistered buildings, collect dues to the **treasurer's personal InstaPay or wallet**, with **AI-reconciled receipts in the app**. Show a full public ledger to every resident, which removes the trust problem. The platform never touches the money.
3. Offer compounds a **Fawry biller listing or Paymob sub-merchant** through the app's B2B dashboard.

---

## 6. BNPL, insurance and advertising economics

| Line | Data found | Status |
|---|---|---|
| valU merchant fee / referral | Not published. valU offers P2P BNPL (with MobileMasr, 2025) and is EGX-listed | **NOT FOUND**; [Wamda](https://www.wamda.com/2025/09/valu-offers-egypt-p2p-bnpl-solution-mobilemasr) |
| Souhoola | 1,600+ merchant partners, 130k+ users (2024), up to 60-month plans, live on Network International POS. Fees not published | **NOT FOUND**; [Network International](https://www.network.ae/en/about-us/press-and-media/news/network-international-partners-with-souhoola-to-power-bnpl-acceptance-on-its-networkpay-point-of-sale-devices-boosting-financial-inclusion-in-egypt) |
| Halan, Contact, Sympl, Aman | Available through Paymob checkout | **NOT FOUND** for fees; [Paymob](https://paymob.com/llms.txt) |
| Egyptian BNPL merchant cost (generic) | ~7% (unattributed); global 2–8% | Low confidence; [Digitology](https://digitology.co/payment-gateway-egypt/) |
| Amenli (FRA-licensed insurtech) | Medical, car, home and business insurance; embedded-insurance API; Careem partnership | **Commission NOT FOUND**; [Egyptian Streets](https://egyptianstreets.com/2024/09/19/amenli-transforming-egypts-insurance-market-with-convenience-speed-and-reliability/), [TechCrunch](https://techcrunch.com/2021/10/05/yc-backed-amenli-raises-2-3m-to-provide-insurance-to-egyptian-consumers/) |
| Fawry digital insurance | 1.1M digital policies (FY2025) | File 03 ([Zawya](https://www.zawya.com/en/press-release/companies-news/fawry-releases-fy2025-results-356861)) |
| AdMob eCPM, Egypt | ~**US$0.29** blended (2025, weak methodology) | Low; [thesrzone](https://www.thesrzone.com/2024/01/admob-ecpm-rates-by-country.html) |
| AdMob eCPM, tier-3 by format (2026) | Rewarded $2–3, interstitial $1–2, anchored banner $0.08–0.14 | Medium; [RevenueLab](https://www.revenuelab.fyi/blog/admob-ecpm-benchmarks-2026) (search snippet; page body did not load) |
| Meta CPM | Global average ~$5.97 (2025, 5,200 accounts). No Egypt figure found | **Egypt NOT FOUND**; [Vaizle](https://insights.vaizle.com/facebook-ad-benchmarks/) |

**ESTIMATE: ad revenue per user.**
- Assumptions: 8 sessions per MAU per month; one anchored banner per session plus one rewarded ad per month. Revenue = 8 × $0.29/1000 + 1 × $2.5/1000 ≈ **$0.005 per MAU per month**, or about **EGP 0.25 per MAU per month**.
- At 200k MAU that is about **US$1,000/month**, which is negligible and harms the brand.
- **Conclusion:** keep programmatic ads out. Monetise attention through **direct hyper-local sponsorship**, as recommended in file 14 §6.

**ESTIMATE: BNPL and insurance referral.**
- Egyptian lead-gen partners typically negotiate **a fixed CPA (for example EGP 50–150 per activated BNPL customer) or 0.5–2% of the financed amount**. Insurance distributors earn **10–20% of premium** under FRA brokerage norms.
- **None of this is verified.** Get term sheets from valU, Souhoola, Halan, Amenli and Fawry Insurance Brokerage before modelling.

---

## 7. Recomputed unit economics (ESTIMATE, using the verified rates above)

Assumptions:
- 14% VAT applies to the platform's commission and fees, so platform revenue is shown **VAT-inclusive**, then net.
- Paymob rate 2.75% + 3; FawryPay wallet QR 1.5% + 3; InstaPay 0.1%.

### 7.1 One marketplace order: AC service + freon (or an equivalent mid-ticket repair)

| Line | EGP | Basis |
|---|---|---|
| Job price to customer (labour) | **1,200** | Freon 1,000–1,200 (§1 #8); electrical job 890–1,500 (#5) |
| Customer service fee (flat) | 20 | Recommended (§8) |
| **Total customer pays** | **1,220** | |
| Technician commission at 12% of labour | 144 | Recommended (§8) |
| **Platform gross revenue (VAT-incl.)** | **164** | 144 + 20 |
| Less VAT 14/114 | −20.1 | Egyptian VAT 14% |
| **Net revenue** | **143.9** | |
| **Scenario A: card via Paymob split** (fee on 1,220) | −36.6 | 1,220 × 2.75% + 3 |
| **Scenario B: wallet QR via FawryPay** | −21.3 | 1,220 × 1.5% + 3 |
| **Scenario C: cash to technician; commission deducted from a prepaid balance topped up by InstaPay** | −0.2 | Top-up fee is borne by the technician (≤ EGP 20 per top-up, spread across ~10 jobs) |
| AI-first support and disputes | −8 | ESTIMATE (≈ 1 human minute + LLM tokens; file 14 §3) |
| Guarantee reserve (2.5% of labour; 30-day re-visit) | −30 | ESTIMATE |
| Technician-side incentives (first-job bonus, amortised) | −5 | ESTIMATE |
| **Contribution: A / B / C** | **64 / 80 / 101** | |
| Contribution as % of GMV, A / B / C | 5.3% / 6.5% / 8.3% | |

- **Small-ticket check (EGP 300 plumbing fix, 12% + EGP 15 fee, card):** revenue 51 incl. VAT = 44.7 net; Paymob −11.7; support −8; reserve −7.5 → **≈ EGP 17.5 contribution**. Small jobs only work if they are **cash or wallet** and **AI-handled**.
- **Big-ticket check (EGP 20,000 painting project at 6% + BNPL):** revenue 1,200 incl. VAT = 1,053 net; Paymob −553 if the platform pays the gateway fee on the full value (it should not: **pass the fee to the customer or contractor**); reserve 1% −200 → **EGP 300–850**, depending on who bears the gateway fee.

### 7.2 One dues payment (EGP 600/month)

| Rail | Cost | Who bears it | Platform revenue | Platform margin |
|---|---|---|---|---|
| InstaPay to the union or treasurer (Option A) | EGP 0.60 | Resident | 0, or an EGP 3 "smart receipt" fee (opt-in, ESTIMATE) | 0 to ~2.6 net of VAT; AI reconciliation cost ~EGP 0.05 (file 14) |
| Wallet QR via FawryPay sub-account | EGP 12.00 (2.0%) | Resident convenience fee, shown as such | Optional mark-up of EGP 3 | ~2.6 |
| Card via Paymob | EGP 19.50 (3.25%) | Resident convenience fee | Optional mark-up of EGP 3 | ~2.6 |
| Fawry reference code (cash at outlet) | EGP 19.66 (incl. SMS) | Resident | Optional mark-up of EGP 3 | ~2.6 |
| FawryPay fixed cost | EGP 999 setup + EGP 499/month minimum | Platform | — | Needs ≥ ~42 wallet payments of EGP 600 per month to cover the minimum (499 ÷ 12) |

**Conclusion:** dues collection is a **retention and data engine, not a profit line**. The money in dues comes from:
- (a) a **building SaaS** for the treasurer (ledger, receipts, reminders, AI bookkeeping), at EGP 50–150 per building per month, paid by large or compound unions only (ESTIMATE);
- (b) **routing building-level purchases** (elevator AMC, tank cleaning, pumps, painting) through the marketplace.

### 7.3 Building-level (B2B) order: elevator AMC

| Line | EGP / month |
|---|---|
| AMC price per lift | 350–800 (§1 #21) |
| Referral take, 10% recurring | 35–80 |
| Less VAT | 31–70 net |
| Payment cost (InstaPay from the union account) | ~0.4–0.8 |
| **Annual contribution per lift** | **~EGP 370–840** |

Five recurring B2B contracts per building (lift, tank, staircase cleaning, pest control, pump service) could yield **EGP 1,500–3,000 per building per year** (ESTIMATE). That is more than most residents' individual service spend, at near-zero leakage risk, because the union pays from a documented account.

---

## 8. Recommended take rate and pricing strategy by category

| Category | Price model | Technician / vendor take | Customer fee | Anti-leakage reasoning |
|---|---|---|---|---|
| Plumbing, electrical, carpentry, appliance (open-ended) | Inspection EGP 120–150, **credited to the job** if booked in-app; quote approved in-app | **10–12% of labour**, capped at EGP 150 per job | EGP 15 flat | Low commission plus a cap removes the incentive to go offline. The 30-day **warranty is valid only if the quote was approved and paid through the app**. The inspection credit is lost if the job leaves the app |
| AC service, freon, install (seasonal, menu-priced) | **Fixed menu** (copy Taskty's structure) | **15%** | EGP 20 | Menu prices plus a pre-sold "summer pack" for the whole building; group booking day per building (one truck, 10 flats) cuts the technician's cost, so they accept 15% |
| Home cleaning (repeat) | Fixed per visit or package | **20% first job → 10% on repeats** inside a subscription | EGP 0 on subscription | Cleaners are the highest-leakage category (Homejoy lesson). A subscription with insurance, replacement guarantee and auto-pay makes in-app booking cheaper than a direct arrangement |
| Pest control (company-delivered) | Fixed menu | **15–20%** | EGP 20 | Delivered by companies with 6–8-month warranties (Taskty), so leakage risk is low. Building-wide spraying is sold to the union |
| Moving | Quote marketplace (3 quotes) | **8–10%**, or EGP 150–300 lead fee | 0 | Movers are companies; charge only for accepted quotes |
| Painting, finishing, tiling (big ticket) | Quote + **BNPL** (valU, Souhoola via Paymob) | **5–8%**, or a lead fee | 0 | High ticket means even 5% is a large absolute amount. Milestone payments in-app protect the customer, and that protection is the reason to stay in-app |
| Elevator AMC, tank cleaning, staircase cleaning, pumps (B2B, union-paid) | Annual or monthly contract signed in-app | **8–12% recurring referral** from the vendor | 0 | Contract, invoices and union approvals (General Assembly vote) live in the app, which makes switching costly |
| Internet, satellite, utilities | Affiliate | Fixed CPA (ESTIMATE EGP 50–150) | 0 | Telco-installed; no leakage issue |
| BNPL, insurance | Referral | Per partner term sheet (**NOT FOUND**) | 0 | — |

**Pricing rules:**
1. **Total platform take ≤ ~15% of the customer's bill** on everyday jobs. That is below Uber's ~27% and close to inDrive's ~10%, the two commission levels Egyptian gig workers already know.
2. **Pass card fees through** ("convenience fee"). Steer users to **wallet or InstaPay** with a small discount.
3. **No commission on parts** (pass-through at receipt cost, photographed). This removes the main source of overcharging complaints (file 06).
4. **Technician subscription alternative:**
   - Pro plan, EGP 300–500/month (ESTIMATE): 0% commission on repeat customers in "their" buildings, priority leads.
   - This makes the platform worth more to the best technicians than taking jobs offline.
5. **Price transparency as a weapon:** show the HomeRun-style "typical price in your district" range in-app, sourced from the platform's own completed jobs. Technicians cannot replicate this offline, and it builds customer trust.

---

## 9. Remaining gaps and the cheapest way to close them

| Gap | Action (zero budget) |
|---|---|
| Real technician commissions (FilKhedma, Fixawy, Taskty) | Register as a technician on each technician app or form and record the contract terms. Interview 10 technicians in a WhatsApp group: "how much does X take?" |
| Paymob per-method, split and payout fees | Request a sales quote, specifically for "marketplace split + wallet payout + InstaPay collection" |
| Fawry biller onboarding for unions, Khales, Sahl | Fawry Business sales; e-finance (Khales) partnerships; Sahl B2B ([sahlpay](https://sahlpay.app/Companies)) — no public terms |
| valU, Souhoola, Halan, Contact, Amenli referral fees | Partnership emails; ask for a CPA term sheet |
| Elevator AMC from Schindler, Kone, Otis Egypt | Ask 3 buildings in the pilot for their current contracts (photo of the invoice) |
| Egypt AdMob / Meta CPM | Run a 1-week EGP 500 Meta test, or read the AdMob report after launch |
| Exact article numbers of Law 119/2008 Executive Regulations on bank accounts | Read the official PDF (PM Decree 144/2009) or get a 1-hour lawyer consult |

---

## 10. Verification log

| # | Claim | Sources | Status |
|---|---|---|---|
| 1 | Paymob 2.75% + EGP 3, no monthly fee | paymob.com/en/pricing (fetched today) + Digitology Aug 2026 | **Confirmed (2 sources)**. Settlement weekly (Paymob page) vs T+1 (WooCommerce, Digitology): **conflict**, so confirm in the contract |
| 2 | Kashier 2.85% + EGP 3, no setup | Kashier FAQ (search) + KrASIA + Digitology | Confirmed (3); kashier.io/pricing refused the connection today |
| 3 | FawryPay 999 setup, 499 monthly minimum, 2.75% / 1.5% QR + 3 | atfawry.com/pricing (fetched today) | Confirmed (official); a third party repeats 2.75% + 3 |
| 4 | InstaPay 0.1%, min 0.50, max 20 | Ahram (fetched) + Egyptian Streets + Amwal Al Ghad | Confirmed; min EGP 1 per Egypt Independent (minor conflict) |
| 5 | Vodafone Cash 1 EGP on-net; 0.5% (1–15) off-net | Vodafone page + MomoCalc + MobileMasr | Confirmed (consumer) |
| 6 | CBE PSP rules June 2025; Cat B 10M, Cat A 30M; transition to June 2026 | Matouk Bassiouny (fetched) + Legal500 (fetched) + Daily News Egypt | Confirmed |
| 7 | Union legal personality on registration; bank account allowed | Youm7 (fetched) + Aziz Avocate (fetched) | Confirmed in substance; article numbers inconsistent |
| 8 | Taskty menu: 120 inspection, AC 1,300–1,700, freon 1,200, pest 1,050–1,700, cleaning 520–1,000 | taskty.com/Offers (fetched today) | Confirmed live; freshness uncertain (old COVID items still listed) |
| 9 | HomeRun plumber jobs 250–3,000 (Feb–Oct 2026) | HomeRun (fetched today) | Confirmed |
| 10 | AC install 850–1,400 | HomeRun + Misr Cool + Carrier agent | Confirmed (3) |
| 11 | Pest control 800–1,700 | Taskty + German Pest + Falcon German | Confirmed (3) |
| 12 | Moving 1,500–4,000 (3BR Cairo, no packing) | Al-Haramain + Naser Trans + El-Khabeer + HomeRun | Confirmed (4; vendor sites) |
| 13 | Elevator AMC from 350/month | Misr Elevator (fetched) | Single vendor source; **low confidence** |
| 14 | Water-tank cleaning 400–3,000 | City Clean | Single source; **low confidence** |
| 15 | Painting labour 25–100/m² | 4 vendor sites + Taskty | Confirmed range |
| 16 | Khidmitty 20–25%, Sal7lyy 30–50% | Gust (file 03); re-fetch returned 403 today | Not re-verified |
| 17 | FilKhedma 30% | — | **NOT FOUND / unverified** |
| 18 | Uber Egypt 26.67%, inDrive 9.9% | 2022 press via search summary | Old; not re-fetched |
| 19 | Egypt AdMob $0.29 | thesrzone | **Low confidence** |
| 20 | Minimum wage 7,000 from Mar 2025 | banker.news (search) | Confirmed; a 2026 increase is not yet decided |
| 21 | Fawry lists 20+ compounds as billers | fawry.com (search) | Confirmed |
| 22 | No Egyptian bank "union account" product | Searches of NBE, Banque Misr, CIB, BdC | **NOT FOUND** (absence of evidence) |

---

## 11. Sources

**Prices**
- Taskty offers menu: https://taskty.com/Offers · AC offer: https://taskty.com/Offers/OfferDetails/2149
- HomeRun Egypt: plumber https://homerun.com.eg/costs-prices/%D8%B3%D8%A8%D8%A7%D9%83_16342 · electrical https://homerun.com.eg/costs-prices/القاهرة-صيانة-كهرباء_42102_30098 · AC maintenance https://homerun.com.eg/costs-prices/القاهرة-صيانة-تكييف_604_30098 · freon https://homerun.com.eg/costs-prices/القاهرة-شحن-فريون-التكييف_8238_30098 · AC install https://homerun.com.eg/costs-prices/%D8%A7%D9%84%D9%82%D8%A7%D9%87%D8%B1%D8%A9-%D8%AA%D8%B1%D9%83%D9%8A%D8%A8-%D8%AA%D9%83%D9%8A%D9%8A%D9%81_40729_30098 · painter https://homerun.com.eg/costs-prices/القاهرة-نقاش_46467_30098 · appliances https://homerun.com.eg/costs-prices/القاهرة-صيانة-اجهزة-منزلية_36860_30098 · cleaning https://homerun.com.eg/costs-prices/%D8%AA%D9%86%D8%B8%D9%8A%D9%81-%D8%B4%D9%82%D9%82_41862 · moving https://homerun.com.eg/costs-prices/%D8%A7%D9%84%D9%82%D8%A7%D9%87%D8%B1%D8%A9-%D9%86%D9%82%D9%84-%D8%B9%D9%81%D8%B4_16341_30098 · carpenter https://homerun.com.eg/%D9%86%D8%AC%D8%A7%D8%B1
- Misr Elevator AMC: https://misrelevator.com/%D8%AA%D9%83%D9%84%D9%81%D8%A9-%D8%B5%D9%8A%D8%A7%D9%86%D8%A9-%D8%A7%D9%84%D8%A7%D8%B3%D8%A7%D9%86%D8%B3%D9%8A%D8%B1/ · villa elevators https://lec-egy.com/%D8%A3%D8%B3%D8%B9%D8%A7%D8%B1-%D9%85%D8%B5%D8%A7%D8%B9%D8%AF-%D8%A7%D9%84%D9%81%D9%84%D9%84/ · parts https://matrix-elevator.com/%D8%A7%D8%B3%D8%B9%D8%A7%D8%B1-%D9%82%D8%B7%D8%B9-%D8%BA%D9%8A%D8%A7%D8%B1-%D8%A7%D9%84%D9%85%D8%B5%D8%A7%D8%B9%D8%AF/
- AC: https://airconditioningeg.com/%D8%A3%D8%B3%D8%B9%D8%A7%D8%B1-%D8%AA%D8%B1%D9%83%D9%8A%D8%A8-%D8%A7%D9%84%D8%AA%D9%83%D9%8A%D9%8A%D9%81-%D9%81%D9%8A-%D9%85%D8%B5%D8%B1/ · https://carrier-egy.net/Carrierairconditioninginstallationnumbers · https://sharpegy.com/sharp-conditioning/ · Dubizzle Suez https://www.dubizzle.com.eg/services/suez-district/
- Pest: https://www.germanpest.com/ar/%D8%A7%D8%B3%D8%B9%D8%A7%D8%B1-%D9%85%D9%83%D8%A7%D9%81%D8%AD%D8%A9-%D8%A7%D9%84%D8%AD%D8%B4%D8%B1%D8%A7%D8%AA-%D9%81%D9%8A-%D9%85%D8%B5%D8%B1/%D8%A7%D9%84%D8%A7%D8%B3%D8%B9%D8%A7%D8%B1/ · https://falcongerman.com/%D8%A7%D8%B1%D9%82%D8%A7%D9%85-%D8%B4%D8%B1%D9%83%D8%A7%D8%AA-%D8%B1%D8%B4-%D8%A7%D9%84%D8%AD%D8%B4%D8%B1%D8%A7%D8%AA · https://insectscenter.com/%D8%A7%D8%B3%D8%B9%D8%A7%D8%B1-%D9%85%D9%83%D8%A7%D9%81%D8%AD%D8%A9-%D8%A7%D9%84%D8%AD%D8%B4%D8%B1%D8%A7%D8%AA-2026-%D8%A7%D9%84%D8%A3%D9%84%D9%85%D8%A7%D9%86%D9%8A%D8%A9-%D8%A7%D9%84%D8%A3/
- Painting: https://hashmistone.com/1883/cost-meter-painting-today/ · https://buildora-group.com/%D8%B3%D8%B9%D8%B1-%D9%85%D8%AA%D8%B1-%D8%A7%D9%84%D9%86%D9%82%D8%A7%D8%B4%D9%87/ · https://golden-view-eg.com/%D8%AA%D9%83%D9%84%D9%81%D8%A9-%D9%86%D9%82%D8%A7%D8%B4%D8%A9-%D8%B4%D9%82%D8%A9-120-%D9%85%D8%AA%D8%B1/ · https://kaydc-eg.com/%D8%AA%D9%83%D9%84%D9%81%D8%A9-%D8%AF%D9%87%D8%A7%D9%86-%D8%B4%D9%82%D8%A9-100-%D9%85%D8%AA%D8%B1/
- Moving: https://alharamain-afsh.com/%D8%A7%D8%B3%D8%B9%D8%A7%D8%B1-%D9%86%D9%82%D9%84-%D8%A7%D9%84%D8%B9%D9%81%D8%B4-%D9%81%D9%8A-%D9%85%D8%B5%D8%B1/ · https://nasertrans.com/%D8%A3%D8%B3%D8%B9%D8%A7%D8%B1-%D9%86%D9%82%D9%84-%D8%A7%D9%84%D8%B9%D9%81%D8%B4-%D9%81%D9%8A-%D9%85%D8%B5%D8%B1/ · https://el-khabeer.com/%D8%A3%D8%B3%D8%B9%D8%A7%D8%B1-%D9%86%D9%82%D9%84-%D8%A7%D9%84%D8%A3%D8%AB%D8%A7%D8%AB-%D9%81%D9%8A-%D9%85%D8%B5%D8%B1-2026/
- Water tanks: https://cityclean-eg.com/%D8%AA%D9%86%D8%B8%D9%8A%D9%81-%D9%88%D8%AA%D8%B7%D9%87%D9%8A%D8%B1-%D8%AE%D8%B2%D8%A7%D9%86%D8%A7%D8%AA-%D9%85%D9%8A%D8%A7%D9%87-%D8%A7%D9%84%D8%B4%D8%B1%D8%A8 · pumps https://www.waterinegypt.com/%D8%A7%D9%81%D8%B6%D9%84-%D9%85%D9%88%D8%A7%D8%AA%D9%8A%D8%B1-%D8%A7%D9%84%D9%85%D9%8A%D8%A7%D9%87-%D8%A7%D9%84%D8%A7%D9%8A%D8%B7%D8%A7%D9%84%D9%8A-1-%D8%AD%D8%B5%D8%A7%D9%86/
- Satellite, internet, CCTV: https://electro-eg.com/%D8%A7%D8%B3%D8%B9%D8%A7%D8%B1-%D8%A7%D8%B7%D8%A8%D8%A7%D9%82-%D8%A7%D9%84%D8%AF%D8%B4-%D9%81%D9%8A-%D9%85%D8%B5%D8%B1-2025-%D9%85%D8%B9-%D8%AF%D9%84%D9%8A%D9%84-%D8%B4%D8%A7%D9%85%D9%84-%D9%84%D9%84/ · https://www.prices2day.net/2021/04/landline-installation-prices.html · https://mobilemasr.com/blogs/we-air-router-without-a-landline-4g · https://www.elbalad.news/6970319 · https://www.pricesworld.net/?p=54191
- Wages: https://banker.news/144869 · https://gate.ahram.org.eg/News/5608267.aspx · https://mosta3ed.com/?p=48920&post_type=jobs
- Fixawy history: https://www.cairo360.com/ar/article/%D8%AA%D8%B3%D9%88%D9%82/%D8%A3%D9%81%D8%B6%D9%84-3-%D8%AA%D8%B7%D8%A8%D9%8A%D9%82%D8%A7%D8%AA-%D8%AA%D8%B7%D9%84%D8%A8-%D9%85%D9%86%D9%87%D9%85-%D8%B5%D9%86%D8%A7%D9%8A%D8%B9%D9%8A-%D9%84%D8%A3%D8%B9%D8%B7%D8%A7%D9%84/

**Commissions**
- Gust Sal7lyy https://gust.com/companies/%D8%B5%D9%84%D8%AD%D9%84%D9%8A · Gust Khidmitty https://gust.com/companies/Khidmitty-s-startup-2/financials · Gust Osta https://gust.com/companies/osta0
- FilKhedma: https://play.google.com/store/apps/details?id=com.filkhedma.customer&hl=en_US · https://www.wamda.com/en/2021/12/filkhedma-receives-new-investment-cairo-angels
- Bricole https://bricoleapp.com/ar/eg/ · Sanayeya https://maashahir.com/archives/1620
- Urban Company https://www.freepressjournal.in/business/urban-company-cuts-commission-to-25-from-30-after-workers-protest · https://inc42.com/?p=571319 · https://www.spglobal.com/market-intelligence/en/news-insights/research/2026/04/urban-company-revenue-to-triple-by-2030-as-take-rates-and-platform-monetization-rise
- Uber / inDrive Egypt https://www.aljazeera.net/ebusiness/2021/9/2/منافسون-على-الطريق-هل-تنهي-إن-درايفر · https://almalnews.com/793679/ · https://www.cairo24.com/1619669
- Talabat https://fabsresearch.bankfab.com/ResearchPortal/Download/Index/961

**Payments and regulation**
- Paymob https://paymob.com/en/pricing · https://paymob.com:443/en/marketplace · https://paymob.com/llms.txt · https://woocommerce.com/products/paymob/
- Kashier https://kashier.io/en/faqs · https://kr-asia.com/egyptian-payments-platform-kashier-raises-six-figure-seed
- Fawry https://atfawry.com/pricing · https://www.fawry.com/business/payment-and-collection/ · https://www.fawry.com/consumer/bill-payment/ · https://flutterwave.com/gh/support/payments/fawry-pay-faq-egypt
- Geidea https://geidea.net/egypt/en/online-selling/pay-by-link · Digitology comparison https://digitology.co/payment-gateway-egypt/
- InstaPay https://english.ahram.org.eg/NewsContent/1/2/543590/Egypt/Society/InstaPay-to-apply-charges-starting--April.aspx · https://egyptianstreets.com/2025/04/03/instapay-now-charging-transfer-fees · https://www.egyptindependent.com/instapay-updates-fees-and-tariffs-for-money-transfers/ · https://enterpriseam.com/egypt/2026/04/06/instapay-hits-profitability-as-demand-keeps-up-one-year-into-0-1-transaction-fee/ · https://www.photonpay.com/hk/blog/article/instapay-egypt?lang=en
- Vodafone Cash https://web.vodafone.com.eg/en/money-transfer · https://momocalc.com/egypt/en/vodafone-cash-fees
- CBE rules https://matoukbassiouny.com/egypts-central-bank-issues-the-licensing-framework-for-psos-and-psps/ · https://www.legal500.com/intelligence/egypt/finance-and-banking/fintech-license-in-egypt-cbe-fra-licensing-guide · https://www.dailynewsegypt.com/2025/06/21/cbe-issues-new-licensing-framework-for-electronic-payment-service-providers/ · https://www.cbe.org.eg/en/news-publications/news/2025/09/01/13/10/payment-system-operators-and-payment-service-providers · https://en.amwalalghad.com/?p=187926 · https://meobserver.news/?p=158523
- Banque Misr tariff https://www.banquemisr.com/-/media/Corporate-Tarrif/Corporate-Tarrif--Eng.ashx · Draft developers' law https://www.dailynewsegypt.com/2026/10/04/egypt-drafts-new-real-estate-developers-law-with-escrow-accounts-buyer-protection-funds/

**Union law**
- https://www.youm7.com/story/2022/9/18/%D8%A7%D9%84%D9%82%D8%A7%D9%86%D9%88%D9%86-%D9%8A%D8%AD%D8%AF%D8%AF-%D9%85%D9%87%D8%A7%D9%85-%D8%A7%D8%AA%D8%AD%D8%A7%D8%AF-%D8%A7%D9%84%D8%B4%D8%A7%D8%BA%D9%84%D9%8A%D9%86-%D9%88%D9%8A%D9%85%D9%86%D8%AD%D9%87-%D8%A7%D9%84%D8%B4%D8%AE%D8%B5%D9%8A%D8%A9-%D8%A7%D9%84%D8%A7%D8%B9%D8%AA%D8%A8%D8%A7%D8%B1%D9%8A%D8%A9-%D8%A8%D9%85%D8%AC%D8%B1%D8%AF-%D9%82%D9%8A%D8%AF%D9%87/5910169
- https://azizavocate.com/2024/06/%D8%A7%D9%84%D9%84%D8%A7%D8%A6%D8%AD%D8%A9-%D8%A7%D9%84%D8%AA%D9%86%D9%81%D9%8A%D8%B0%D9%8A%D8%A9-%D8%A7%D8%AA%D8%AD%D8%A7%D8%AF-%D8%A7%D9%84%D8%B4%D8%A7%D8%BA%D9%84%D9%8A%D9%86.html
- https://mohamymasr.com/%D8%A5%D8%AA%D8%AD%D8%A7%D8%AF-%D8%A7%D9%84%D8%B4%D8%A7%D8%BA%D9%84%D9%8A%D9%86-%D9%81%D9%89-%D8%A7%D9%84%D9%85%D8%A8%D8%A7%D9%86%D9%8A-%D8%A7%D9%84%D9%85%D8%B3%D8%AA%D8%A3%D8%AC%D8%B1%D8%A9-%D8%A7/
- https://www.shandpartners.com/maintenance-deposit-under-egyptian-laws/

**BNPL, insurance, ads**
- https://www.wamda.com/2025/09/valu-offers-egypt-p2p-bnpl-solution-mobilemasr · https://www.network.ae/en/about-us/press-and-media/news/network-international-partners-with-souhoola-to-power-bnpl-acceptance-on-its-networkpay-point-of-sale-devices-boosting-financial-inclusion-in-egypt · https://egyptianstreets.com/2024/09/19/amenli-transforming-egypts-insurance-market-with-convenience-speed-and-reliability/ · https://www.thesrzone.com/2024/01/admob-ecpm-rates-by-country.html · https://www.revenuelab.fyi/blog/admob-ecpm-benchmarks-2026 · https://insights.vaizle.com/facebook-ad-benchmarks/
