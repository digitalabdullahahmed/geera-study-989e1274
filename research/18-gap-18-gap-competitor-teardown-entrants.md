# 18 — Competitor Teardown, New Entrants and Threat Scan (Gap-Filling)

> **Research date:** 2026-10-12. **Market:** Egypt only (Arab and international players are included for ideas and for threat context).
> **Purpose:** Fill the gaps left by files 01–04:
> - conflicting install numbers;
> - no inspection of the Amarati and Imarti business models;
> - no feature-by-feature teardown of the main products;
> - no iOS data;
> - no traction numbers for Arab apps;
> - almost no coverage of the Egyptian giants next door to this market.
>
> **Notation:**
> - **ESTIMATE** marks my own inference, with the reasoning given.
> - **[self-reported]** marks a vendor's own claim.
> - **[unverified]** marks a claim I could not confirm with a second source.
> - **Not found** means I searched and found nothing. It does not prove the thing doesn't exist.

---

## 0. Executive summary (the 12 things that matter)

1. **The conflicting install numbers are resolved.** Google Play's page data contains an exact install counter. I pulled it with `google-play-scraper` (country=eg) on 2026-10-12. Amarati has **1,416** installs (bucket "1K+"). Imarti has **125** ("100+"). صندوق العمارة has **961** ("500+"). Earlier files that said "not verified" or gave only a bucket were not wrong. They were just less precise. Caveat: the counter is **worldwide**, not Egypt-only (§1.1).
2. **The real leader among ordinary-building apps is not one the founder named.** It is **إتّحاد (Ettihad, `com.ittihad.ettihad`)**:
   - **3,000 installs in 63 days** (released 10 Aug 2026), so about 48 per day;
   - free forever, native on iOS and Android, Arabic and English;
   - an AI assistant ("فاري") that understands voice and text;
   - QR visitor passes, voting, receipt OCR, pay links for non-app users, and passkeys.
   
   Its company is registered in the Netherlands, with a business start date of 11 Aug 2026. **Ettihad is the most direct threat to the founder's phase-1 "free and everywhere" strategy.**
3. **The whole Egyptian ordinary-building category is still tiny.** The 19 building and union apps I found on Play total about **8,900 installs** (sum of exact counters, §2). The largest has 3,000. **Nobody has won yet.**
4. **There is a wave of copycats.** At least **14 new building-ledger apps appeared on Play or the App Store between May and October 2026**: Ettihad, Ammarty, Omaraty, Amarati, Imarti, صندوق العمارة, Homena, Bonian, Darna (×2), BOS, Sandouq Online, اتحاد الملاك (ISG), دفتر العمارة and others. Most are solo-developer ledger tools with fewer than 300 installs. **The barrier to building a ledger app is close to zero, so the ledger is not a moat.** Distribution and network effects are the moat.
5. **Amarati's monetization:** free, with no in-app purchases and no ads declared on Play. "مجاني للبدء" ("free to start") hints at a future paywall. It is built in Palestine and written in Levantine Arabic. **Imarti's monetization:** no in-app purchases declared on either store, despite one Play review complaining "الاشتراكات غاليه اوي" ("the subscriptions are very expensive"). Any plan is probably sold outside the store or isn't live yet [unverified]. Its iOS seller name is "craft future for e commerce". **I could not inspect the admin plans of either app**, because that needs an installed and registered account (§1.3).
6. **Paid ledger apps are converging on 50–110 EGP a month:**
   - صندوق العمارة: 49.99 EGP/month or 499.99 EGP/year;
   - Homena: 109.99–569.99 EGP per item;
   - Sandouq Online: 83.99–839.99 EGP;
   - دفتر العمارة: 30–450 EGP;
   - Saknna: from 450 EGP/month for 5 units.
   
   **Free (Ettihad, Amarati, Unitify's Free tier) is becoming the baseline.** The founder's "free core" stance is necessary but not differentiating.
7. **Compounds are a different, B2B market.** Exact Android counters:
   - Lyve's app family has about **77,300** installs across 8 apps;
   - Milango's has about **82,700** across 6 apps;
   - Emaar Misr's app, 44,478, sits on the Kijamii/Milango package lineage but links to iamlyve.com.
   
   Ratings are weak: SODIC is 3.26★ on Play and **2.22★ on iOS Egypt**, Palm Hills is 2.97★, and New Giza's OneCommunity is 2.42★.
8. **Unitify** is the most capable product: 85+ features, AI concierge, free plan, an Egypt page and Law 119 knowledge. On Play it has **only 688 worldwide installs**, has no rating, and I found no Egyptian press. ESTIMATE: it is a real threat only if it localizes WhatsApp and Egyptian dialect and signs Egyptian facility-management (FM) firms.
9. **The WhatsApp bot idea is not unique.** **Boyot** (Cairo, seed-funded in 2022) advertises a "WhatsApp Chat Bot & integration" for compound operators [self-reported]. Unitify ingests WhatsApp exports for AI reports. Nobody yet sells an **in-group bot for ordinary buildings**.
10. **The adjacent giants are mostly partners, not entrants.**
    - Breadfast (pre-Series C of $50M in Feb 2026, "single app for daily household spending") is the most plausible **phase-2** threat on home services.
    - Fawry, InstaPay, Vodafone Cash and the BNPL players (valU, Halan) are **payment and finance rails to plug into**.
    - The **black swan** is a **government union portal**. Saudi Arabia already runs one ("Mullak").
11. **Arab apps have small traction** (exact Play counters, worldwide):
    - Syndic Connect (Morocco): **8,147**;
    - Binayati (Lebanon): **2,991**;
    - Sukkan (Jordan): 1K+ bucket, 3.6★;
    - Majma'i and Khedma Complex: no Play listing found, 0 iOS ratings.
    
    Nothing in the Arab region proves product-market fit at scale. The scale proof comes from India: **ADDA has 1,149,255 Play installs** and MyGate is covered in file 01.
12. **How to beat them all:** combine what no single competitor has together:
    1. a WhatsApp-native bot inside the existing group;
    2. a free core for treasurer and residents;
    3. Egyptian-dialect voice and AI;
    4. a doorman (بواب) mode;
    5. a union-formation legal kit (Law 119/2008);
    6. a viral loop where each building recruits the next;
    7. later, a trusted services marketplace.
    
    Ettihad already has 2, part of 3 and part of 5. The founder must out-distribute Ettihad within about the next 6–9 months, before someone consolidates the category. That timing is an **ESTIMATE**, based on Ettihad's current growth of about 48 installs a day and the speed at which copycats appeared.

---

## 1. Re-verification of the three named apps

### 1.1 Method, and why the numbers conflicted

- **Google Play.** I used `google-play-scraper` 1.x (Python) with `country='eg'` and `lang='ar'` (plus `lang='en'` for descriptions). The `realInstalls` field is the exact install counter embedded in the Play page data. The visible "1K+" style bucket is a floor derived from it. **Caveat:** the counter is global across all countries, and Play does not expose a per-country split.
- **Apple App Store.** I used the iTunes Search API with `country=eg`. Ratings returned there are **Egypt-storefront ratings only**. Apple does not publish download counts.
- **AppBrain and AppFollow.** These were not needed once the Play counter was available. Earlier sessions hit 403, 429 and truncation errors on these mirrors.
- **Why the files disagreed.** Files 08 and 11 could not fetch Play at all ("not verified"). File 12 first recorded "no install count shown" and then corrected it to buckets. Files 06 and 07 already had the exact counters. **The exact counters below supersede all earlier figures.**

### 1.2 Verified store data, 2026-10-12

| Field | **Amarati — عمارتي** | **Imarti — عمارتي - إدارة اتحاد الملّاك** | **Saknna — سَكَنة** |
|---|---|---|---|
| Android package | `com.amarati.app` | `com.craftfuture.imarti` | **No Play listing found.** Web/PWA only ("no app store download needed") |
| Installs (exact, global) | **1,416** (bucket 1K+) | **125** (bucket 100+) | n/a |
| Play rating | **4.74★ from 43 ratings**, 3 text reviews | **No rating** (too few) | n/a |
| Released on Play | 21 Jun 2026 | 26 Jul 2026 | n/a |
| Last update / version | Updated after release; v1.1.7 | Not exposed; version "varies with device" | n/a |
| Developer | "Amarati Technologies"; email issa_kassabry@hotmail.com; site amarati-site.web.app | "Craft Future"; craftsolutionsapp@gmail.com; privacy policy on admin.craftsolutions.com.sa | © 2026 سَكَنة; +20 122 653 9203 (an Egyptian number) |
| Country (inferred) | **Palestine.** The description says "بناه رؤساء لجان عمارات فعلية في فلسطين" | Ambiguous. File 12 recorded an address in Haram, Giza; the privacy policy sits on a Saudi `.com.sa` domain | Egypt-based contact; markets to Egypt, KSA, UAE and the Gulf |
| Price / in-app purchases | Free. **No IAP, no ads declared.** "مجاني للبدء… لا توجد رسوم خفية" | Free. **No IAP, no ads declared** | **450 / 900 / 2,200 / 7,500 EGP per month** (≤5 / ≤10 / ≤20 / unlimited units); 14-day trial; annual billing gives "2 months free"; promo SAKN30 |
| Category | Productivity | Business | — |
| Android permissions | Camera, **microphone**, **precise location**, run at startup, vibration | Camera, network only | — |
| iOS (Egypt storefront) | **id6791464029 "Amarati - عمارتي"**, seller Issa Kasabri, **4.5★ (4)**, released 19 Jul 2026, updated 2 Oct 2026 | **id6796346427 "عمارتي"**, seller "craft future for e commerce", 0 ratings, released 5 Aug 2026, updated 9 Sep 2026 | Not found on the App Store |
| Sources | [Play](https://play.google.com/store/apps/details?id=com.amarati.app&hl=ar&gl=EG) · [App Store](https://apps.apple.com/eg/app/id6791464029) | [Play](https://play.google.com/store/apps/details?id=com.craftfuture.imarti&hl=ar&gl=EG) · [App Store](https://apps.apple.com/eg/app/id6796346427) | [saknna.com/ar](https://saknna.com/ar) |

### 1.3 Monetization and admin plans: what can and cannot be known

- **Amarati.** No in-app purchases are declared on Play, and the App Store lists it as Free. The copy says "مجاني للبدء" (free *to start*), which implies a planned paid tier. Its positioning line is "ما بنلمس فلوسك" ("we don't touch your money"). The app does not process payments, it only records them. **ESTIMATE:** a future freemium tier for committee heads is likely, but **no price exists today.**
- **Imarti.** No in-app purchases on either store. A 2★ review dated 2026-10-01 says "الاشتراكات غاليه اوي" (file 06), but that may refer to the building's own monthly fees, not app fees. The description's "إدارة الاشتراكات" (managing subscriptions) means **residents' monthly dues**. That is the most likely source of the confusion. **Conclusion:** I found no evidence that Imarti charges for the app [unverified either way].
- **What I could not do.** Neither app's admin plan can be inspected without installing it, registering and creating a building. My tools cannot do that. **Recommended manual check (30 minutes):** install both apps on a test phone, create a building with 6 flats, and screenshot every paywall, limit and "upgrade" prompt.

### 1.4 Saknna: deeper teardown

- **Modules** ([saknna.com/ar](https://saknna.com/ar)):
  - finance (invoices, payments, reports: "تشوف مين دفع ومين لسه من غير إكسل", i.e. see who paid without Excel);
  - maintenance (requests with priority, status and photos);
  - residents (owners and tenants, unit and contract data, units with more than one owner);
  - an **Arabic AI assistant** that summarizes the building's status and answers management questions;
  - automatic reminders, an account statement, a dashboard showing collection rate and open requests, Excel/CSV import, and an installable PWA.
- **Payment rails:** InstaPay, Vodafone Cash and bank transfer in Egypt; Barq and e-payment in KSA.
- **WhatsApp:** only "notifications instead of group chaos" and a support link. There is **no group bot**.
- **Traction:** "500+ مبنى" (500+ buildings) [self-reported]. The animated counters rendered "0" during my fetch. I found no press, funding, team page, Play listing or YouTube channel. A web search for "Saknna سكنة" returned only unrelated "Sakani" and "SAKNA" projects.
- **Business model:** sales-led SaaS charged per building. At under 90–110 EGP per unit per month (Saknna's own figure), it costs about as much as many buildings' entire monthly maintenance fee (file 01). **This is the weakness to exploit.**

---

## 2. New entrants, 2025–2026: full Play + App Store sweep

**Method:**
- 14 Arabic and English Play queries (country=eg): اتحاد ملاك، إدارة عمارة، اتحاد الشاغلين، سكان العمارة، كمبوند، مجتمع سكني، بواب، صيانة العمارة، عمارتي، مصاريف العمارة, plus "building management Egypt", "HOA app", "community app compound" and "owners association". These returned 529 unique apps, which I filtered by title keywords.
- 17 App Store queries (country=eg).
- Details for every relevant hit.

### 2.1 Ordinary-building / union apps (the founder's direct arena)

| # | App (package) | Developer (country signal) | Released | **Installs (exact)** | Rating (n) | Monetization | iOS (EG) | Notes |
|---|---|---|---|---|---|---|---|---|
| 1 | **إتّحاد: إدارة اتحاد الشاغلين** (`com.ittihad.ettihad`) | Ettihad Community / Ettihad Software, **NL-registered**; iOS seller Ahmed Talat | 10 Aug 2026 | **3,000** | 4.5 (8) | **Free forever**; donations planned | id6760418161, 5★ (1), updated 11 Oct 2026 | Leader. AI "فاري"; QR visitor passes; voting; receipt OCR; pay links; passkeys; 7 countries |
| 2 | **عمارتي - إدارة إتحاد الملاك** — Ammarty (`com.ammarty.ammarty`) | HopenWorks LTD | 8 Sep 2026 | **1,684** | 4.78 (9) | No IAP declared (file 06 noted a subscription after 1 month [unverified]) | not found | Resident login by flat number + PIN; offline + sync; WhatsApp receipts |
| 3 | **Amarati** (`com.amarati.app`) | Amarati Technologies (Palestine) | 21 Jun 2026 | **1,416** | 4.74 (43) | Free, "free to start" | 4.5★ (4) | Meter OCR; WhatsApp summary image |
| 4 | **صندوق العمارة** (`com.amrem.sandooqelamara`) | Amr Emam (Egypt) | 25 Aug 2026 | **961** | 4.75 (16) | **49.99 EGP/mo, 499.99 EGP/yr** | not found | Voice "عم أمين"; v1.0.175 |
| 5 | **عمارتي - ادارة اتحاد الملاك** — Omaraty (`com.omaraty.app`) | Youssef Mohamed Ramzy / techiato.org | 10 Aug 2026 | **365** | 5.0 (7) | No IAP | — | — |
| 6 | **كمبوندى (حدائق الاهرام)** (`com.melsayed25.compoundy`) | Compoundy Solutions | 15 Aug 2026 | **274** | — | No IAP | — | Grassroots compound directory and shopping |
| 7 | **Bonian - بُنيان** (`com.bonian.mobile`) | Elnooronline / bonian.app | 1 Sep 2026 | **247** | — | No IAP | id6807542704, 5★ (1) | Ledger, flat types and prices, export, backup |
| 8 | **ملاك المرافق** (`com.njik.molakmarafeq`) | Njik Labbak (KSA, njik.com.sa) | 4 Jul 2026 | **194** | — | — | id6782949114 | Saudi |
| 9 | **Mullak** (`com.resaleapp.resaleApp`) | Mo Abdelhamid / mullak-eg.com | 21 Sep 2026 | **171** | — | Paid listings | id6777804084 | **An owner-to-buyer no-broker classifieds app, not union management.** Relevant to a later rent/resale module |
| 10 | **Pinpund: دليل كمبوندك ومنطقتك** (`com.pinpund.app`) | Grevo For Programming | 7 Sep 2026 | **144** | 5.0 (8) | **IAP 50–1,800 EGP** (likely merchant listings) | — | Hyper-local compound directory. **A phase-2 ad model copy** |
| 11 | **Imarti** (`com.craftfuture.imarti`) | Craft Future | 26 Jul 2026 | **125** | — | No IAP | id6796346427 | Voting; emergency funds; rated providers with countdown offers |
| 12 | **عمارتي \| مصاريف العمارة** (`com.tarek.imarati`) | Alfahd Alaswad Co. | 7 Jun 2026 | **110** | — | — | — | — |
| 13 | **هومينا Homena** (`io.homena.app`) | HomenaApp / homena.io (iOS seller Mohamed Nassar) | 2 Sep 2026 | **91** | — | **IAP 109.99–569.99 EGP** | id6818112920, released **12 Oct 2026** | Multi-building; AR/EN |
| 14 | **صندوق اونلاين** (`com.mk.theboxproject`) | Mk Applications | 23 May 2026 | **84** | — | **IAP 83.99–839.99 EGP** | id6787190370 | — |
| 15 | **اتحاد ملاك عمارة 1310** (`com.building1310.app`) | HopenWorks LTD | 2 Aug 2026 | **67** | — | — | — | A single-building custom app by the same developer as Ammarty |
| 16 | **العمارة - إدارة ذكية للعمارات** (`com.beemind.alemara`) | Eyad Ramzy | 6 Jul 2026 | **36** | — | — | — | — |
| 17 | **دفتر العمارة** (`com.mrizk.emara.building`) | Hilal.Trade.dev | 14 Jul 2026 | **30** | — | **IAP 30–450 EGP** | — | — |
| 18 | **اتحاد الملاك** (`com.elgoktech.buildingmanagement`) | Abdelrahman Taha / elgoktech | 29 Sep 2026 | **17** | — | — | — | — |
| 19 | **Darna - دارنا** (`com.darna.egypt`; another Darna, `com.buildingfund.app`, is KSA) | "DArna" | 23 Sep 2026 | **12** | — | — | id6811596119 (seller Mohamed Elkilany) | — |
| 20 | **اتحاد الملاك: إدارة الأملاك** (`app.isgapps.OwnersAssociation`) | ISG Intelligent Systems Group (egisg.com, Egypt) | 6 Sep 2026 | **12** | — | — | — | An established Egyptian systems integrator entering the category |
| 21 | **BOS — إدارة صندوق العمارة** | JAMAL KAMLA | iOS only, 26 Sep 2026 | n/a | 0 | — | id6810878518 | — |

**Category total, chart-ready.** The sum of the exact counters for the building/union apps above (excluding Mullak and Pinpund) is **≈ 8,900 installs**. For comparison, ADDA (India) alone has **1,149,255**.

```csv
app,installs_exact_2026_10_12,release_date,days_live,installs_per_day
Ettihad,3000,2026-08-10,63,47.6
Ammarty,1684,2026-09-08,34,49.5
Amarati,1416,2026-06-21,113,12.5
Sandooq El Emara,961,2026-08-25,48,20.0
Omaraty,365,2026-08-10,63,5.8
Compoundy,274,2026-08-15,58,4.7
Bonian,247,2026-09-01,41,6.0
Imarti,125,2026-07-26,78,1.6
Homena,91,2026-09-02,40,2.3
Sandouq Online,84,2026-05-23,142,0.6
Unitify (global),688,2025-09-04,403,1.7
```

**Reading the velocity.** Ettihad and Ammarty are each adding about 50 installs a day. That is roughly 1,500 a month, or about 30–60 buildings a month (ESTIMATE: 25–50 installs per building, assuming a treasurer plus 40–70% of the flats in a 10–40-flat building install). **At this speed no one reaches even 1% of Egyptian buildings in 2027.** A viral WhatsApp-native loop could reach 10× that speed (see files 10 and 13).

### 2.2 Compound / B2B-platform apps (exact counters)

| Family | App | Installs (exact) | Play rating (n) | iOS EG rating (n) |
|---|---|---|---|---|
| **Lyve** (New Moonshot / Lyve Inc / Moonshot Labs) | Lyve-App | 36,430 | 4.4 (354) | **3.32 (69)** |
| | Palm Hills Live | 15,094 | 3.6 (38) | — |
| | La Vista | 12,469 | 4.27 (106) | — |
| | SED Communities | 6,066 | 4.4 (36) | — |
| | Al Marasem | 2,444 | 4.57 (15) | — |
| | Places by Hyde Park | 1,991 | — | — |
| | Hassan Allam Properties | 1,725 | 4.0 (10) | — |
| | DORRA Egypt | 1,104 | 4.83 (6) | — |
| | **Lyve family total** | **77,323** | | |
| **Milango** (Milango APM / Milango, LLC) | City Edge Developments | 44,998 | 3.76 (93) | 4.11 (9) |
| | Morshedy Group | 10,760 | 3.62 (47) | 3.36 (25) |
| | SODIC | 9,239 | 3.26 (51) | **2.22 (81)** |
| | Al-Ahly Sabbour | 8,921 | 3.47 (17) | 3.95 (22) |
| | MyPorto (Amer Group) | 8,357 | 4.35 (47) | 3.72 (18) |
| | Misr Italia Engage | 430 | — | — |
| | Also on iOS only: WRK+ 4.67 (12); Smart Village Community 4.38 (8) | | | |
| | **Milango family total (Android)** | **82,705** | | |
| Ambiguous lineage | Emaar Misr App (`com.kijamii.emaarcommunities`, website field iamlyve.com) | 44,478 | 3.94 (261) | — |
| In-house / other | Mountain View Community (Intcore) | 14,209 | 3.67 (34) | — |
| | PALM HILLS (in-house; replaced Lyve) | 7,206 | 2.97 (34) | — |
| | OneCommunity (New Giza) | 4,347 | **2.42 (38)** | — |
| | ORA Developers | 1,895 | 2.67 (7) | — |
| | Vives Compound (RAY Labs) | 1,110 | — | — |
| | Marvela Compound (Toweron, Saudi email) | 599 | — | — |
| | Boyot tenant app | 326 | — | — |
| Grassroots | **أهل مدينتي** — Ahl Madinaty (community-run) | **43,668** | **4.62 (199)** | — |

**Takeaways:**
- **A volunteer-built Madinaty directory app (43.7K, 4.62★) nearly matches whole vendor app families and outrates them all.** Residents reward community-first, useful-every-day apps more than gate-and-billing apps imposed by developers.
- **Lyve leadership conflict.** lyve-app.com currently names "Ahmed Amr, Founder & CEO", next to a lorem-ipsum testimonial and "0+" counters. Every news source (Egypt Innovate 2020; Enterprise 2021; Enterprise AR, Aug 2024) names **Karim Akram** as CEO or co-founder/managing director. Treat the website as a placeholder template [unverified].
- **Lyve's website traction counters** (communities, contracted units, gate invitations, tickets) all render as "0". I found no public 2025–2026 traction or funding news for Lyve. The last known funding is Algebra Ventures (Series A, Oct 2018, $600K total per Tracxn).
- **Milango** had "nearly EGP 100 million in transactions" through the platform (Feb 2022, CairoScene) and acquired its rival **Circle** (500 Startups-backed). Its founder interview (Enterprise, Dec 2022) names El Gouna as a client, plans Gulf expansion, and describes a "plug-and-play" model where the manager controls content, invoices and services. Milango has no public raise after its A15 seed (Oct 2020).

### 2.3 Startup-news scan (Wamda, Enterprise, Disrupt Africa, Startup Scene, MENAbytes, Tracxn)

- **No Egyptian community/building-management startup raised publicly in 2025–2026.** That was the result of an extended search, and Tracxn's Cairo property-management list shows no 2025–2026 rounds. Rounds in this space:
  - Boyot: seed, Jun 2022;
  - Shatablee: seed, Mar 2022, $1.2M (finishing/renovation, not community);
  - Milango: seed, Oct 2020;
  - iCommunity/Lyve: Series A, Oct 2018.
- Proptech money in Egypt goes to **transactions**, not communities:
  - **Nawy:** $52M Series A (TechCrunch, May 2025), later reported as $75M in total for the round (Dabafinance);
  - **Byit:** $1.1M (A15 and Beltone), expanded to the UAE in May 2026 (Wamda).
- **Egypt PropTech Challenge 2026** (Cityscape): applications for 12 startups, including property and asset management, closed 3 Sep 2026. **ESTIMATE:** this is a cheap credibility and PR channel for the founder next year.
- **Egypro FME** is an Egyptian facility-management firm managing **800 buildings and 3.5M m²** with 1,500+ technicians (Amwal Al Ghad, Oct 2025). It names no app or software platform. **That makes it a natural phase-2 supply partner, or a white-label B2B customer.**

---

## 3. Deep teardowns: Saknna, صندوق العمارة, ELOMARA, Unitify, Lyve, Milango (+ Ettihad, Amarati, Imarti, Ammarty)

### 3.1 Master feature matrix (85 features × 10 products)

Legend:
- ✅ = confirmed in the vendor's own public material or store listing;
- ◐ = partial or limited;
- ❌ = **not mentioned** in public material (not proof of absence);
- ? = unknown (the material is too thin).

Sources: Play descriptions pulled 2026-10-12; [ettihad.org](https://www.ettihad.org); [sandoqalemara.com](https://sandoqalemara.com); [saknna.com/ar](https://saknna.com/ar); [elomara.com/ar](https://elomara.com/ar); [unitify.com/egypt](https://unitify.com/egypt); [lyve-app.com](https://lyve-app.com); Tracxn; file 01.

| # | Feature | Amarati | Imarti | **Ettihad** | Sandooq | Saknna | ELOMARA | **Unitify** | Lyve | Milango | Ammarty |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **A** | **Ledger & dues** | | | | | | | | | | |
| 1 | Unit/flat registry | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| 2 | Bulk flat generation by floor | ❌ | ❌ | ✅ floor mapping | ✅ | ✅ floors | ? | ✅ Excel | ? | ? | ❌ |
| 3 | Owners + tenants / multi-owner units | ❌ | ❌ | ◐ | ❌ | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ |
| 4 | Auto monthly dues generation | ✅ | ✅ | ✅ recurring | ✅ | ✅ | ✅ | ✅ | ◐ reminders | ◐ invoices | ✅ |
| 5 | Unequal shares (area/custom) | ❌ | ❌ | ✅ equal or by area | ✅ per-flat | ? | ? | ✅ m²/apt/resident/flat | ? | ? | ✅ per-flat |
| 6 | Exemptions | ❌ (requested in reviews) | ❌ | ◐ | ✅ | ? | ? | ? | ? | ? | ❌ |
| 7 | Partial / advance / multi-month payments | ❌ | ❌ | ✅ credit balance | ✅ 3/6/12 months | ? | ? | ✅ | ? | ? | ❌ |
| 8 | Arrears statement | ◐ balance | ✅ debt statement | ✅ unit statement up to 2 years | ✅ cumulative | ✅ | ? | ✅ debt reminders | ? | ? | ✅ |
| 9 | One-off levies / special projects | ❌ | ◐ | ◐ | ✅ projects | ? | ? | ✅ split bills | ? | ? | ❌ |
| 10 | Emergency / donation campaigns | ❌ | ✅ | ❌ | ◐ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| 11 | Multiple treasuries (cash/bank) | ❌ | ❌ | ✅ building funds | ✅ | ? | ✅ cash records | ? | ❌ | ❌ | ◐ |
| 12 | Reserves pay part of an expense | ❌ | ❌ | ✅ | ◐ | ❌ | ? | ? | ❌ | ❌ | ❌ |
| 13 | Treasury loans as liabilities | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| 14 | Doorman/technician petty-cash custody | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| 15 | Mosque fund | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| 16 | Expense categories | ◐ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ | ❌ | ✅ |
| 17 | Receipt photo on expense | ❌ | ◐ | ✅ | ✅ up to 5 | ? | ✅ proofs | ✅ | ❌ | ❌ | ◐ |
| 18 | **Receipt OCR (AI reads amount/date)** | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ◐ AI reports | ❌ | ❌ | ❌ |
| 19 | Recurring expenses | ❌ | ❌ | ✅ | ? | ? | ? | ✅ | ❌ | ❌ | ◐ |
| 20 | **Meter reading by camera / utility split** | ✅ | ❌ | ❌ | ❌ | ❌ | ✅ utilities | ✅ meter readings | ❌ | ❌ | ❌ |
| 21 | Audit log / append-only ledger | ◐ cash-claim log | ◐ | ✅ | ◐ undo | ? | ? | ? | ? | ? | ❌ |
| **B** | **Payments** | | | | | | | | | | |
| 22 | Resident uploads payment proof | ◐ cash claim | ❌ | ✅ | ❌ | ? | ✅ | ✅ | ? | ? | ❌ |
| 23 | Admin confirm/reject claims | ✅ | ❌ | ✅ | ❌ | ? | ✅ | ✅ | ? | ? | ❌ |
| 24 | InstaPay / wallet instructions | ❌ | ❌ | ✅ per-community link/phone/QR | ◐ (app subscription only) | ✅ | ? | ✅ InstaPay/Meeza/EG-ACH | ? | ? | ❌ |
| 25 | **Pay links for non-app users** (≤200 units, 48 h) | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| 26 | In-app card/wallet gateway | ❌ | ❌ | ❌ (by design) | ❌ | ❌ | ? | ✅ (rails reconciled) | ◐ | ✅ (~EGP 100M processed by 2022) | ❌ |
| 27 | Automated reconciliation | ❌ | ❌ | ◐ | ❌ | ❌ | ❌ | ✅ | ? | ? | ❌ |
| 28 | Digital receipts | ◐ | ✅ | ✅ | ✅ image cards | ✅ | ✅ | ✅ PDF + QR | ? | ? | ✅ |
| 29 | Receipt/statement shared to WhatsApp | ✅ summary image | ❌ | ✅ images/Excel | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ |
| **C** | **Reports & data** | | | | | | | | | | |
| 30 | Monthly/annual reports | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ? | ? | ✅ |
| 31 | PDF export | ❌ | ✅ | ❌ | ✅ | ? | ? | ✅ | ? | ? | ✅ |
| 32 | Excel export | ❌ | ❌ | ✅ AR/EN | ✅ | ? | ? | ✅ | ? | ? | ◐ |
| 33 | Excel/CSV import | ❌ | ❌ | ❌ | ✅ | ✅ | ? | ✅ | ? | ? | ❌ |
| 34 | AI column mapping on import | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ | ◐ | ❌ | ❌ | ❌ |
| 35 | Collection-rate dashboard | ◐ | ✅ live balance | ✅ "الباقي مع العمارة" | ✅ % paid | ✅ | ? | ✅ analytics | ? | ? | ✅ |
| 36 | Residents see building expenses | ✅ | ✅ | ✅ | ❌ (no resident app) | ◐ | ✅ | ✅ | ? | ? | ✅ |
| 37 | Former-member financial history | ❌ | ✅ | ✅ (deleted-unit history kept) | ✅ (fee changes keep past records) | ? | ? | ? | ? | ? | ❌ |
| **D** | **Communication & governance** | | | | | | | | | | |
| 38 | Announcements | ❌ | ◐ | ✅ | ❌ | ◐ | ✅ | ✅ | ✅ | ✅ | ❌ |
| 39 | Push notifications | ✅ with Arabic sound | ✅ deep link | ✅ | ❌ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| 40 | Automatic payment reminders | ✅ | ✅ | ◐ | ✅ via WhatsApp | ✅ | ? | ✅ | ✅ | ? | ✅ |
| 41 | Voting / polls | ❌ | ✅ | ✅ dated proposals | ❌ | ❌ | ? | ✅ mini-app | ? | ? | ❌ |
| 42 | Decisions archive | ❌ | ✅ | ✅ results visible | ❌ | ❌ | ? | ✅ assembly papers | ? | ? | ❌ |
| 43 | Complaints / suggestions | ❌ | ✅ | ✅ suggestions | ❌ | ❌ | ? | ✅ | ✅ | ✅ | ◐ contact admin |
| 44 | Maintenance tickets with photos | ❌ | ❌ | ✅ up to 3 photos | ❌ | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ |
| 45 | Ticket priority/status tracking | ❌ | ❌ | ✅ | ❌ | ✅ | ✅ | ✅ kanban | ✅ | ✅ | ❌ |
| 46 | Anonymous reporting | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| 47 | Public issue board | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| 48 | Resident chat / groups | ❌ | ❌ | ❌ (by design) | ❌ | ❌ | ✅ | ✅ | ✅ (Tracxn) | ? | ❌ |
| 49 | **WhatsApp bot inside the building group** | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| 50 | WhatsApp outbound (reminders/receipts) | ◐ share | ❌ | ◐ share | ✅ one-tap | ◐ | ❌ | ❌ | ❌ | ❌ | ✅ share |
| 51 | Telegram bot | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ |
| 52 | WhatsApp export → AI report | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ |
| **E** | **Access & building** | | | | | | | | | | |
| 53 | Visitor QR passes | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ✅ | ✅ | ✅ | ❌ |
| 54 | Guard/gate scanning | ❌ | ❌ | ✅ guard verifies | ❌ | ❌ | ❌ | ✅ + plate recognition | ✅ | ✅ | ❌ |
| 55 | Intercom / door opening from phone | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ? | ? | ❌ |
| 56 | Facility booking | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ✅ | ✅ | ❌ |
| 57 | Smart building / IoT / EV charging | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ |
| **F** | **AI** | | | | | | | | | | |
| 58 | **Voice entry in Egyptian Arabic** | ❌ (mic permission only) | ❌ | ✅ voice AR/EN | ✅ "عم أمين" | ❌ | ❌ | ◐ AI concierge calls | ❌ | ❌ | ❌ |
| 59 | AI chat assistant / Q&A | ❌ | ❌ | ✅ "فاري" (cards, confirm-first) | ✅ (+ legal guidance) | ✅ Arabic summary | ❌ ("smart" only) | ✅ | ❌ | ❌ | ❌ |
| 60 | AI ticket classifier | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ |
| 61 | AI reports from raw files | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ |
| 62 | AI maintenance-plan drafting | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ "AI Engineer" | ❌ | ❌ | ❌ |
| 63 | AI drafts WhatsApp messages | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| **G** | **Marketplace & commerce (phase 2)** | | | | | | | | | | |
| 64 | Service-provider directory | ❌ | ✅ | ❌ | ❌ | ❌ | ✅ approved providers | ✅ contractor marketplace | ✅ | ✅ supplier network | ❌ |
| 65 | Provider ratings / time-limited offers | ❌ | ✅ countdown | ❌ | ❌ | ❌ | ? | ? | ? | ? | ❌ |
| 66 | Local businesses / nearby services | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ | ✅ stores | ◐ | ❌ |
| 67 | Commerce + consumer finance | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ◐ paid services | ✅ Raya (2021) | ❌ | ❌ |
| 68 | Discounts / benefits | ❌ | ✅ offers | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ Lyve Benefits | ? | ❌ |
| 69 | Unit rent/resale listings | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ◐ (DORRA app) | ❌ | ❌ |
| **H** | **Roles & operations** | | | | | | | | | | |
| 70 | Roles (manager/treasurer/member) | ◐ admin/resident | ✅ 3 roles | ✅ | ❌ treasurer only | ✅ | ✅ 5 roles | ✅ | ✅ | ✅ | ✅ 2 |
| 71 | Doorman (بواب) / guard mode | ❌ | ❌ | ◐ guard scans QR | ◐ custody | ❌ | ◐ supervisors | ✅ technician app | ✅ gate | ✅ gate | ❌ |
| 72 | Technician app | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ? | ? | ❌ |
| 73 | Multi-building | ❌ | ❌ | ✅ (up to tens of thousands of units) | ❌ | ✅ (Mujamma plan) | ✅ | ✅ | ✅ | ✅ | ❌ |
| 74 | Offline-first | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ |
| 75 | Demo mode with sample data | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| 76 | Invite residents by link/WhatsApp | ✅ | ◐ join-data screen | ✅ (name-only allowed) | ❌ | ✅ file import | ? | ✅ | ✅ invite code | ✅ | ✅ PIN |
| **I** | **Platform & trust** | | | | | | | | | | |
| 77 | Android | ✅ | ✅ | ✅ | ✅ | PWA | ✅ claimed | ✅ | ✅ | ✅ | ✅ |
| 78 | iOS | ✅ | ✅ | ✅ | ❌ | PWA | ? | ? (none found in EG) | ✅ | ✅ | ❌ |
| 79 | Web dashboard | ❌ | ❌ | ❌ | ◐ free tools | ✅ | ✅ | ✅ CRM | ✅ | ✅ | ❌ |
| 80 | Arabic | ✅ (Levantine) | ✅ | ✅ | ✅ (Egyptian) | ✅ | ✅ | ✅ (site) | ◐ RTL bugs | ◐ | ✅ |
| 81 | English | ❌ | ✅ | ✅ | ❌ | ❌ | ? | ✅ | ✅ | ✅ | ❌ |
| 82 | Dark mode | ❌ | ❌ | ✅ | ✅ | ❌ | ❌ | ? | ? | ? | ❌ |
| 83 | Passkeys / MFA | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ? | ❌ (OTP issues) | ❌ (OTP issues) | ❌ |
| 84 | Law 119/2008 guidance | ❌ | ❌ | ❌ | ✅ guides + assistant | ❌ | ❌ | ✅ Egypt page | ❌ | ❌ | ❌ |
| 85 | Open API / white-label | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ✅ white-label | ✅ white-label | ❌ |
| | **Count of ✅** (approx.) | **12** | **21** | **50** | **36** | **22** | **22** | **58** | **20** | **17** | **17** |

**What the matrix says:**
1. **Feature #49, a WhatsApp bot inside the building group, is ❌ for all 10.** It is the single clearest open feature (white space), and it is the founder's idea #3. Boyot claims a WhatsApp bot for client communication, but it is a business-to-resident support bot for compound operators, not a member of the building's group [self-reported].
2. **Ettihad is the benchmark for a free resident-plus-manager app.** Its gaps:
   - no in-group bot and no resident chat (deliberate);
   - no doorman mode;
   - no marketplace;
   - no offline mode;
   - no Excel import;
   - no Egyptian legal kit.
3. **Sandooq is the benchmark for treasurer depth** (custody, mosque fund, loans, voice). Its gaps are **no resident app, no iOS, and a paid model.**
4. **Unitify is the benchmark for breadth**, but it is built for management companies. It has no in-group WhatsApp presence, uses Telegram, and charges per apartment above its free tier.
5. **Doorman mode (#71) and petty-cash custody (#14) are almost empty.** Only Sandooq covers custody, and nobody gives the بواب a real tool.

### 3.2 Pricing and business-model table

| Product | Model | Price points | Payer | Free tier | Source |
|---|---|---|---|---|---|
| Ettihad | Free; donations "planned" | 0 | — | Everything | [ettihad.org](https://www.ettihad.org) |
| Amarati | Free, "to start" | 0 (no IAP declared) | — | Everything today | [Play](https://play.google.com/store/apps/details?id=com.amarati.app) |
| Imarti | Free | 0 (no IAP declared) | — | Everything today | [Play](https://play.google.com/store/apps/details?id=com.craftfuture.imarti) |
| Ammarty | Free on store (file 06: subscription after 1 month [unverified]) | none declared | Treasurer | ? | [Play](https://play.google.com/store/apps/details?id=com.ammarty.ammarty) |
| صندوق العمارة | Freemium subscription | **49.99 EGP/mo; 499.99 EGP/yr** | Treasurer | Free trial (length not stated) | [site](https://sandoqalemara.com) · [Play](https://play.google.com/store/apps/details?id=com.amrem.sandooqelamara) |
| Homena | Subscription | **109.99–569.99 EGP** per item | Admin | ? | [Play](https://play.google.com/store/apps/details?id=io.homena.app) |
| Sandouq Online | Subscription | **83.99–839.99 EGP** per item | Admin | ? | [Play](https://play.google.com/store/apps/details?id=com.mk.theboxproject) |
| دفتر العمارة | Subscription | **30–450 EGP** per item | Admin | ? | [Play](https://play.google.com/store/apps/details?id=com.mrizk.emara.building) |
| Saknna | SaaS per building | **450 / 900 / 2,200 / 7,500 EGP/mo** | Committee / compound | 14-day trial | [saknna.com/ar](https://saknna.com/ar) |
| Unitify | SaaS per apartment | **$0 / $0.5 / $1.5 per apartment per month**; billing add-on $0.5/invoice (free on Pro); video/intercom +$1/apt; AI beyond cap billed per token | Management company | Free forever, no AI, 1 news post/month | [unitify.com/egypt](https://unitify.com/egypt) |
| Lyve | B2B white-label licence | Not public | Developer / FM | — | [lyve-app.com](https://lyve-app.com) |
| Milango | B2B "plug-and-play" modular licence + payments | Not public | Developer / club | — | [Enterprise 2022](https://enterpriseam.com/egypt/2022/12/27/meet-our-founder-of-the-week-milangos-amr-mostafa/) |
| Boyot | SaaS + 360 POS for compounds; unlimited users | Not public | Property managers | — | [boyot.app](https://boyot.app/) |
| ELOMARA | Not stated | — | — | — | [elomara.com/ar](https://elomara.com/ar) |
| Pinpund | Paid merchant listings (likely) | IAP 50–1,800 EGP | Local businesses | Users free | [Play](https://play.google.com/store/apps/details?id=com.pinpund.app) |

**ESTIMATE: what the market will bear.** The building-paid price anchor is **about 50 EGP a month**, set by Sandooq, the cheapest app with real usage. A 20-flat building paying 50 EGP a month is **2.5 EGP per flat**. Charging buildings will never fund the business. The founder's phase-2 thesis (services, ads and payments) is the right one, and **free is mandatory**.

---

## 4. Product-by-product SWOT, the weakness to exploit and how we beat them

### 4.1 Ettihad (إتّحاد): **highest-priority rival**

| Strengths | Weaknesses |
|---|---|
| Free forever; iOS + Android + tablets; AR/EN; fastest growth (~48 installs/day) | No group chat **by design**: residents stay in WhatsApp, so Ettihad is a "second app" |
| AI "فاري" (voice + text, confirm-first cards); receipt OCR | No WhatsApp bot; sharing to WhatsApp is manual |
| Pay links for non-app users; QR visitor passes; voting; anonymous issues | No doorman mode, no marketplace, no offline mode, no Excel import |
| Serious security (passkeys, MFA, EU hosting, append-only ledger) | Foreign (Dutch) entity; formal MSA-Arabic copy; no Egyptian legal kit |
| 7 countries; demo mode | No revenue model ("donations planned"), so long-term survival is a risk; tiny social presence |

| Opportunities (for them) | Threats (from them to us) |
|---|---|
| Add a WhatsApp bot, a marketplace or a paid tier | Becomes the default "free union app" through word of mouth before we launch |

- **Weakness to exploit:** *"Another app residents must open."* Ettihad's copy explicitly says there is no resident group chat. Egyptians live in the WhatsApp group.
- **How we beat them:** **become a member of the WhatsApp group.** Ettihad sits outside the group. Our bot joins it and logs "دفعت" automatically, posts the monthly summary, and answers "مين لسه مدفعش؟". Add a doorman mode, Egyptian-dialect copy and a "form your union in 10 minutes" legal kit, then publish a **one-tap Ettihad/Excel import** to lower switching cost.

### 4.2 صندوق العمارة (Sandooq El-Emara)

| Strengths | Weaknesses |
|---|---|
| Deepest treasurer feature set: custody, mosque fund, loans, projects, multiple treasuries | **Treasurer-only, no resident accounts**, so no network effect |
| Egyptian-dialect voice "عم أمين"; AI Excel mapping; offline-first | Android only; paid (49.99 EGP/mo) |
| Very active solo developer (v1.0.175 within 48 days); free SEO tools (fee calculator, receipt generator, law guides) | Solo developer, a bus-factor risk; 961 installs |

- **Opportunities:** add a resident portal and WhatsApp automation.
- **Threats:** could pivot into a resident network quickly, since the developer ships almost daily.
- **Weakness to exploit:** residents can't see anything. Transparency, the #1 source of building disputes, is one-way.
- **How we beat them:** match the treasurer depth (custody, mosque fund, projects, exemptions) **for free**, and add resident accounts plus the bot. Copy the SEO play: free Arabic calculators and Law 119 guides as an acquisition funnel. **Consider an acqui-hire or partnership.** The developer is the most Egyptian-native builder in the space.

### 4.3 Saknna (سَكَنة)

| Strengths | Weaknesses |
|---|---|
| Polished web SaaS; finance + maintenance + residents; Arabic AI assistant | **Price: 450 EGP/mo for ≤5 units** (≈90 EGP/unit) |
| Multi-country (EG + GCC) with local payment rails | No native app; no WhatsApp bot; no voting, gate or marketplace |
| — | No visible team, funding or press; "500+ buildings" is unverified |

- **Opportunities:** Gulf buildings can afford its prices.
- **Threats:** it could drop prices or launch a free tier.
- **Weakness to exploit:** its price excludes 95%+ of Egyptian عمارات (ESTIMATE, based on typical dues in files 01 and 08).
- **How we beat them:** free core, plus a **"switch from Saknna" CSV import**. Target its trial-expiry churn with SEO content such as "بديل مجاني لإدارة العمارة" ("a free alternative for managing the building").

### 4.4 ELOMARA (العُمارة)

| Strengths | Weaknesses |
|---|---|
| Conceptually closest to the founder's vision: residents + managers + supervisors + **approved providers + nearby businesses**, V3 finance, chat | **No store listing found**, no pricing, no team, no traction, no press. Web search found nothing beyond its own site |

- **Opportunities:** none visible.
- **Threats:** low. It looks pre-launch or dormant (ESTIMATE).
- **Weakness to exploit:** vapor. It has no distribution.
- **How we beat them:** ship first and treat ELOMARA's module list as a checklist.

### 4.5 Unitify

| Strengths | Weaknesses |
|---|---|
| Broadest product (58 ✅); free forever tier; AI concierge, classifier and reports | **688 global Play installs**, no ratings, no Egyptian press found |
| Egypt landing page with Law 119 and InstaPay/Meeza/EG-ACH reconciliation | Telegram-centric (Egyptians use WhatsApp); per-apartment pricing |
| Technician app; smart-building integrations; open API | Built for management companies, not volunteer committees; CIS-origin team |
| Vendor claims 10,000 management companies and 5M apartments [self-reported] | — |

- **Opportunities:** partner with Egyptian FM firms such as Egypro FME (800 buildings).
- **Threats:** if it adds WhatsApp and Egyptian dialect, it owns the compound and FM-managed segment.
- **Weakness to exploit:** no local community, no WhatsApp and no Egyptian voice.
- **How we beat them:** **don't fight for FM companies in year 1.** Own the volunteer-run عمارة, where Unitify's sales motion can't reach. In year 2, offer FM firms a free B2B dashboard over buildings that already use our app (bottom-up). That is the reverse of Unitify's top-down model.

### 4.6 Lyve (ex-iCommunity)

| Strengths | Weaknesses |
|---|---|
| ~77K Android installs across 8 white-labels; 2016 incumbent; developer contracts (Palm Hills, La Vista, SED, Hassan Allam, Al Marasem) | iOS 3.32★ (EG); OTP and invite-code failures; Palm Hills **left** for an in-house app |
| Commerce precedent (Raya appliances + consumer finance, Lyve Benefits) | Website shows placeholders (0 counters, lorem ipsum); no public news after 2021 |
| — | B2B-paid, so weak incentive to delight residents |

- **Opportunities:** a "Lyve Lite" for buildings.
- **Threats:** low for ordinary buildings, high inside compounds.
- **Weakness to exploit:** residents are forced users who rate the app poorly. Developers churn: PALM HILLS and DORRA moved in-house.
- **How we beat them:** stay out of their contracts. Offer compound residents a **community layer** they choose themselves, as Ahl Madinaty does at 43.7K installs and 4.62★: directory, neighbours, offers, and a WhatsApp bot. Over time, become the neighbour app that sits above the gate app.

### 4.7 Milango

| Strengths | Weaknesses |
|---|---|
| ~82.7K Android installs; City Edge (45K), SODIC, Morshedy, Amer, Ahly Sabbour, El Gouna, Smart Village; acquired Circle (2022); payments (~EGP 100M by 2022) | **SODIC 2.22★ iOS**, 3.26★ Play; login and loading complaints (file 01) |
| Modular, manager-controlled content | No public raise since 2020; no AI; no resident-to-resident social layer |

- **Opportunities:** Gulf expansion.
- **Threats:** medium inside compounds.
- **Weakness to exploit:** its reliability and UX reputation.
- **How we beat them:** the same play as against Lyve. Also court their **FM and community managers** with free AI tools (ticket classifier, WhatsApp-export digest).

### 4.8 Amarati

| Strengths | Weaknesses |
|---|---|
| 4.74★ (43); simple, elderly-friendly UI (Cairo font, big buttons); meter OCR; WhatsApp summary image; iOS + Android | **Levantine copy** ("ما في"، "بدو"); Palestinian team; no voting, tickets or doorman; "free to start" implies a future paywall |

- **Opportunities:** grow in the Levant.
- **Threats:** low in Egypt.
- **Weakness to exploit:** it is not Egyptian, and residents in reviews explicitly ask whether it will stay free (file 06).
- **How we beat them:** copy the best two ideas (**meter-photo split** and the **one-tap WhatsApp summary image**) in Egyptian dialect, and promise "مجاني للأبد" (free forever) for the core.

### 4.9 Imarti

| Strengths | Weaknesses |
|---|---|
| Voting + decisions archive; emergency funds; **rated providers with countdown offers** (a marketplace seed); 3 roles; AR/EN | 125 installs; no ratings; RTL and digit bugs in the changelog (file 12); unclear origin (Giza address vs. Saudi domain) |

- **Opportunities:** none visible.
- **Threats:** low.
- **Weakness to exploit:** no traction or trust.
- **How we beat them:** ship the countdown-offer mechanic, adapted to building-level **group deals** (for example, "تنظيف خزان المياه للعمارة كلها – العرض ينتهي خلال 48 ساعة": tank cleaning for the whole building, offer ends in 48 hours).

### 4.10 Ammarty (HopenWorks)

- **Strengths:** second-fastest growth (~50/day); resident login by flat number + PIN, so no phone is needed; offline + sync.
- **Weaknesses:** basic features; the same developer ships single-building custom apps ("عمارة 1310"), which signals an agency model.
- **Weakness to exploit:** shallow features.
- **How we beat them:** copy the low-friction **flat number + PIN login** for elderly residents.

---

## 5. Adjacent Egyptian giants: entry likelihood, route and stance

Installs are exact Play counters (global) as of 2026-10-12. Likelihood and impact are **ESTIMATES** on a 1–5 scale, reasoned in the table.

| Giant | Android installs (exact) | Existing building-related features found | Likely entry route | Likelihood (1–5) | Impact if it enters (1–5) | **Stance** |
|---|---|---|---|---|---|---|
| **Fawry / myFawry** | 13,498,482 (3.91★, 178K ratings); Fawry Business invoicing app 57,608 | Prepaid electricity card top-up by NFC (myFawry, per EEHC via Masrawy); bill payments. **No union/compound-dues product found** in searches (AR + EN) | A "collect from residents" invoicing link via Fawry Business; utility bills for the building's common meter | 2 | 4 | **Partner.** Offer Fawry reference codes as a dues rail and pay common-area bills in the app |
| **InstaPay (IPN)** | 25,328,361 (4.28★); ~22M registered (file 08) | Payment rail only; merchant service planned for 2025, status unconfirmed | None (infrastructure) | 1 | 2 | **Partner.** InstaPay deep links and handle are the default dues rail (≈0.1% to the payer) |
| **Banks** (union collection accounts) | — | **Not found.** No bank product marketed to اتحاد الشاغلين surfaced in searches | A union current account + collection | 1 | 2 | Partner later (union account opening is a legal-kit upsell) |
| **MoneyFellows** (جمعيات) | 7,300,721 (4.61★); 7–8.5M users claimed | ROSCA circles; prepaid card; Apple Pay (Aug 2026 [self-reported]); planned cards, insurance and payroll | "Building circle" to fund big projects (elevator, façade) | 2 | 2 | **Partner.** Embed a MoneyFellows circle for special projects (a phase-2 finance revenue share) |
| **valU** (EFG) | 4,917,494 (3.51★) | **Home maintenance and finishing installment deals with developers** (Arab Developers Holding, Makadi Heights, SODIC, 2022) | BNPL for building-level and big-ticket home jobs | 2 | 3 | **Partner.** BNPL at checkout for big jobs (file 14) |
| **Halan** (حالا) | 15,470,954 (3.75★) | BNPL across 4,000+ vendors; home-finishing loans up to 4M EGP [third-party profile] | Super-app adding home services | 2 | 3 | Partner (BNPL); watch |
| **Nawy** | 3,644,953 (4.11★) | "Buy, sell, invest, manage"; **Nawy Unlocked** (finish, furnish and rent out idle units); **no resident app found** | Post-sale "Nawy Home" for buyers in compounds | 3 | 3 | **Partner/watch.** Feed resale and rent listings from our buildings to Nawy (a lead-fee revenue line) |
| **Dubizzle EG (OLX)** | 10M+ bucket (exact package not resolved) | Classifieds; services category in Egypt **not confirmed** | Services vertical | 1 | 2 | Partner for listings syndication |
| **Aqarmap** | 903,100 (4.68★) | A search snippet reports an "Ask Your Neighbors" feature [unverified]; resident advice content | Neighbourhood Q&A | 2 | 2 | Watch; possible content partner |
| **Property Finder / Bayut EG** | 1M+ each (bucket) | Listings only | — | 1 | 1 | Ignore / syndicate |
| **Talabat** | 52,323,911 (4.33★) | Food, grocery, pharmacy, flowers. **No home services in Egypt found** | Home services vertical | 2 | 4 | Phase-2 partner (building-level group orders) |
| **Breadfast** | 5,232,623 (**4.79★**) | Groceries; "Breadfast Food" launched Sep 2026; $50M pre-Series C (Feb 2026) for "new business lines" and "a single app for daily household spending" | **Home services** (cleaning, maintenance) | **3** | **4** | **Phase-2 threat and partner.** Best-rated consumer brand in Egypt. Pitch "Breadfast for the building" (bulk delivery, doorman pickup) |
| **Careem** | 64,834,110 (4.16★) | Home services via Justlife in the UAE; **Egypt not confirmed** | Port home services to Egypt | 2 | 3 | Watch |
| **Vodafone (Ana Vodafone / Vodafone Cash)** | 70,829,724 (4.38★); wallet share ~53% (file 08) | Wallet, bills, home internet; no building feature found | Fibre/internet "building deals"; wallet collection | 2 | 4 | **Partner.** Hyper-local ISP sponsorship; Vodafone Cash as a dues rail |
| **Orange Egypt (Max it)** | 38,005,671 (4.54★) | Wallet + super-app ("Max it") | Same | 1 | 3 | Partner (ads) |
| **e& Egypt** (My etisalat / e& money) | My etisalat 10M+ bucket; e& money 8,283,271 | Wallet | Same | 1 | 2 | Partner |
| **Telecom Egypt (My WE / WE Pay)** | 33,510,359 (3.10★); WE Pay 1M+ | Landline/fibre, which is **building-centric** | Fibre roll-out per building | 2 | 3 | **Partner.** Fibre lead generation from building admins |
| **Digital Egypt (مصر الرقمية)** | 2,917,204 (4.14★) | Gov e-services; real-estate registration; Egypt Real Estate platform (beta 2025, blogs.realestate.gov.eg) | **A government union registry/portal** (Saudi Arabia already runs Mullak) | 2 | **5** | **Partner/comply.** Build for future e-filing of union documents |
| **Electricity apps** (الكهربا خالص, Sahl) | Khales 78,428 (**1.46★**); Sahl 5,216,403 (4.73★) | Prepaid meter top-up (NFC/Bluetooth) | None in community features | 1 | 1 | **Opportunity.** Khales's 1.46★ shows utility pain. Add common-meter tracking and reminders |
| **Neighbourhood apps** (Ahl Madinaty, Pinpund, Compoundy) | 43,668 / 144 / 274 | Directories, offers, bus schedules | Expand to more compounds | 3 | 2 | **Learn and copy.** Possibly acquire or partner with Ahl Madinaty |
| **Facility-management firms** (Egypro FME, 800 buildings) | — | Hard and soft FM; no app named | Adopt Unitify or Boyot | 2 | 3 | **Phase-2 supply partner** and B2B channel |

### 5.1 Threat heatmap (likelihood × impact)

Score = likelihood × impact, from 1 to 25. **Bold = act now.**

| Impact ↓ / Likelihood → | 1 Rare | 2 Unlikely | 3 Possible | 4 Likely | 5 Almost certain |
|---|---|---|---|---|---|
| **5 Severe** | | Gov union portal (10) | | | |
| **4 Major** | | Fawry (8), Talabat (8), Vodafone (8) | **Breadfast home services (12)**, **Unitify localizes (12)** | | **Ettihad wins the free segment (20)** |
| **3 Moderate** | Orange (3) | valU (6), Halan (6), Careem (6), Telecom Egypt (6), FM firms (6) | Nawy Home (9), **Lyve/Milango "Lite" (9)** | **Solo-dev copycat wave (12)** | |
| **2 Minor** | InstaPay (2), Dubizzle (2), banks (2), e& (2) | MoneyFellows (4), Aqarmap (4) | Ahl Madinaty-style apps spread (6) | Sandooq adds resident app (8) | |
| **1 Negligible** | Property Finder (1), Khales (1) | | | | ELOMARA (n/a) |

**Reasoning for the top cells:**
- **Ettihad: likelihood 5, impact 4.** It is already live, free and growing fastest, with an AI assistant.
- **Copycat wave: likelihood 4, impact 3.** Fourteen or more apps appeared in five months. They fragment attention and push "free" as the baseline.
- **Unitify: likelihood 3, impact 4.** It has an explicit Egypt page and a free tier, but low installs today.
- **Breadfast: likelihood 3, impact 4.** It has new capital and a stated household-spending strategy, and it would compete with the founder's phase-2 marketplace, not phase 1.
- **Government portal: likelihood 2, impact 5.** The Saudi precedent and Egypt's push on unions (file 01) make it possible. If a state portal became mandatory for union records, private apps would have to integrate with it.

---

## 6. Arab apps: completed traction data

| App | Country | Play package | **Play installs (exact, global)** | Play rating | iOS | Notes / source |
|---|---|---|---|---|---|---|
| **Syndic Connect** | Morocco | `com.seocom.syndic` (Seocom mobile) | **8,147** | none shown | id1643767770, 0 ratings (EG store), updated Jun 2025 | Released Mar 2022 on Play; EBF incubator (file 04) |
| **Binayati** | Lebanon | `com.binayati` (ourjouwan) | **2,991** | 4.93 (bucket search) | id1378048412, updated 31 Mar 2026 | "Trusted by dozens of buildings" [self-reported] ([binayati.com](https://www.binayati.com/property-management-application/)) |
| **Sukkan (سكان)** | Jordan | not resolved (top card) | **1K+ bucket** | 3.63 | id6772121376, released 20 Aug 2026 | Developer Mohannad Maqdah |
| **Syndic Digital** | Morocco | `com.essyndic.essyndic` | 1K+ bucket | — | — | Search result, Play (ma) |
| **Majma'i (مجمعي)** | Arabic | not found on Play | — | — | id6744065457, 0 ratings, last update Apr 2025 | Appears dormant |
| **Khedma Complex** | Arabic | not found | — | — | id6742105033 (file 04) | No traction found |
| **مجمع الرحاب السكني** | Iraq/Gulf | — | — | — | id6756591318, 0 ratings | One of many single-compound apps (Lamassu UAE builds several in Iraq: Baghdad complexes 100–1K+ each) |
| **ملاك المرافق** | KSA | `com.njik.molakmarafeq` | 194 | — | id6782949114 | — |
| **Ethadna (اتحادنا)** | KSA | `sa.ethadna.app` | 1+ | — | — | — |
| *Benchmark:* **ADDA** | India | `com.threefiveeight.adda` | **1,149,255** | 4.2 (44,639) | — | Scale proof for the category |
| *Benchmark:* **Justlife** (home services) | UAE | `com.mobile.justmop` | 962,423 | 4.21 | — | Careem's home-services partner |
| *Benchmark:* **ServiceMarket** | UAE | not resolved | 100K+ bucket | 4.70 | — | — |

**Conclusion:** no Arab building app has passed about 10K installs. The region has **no proof of scale**. Whoever wins Egypt (about 100M+ people, dense apartment stock) becomes the Arab leader by default (ESTIMATE).

---

## 7. Chart-ready datasets

### 7.1 Installs by segment (exact Play counters, 2026-10-12)

```csv
segment,player,installs
ordinary_building,Ettihad,3000
ordinary_building,Ammarty,1684
ordinary_building,Amarati,1416
ordinary_building,Sandooq El Emara,961
ordinary_building,Omaraty,365
ordinary_building,Bonian,247
ordinary_building,Imarti,125
ordinary_building,others (12 apps),~1000
compound_b2b,Milango family,82705
compound_b2b,Lyve family,77323
compound_b2b,Emaar Misr App,44478
compound_b2b,Mountain View (Intcore),14209
compound_b2b,PALM HILLS in-house,7206
compound_b2b,OneCommunity New Giza,4347
grassroots,Ahl Madinaty,43668
foreign,Unitify,688
benchmark,ADDA (India),1149255
```

### 7.2 Ratings: resident sentiment (Play vs iOS Egypt)

```csv
app,play_rating,play_n,ios_eg_rating,ios_n
Lyve-App,4.4,354,3.32,69
SODIC (Milango),3.26,51,2.22,81
Morshedy (Milango),3.62,47,3.36,25
Al-Ahly Sabbour (Milango),3.47,17,3.95,22
City Edge (Milango),3.76,93,4.11,9
MyPorto (Milango),4.35,47,3.72,18
Amarati,4.74,43,4.5,4
Ettihad,4.5,8,5.0,1
Ahl Madinaty,4.62,199,,
OneCommunity (New Giza),2.42,38,,
PALM HILLS in-house,2.97,34,,
```

### 7.3 Adjacent-giant reach (Android, exact)

```csv
giant,installs
Ana Vodafone,70829724
Careem,64834110
Talabat,52323911
Orange EG,38005671
My WE,33510359
InstaPay,25328361
Halan,15470954
myFawry,13498482
e& money,8283271
MoneyFellows,7300721
Sahl,5216403
Breadfast,5232623
valU,4917494
Nawy,3644953
Digital Egypt,2917204
Aqarmap,903100
FilKhedma,178066
```

---

## 8. Strategic implications for the founder

1. **Speed matters more than features.** The ledger is commoditized: 14+ clones appeared in 5 months, several free. The defensible assets are:
   1. **WhatsApp-group presence** (a bot in every group, so each group carries the brand to 10–40 people);
   2. **resident accounts and network density** (buildings → streets → districts);
   3. **trust data**, such as payment history and provider ratings, which later powers the marketplace.
2. **Out-feature Ettihad where it is deliberately absent:** WhatsApp, chat, doorman, Egyptian dialect, legal kit, marketplace and offline. Match it on free, iOS, AI voice, pay links, QR visitors, voting and OCR. A **feature-parity floor** for launch is matrix items 1–9, 16–18, 22–25, 28–30, 32, 35–36, 38–45, 53–54, 58–59, 70–71, 73, 76–78, 80 and 83–84.
3. **Steal the best single ideas** (each is proven by one competitor):
   - meter-photo split (Amarati);
   - WhatsApp summary image (Amarati);
   - custody and mosque fund (Sandooq);
   - voice in Egyptian dialect (Sandooq);
   - pay links for non-app users (Ettihad);
   - anonymous issues plus a public board (Ettihad);
   - countdown offers (Imarti);
   - flat number + PIN login (Ammarty);
   - AI classifier and WhatsApp-export digest (Unitify);
   - Law 119 guides and free calculators as SEO (Sandooq);
   - a directory of nearby businesses (Ahl Madinaty, ELOMARA).
4. **Treat the giants as rails:**
   - payments: InstaPay links, Fawry references and Vodafone Cash;
   - big-ticket financing: valU, Halan and MoneyFellows;
   - phase-2 supply: Breadfast, FilKhedma and FM firms such as Egypro;
   - leads: Nawy for resale and rent, Telecom Egypt and Vodafone for fibre.
   
   Each is a **revenue share, not a build**.
5. **Hedge against a government portal.** Store union documents in a format that could be exported to a state registry, and position the product as the tool that prepares the official 8-document union file (file 01).

---

## 9. Verification log

| # | Claim | Status | Second source / method | Source |
|---|---|---|---|---|
| 1 | Amarati: 1,416 installs, 4.74★ (43), released 21 Jun 2026, no IAP | **confirmed** | Matches files 06 and 07 (same counter); iOS 4.5★ (4) via iTunes API | [Play](https://play.google.com/store/apps/details?id=com.amarati.app) · [iOS](https://apps.apple.com/eg/app/id6791464029) |
| 2 | Imarti: 125 installs, no rating, no IAP, released 26 Jul 2026 | **confirmed** | Matches file 07; iOS listing found (0 ratings) | [Play](https://play.google.com/store/apps/details?id=com.craftfuture.imarti) · [iOS](https://apps.apple.com/eg/app/id6796346427) |
| 3 | Imarti charges a subscription | **unverified / likely a misreading** | No IAP on either store; "اشتراكات" in the description means residents' dues | as above |
| 4 | Sandooq: 961 installs, 4.75★ (16), 49.99/499.99 EGP | **confirmed** | Play IAP range + website pricing | [Play](https://play.google.com/store/apps/details?id=com.amrem.sandooqelamara) · [site](https://sandoqalemara.com) |
| 5 | Ettihad: 3,000 installs, free, NL company, AI "فاري" | **confirmed** | Play counter + ettihad.org company section | [Play](https://play.google.com/store/apps/details?id=com.ittihad.ettihad) · [site](https://www.ettihad.org) |
| 6 | Saknna pricing 450/900/2,200/7,500 EGP; 500+ buildings | **pricing confirmed** (2nd fetch, same as files 01, 08 and 11); **500+ unverified** | Counter renders 0; no press found | [saknna.com/ar](https://saknna.com/ar) |
| 7 | Saknna has no store app | **confirmed (not found)** | Play + iOS search, EG | — |
| 8 | Unitify pricing $0/$0.5/$1.5 per apartment | **confirmed** | Matches file 01 | [unitify.com/egypt](https://unitify.com/egypt) |
| 9 | Unitify 688 global installs | **confirmed** | Play counter; file 01 bucket 500+ is consistent | [Play](https://play.google.com/store/apps/details?id=com.unitify.client) |
| 10 | Unitify "10,000 management companies, 5M apartments" | **self-reported, unverified** | Contradicted in spirit by low installs; no press | unitify.com/egypt |
| 11 | Lyve family ≈77,323; Milango family ≈82,705 Android installs | **confirmed (sum of exact counters)**; family membership based on developer names | Play | §2.2 |
| 12 | Lyve CEO | **conflict:** site says Ahmed Amr; press says Karim Akram | Enterprise AR (Aug 2024); Egypt Innovate (2020) | [lyve-app.com](https://lyve-app.com) · [Enterprise AR](https://enterpriseam.com/egypt-ar/2024/08/08/روتيني-الصباحي-كريم-أكرم-العضو-المنتد/) |
| 13 | Milango ~EGP 100M transactions; acquired Circle (2022) | **confirmed** (CairoScene; Startup Scene mirror) | Two outlets | [CairoScene](https://cairoscene.com/Business/Egyptian-Community-Management-Startup-Milango-Acquires-Circle) |
| 14 | Boyot offers a WhatsApp chatbot | **self-reported** | Only boyot.app | [boyot.app](https://boyot.app/) |
| 15 | Boyot seed Jun 2022; iCommunity $600K, Series A 2018 | **confirmed** (Tracxn) | CB Insights (file 01) for iCommunity | [Tracxn](https://tracxn.com/d/explore/property-management-tech-startups-in-cairo-egypt/__S5mrR_yUK7xCxshl2P8AV0Nrdf03fnmn64U_LHd3ZJY) |
| 16 | Breadfast $50M pre-Series C (Feb 2026); Breadfast Food (Sep 2026) | **confirmed** (search summary of Dabafinance / AllAfrica) | Two outlets in results | [Dabafinance](https://dabafinance.com/en/news/breadfast-egypt-l-ve-de-la-pr--s-rie-c-expansion-ipo) · [AllAfrica](https://fr.allafrica.com/stories/202609140722.html) |
| 17 | No Breadfast/Talabat home services in Egypt | **not found** (absence) | — | search, 2026-10-12 |
| 18 | valU home-maintenance installments with developers | **confirmed (2022)** | EFG + Invest-Gate + CairoScene | [EFG](https://efghldg.com/media/news/valu-partners-with-arab-developers-holding) |
| 19 | MoneyFellows 7.3M Play installs; 7–8.5M users | installs **confirmed**; user count **conflicting** | Play counter; TechCrunch / LaunchBase | [TechCrunch](https://techcrunch.com/2025/05/04/moneyfellows-raises-13m-to-take-its-group-savings-model-outside-egypt) |
| 20 | Fawry union/compound-dues product | **not found** | AR + EN searches | — |
| 21 | Egypro FME manages 800 buildings | **single source** | Amwal Al Ghad, 21 Oct 2025 | [Amwal Al Ghad](https://amwalalghad.com/2025/10/21/%d8%b4%d8%b1%d9%83%d8%a9-egypro-fme-%d8%aa%d8%af%d9%8a%d8%b1-800-%d9%85%d8%a8%d9%86%d9%89-%d8%a8%d9%85%d8%b3%d8%a7%d8%ad%d8%a9-%d8%a5%d8%ac%d9%85%d8%a7%d9%84%d9%8a%d8%a9-3-5-%d9%85%d9%84/) |
| 22 | Syndic Connect 8,147; Binayati 2,991 installs | **confirmed** | Play counters; Binayati 1K+ bucket matches the web search | Play |
| 23 | ELOMARA has no store listing, team or traction | **confirmed (not found)** | Site + web search + Play/iOS search | [elomara.com/ar](https://elomara.com/ar) |
| 24 | No Egyptian community-management raise in 2025–2026 | **not found** (absence) | Extended search + Tracxn | — |
| 25 | Electricity Khales app 1.46★ | **confirmed** | Play | Play `com.efinance.deltamobilepay` |

---

## 10. Gaps that remain (honest list)

- **Admin plans and paywalls of Amarati and Imarti** need a hands-on install (§1.3).
- **Per-country install splits** are not public. All Play counters are global. Amarati's (Palestine) and Ettihad's (7 countries) Egyptian shares are unknown.
- **YouTube demos and social pages** of Saknna, ELOMARA, Lyve and Milango were not reviewed in video form. milango.com failed with a TLS error during this session.
- **Fawry, InstaPay and Vodafone Cash merchant collection pricing** is not public (see file 14).
- **Dubizzle EG package** was not resolved, so only the bucket (10M+) is used.
- **Sukkan exact installs** were not resolved (the top search card hides the package ID).

---

## 11. Sources

**Store data (pulled 2026-10-12, google-play-scraper, country=eg; iTunes Search API, country=eg)**
- Play: [com.amarati.app](https://play.google.com/store/apps/details?id=com.amarati.app&hl=ar&gl=EG) · [com.craftfuture.imarti](https://play.google.com/store/apps/details?id=com.craftfuture.imarti&hl=ar&gl=EG) · [com.ittihad.ettihad](https://play.google.com/store/apps/details?id=com.ittihad.ettihad) · [com.ammarty.ammarty](https://play.google.com/store/apps/details?id=com.ammarty.ammarty) · [com.amrem.sandooqelamara](https://play.google.com/store/apps/details?id=com.amrem.sandooqelamara) · [com.omaraty.app](https://play.google.com/store/apps/details?id=com.omaraty.app) · [io.homena.app](https://play.google.com/store/apps/details?id=io.homena.app) · [com.bonian.mobile](https://play.google.com/store/apps/details?id=com.bonian.mobile) · [com.mk.theboxproject](https://play.google.com/store/apps/details?id=com.mk.theboxproject) · [com.mrizk.emara.building](https://play.google.com/store/apps/details?id=com.mrizk.emara.building) · [com.pinpund.app](https://play.google.com/store/apps/details?id=com.pinpund.app) · [com.melsayed25.compoundy](https://play.google.com/store/apps/details?id=com.melsayed25.compoundy) · [com.resaleapp.resaleApp](https://play.google.com/store/apps/details?id=com.resaleapp.resaleApp) · [app.isgapps.OwnersAssociation](https://play.google.com/store/apps/details?id=app.isgapps.OwnersAssociation) · [com.unitify.client](https://play.google.com/store/apps/details?id=com.unitify.client) · [boyot.tenant.app](https://play.google.com/store/apps/details?id=boyot.tenant.app)
- Compounds: [com.moonshot.icommunity](https://play.google.com/store/apps/details?id=com.moonshot.icommunity) (+ `.lavista`, `.palmhills`, `.hydePark`, `.hap`, `.dorra`, `.almarasem`, `.sed`) · [app.milango.cityedge](https://play.google.com/store/apps/details?id=app.milango.cityedge) (+ `.morshedy`, `.amergroup`, `.alahlysabbour`, `.misritalia`, `com.kijamii.sodiccommapp`) · [com.kijamii.emaarcommunities](https://play.google.com/store/apps/details?id=com.kijamii.emaarcommunities) · [com.congora.mountainview](https://play.google.com/store/apps/details?id=com.congora.mountainview) · [com.palmhills.communityapp](https://play.google.com/store/apps/details?id=com.palmhills.communityapp) · [com.newgiza.onecommunity](https://play.google.com/store/apps/details?id=com.newgiza.onecommunity) · [com.oradevelopers.users.app](https://play.google.com/store/apps/details?id=com.oradevelopers.users.app) · [com.ahl.madenty](https://play.google.com/store/apps/details?id=com.ahl.madenty)
- Giants: [com.fawry.myfawry](https://play.google.com/store/apps/details?id=com.fawry.myfawry) · [com.egyptianbanks.instapay](https://play.google.com/store/apps/details?id=com.egyptianbanks.instapay) · [com.moneyfellows.mobileapp](https://play.google.com/store/apps/details?id=com.moneyfellows.mobileapp) · [com.efgh.customer](https://play.google.com/store/apps/details?id=com.efgh.customer) · [com.halanuser](https://play.google.com/store/apps/details?id=com.halanuser) · [com.cooingestate.cooing_app](https://play.google.com/store/apps/details?id=com.cooingestate.cooing_app) · [com.aqarmap.android](https://play.google.com/store/apps/details?id=com.aqarmap.android) · [com.talabat](https://play.google.com/store/apps/details?id=com.talabat) · [com.breadfast](https://play.google.com/store/apps/details?id=com.breadfast) · [com.careem.acma](https://play.google.com/store/apps/details?id=com.careem.acma) · [com.emeint.android.myservices](https://play.google.com/store/apps/details?id=com.emeint.android.myservices) · [com.orange.mobinilandme](https://play.google.com/store/apps/details?id=com.orange.mobinilandme) · [com.ucare.we](https://play.google.com/store/apps/details?id=com.ucare.we) · [com.etisalat.flous](https://play.google.com/store/apps/details?id=com.etisalat.flous) · [Digital Egypt](https://play.google.com/store/apps/details?id=gov.ministryofcommunicationsandinformationtechnology.digitalegypt) · [com.efinance.deltamobilepay](https://play.google.com/store/apps/details?id=com.efinance.deltamobilepay) · [gtpay.gtronicspay.com](https://play.google.com/store/apps/details?id=gtpay.gtronicspay.com) · [com.filkhedma.customer](https://play.google.com/store/apps/details?id=com.filkhedma.customer)
- Arab and benchmarks: [com.seocom.syndic](https://play.google.com/store/apps/details?id=com.seocom.syndic) · [com.binayati](https://play.google.com/store/apps/details?id=com.binayati) · [com.threefiveeight.adda](https://play.google.com/store/apps/details?id=com.threefiveeight.adda) · [com.mobile.justmop](https://play.google.com/store/apps/details?id=com.mobile.justmop)
- iOS (EG): [Amarati id6791464029](https://apps.apple.com/eg/app/id6791464029) · [Imarti id6796346427](https://apps.apple.com/eg/app/id6796346427) · [Ettihad id6760418161](https://apps.apple.com/eg/app/id6760418161) · [Lyve-App id1138437170](https://apps.apple.com/eg/app/id1138437170) · [SODIC id1390362823](https://apps.apple.com/eg/app/id1390362823) · [Homena id6818112920](https://apps.apple.com/eg/app/id6818112920) · [BOS id6810878518](https://apps.apple.com/eg/app/id6810878518) · [Bonian id6807542704](https://apps.apple.com/eg/app/id6807542704) · [Sukkan id6772121376](https://apps.apple.com/eg/app/id6772121376) · [Binayati id1378048412](https://apps.apple.com/eg/app/id1378048412) · [Majma'i id6744065457](https://apps.apple.com/eg/app/id6744065457) · [Syndic Connect id1643767770](https://apps.apple.com/eg/app/id1643767770)

**Company websites**
- [saknna.com/ar](https://saknna.com/ar) · [sandoqalemara.com](https://sandoqalemara.com) · [elomara.com/ar](https://elomara.com/ar) · [unitify.com/egypt](https://unitify.com/egypt) · [ettihad.org](https://www.ettihad.org) · [lyve-app.com](https://lyve-app.com) · [boyot.app](https://boyot.app/) · [geraan.com](https://geraan.com/) · [binayati.com](https://www.binayati.com/property-management-application/)

**News and databases**
- Milango: [CairoScene](https://cairoscene.com/Business/Egyptian-Community-Management-Startup-Milango-Acquires-Circle) · [Enterprise, Dec 2022](https://enterpriseam.com/egypt/2022/12/27/meet-our-founder-of-the-week-milangos-amr-mostafa/) · [Wamda, 2020](https://www.wamda.com/en/2020/10/milango-raises-seed-investment)
- Lyve: [Egypt Innovate](https://egyptinnovate.com/en/news/icommunity-is-now-lyve-a-new-facelift-simplifying-life-in-compounds) · [Enterprise 2021](https://enterpriseam.com/egypt/2021/06/01/raya-trade-doing-consumer-finance-with-lyve-hawaya-hits-4-mn-users/)
- Tracxn: [Cairo property-management tech list](https://tracxn.com/d/explore/property-management-tech-startups-in-cairo-egypt/__S5mrR_yUK7xCxshl2P8AV0Nrdf03fnmn64U_LHd3ZJY)
- Proptech: [Wamda, Byit](https://www.wamda.com/2026/05/egypt-born-proptech-byit-expands-uae) · [TechCrunch, Nawy](https://techcrunch.com/2025/05/11/egypts-nawy-lands-a-52m-series-a-to-take-on-mena) · [Dabafinance, Nawy](https://dabafinance.com/en/news/egypts-nawy-raises-75m-series-a-to-scale-proptech-platform) · [MENA Startup Digest, PropTech Challenge](https://menastartupdigest.com/egypt-proptech-challenge-2026-opens-applications-for-12-startups/)
- Breadfast: [Dabafinance](https://dabafinance.com/en/news/breadfast-egypt-l-ve-de-la-pr--s-rie-c-expansion-ipo) · [AllAfrica](https://fr.allafrica.com/stories/202609140722.html)
- MoneyFellows: [TechCrunch](https://techcrunch.com/2025/05/04/moneyfellows-raises-13m-to-take-its-group-savings-model-outside-egypt) · [LaunchBase](https://launchbaseafrica.com/2025/05/05/egypts-moneyfellows-secures-13m-to-prove-roscas-can-scale-across-borders/)
- valU: [EFG](https://efghldg.com/media/news/valu-partners-with-arab-developers-holding) · [CairoScene, SODIC](https://cairoscene.com/buzz/valu-provides-sodic-with-exclusive-summer-home-finishing-payment-pla)
- Careem: [Entrepreneur, Justlife](https://mena.entrepreneur.com/?p=27098)
- Egypro FME: [Amwal Al Ghad](https://amwalalghad.com/2025/10/21/%d8%b4%d8%b1%d9%83%d8%a9-egypro-fme-%d8%aa%d8%af%d9%8a%d8%b1-800-%d9%85%d8%a8%d9%86%d9%89-%d8%a8%d9%85%d8%b3%d8%a7%d8%ad%d8%a9-%d8%a5%d8%ac%d9%85%d8%a7%d9%84%d9%8a%d8%a9-3-5-%d9%85%d9%84/)
- Electricity top-up: [Masrawy](https://www.masrawy.com/news/news_egypt/details/2025/1/22/2714129)
- Unions context: [Akhbar El Yom](https://m.akhbarelyom.com/news/newdetails/4808370/1/مأساة-اتحادات-الشاغلين) · [Amwal Al Ghad](https://amwalalghad.com/4z1e)
- InstaPay: [Egyptian Streets](https://egyptianstreets.com/2026/01/04/inside-egypts-instapay-economy-how-instant-payments-are-changing-access-for-a-new-generation/)
- Egypt real-estate platform: [realestate.gov.eg blog](https://blogs.realestate.gov.eg/empowering-governance-egypts-official-real-estate-platform)

**Cross-references:** files 01 (building apps), 04 (Arab), 06 and 07 (reviews), 08 (market size: InstaPay ~22M, wallet shares), 10 (WhatsApp bot), 12 (UX), 13 (growth), 14 (costs and payments).
