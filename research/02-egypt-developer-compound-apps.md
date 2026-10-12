# 02: Egyptian Developer & Compound Resident Apps, Community-Management Vendors, Access Control and PropTech

**Research angle:** What large Egyptian developers, their facility-management (FM) arms and proptech platforms already offer residents. Where these apps fail, who builds them, and what that means for an independent building/compound app: partner or compete.
**Research date:** 2026-10-12
**Method:** I pulled Google Play listings live with `gl=EG`, including install bands, ratings, last-update dates and the 30–40 newest reviews per app through Play's public review endpoint. I also ran web searches in Arabic and English (news, startup databases, vendor sites, court and policy news). I quote reviews verbatim, with the star rating and date shown on Google Play. Anything marked **ESTIMATE** is my own reasoning, not a sourced fact.

> Note on Play links: every app below links to `https://play.google.com/store/apps/details?id=<package>`. Install bands, ratings and dates are the values Google Play showed on 2026-10-12.

---

## 0. Executive summary (TL;DR)

1. **Almost every major Egyptian developer now has a resident app, and almost none of them work well.** I sampled 314 recent Google Play reviews across 18 developer and compound apps. **51% were 1–2 stars.** Recent reviews for SODIC, Emaar Misr, Mountain View, Palm Hills and Madinet Masr were **67–78% negative**.
2. **The apps are small.** The largest, TMG Life (Madinaty, Rehab and other TMG cities), has **50K+ installs**, and Madinaty alone is planned for about 120,000 units. Most others sit at **1K–10K installs**. No single app has mass reach, and **no cross-developer resident identity exists**.
3. **A handful of white-label vendors build them.** The main ones are **Lyve** (ex-iCommunity, backed by Algebra Ventures), **Milango** (spun out of the agency Kijamii, backed by A15, bought rival Circle and claimed 100K+ contracted units in 2022), **Intcore/"Lighthouse"** (which took Mountain View from Milango in late 2025) and smaller shops (COMET, TownTender, RAY Labs, Cyparta, JTech). Their business is **B2B SaaS sold to developers and FM companies**. Residents are not their customer.
4. **The complaints repeat everywhere:** login and OTP failures (27% of negative reviews), crashes and slowness (44%), phantom "update required" loops (12%), false "insecure device" blocks and single-device bans (9%), no support (11%), failure for owners abroad or with foreign numbers, gate QR codes that fail at the barrier, service requests that are never fulfilled, and promotional spam in notifications.
5. **Structurally, developer apps sit on the developer's side** of a growing developer-vs-resident conflict over maintenance deposits and fees (court cases, and in **Sept 2026** the head of the Real Estate Development Chamber called for separating maintenance and management from developers). **No app represents the resident or the occupants' union (اتحاد الشاغلين).**
6. **The 90%+ of urban Egypt that is not a premium gated compound is almost untouched**: ordinary عمارات, mid-tier compounds, state compounds and self-managed buildings. Only tiny one-off apps exist there (for example "كمبوندى (حدائق الاهرام)", 100+ installs).
7. **Recommendation:**
   - **Compete** where developers are absent: ordinary buildings, mid-tier and self-managed compounds, and occupants' unions.
   - **Partner, don't fight,** inside premium developer compounds. There, be the *resident layer* (WhatsApp bot, neighbor network, personal alerts, marketplace) that sits above the developer's gate/FM app, and integrate through APIs with gate vendors (Lyve Key, GateFlow, ANPR Hub). Later, offer FM firms (EFS, SODIC's Edara and others) a free operations console in exchange for distribution.
   - Every negative review theme above is a ready-made **"we fix this"** feature list.

---

## 1. Landscape map: who serves Egyptian compound residents digitally

### 1.1 Developer-branded resident apps (Google Play Egypt, 2026-10-12)

| # | App (developer) | Package / builder | Installs | Rating (reviews) | Last update | Core features (from listing) |
|---|---|---|---|---|---|---|
| 1 | **TMG Life** (Talaat Moustafa Group – Madinaty, Rehab, Noor, etc.) | `com.tmglife.app`, publisher TMG | **50K+** | 4.8 (1.16K) | 11 Aug 2026 | Pay bills, renew club membership, access services, events/news, **NFC charging of prepaid utility cards**, QR |
| 2 | **Emaar Misr App** (Uptown Cairo, Mivida, Marassi) | `com.kijamii.emaarcommunities` (Kijamii = Milango's origin agency) | 10K+ | 3.9 (261) | 7 Oct 2026 | ID badge, visitor QR, announcements, home services, utility bill payment, permits, feedback |
| 3 | **Mountain View Community** (new, "Powered by Lighthouse") | `com.congora.mountainview`, Intcore | 10K+ | 3.7 (34) | 25 Aug 2026 | In-app badge, guest QR, service requests, curated cleaning/landscaping/pest control, news, offers |
| 4 | Mountain view (old app) | `app.milango.mountainview`, Milango APM | 10K+ | 3.0 (52) | 8 Dec 2025 (abandoned) | "Facilitate unit operations" |
| 5 | **SODIC** | `com.kijamii.sodiccommapp`, Milango APM | 5K+ | 3.3 (51) | 23 Sep 2026 | Home services, E-Gate passes, events, feedback by text/voice/image/call |
| 6 | **PALM HILLS** | `com.palmhills.communityapp`, Palm Hills Development Co. | 5K+ | 3.0 (34) | 7 Oct 2026 | News, unit management/payment history/documents, family access, maintenance requests |
| 7 | **City Edge Developments** (state-linked developer, New Capital/Alamein) | `app.milango.cityedge` | 10K+ | 3.8 (93) | 30 Sep 2026 | Request services, notifications, feedback, add home-mates |
| 8 | **Smart Village** | `app.milango.smartvillage` | 10K+ | 3.5 (35) | 28 Sep 2026 | News, events, privileges, services |
| 9 | **Morshedy Group** | `app.milango.morshedy` | 10K+ | 3.6 (47) | 5 Aug 2026 | Announcements, alerts, services, feedback |
| 10 | **La Vista** | `com.moonshot.lavista`, Lyve | 10K+ | 4.3 (106) | 22 Sep 2026 | Services, ID badge, guest invites, nearby places, "100% authenticated residents" |
| 11 | **Lyve-App** (generic multi-compound) | `com.moonshot.icommunity` | 10K+ | 4.4 (354) | 21 Sep 2026 | Notifications, in-home services, public-area issue reports, gate passes, local stores |
| 12 | **Madinet Masr** (Taj City, Sarai) | `com.madinetmasr.community`, in-house "Madinet Masr Innovation Labs" | 5K+ | **2.4** (24) | 30 Mar 2026 | Home help, installment tracking, E-Gate |
| 13 | **MyPorto** (Amer Group/Porto) | `app.milango.amergroup` | 5K+ | 4.3 (47) | 14 Jul 2026 | Community app, CRM, services |
| 14 | Wadi Degla Developments | `app.milango.wadidegla` | 5K+ | 4.4 (25) | 19 May 2026 | Requests, notifications, feedback, home-mates |
| 15 | Al-Ahly Sabbour | `app.milango.alahlysabbour` | 5K+ | 3.5 (17) | 1 Sep 2026 | Mostly sales: projects, virtual tours, payments |
| 16 | **Tatweer Misr Communities** | `com.macber.eg.tatweer`, COMET Innovations (UAE) | 1K+ | 3.4 (14) | 23 Sep 2026 | Property mgmt, access-gate control, guests, facility requests, city guide |
| 17 | **Hassan Allam Properties App** | `com.moonshot.hap`, Lyve | 1K+ | 4.0 (10) | 21 Sep 2026 | Alerts, in-house services, QR gate, guest entry |
| 18 | Places by Hyde Park | `com.moonshot.hydePark`, Lyve | 1K+ | n/a | 21 Sep 2026 | (Lyve white label) |
| 19 | Al Marasem / DORRA / Marakez Spaces / ALBUROUJ | `com.moonshot.*`, Lyve | 1K+ each | 4.6 / 4.8 / 4.7 / 4.6 | 2026 | Lyve white label |
| 20 | **ORA Developers** (ZED, Silversands) | `com.oradevelopers.users.app` | 1K+ | 2.7 (7) | 15 Jun 2026 | QR gate, guests, service requests, payments/installments, family, nearby shops |
| 21 | El Gouna – Red Sea (Orascom) | `com.orascomhd.elgounaapp` | 1K+ | n/a | 30 Sep 2026 | Town app |
| 22 | Hacienda App (Palm Hills North Coast) | `com.towntender.haciendapp`, TownTender LLC (+ separate staff app) | 100+ | n/a | 15 Aug 2026 | Smart-gate QR, requests with rating, alerts, directory |
| 23 | Badya (Palm Hills) | `com.cyparta.badya`, Cyparta | 100+ | n/a | Oct 2025 | — |
| 24 | Canary Village / Kingdom City compounds | `com.getray.*`, RAY Labs (Beirut-based SaaS) | 100+ | n/a | 11 Oct 2026 | — |
| 25 | Misr Italia Engage | `app.milango.misritalia` | 100+ | n/a | Mar 2026 | — |
| 26 | كمبوندى (حدائق الاهرام) | `com.melsayed25.compoundy` | 100+ | n/a | Sep 2026 | Independent app for a mid-tier area |
| 27 | Ahl Madinaty (resident-made guide) | `com.ahl.madenty`, "thelegend" | 10K+ | 4.6 (199) | 7 Oct 2026 | Directory of restaurants, clinics, doctor schedules, **bus schedules**, offers, magazine |

Sources: the Google Play page for each package (e.g. https://play.google.com/store/apps/details?id=com.tmglife.app, https://play.google.com/store/apps/details?id=com.kijamii.sodiccommapp, https://play.google.com/store/apps/details?id=com.palmhills.communityapp, https://play.google.com/store/apps/details?id=com.congora.mountainview, https://play.google.com/store/apps/details?id=com.kijamii.emaarcommunities, https://play.google.com/store/apps/details?id=com.moonshot.icommunity, https://play.google.com/store/apps/details?id=com.macber.eg.tatweer, https://play.google.com/store/apps/details?id=com.madinetmasr.community, https://play.google.com/store/apps/details?id=com.oradevelopers.users.app, https://play.google.com/store/apps/details?id=app.milango.cityedge, https://play.google.com/store/apps/details?id=com.ahl.madenty and so on). The Apple App Store lists TMG Life at 4.7 from 51 ratings, the SODIC Community App at 2.7 from 12 ratings, PALM HILLS at 1.7 from 10 ratings, and Palm Hills Live (the older Lyve-built app) at 4.0 from 4 ratings (search snippets of https://apps.apple.com/app/id6502700910, https://apps.apple.com/app/id1390362823, https://apps.apple.com/us/app/-/id6477568109, https://apps.apple.com/us/app/-/id1508135755).

**Not found:** I found **no dedicated resident app** on Google Play for **Hyde Park** (other than the Lyve white-label "Places by Hyde Park"), **ACUD / New Administrative Capital residential districts**, **Mivida/Uptown as separate apps** (they are inside the Emaar Misr app), or **Rehab city** (two unofficial apps exist: `com.newsmart.rehab` with 5K+ installs, last updated Aug 2023, and `alrehab.city` with 500+, last updated Sep 2022; TMG Life covers Rehab officially). Emaar's global **Emaar One** app (100K+, 4.7) serves **UAE** customers, whose reviews reference "UAE Pass" and "800-EMAAR", so it is not an Egypt resident app.

### 1.2 The vendor layer: who actually builds these apps

| Vendor | Origin / backing | Scale claims (sourced) | Known Egyptian clients | Notes |
|---|---|---|---|---|
| **Lyve** (ex-**iCommunity**, publisher "New Moonshot for Information Technologies", Heliopolis) | Founded Aug 2016; **US$600K Series A from Algebra Ventures (Oct 2018)** | 2020: "over 50 compounds with about 40,000 units"; LinkedIn: 11–50 staff | Palm Hills (Palm Hills Live), La Vista, Rooya, MNHD, Katameya Heights, Hassan Allam, Hyde Park, Al Marasem, DORRA, Marakez, AlBurouj, TAMEER, Stella | 2020 rebrand **opened the app to third-party sellers**. Side apps: **Lyve Key** (access), **Lyve Loyalty** (badge-QR discounts), **Lyve Truck Entry** (truck permits) |
| **Milango APM** (Maadi) | Spun out of the Cairo agency **Kijamii** (serving clients since 2016) in early 2020; **six-figure seed from A15**; **acquired Circle (500 Startups-backed) in Feb 2022** | "contracted user base … more than 100,000 residential units"; users "nearing EGP 100 million in financial transactions" (2022) | SODIC, Emaar Misr (kijamii namespace), El Gouna, Almaza Bay, Mountain View (lost in 2025), City Edge, Wadi Degla, Smart Village, Morshedy, Amer/Porto, Al-Ahly Sabbour, Misr Italia, Makadi Heights, Masaya, Manaj, Arkan Plaza | Also serves sporting clubs (digital IDs, bookings) |
| **Intcore** ("Lighthouse" platform) | Cairo software house | — | Mountain View (new app, late 2025) | Mountain View moved from Milango to Intcore. An old-app review (22 Dec 2025) complains of being told "to delete the old app" |
| **COMET Innovations IT LLC** | UAE | — | Tatweer Misr | — |
| **TownTender LLC** | — | — | Hacienda (Palm Hills) | Separate staff app |
| **RAY Labs (getray)** | Beirut-based property SaaS (founded 2016) per data aggregators | — | Canary Village, Kingdom City compounds | Also active in KSA/Dubai |
| **GAIT** (Ghanem AI Technology) | Egyptian | Says it built a city-services platform for "one of Egypt's major urban developments", "tens of thousands of residents" (vendor claim) | Unnamed | Blog of 11 Jul 2026 |
| In-house | — | — | TMG (TMG Life), Madinet Masr ("Innovation Labs"), Palm Hills (new 2024 app), ORA | — |

Sources: Lyve and iCommunity: https://egyptinnovate.com/en/news/icommunity-is-now-lyve-a-new-facelift-simplifying-life-in-compounds, https://mena.entrepreneur.com/finance/we-got-funded-cairo-based-icommunity-raises-us600000/321045, https://www.menabytes.com/icommunity-600k/, https://www.linkedin.com/company/lyve-app, https://play.google.com/store/apps/details?id=com.moonshot.lyvekey, https://play.google.com/store/apps/details?id=com.moonshot.lyvetrucks, https://play.google.com/store/apps/details?id=com.moonshot.lyveloyalty. Milango: https://www.menabytes.com/milango-acquires-its-local-rival-circle/, https://www.wamda.com/2022/02/milango-acquires-proptech-startup-circle, https://www.menabytes.com/milango-seed/, https://www.wamda.com/2020/10/milango-raises-seed-investment. RAY: https://www.datanyze.com/companies/ray/440486743. GAIT: https://gaitco.com/blog/compound-management-system-resident-app-egypt.

**Funding gap:** I found **no 2023–2026 funding round** for Lyve or Milango. The most recent public events are Milango buying Circle (Feb 2022) and Lyve's Series A (2018). Tracxn reports Egyptian startup funding for Jan–Sep 2026 **down about 47.6% vs the same period of 2025** (US$188M across 19 equity rounds vs US$358M across 33) **[corrected: the earlier draft said 62.76%]** (https://tracxn.com/d/geographies/egypt/__aRcH8lYOC74CSa9mr7vgyEJG0aUdj3E52SUBjjv4gy0). **Interpretation:** the incumbents are small, capital-constrained B2B shops, not well-funded consumer platforms.

### 1.3 Proptech platforms: do they touch resident services?

| Platform | Play installs / rating | Resident-service relevance |
|---|---|---|
| **Nawy** (Cooing) | 1M+ / 4.1 (2.64K) | Buy/sell/invest. **Nawy Unlocked** (after buying property manager **ROA** in Jan 2025): finishes and furnishes owners' units, covers up to 50% of cost, finds tenants, manages leases and maintenance. Partnerships with **Marakez and SODIC**; 60+ units across 18 compounds at launch. **Nawy Now** (move in now, pay over 7 years), **Nawy Shares** (100K+, fractional). This is the closest proptech gets to post-sale owners, and it targets investors, not daily life. |
| **Aqarmap** | 500K+ / 4.7 (6.81K) | Listings plus guides. No resident ops found. |
| **Property Finder** (regional app) | 1M+ / 4.0 (8.58K) | Listings. No resident ops found. |
| **Bayut Egypt** | 1M+ / 4.6 (2.89K) | Listings only (search, favorites, call agent). |
| **dubizzle EG (OLX)** | **10M+ / 4.7 (697K)** | Has a **"Home Services & Maintenance"** category: electricians, AC and appliance repair priced in EGP, some "verified" sellers. This is the de-facto informal marketplace for فني/سباك/كهربائي today, with no building context and no trust layer. |

Sources: https://play.google.com/store/apps/details?id=com.cooingestate.cooing_app, https://www.wamda.com/en/2025/01/nawy-acquires-roa-launch-new-products, https://invest-gate.me/news/nawy-expands-services-with-acquisition-of-roa-launch-of-nawy-unlocked/, https://www.nawy.com/blog/113359-unlock-unlimited-profits-with-nawy-unlocked, https://play.google.com/store/apps/details?id=com.aqarmap.android, https://play.google.com/store/apps/details?id=ae.propertyfinder.propertyfinder, https://play.google.com/store/apps/details?id=com.bayut.bayuteg, https://play.google.com/store/apps/details?id=com.olxmena.horizontal, https://www.dubizzle.com.eg/en/services/maintenance/dokki/q-electric-services-services/

**Implication:** the listing proptechs have the **pre-sale** moment (millions of users). Nawy is starting to reach **post-sale owners** through Unlocked. Nobody owns the **daily life of the resident**, and dubizzle shows that demand for home services already exists in an untrusted, unstructured form.

---

## 2. What residents actually say: a review analysis

### 2.1 Quantitative snapshot

I took the newest 30–40 Google Play reviews (or all of them, if fewer) for 18 developer and community apps, 314 reviews in total, collected 2026-10-12.

| App | Reviews sampled | Share 1–2★ |
|---|---|---|
| SODIC (Milango) | 23 | **78%** |
| Mountain view (old, Milango) | 23 | **78%** |
| Smart Village (Milango) | 4 | 75% |
| Mountain View Community (Intcore) | 14 | **71%** |
| Madinet Masr | 14 | **71%** |
| Emaar Misr App | 30 | **70%** |
| PALM HILLS | 12 | **67%** |
| City Edge (Milango) | 13 | 62% |
| Morshedy (Milango) | 20 | 60% |
| Tatweer Misr | 9 | 56% |
| Wadi Degla (Milango) | 4 | 50% |
| Lyve-App | 40 | 48% |
| TMG Life | 40 | 38% |
| ORA / Al-Ahly Sabbour | 3 / 3 | 33% / 33% |
| La Vista (Lyve) | 26 | 23% |
| ALBUROUJ (Lyve) | 7 | 14% |
| MyPorto (Amer, Milango) | 23 | 13%\* |
| **All** | **314** | **51% (161 reviews)** |

\*MyPorto has **14 five-star reviews posted on a single day (11 Jun 2026)**, many in similar marketing language. That pattern suggests a coordinated launch push, so treat its low negative share with caution.

**Themes in the 161 negative reviews.** Keyword classification, one review can carry several themes:

```
Crashes / slow / "not working"        ██████████████████████  44%
Login / OTP / registration failures   █████████████▌          27%
Forced or phantom "update" loops      ██████                  12%
Support unresponsive                  █████▌                  11%
"Insecure device" / device bans       ████▌                    9%
Service request never fulfilled       ███                      6%
Gate / QR / badge failure             ██▌                      5%
Abroad / foreign number blocked       ██                       4%
Payments / utility recharge failed    █▌                       3%
```

(ESTIMATE: keyword matching undercounts gate and service failures, because many "not working" complaints are really about the gate.)

### 2.2 Verbatim complaints by theme (Google Play, Egypt)

**A. Login, OTP and registration (the #1 adoption killer)**
- SODIC, 1★, 11 Sep 2024: *"you have to get OTP over sms each time you open it from the very same mobile and after this it takes ages to load"*
- SODIC, 2★, 12 Feb 2024: *"مش راضي يقبل الرقم بيقولي expired otp"*
- City Edge, 1★, 15 Dec 2025: *"انا ك اونر مش عارف اعمل log in لان الابليكيشن مش عارف حتي يبعت كود!؟؟"*
- Mountain View Community, 1★, 24 Jun 2026: *"didn't send me the OTP either by SMS nor by WhatsApp"*
- Morshedy, 1★, 28 Oct 2025: *"A bug in the Verify Code screen … did you use Vibe Coding to generate this app?!"*
- Palm Hills, 1★, 8 Feb 2026: *"Owning my unit in PHNC since 2 years and when I tried to register, the sms I got was 'We're sorry … your Community App account has been reviewed and was not approved'"*
- Palm Hills, 1★, 19 May 2026: *"I am an owner of a unit in Badya palm hills. No after 6 months they expected my account"*
- Madinet Masr, 1★, 8 Mar 2025: *"I didn't sign up and it has been 21 days."*
- SODIC, 1★, 8 Apr 2020: *"Activation process is very bad and takes 5 days and counting"*

**B. Over-zealous security: device bans and "insecure device"**
- Mountain View Community, 2★, 6 May 2026: *"I changed my phone device and now I am blocked … 'You are now blocked due to violation of the single device role, Please visit your nearest office'"*
- Tatweer Misr, 1★, 20 Mar 2026: *"Says that I'm already on another device although this is incorrect … no option to logout of another devices"*
- Emaar Misr, 1★, 21 Dec 2024: *"It says can't run on an insecure device which is not true as I have tens of banking and secure apps"*
- TMG Life, 1★, 3 Jul 2026: *"the app keeps crashes and get me a ( security issue detected: 501 )"*
- ORA, 3★, 3 May 2026: *"(Security Alert This app can't run on this device due to security reasons.)"*

**C. Gate and QR failures (when the app *is* the key)**
- Emaar Misr, 2★, 18 Aug 2026: *"constantly crashes … as a resident, we must depend heavily on this app … people are impatient and dependent on the timing for the app to open gates"*
- Emaar Misr, 2★, 22 Jun 2024: *"IdDbadge doesn't open the gate many times. Says gate out of range. No way to enter my building if app is not working right."*
- SODIC, 1★, 18 Feb 2026: *"It is unacceptable that the barcode issue for the project gate has not been resolved for more than a month"*
- Mountain view (old), 1★, 19 Aug 2025: *"relies on strong signal and internet connection, which is not there in the compound"*
- Mountain view (old), 1★, 6 Jun 2025: *"why we have to take all our phones to the beach !! … I spent almost 2 hours to add 2 members"*
- TMG Life, 3★, 17 Feb 2026: *"The new update is making the app load very slowly and the QR doesn't load fast enough."*
- ALBUROUJ, 4★, 27 Jan 2026: *"كل ما ابعث QR CODE يوصل مش كامل"*
- SODIC, 1★, 30 Nov 2020: *"People can buy the cards used to go into the compound this rendering this feature useless."* (The guest QR gets bypassed when gate staff can be paid.)

**D. Service requests that go nowhere**
- TMG Life, 3★, 20 Oct 2025: *"booked a plumbing service months ago and i'm still waiting on it to get dispatched :D … unable to register my car through the app as requested by the city hall since the feature is missing"*
- TMG Life, 1★, 15 Jul 2025: *"للأسف مفيش إهتمام او رد بعد تقديم طلب/شكوي من خلال الأبلكيشن!"*
- Wadi Degla, 1★, 4 Dec 2025: *"not useful as no one replying and if you request something no one will respond"*
- La Vista, 3★, 9 Jul 2020: *"يتم غلق الطلب بدون التأكد من التنفيذ ام لا"* (requests get closed without confirming the work was done)
- Mountain view (old), 1★, 30 Jan 2025: *"too much phone calls … instead of 10 seconds call to facility members."*
- Lyve-App, 3★, 23 Mar 2023: *"Complaints u can't see history … No reply via attachment on posts"*

**E. Owners abroad and foreign numbers (a large Egyptian expat-owner segment)**
- TMG Life, 1★, 21 Sep 2025: *"I am not in egypt now but I am owner at madinaty"*. The developer replied that the app is "only available for users within Egypt".
- TMG Life, 4★, 28 Aug 2025: *"بسافر كتير، وللأسف مش شغال بره مصر للمتابعة.. رجاء فتحه بره مصر"*
- Tatweer Misr, 1★, 4 Jun 2025: *"does not accept login from my registered mobile number when it is from outside Egypt"*
- Mountain view (old), 2★, 11 Oct 2024: *"bug in the sign in for UAE numbers … 9 numbers … you expect to get 10"*
- Madinet Masr, 1★, 28 Jan 2025: *"I couldn't register with my international mobile number."*
- SODIC, 1★, 20 Jul 2020: *"'National ID' - SODIC have no international property owners?"*

**F. Tenants and family excluded or made hard**
- Lyve-App, 1★, 8 Mar 2021: *"only unit owners can sign up & get verified !!!! Anyone who is just a resident or renting the unit cannot siguup"*
- Mountain View Community, 3★, 25 Jul 2026: *"i need to be able to remove tenants instead of calling customer service"*
- Mountain view (old), 1★, 6 Jun 2025: adding two family members took about 2 hours.

**G. Payments and utilities (the feature that drives usage)**
- TMG Life, 5★, 20 Sep 2025: *"Great app specially for Recharge electricity and i wish to have water recharging very soon"*
- TMG Life, 3★, 4 Aug 2025: *"شحن عداد المياه والغاز"* (a request for water and gas meter recharge)
- TMG Life, 1★, 9 Aug 2026: *"… Payment completes 6. Money is taken 7. Electricity card is NOT updated"*
- TMG Life, 2★, 13 Aug 2025: *"سئ جدا بس ارحم من الوقفه في طابونه العيش اللي اسمها شركه كهرباء مدينتي"* (bad, but better than queueing at the Madinaty power office)
- Madinet Masr, 3★, 16 May 2025: the developer postponed the maintenance cheque, but *"البرنامج مصر إن الدفعة … متأخرة"* (the app keeps flagging it as overdue, so billing data is out of sync)

**H. Spam and irrelevant content**
- Emaar One (UAE, same group), 1★, 30 Sep 2026: *"in app notifications are full of promotions … I don't want adds for new stuff, I want to register my plates, pay my dues."*
- Mountain View Community, 1★, 9 Apr 2026: *"useless news, just showing app"*
- Palm Hills, 5★, 10 Apr 2026: *"Serve the purpose, but news must be updated"*

**I. Phantom updates and update fatigue**
- Lyve-App: four separate reviews (2023–2026) say the app demands an update that does not exist on Play.
- Emaar Misr, 1★, 26 Sep 2026: *"update every 2 days? that's very annoying"*
- Mountain view (old), 1★, 4 Jun 2025: *"كل شويه يخرجنا و يقولنا up date و بعدين يعلق"*

**J. Arabic and RTL quality**
- Mountain view (old): *"why is there no arabic language"* (14 Sep 2025); *"هل متوفر إضافة اللغة العربية"* (9 Jun 2025)
- Lyve-App, 4★, 29 Jun 2025: *"still needs RTL alignment for arabic text"*

**K. What people praise (keep these)**
- Lyve-App, 4★, 13 Feb 2021: *"I use this app weekly to order drinks, find out about any issues where I live and produce gate passes for visitors."* (A marketplace plus gate plus news loop works.)
- Mountain View Community, 5★, 3 Jul 2026: *"this is a must for someone in mountain view it's your remote."*
- Emaar Misr, 5★, 12 Dec 2023: *"Paying utilities and booking services are very easy and convenient."*
- Ahl Madinaty (resident-made directory, 4.6★): dozens of 5★ Arabic reviews praising a simple local directory with doctor and bus schedules. **Hyper-local information alone creates love.**

Sources: Google Play pages and reviews for the packages listed in §1.1, retrieved 2026-10-12.

### 2.3 Developer response quality
Most vendors answer with boilerplate such as TMG's *"please email info@tmglife.app"*, Milango's *"We're sorry for the inconvenience and will review the issue"*, or Emaar's *"reach us on 800-EMAAR"*, and many reviews describe support that never replies. **Support is outsourced to email and call centers, and the in-app request loop is not trusted.**

---

## 3. Feature benchmark: what developer apps include vs what is missing

| Capability | TMG Life | Emaar Misr | SODIC | Palm Hills | Mountain View | Lyve apps | Tatweer | ORA | **Gap / opportunity** |
|---|---|---|---|---|---|---|---|---|---|
| Resident ID badge / QR gate | ✓ | ✓ | ✓ | (old app ✓) | ✓ | ✓ | ✓ | ✓ | Commodity in premium compounds; absent in ordinary buildings |
| Guest invitations (QR) | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | Same as above |
| Service / maintenance requests | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | **Fulfilment and transparency are broken**: no SLA, no technician tracking, no rating loop (only Hacienda advertises rating) |
| Bills / maintenance fee payment | ✓ | ✓ | – | history only | – | fee tools (2020) | – | installments | Payment confusion and sync errors; nothing for ordinary-building shared expenses |
| Prepaid utility card recharge (NFC) | **✓** | utilities | – | – | – | – | – | – | **Highest-value daily hook**; water and gas wanted |
| Family / household members | – | – | – | ✓ | ✓ (painful) | ✓ | – | ✓ | Tenants often excluded |
| Tenant accounts | ✓ (owner/tenant choice) | ? | – | – | via call center | owners only (2021) | – | – | **Tenant-first design** |
| Car / plate registration | missing for some | – | – | – | – | Truck Entry app | – | – | ANPR integration |
| Announcements / news | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | Feels like marketing spam; no personalization |
| Local directory / offers | – | – | – | – | offers | stores, Loyalty | city guide | nearby | Ahl Madinaty shows the demand |
| Neighbor-to-neighbor chat / community | – | – | – | – | – | "private social network" (claimed) | – | – | **Absent.** WhatsApp groups fill it |
| Works abroad / foreign numbers | **✗** (Egypt only) | ? | ✗ (national ID) | ? | ✗ | ? | ✗ | ? | **Expat owners underserved** |
| Offline gate pass | – | – | – | – | – | – | – | – | Weak signal in compounds; GateFlow sells offline scanning |
| Arabic-first UX | partial | ? | partial | ? | **no Arabic** (old) | RTL bugs | ? | ? | **Arabic-first, Egyptian dialect** |
| AI (chat, auto-triage, voice) | – | – | voice feedback | – | – | – | – | – | Emaar One (UAE) has "voice service request" |
| Occupants' union (اتحاد الشاغلين) governance: votes, budgets, transparency | – | – | – | – | – | – | – | – | **Fully absent** |

Sources: Play listings in §1.1. "–" means not advertised in the listing; "?" means unknown.

---

## 4. Access control, smart gates and intercoms in Egyptian compounds

### 4.1 What exists

| Solution | Type | Egypt evidence | Integration relevance |
|---|---|---|---|
| **Developer-app QR / ID badge** (Lyve, Milango, Intcore, COMET, TownTender) | Mobile credential + guest QR | All the major apps above | Locked to the developer's vendor |
| **Lyve Key** (`com.moonshot.lyvekey`) | Access app ("number 1 community access app") | 100+ installs; last update Mar 2024 | Lyve's gate product |
| **Lyve Truck Entry** | Truck / delivery permit validation | 10+ installs, Jun 2026 | Shows contractor and truck entry is a real pain point |
| **ANPR Hub (Golden Developer)** | License-plate recognition for **Egyptian Arabic plates** (old and new), whitelist/blacklist, face capture, gate control, SDK | Case study: **Mountain View New Cairo** (with "SignMe"); Egyptian Drug Authority | SDK, so integration is possible |
| **GateFlow** | Dynamic signed QR, **offline-first scanning**, guard app, resident portal, admin dashboard, API | "Made in Egypt", Egypt & Gulf, free trial, "live in 48 hours" | Logo wall shows Palm Hills, SODIC, Emaar, Mountain View, Madinaty and others, but **these are unverified and may be decorative**. Testimonial claims (e.g. "60% reduction in gate wait times") are vendor-supplied |
| **Hikvision / Egypt Techno Trade, EXA, AI Solutions, Speed4Trading, EGY Blanco** | Barriers, turnstiles, ANPR, intercoms (installers) | Egyptian installers | Hardware layer; usually no resident app |
| Intercom brands (Comelit via Advanced Communication Systems; Fermax; Alfanar video intercom) | Building intercom | Yellow Pages EG and others | Mostly closed systems |
| Prepaid **NFC utility-card recharge** (Egyptian Electricity Holding Co. via Sahl, MyFawry, Kahraba Khales) | Utility | Official NFC recharge process | **Can be embedded through payment aggregators** (Fawry and similar) |

Sources: https://play.google.com/store/apps/details?id=com.moonshot.lyvekey, https://play.google.com/store/apps/details?id=com.moonshot.lyvetrucks, https://goldendeveloper.net/product/anpr-hub/, https://www.gateflow.site/en, https://hikvision-eg.com/smart-garage-barrier-gates-in-egypt-automated-parking-systems-by-egypt-techno-trade/, https://www.exa-eg.com/, https://aisolutions-eg.com/, https://speed4trading.com/blog/turnstile-access-gate-solutions/, https://www.egyblancosecurity.com/en/services/tech-security-solutions/access-control-security.html, https://yellowpages.com.eg/en/keyword/intercom, https://www.masrawy.com/news/news_egypt/details/2026/3/14/2957265/, https://www.masrawy.com/news/news_egypt/details/2025/1/22/2714129

### 4.2 Interpretation
- **Gate access is the "must-use" feature** that forces downloads in premium compounds: Emaar residents say they *"must depend heavily on this app"*. It is also the **riskiest feature to own**, because a failure means a resident locked outside, which produces most 1★ reviews. Hardware integration needs developer or FM contracts and on-site work.
- **Recommendation:** do **not** build gate hardware or compete for gate contracts in phase 1. Instead:
  1. In **ordinary buildings** (عمارات), offer a lightweight "digital بواب": a visitor log, guest pre-announcement to the doorman on WhatsApp, and a delivery log. No hardware.
  2. In **compounds**, integrate later with gate vendors that have APIs or SDKs (GateFlow, ANPR Hub, and Lyve/Milango if they agree), so our app *displays* the resident's pass. Our differentiators: **offline QR, multi-device, works abroad**.

---

## 5. Facility management (FM) firms: the operators behind the apps

| Player | Facts | Source |
|---|---|---|
| **Edara** (SODIC's FM arm) | "Over 3,000 professionals"; security, housekeeping, maintenance, agriculture | https://sodic.force.com/PropertyManagement |
| **EFS Facilities Services Group** | Won the exclusive contract for all FM at **Palm Hills** developments, more than 10M sqm. The article is undated (about 2019), so current status is unverified | https://gulfnews.com/business/property/efs-picks-up-a-major-fm-contract-in-egypt-1.1444594 ; https://www.linkedin.com/company/efsmisr |
| **Eden Facility Management** | Listed as a member of the Hassan Allam Group (ZoomInfo, low confidence) | https://www.zoominfo.com/p/Mohamed-Shaalan/14538684638 |
| Contrack FM (Orascom Construction), Enova, Egypro FME, SIAC FM, Apleona IFMC | Listed as key Egypt FM players | https://www.kenresearch.com/industry-reports/egypt-facility-management-market ; https://www.mordorintelligence.com/industry-reports/egypt-facility-management-market/companies |
| Savills Egypt | Manages villa compounds and communities | https://www.savills.com.eg/services/property-and-facilities-management.aspx |
| Historic structure | "only providers … able to offer a range of services are … subsidiaries of major developers, such as Emaar Hospitality, Key-Mountain View and Sodic Edara"; Falcon serves several compounds (older article) | https://invest-gate.me/features/mapping-egypts-facility-management-market/ |

**FM market size, Egypt (estimates conflict):** USD 2.25B (2024, Verified Market Research) **[unverified: the page returned 403]**; USD 2.6B (2025) growing to USD 4.63B by 2032 at 8.6% CAGR (Ken Research, confirmed); USD 7B (2025), USD 7.77B (2026) and USD 13.11B by 2031 at 11.05% CAGR (Mordor, confirmed), while Mordor's own integrated-FM figure is USD 1.63B. Sources: https://www.verifiedmarketresearch.com/product/egypt-facility-management-market/, https://www.kenresearch.com/industry-reports/egypt-facility-management-market, https://www.mordorintelligence.com/industry-reports/egypt-facility-management-market, https://www.mordorintelligence.com/industry-reports/egypt-integrated-facility-management-market

**Not found:** I found no verifiable public data on "Khidma" or "Elite" as Egyptian residential FM firms. The `com.khidmah.app` on Play is by "ViiVa Smart IT Solutions" (50+ installs) and is not clearly Egyptian. A firm called "Saudi-Egyptian FM" did not appear in any result.

**Why it matters:** FM companies are the **supply side** of in-compound services (plumber, electrician, housekeeping, pest control, landscaping). In phase 2 they are either the **partners** that fulfil marketplace orders (we take a commission or lead fee) or the **competitors** that want to keep the in-home services margin. Mountain View's new app already advertises "curated" cleaning, landscaping, maintenance and pest control, and Lyve opened to third-party sellers in 2020. **The incumbents already intend to monetize as service intermediaries.** That is exactly the client's phase-2 model, and it confirms the model works.

---

## 6. The structural opening: developer-vs-resident conflict and governance

- **Maintenance-deposit disputes are public and growing.** Occupants' unions have sued developers to return maintenance deposits and their returns, for example a court order reported for the "Diyar Park" union in New Cairo to recover EGP 14 million (ruling of 17 Feb 2026 against the developer ARCO: EGP 13.1M principal plus returns and interest; reported 8 Apr 2026) (https://www.altreeq.com/533939). Owners report being billed extra maintenance "دون إثبات للاحتياج" (without proof of need), and a TV host claims deposits reach **up to 10% of unit price** (https://www.vetogate.com/5687653; https://www.egypttelegraph.com/article/279824/).
- **Courts have also pushed in the other direction:** an administrative-court ruling voided an occupants'-union election and directed residents to form a management company to run maintenance and protect the deposit (https://www.parlmany.com/News/2/500935/ ; https://www.soutalomma.com/Article/1031700/). The date is unclear from the search results.
- **29 Sep 2026:** Tarek Shokry, head of the Real Estate Development Chamber, called for **separating management and maintenance from the developer**, independent companies for security, landscaping, parking and elevators, **separate bank accounts audited independently**, **published cost data** for fair fees, graduated collection steps for late payers, and activation of occupants'-union rules. He mentioned no digital platform (https://www.youlyou.com/63331 ; https://banker.news/154253).
- **3 Aug 2026 (added during verification):** Housing Minister Randa El-Menshawy reviewed draft **Building Law amendments**. They cover how occupants' unions are formed, registered and governed (boards, general-assembly powers), the developer's management and maintenance duties during the statutory period, and what happens when no union is formed. The minister asked for final drafts to be prepared quickly. A regulatory change to union governance is therefore under way, and a union-governance toolkit may soon be needed for compliance (https://almalnews.com/2127746/).
- **Residents organize outside the official apps**, through Facebook pages such as "Madinaty Residence Complaints" (https://www.facebook.com/MadinatyResComp/) and resident-made apps such as Ahl Madinaty. GAIT's 2026 blog lists "several overlapping WhatsApp groups", paper visitor logbooks and lost requests as the norm (https://gaitco.com/blog/compound-management-system-resident-app-egypt).

**Implication for the independent app:** a developer's app can never credibly be the residents' **transparency and governance tool** (budgets, votes, deposit tracking, union elections, contractor bids), because the developer is the counterparty. An independent, resident-owned or neutral platform can be. This positioning is **policy-tailwind aligned**: the industry chamber is itself asking for transparency and separation. **ESTIMATE:** as management separates from developers over 2026–2028, many compounds will need **new, neutral management software**, and the white-label vendors that sell *to developers* are poorly positioned for that buyer.

---

## 7. Market sizing relevant to this angle

| Indicator | Value | Source |
|---|---|---|
| Compounds listed on Nawy, New Cairo | **368** | https://www.nawy.com/area |
| Compounds listed on Nawy, Sheikh Zayed / New Zayed | **112 / 69** | https://www.nawy.com/area/el-sheikh-zayed ; https://www.nawy.com/area |
| Madinaty planned capacity | ~120,000 units; 600–700K residents (listing sites; the gov blog says 600K+) | https://www.bayut.eg/en/property/details-503870584.html ; https://blogs.realestate.gov.eg/?p=75124 |
| Lyve footprint (2020) | 50+ compounds, ~40K units | egyptinnovate (above) |
| Milango contracted units (2022) | >100K units | MENAbytes (above) |
| Housing units completed in Egypt, FY2024/25 | **~212K** (EGP 245.3B investment; private sector 107.2K) vs 158.9K the year before | https://almalnews.com/2130098/ ; https://www.youm7.com/story/2026/8/23/%D8%A7%D9%84%D8%A5%D8%AD%D8%B5%D8%A7%D8%A1-107-2-%D8%A3%D9%84%D9%81-%D9%88%D8%AD%D8%AF%D8%A9-%D9%86%D9%81%D8%B0%D9%87%D8%A7-%D8%A7%D9%84%D9%82%D8%B7%D8%A7%D8%B9-%D8%A7%D9%84%D8%AE%D8%A7%D8%B5-%D8%B9%D8%A7%D9%85-2024/7522235 |
| Largest developer app installs | TMG Life 50K+; everyone else ≤10K+ | Google Play |
| International benchmark (MyGate, India) | 27K+ communities, ~5.7M households (Inc42 says "nearly 5M homes"); FY25 operating revenue ₹173.5 Cr (+80% from ₹96.2 Cr), net loss ₹15.4 Cr; FY26 ₹232 Cr **[unverified: no reported FY26 actual found; the CEO guided 25–30% growth]**; **free or low-cost for communities, monetized via ads (about 65–70% of revenue), with SaaS and smart-home hardware making up the remaining 30–35%**. Payments volume: ₹9,000 Cr invoices/yr **[unverified: the only sourced figure is ">₹3,000 Cr maintenance payments/yr" from 2024]** | https://inc42.com/buzz/mygate-trims-fy25-loss-by-61-to-%E2%82%B915-4-cr/ ; https://yourstory.com/2025/02/journey-mygate-founder-abhishek-kumar-home-security-app ; https://inc42.com/buzz/mygate-secures-%e2%82%b9225-cr-to-fuel-footprint-expansion/ |

**ESTIMATE: developer-app penetration.** Add up the visible installs of all developer and community apps in §1.1 at their band floors and the total is about **200K–250K installs**. That counts the 50K TMG Life band, about ten 10K+ bands, about six 5K+ bands, plus smaller ones (floor-based, so the true number may be up to about 2× higher). Installs are not active users. Reviews show many accounts stuck at registration and devices blocked, so active resident users across *all* Egyptian developer apps are plausibly **below 300K people**. For comparison, MyGate has 5.7M households in India. **The premium-compound digital market is fragmented and shallow, with no consumer brand.** Mass-market buildings are a greenfield. (Reasoning: install bands from Play; the active-user discount comes from review evidence of failed onboarding. This is not a sourced figure.)

---

## 8. Partner vs compete: strategic analysis for an independent app

### 8.1 Segment-by-segment stance

| Segment | Who's there today | Our stance | Why |
|---|---|---|---|
| **A. Premium developer compounds** (Madinaty, SODIC, Palm Hills, Emaar, MV, etc.) | Developer app (gate + FM) with mandatory use, built by Lyve/Milango/Intcore | **Coexist and complement** (resident layer). Do not try to replace the gate app. | The gate is contractual and hardware-bound. Their weak spots are community, personalization, the WhatsApp channel, fulfilment transparency and the marketplace. Win residents through **WhatsApp groups and building/street-level micro-communities** inside the compound |
| **B. Mid-tier and self-managed compounds** (Hadayek October / Hadayek al-Ahram, Obour, Shorouk, 10th of Ramadan, state "Compound 700 feddan", Sakan Masr/Dar Masr) | Almost nobody: WhatsApp, paper, sometimes a tiny custom app (Compoundy 100+) | **Compete and own** | No incumbent; residents or unions run operations; budget-sensitive → **free** wins |
| **C. Ordinary buildings (عمارات)** in Cairo, Giza, Alexandria and Delta cities | Amarati/Imarti/Saknna-type apps (see other research files), WhatsApp groups | **Compete and own** (core market) | The developer-app vendors don't sell here at all |
| **D. Occupants' unions (اتحاد الشاغلين) in any segment** | Nothing | **Own** with a governance and transparency toolkit | Policy tailwind (Chamber, Sept 2026); developer apps can't credibly serve them |
| **E. FM companies** (EFS, Edara, Contrack FM, Savills, small local FMs) | Use the developer's app or paper | **Partner**: free ops console and technician app in exchange for routing their residents onto our platform; later, revenue share on marketplace jobs | FMs are the supply side for phase-2 services |
| **F. Gate and intercom vendors** (GateFlow, ANPR Hub, Hikvision installers) | Hardware plus their own dashboards | **Partner through API** | Lets us show passes and visitor alerts without owning hardware risk |
| **G. White-label vendors** (Lyve, Milango, Intcore) | B2B to developers | **Watch; possible partner or acquirer later** | They are small, unfunded since 2018/2022, and could become distribution partners (embed our marketplace or bot) or targets |
| **H. Proptech portals** (Nawy, Aqarmap, PF, Bayut, dubizzle) | Pre-sale; Nawy Unlocked for investor owners | **Partner** (co-marketing at hand-over, rental-management referrals) | Their users become residents. Nawy already partners with SODIC and Marakez for post-sale owners |

### 8.2 How to win residents *inside* developer compounds without the developer's permission (zero-budget)
1. **WhatsApp-first entry.** Compound life already runs on WhatsApp groups (GAIT). A bot that joins the building or cluster group, summarizes, logs requests, reminds people and answers "who's a good plumber?" delivers value with no download and no developer approval. (The bot's feasibility is covered in 10-whatsapp-bot.md.)
2. **Solve what the official app breaks:** a **"my compound passes" wallet** that stores screenshots or links of developer QR codes for family and guests (ESTIMATE: needs care with each vendor's terms), **reminders for fee due dates**, and **outage alerts** gathered from residents.
3. **Hyper-local directory and offers** (the Ahl Madinaty pattern, 10K+ installs and 4.6★ for a simple directory): doctors' schedules, buses, pharmacies, and trusted فني/سباك rated *by neighbors*.
4. **Expat-owner mode:** works with any international number and from abroad, with a remote view of the unit, rent and tenant handling. This directly addresses the TMG, Tatweer, MV and Madinet Masr complaints.
5. **Tenant-first accounts:** tenants are excluded or second-class in developer apps (Lyve 2021, MV 2026 reviews). Tenants are numerous and churn often, and every move-in is a growth event.

### 8.3 How to make developers and FMs *want* us (later)
- **Offer the resident layer free and white-label it if needed:** "Keep your gate vendor; we add AI triage, a WhatsApp channel, Arabic voice requests and a neighbor community." This turns competitors' clients into our distribution.
- **Fulfilment marketplace for FMs:** FMs can't staff every niche service. We bring vetted vendors and share the margin, the same move Lyve announced in 2020 and Mountain View in 2025.
- **Data-backed collection help:** fee collection is the developers' and the Chamber's #1 pain. Polite AI reminders, installment plans and transparent cost dashboards help collection without the developer acting as the "bad guy".

### 8.4 Risks
- **Mandatory developer apps** already occupy the home-screen slot in premium compounds, so a second app faces friction. Mitigation: WhatsApp-first, then a PWA, then the native app.
- Developers may **block third-party access** to gate systems or forbid vendor marketing inside compounds. Mitigation: target segments B, C and D first.
- **Incumbents could copy features**, but their record (crashes, OTP failures, 2★ averages, no funding since 2018/2022) suggests slow execution.
- **Security vs usability:** incumbents over-correct with root detection, single-device bans and OTP on every launch. We need strong security that does not lock people out (passkeys or biometrics, multi-device with approval, WhatsApp OTP fallback, and an offline cached pass with short validity).

---

## 9. Feature requirements derived from this research ("fix-the-incumbents" spec)

| # | Requirement | Evidence driving it |
|---|---|---|
| R1 | **Login that never fails:** WhatsApp OTP plus SMS fallback plus email magic link; remember the device; passkeys/biometrics; **no OTP on every open** | SODIC, City Edge, MV, Morshedy, Madinet Masr reviews |
| R2 | **Any country code, works abroad** (no geo-block) | TMG, Tatweer, MV, Madinet Masr, SODIC |
| R3 | **Multi-device with self-service device management** (log out other devices) | MV single-device ban, Tatweer |
| R4 | **No false "insecure device" blocks.** Risk-based checks only on payments | Emaar Misr, TMG 501, ORA |
| R5 | **Instant onboarding** (approval in minutes; invite links from neighbors or admin; tenants allowed) | Palm Hills approvals of 6 months and outright rejections; Madinet Masr 21 days; Lyve owners-only |
| R6 | **Offline QR passes** (signed, time-boxed) and **fast QR render (<1 s)** | MV "no signal", TMG slow QR, GateFlow offline-first |
| R7 | **Service-request lifecycle with SLA, technician ETA, photo proof and resident confirmation before close, plus a rating** | TMG plumbing "months", La Vista closing without confirmation, Wadi Degla "no one replying" |
| R8 | **Request history and threaded replies with attachments** | Lyve 2023 review |
| R9 | **Utility hub:** NFC electricity/water/gas card recharge through an aggregator; maintenance-fee payment with reconciliation | TMG praise and failures; Madinet Masr cheque desync |
| R10 | **Car plate registration** and **truck/contractor permits** | TMG missing plates; Lyve Truck Entry; Emaar One plates |
| R11 | **Household and tenant management in-app** (add or remove in seconds) | MV 2 hours for 2 members; MV remove tenant via call center |
| R12 | **Personalized, relevance-ranked notifications; promotions opt-in and separated** | Emaar One "full of promotions"; MV "useless news" |
| R13 | **Arabic-first (Egyptian dialect), perfect RTL** | MV "no Arabic"; Lyve RTL |
| R14 | **Silent updates; never block on phantom versions**; staged rollouts | Lyve phantom updates; Emaar "every 2 days" |
| R15 | **Hyper-local directory**: doctors, buses, shops, trusted craftsmen | Ahl Madinaty 4.6★ |
| R16 | **Governance toolkit:** budgets, deposit tracker, votes, union elections, contractor bids, audited statements | Chamber head Sept 2026; deposit lawsuits |
| R17 | **Human support SLA inside the app** (an AI first line with escalation; no "email us") | Boilerplate replies across vendors |

---

## 10. Ideas to borrow (adapted from what incumbents do well)

- **TMG Life NFC recharge:** the single most-praised feature. Copy it and extend it to water and gas, which users explicitly ask for.
- **Lyve Loyalty:** a resident badge doubles as a **discount card** at local shops. This is a simple monetizable merchant network for phase 2.
- **Lyve Truck Entry / Tatweer guest management:** contractor, delivery and truck permits are a real daily need, especially during the fit-out period after hand-over.
- **Mountain View "curated services"**: cleaning, landscaping, pest control and maintenance, which validates the in-app service marketplace.
- **Emaar One "voice service request"** (UAE): voice-note requests fit Egyptian users well and pair with AI transcription and triage.
- **SODIC feedback by "text, voice, images, or even direct calls"**: multimodal intake.
- **Hacienda separate Staff app**: a dedicated technician/guard app is necessary for closing the loop.
- **MyGate (India)**: free or near-free for communities, monetized through ads, payments, SaaS and smart locks at multi-million-household scale. This is the closest analogue to the client's "dominate, then monetize" plan.

---

## 11. Gaps and caveats in this research
- **Apple App Store** pages returned HTTP 429 (rate limited), so iOS ratings come only from search snippets.
- **Facebook, X and Reddit**: searches surfaced the "Madinaty Residence Complaints" page but no indexed Reddit threads on Egyptian compound apps. Social-media complaint mining is thin in this file. Play reviews are the primary voice-of-customer source.
- Install counts are Google Play **bands**, not active users. The negative-review share is a recent-review sample, not the all-time rating.
- I could not verify the GateFlow client logos, the current EFS–Palm Hills contract status, "Khidma" or "Elite" as Egyptian residential FMs, ACUD resident apps, or any 2023–2026 funding for Lyve or Milango.
- Theme percentages come from keyword classification (ESTIMATE-grade). I quote reviews exactly but did not verify the reviewers' identities.

---

## 12. Bottom line for the founder
The large developers have shown that **residents will install a compound app when it controls something essential** (the gate, utility top-ups, fees). They have also shown that **they can't build a product people love**: about half of recent reviews are 1–2★, there is no community layer, AI is absent, and the apps are geo-blocked, owner-only and developer-centric. The B2B vendors behind them are small and stagnant.

The winning independent play is:
1. **Own the segments developers ignore:** ordinary buildings, mid-tier and self-managed compounds, and occupants' unions.
2. **Enter premium compounds through residents** (WhatsApp, tenants, expat owners, a hyper-local directory) rather than through developers.
3. **Partner with FM firms, gate vendors and proptech portals** for supply and distribution.
4. **Monetize as the trusted intermediary** for home services, utilities and local commerce. The incumbents already aim at this model but are too weak to execute it.

---

## Verification log

Adversarial re-check done 2026-10-12. Google Play values were re-fetched live with `gl=EG`. Every other claim was checked against fresh web searches or fetches.

| # | Claim | Verdict | Evidence URL |
|---|---|---|---|
| 1 | TMG Life: 50K+ installs, 4.8★ (1.16K reviews), updated 11 Aug 2026, NFC utility-card charging | confirmed | https://play.google.com/store/apps/details?id=com.tmglife.app |
| 2 | Emaar Misr App: 10K+, 3.9★ (261) | confirmed | https://play.google.com/store/apps/details?id=com.kijamii.emaarcommunities |
| 3 | Mountain View Community: 10K+, 3.7★, updated 25 Aug 2026, publisher Intcore, "Lighthouse"; the old Milango app was last updated 8 Dec 2025 (3.0★) | confirmed | https://play.google.com/store/apps/details?id=com.congora.mountainview ; https://play.google.com/store/apps/details?id=app.milango.mountainview |
| 4 | SODIC 5K+/3.3★; Madinet Masr 5K+/2.4★; Lyve-App 10K+/4.4★; Ahl Madinaty 10K+/4.6★ (199) | confirmed | https://play.google.com/store/apps/details?id=com.kijamii.sodiccommapp ; https://play.google.com/store/apps/details?id=com.madinetmasr.community ; https://play.google.com/store/apps/details?id=com.moonshot.icommunity ; https://play.google.com/store/apps/details?id=com.ahl.madenty |
| 5 | dubizzle EG 10M+ / 4.7★ (697K); Nawy 1M+ / 4.1★ (2.64K); Aqarmap 500K+ / 4.7★; Bayut EG 1M+ / 4.6★ (2.89K) | confirmed | https://play.google.com/store/apps/details?id=com.olxmena.horizontal ; https://play.google.com/store/apps/details?id=com.cooingestate.cooing_app ; https://play.google.com/store/apps/details?id=com.aqarmap.android ; https://play.google.com/store/apps/details?id=com.bayut.bayuteg |
| 6 | iCommunity (Lyve) raised a US$600K Series A from Algebra Ventures, Oct 2018 | confirmed | https://weetracker.com/2018/10/02/icommunity-secures-funding-algebra-ventures/ |
| 7 | Lyve in 2020: 50+ compounds, ~40K units, app opened to third-party sellers (press release dated 26 Jan 2020) | confirmed | https://egyptinnovate.com/en/news/icommunity-is-now-lyve-a-new-facelift-simplifying-life-in-compounds |
| 8 | Milango acquired Circle (500-backed) in Feb 2022, taking its contracted base to >100K units | confirmed | https://www.wamda.com/2022/02/milango-acquires-proptech-startup-circle |
| 9 | Nawy acquired ROA in Jan 2025 and launched Nawy Unlocked (covers up to 50% of finishing cost) | confirmed | https://www.wamda.com/2025/01/nawy-acquires-roa-launch-new-products |
| 10 | Tracxn: Egypt startup funding 2026 down 62.76% vs 2025 | **corrected**: down 47.6% for Jan–Sep 2026 YoY ($188M vs $358M) | https://tracxn.com/d/geographies/egypt/__aRcH8lYOC74CSa9mr7vgyEJG0aUdj3E52SUBjjv4gy0 |
| 11 | 29 Sep 2026: Chamber head Tarek Shokry called for separating maintenance/management from developers, separate audited accounts and published costs; no digital platform mentioned | confirmed | https://www.youlyou.com/63331 ; https://banker.news/154253 |
| 12 | Diyar Park union won ~EGP 14M deposit recovery | confirmed (ruling of 17 Feb 2026) | https://www.altreeq.com/533939 |
| 13 | Egypt completed ~212K housing units in FY2024/25 (EGP 245.3B; private sector 107.2K) vs 158.9K the year before | confirmed | https://almalnews.com/2130098/ |
| 14 | Madinaty planned for ~120K units and ~600K residents | confirmed (design capacity, not a census) | https://aqarmap.com.eg/ar/advice/madinty-city/ |
| 15 | MyGate: FY25 revenue ₹173.5 Cr (+80%), ads the largest revenue share, 27K+ communities / 5.7M homes | confirmed (ads are 65–70%; Inc42 says "nearly 5M homes") | https://inc42.com/buzz/mygate-trims-fy25-loss-by-61-to-%E2%82%B915-4-cr/ |
| 16 | MyGate FY26 ₹232 Cr; ₹9,000 Cr invoices/yr | **unverified** (FY26 is CEO guidance only; the only sourced payments figure is >₹3,000 Cr in 2024) | https://inc42.com/buzz/mygate-trims-fy25-loss-by-61-to-%E2%82%B915-4-cr/ ; https://cwv.yourstory.com/2024/03/mygate-revenue-growth-via-business-maturity |
| 17 | Egypt FM market: Ken USD 2.6B (2025) to 4.63B (2032) at 8.6%; Mordor USD 7B (2025) | confirmed; Verified Market Research USD 2.25B **unverified** (403) | https://www.kenresearch.com/industry-reports/egypt-facility-management-market ; https://www.mordorintelligence.com/industry-reports/egypt-facility-management-market |
| 18 | (New) Housing Ministry is drafting Building Law amendments on occupants'-union governance (3 Aug 2026) | added | https://almalnews.com/2127746/ |

**Net assessment:** the Play-store numbers and the vendor and funding history in this file hold up. One statistic was wrong (Tracxn), two MyGate figures could not be sourced, and the governance tailwind is stronger than the original draft said, because a Building Law amendment is now being drafted.
