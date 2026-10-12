# 01 — Egyptian Building, Owners'-Association and Compound Management Apps: Full Competitor Landscape

> Research angle: direct competitors in Egypt (apps and websites for managing residential buildings, اتحاد الشاغلين / اتحاد الملاك, compounds, maintenance-fee collection, resident communication and gate/visitor management).
> Research date: 2026-10-12. Google Play data was pulled live on 2026-10-12 with `gl=EG` (Egypt storefront). Download figures are Google Play's public buckets (for example "10K+" means 10,000–49,999 installs). Reviews were pulled from Google Play's public review feed (Arabic and English). They are quoted verbatim with star rating and date.
> Convention: **ESTIMATE** marks my own inference, with the reasoning given. "Not found" means I searched and could not verify it.

---

## 0. Executive summary (TL;DR)

1. **The Egyptian market splits into two worlds that don't talk to each other:**
   - **(A) Gated compounds (B2B2C).** Big developers (TMG, Emaar Misr, SODIC, Palm Hills, Mountain View, Hyde Park, La Vista, Madinet Masr, Tatweer Misr, ORA, City Edge and others) pay white-label vendors, mainly **Lyve (ex-iCommunity)** and **Milango**, for a branded resident app: gate QR passes, service requests, announcements and bill payment. These apps reach thousands of users only because residents are *forced* to use them to get through the gate. Their reviews are dominated by **OTP/login failures, crashes after updates, "single-device" lockouts, slow approvals and unanswered service requests**.
   - **(B) Ordinary apartment buildings (عمارات), where most Egyptians live.** They are served by a **swarm of tiny, mostly solo-developer apps**, almost all named some variant of "عمارتي": Amarati, Imarti, Omaraty, Ammarty, Amarti, صندوق العمارة, ملاك المرافق, MulakHub, اتحاد الملاك, العمارة and others. **None has more than 1K+ downloads on Google Play.** Most are bookkeeping tools for the building treasurer (who paid, who didn't, expenses, receipts). Web SaaS players such as **Saknna** (claims 500+ buildings) and **ELOMARA** sit beside them.
2. **Nobody owns segment B.** The three apps the founder named are all very small:
   - **Amarati (com.amarati.app):** 1K+ downloads, 4.7★, 43 reviews. Built by building-committee heads in **Palestine**, not Egypt.
   - **Imarti (com.craftfuture.imarti):** 100+ downloads, no rating yet. Developer "Craft Future", whose privacy policy sits on a **Saudi `.com.sa` domain**.
   - **Saknna:** a web/PWA SaaS priced at 450–7,500 EGP/month, with no Play Store app found.
   The category is wide open in Egypt.
3. **Every building-level competitor builds a "treasurer tool".** None builds a **"resident network"**. Common gaps:
   - No viral loop; the manager has to type everyone in.
   - No real in-app payment rails, only receipt-photo upload and manual approval.
   - No WhatsApp-native experience; at most they share a summary image to the group.
   - Weak or no AI. Exceptions: Saknna's Arabic assistant and صندوق العمارة's Egyptian-Arabic voice entry "عم أمين".
   - No marketplace beyond a few listings (Imarti and ELOMARA have embryonic "trusted providers").
   - No support for the doorman (البواب), the most important human in the Egyptian building.
4. **Monetization proof exists, but only in compounds.**
   - Lyve put a services/stores marketplace inside compounds early (Raya Trade appliances plus consumer finance in 2021) and a QR "Lyve Benefits" discount scheme. That is phase 2 of the founder's plan.
   - Abroad, **MyGate (India)** shows the end state: 27,000+ communities and ~5.7M homes (June 2026) [corrected], ~₹173.5 crore FY25 operating revenue, **~65–70% of income from advertising**.
5. **The white space:** a **free, resident-first, WhatsApp-native, AI-first network for ordinary Egyptian عمارات**. The bot joins the existing building WhatsApp group, and the app gives everyone an account. It is built around the doorman, the treasurer and the resident together, with real payment rails (InstaPay, wallets, Fawry) and the services marketplace layered on later. No Egyptian player combines these. Detail in §8.

---

## 1. Market context: why this category exists in Egypt

| Fact | Detail | Source |
|---|---|---|
| Legal obligation | Buildings/complexes with **≥5 units** must form an occupants' union (اتحاد الشاغلين) under the Unified Building Law 119/2008 and its executive regulation 144/2009. Members include owners **and tenants**. | Unitify Egypt page summarising the law: https://unitify.com/egypt ; Al-Watan: https://www.elwatannews.com/news/details/5864320 |
| Active 2026 enforcement push | **June 9, 2026**: East and West Nasr City districts (Cairo) launched a campaign urging buildings to register a union at district tech centres. They called it a "legal obligation", warned of field inspections and legal action against non-compliant buildings, and listed **8 required documents** (assembly invitation 15 days ahead, notarised minutes, member list with national IDs, and others). | https://www.elwatannews.com/news/details/8298565 |
| Pending amendments | Experts and the Ministry of Housing have discussed amendments (for example, developer chairs the union for the first 3 years; general assembly at 40% occupancy). I could not confirm parliamentary passage in 2026. | https://www.dostor.org/5657044 ; https://gate.ahram.org.eg/daily/News/203786/5/812487/ |
| Non-payment fines (draft) | Draft law text discussed: mandatory monthly maintenance payment, with a **fine of EGP 10–100/month** for non-payers. | Invest-Gate, 1 Jun 2021: https://invest-gate.me/features/management-dilemma-occupants-union-or-developer-management/ |
| Union governance | 3-year board term. 25% of owners can trigger withdrawal of confidence. | same Invest-Gate article |
| Compound management companies | Integrated compounds must set up a management-and-maintenance company once public electricity is connected and 60% of units are occupied (art. 158, as summarised by Unitify). | https://unitify.com/egypt |
| Developer vs union tension | 82% of an Invest-Gate survey preferred developer management. The article describes disputes over maintenance revenues. | Invest-Gate 2021 (above) |
| Building stock | CAPMAS 2017 census: **~16.185 million buildings**, **91.2% residential**. | Amwal Al Ghad summarising CAPMAS: https://amwalalghad.com/ihtg ; CAPMAS: https://www.capmas.gov.eg/Admin/Pages%20Files/2017104122258.pdf |
| New supply | ~212,000 housing units built in new cities in FY2024/25, about half by private developers. | Ahram Online: https://english.ahram.org.eg/News/574749.aspx |
| Long-standing pain | A 2020 call from former parliament speaker Ali Abdel Aal to oblige unions to contract specialised management/maintenance firms. Akhbar El-Yom ran an April 2026 op-ed titled "مأساة اتحادات الشاغلين" (the article page returned 403 to my fetcher; title verified from search results only). | https://www.youm7.com/story/2020/3/9/…/4664251 ; https://akhbarelyom.com/news/newdetails/4808370/1/ |

**Implication for the product.** Because unions are legally mandatory, under-formed in practice, and now being pushed by district authorities in 2026, a product that **helps a building form and run its union legally** has a timely hook. It can generate assembly invitations, minutes, member lists and the 8-document pack. That hook is free to market: "سجّل اتحاد الشاغلين بتاعك في 10 دقايق". Note the legal limit: Unitify states that Egyptian law does **not** provide for electronic voting at general assemblies. In-app votes can prepare and archive decisions, but cannot claim legal sufficiency by themselves (https://unitify.com/egypt).

---

## 2. Deep dive: the three reference apps named by the founder

### 2.1 Amarati — "عمارتي" (Google Play `com.amarati.app`)

| Field | Data (fetched 2026-10-12) |
|---|---|
| Store page | https://play.google.com/store/apps/details?id=com.amarati.app |
| Developer | **Amarati Technologies** (individual developer, listed address Palestine, +970 phone); contact e-mail issa_kassabry@hotmail.com; site https://amarati-site.web.app/ (Firebase hosting, title only) |
| Origin | The listing says: "It was built by the heads of actual building committees in **Palestine**… a solution we built for ourselves". It is **not an Egyptian company**. |
| Downloads | **1K+** |
| Rating / reviews | **4.7★ / 43 reviews** |
| Last update | **Sep 30, 2026** (active) |
| Price | "Free to get started. No hidden fees." No pricing published. Reviewers ask "هل هو مجاني؟" (is it free?), so monetization is unclear. |
| Funding / founders | Not found (no company website content, no press). |
| Language | **Arabic only, RTL, Cairo font**: "Not a single English word. Large buttons… suitable for all ages." |

**Features (from listing):**
- Shared ledger: each resident sees their own balance, and admins see everything.
- **Automatic monthly bills** for occupied apartments on a set date.
- **Meter readings via camera**: photograph a water/gas meter and the app computes consumption per apartment. This is a real AI/OCR hook.
- Automatic reminders, with Arabic notifications and an audible alert.
- "Resident claims": a resident reports a cash payment and the admin confirms or rejects it.
- **One-click WhatsApp share** of a monthly building summary *as an image* to the group.
- 5-minute onboarding: create the building in 2 steps, then share an invite link on WhatsApp.
- "We don't touch your money": the app records payments only. Firebase daily backups. Data deletion available.

**Verbatim user reviews (Google Play):**
- 2★, 2026-09-26: «هو مبدئيا تطبيق جيد ينقصه الاتي : ـ تخصيص الدفع لبعض الخدمات اي ان بعض شاغلي الوحدات يدفعون في بعض الخدمات والاخرى لا . ـ اضافة تحصيل الايجار من الوحدات المؤجرة . ـ اضافه امكانية طلب دفع فواتير او خدمات استثنائية لمره واحده او عده مرات. ـ وضع امكانية اخفاء بعض الامكانيات عن السكان لمنع الإحراج…»
- 5★, 2026-10-01: «هيبقي مجاني ولا برسوم وياريت ميبقاش رسوم غاليه علشان في طبيق غالي اوي»
- 5★, 2026-07-04: «تطبيق طال انتظارة الصراحة .. جدا سهل وشامل كلشي بحتاجه كمدير لجنة العمارة … بس هل رح يتوفر منه عال App store كمان ؟»

**Strengths:** the cleanest "for-elderly" Arabic UX positioning; camera meter reading; WhatsApp invite link onboarding; active development.
**Weaknesses:**
- Not Egyptian: dialect, payment methods and legal framework (اتحاد الشاغلين) are not Egypt-specific.
- Android only, according to reviewers.
- No online payment, no marketplace, no gate/doorman module, no AI assistant beyond meter OCR.
- Missing: partial/optional service charges, one-off levies, rent collection, privacy controls between residents (per the reviews).
- Tiny traction.

### 2.2 Imarti — "عمارتي - إدارة اتحاد الملّاك" (Google Play `com.craftfuture.imarti`)

| Field | Data (fetched 2026-10-12) |
|---|---|
| Store page | https://play.google.com/store/apps/details?id=com.craftfuture.imarti |
| Developer | **Craft Future**; e-mail craftsolutionsapp@gmail.com; privacy policy hosted at `admin.craftsolutions.com.sa`. **ESTIMATE:** a Saudi-based software house (the `.com.sa` domain). Web searches for the company returned nothing. |
| Downloads | **100+** |
| Rating / reviews | No public rating yet (too few ratings) |
| Last update | **Sep 5, 2026** |
| Price | Not stated on the listing |
| Funding / founders | Not found |
| Language | Arabic **and** English, switchable in-app |

**Features (from listing):**
- Subscriptions and debts: monthly dues per apartment, debt statement with monthly average, receipts.
- Expenses by category (maintenance, electricity, cleaning…), real-time balance, **PDF financial reports**.
- **Emergency funds / fundraising campaigns** with contributor counts.
- **Voting** on decisions, with transparent results and an archive of approved decisions.
- Complaints and suggestions channel.
- Roles: Building Manager, Treasurer, Member.
- Deep-linked instant notifications.
- Governorate/city selection at signup.
- **"Offers and trusted service providers with ratings and a countdown timer."** This is an embryonic marketplace and the closest thing among the three to the founder's phase-2 idea.
- Financial history kept for previous members (handles residents moving out).

**Strengths:** the most complete governance set (voting, emergency funds, roles); bilingual; the marketplace seed is already in.
**Weaknesses:** almost no traction; Saudi-oriented terminology ("اتحاد الملّاك" is the Saudi term, while in Egypt the legal term is "اتحاد الشاغلين"); no payments; no WhatsApp integration; no AI.

### 2.3 Saknna — "سَكَنة" (https://saknna.com)

| Field | Data (fetched 2026-10-12) |
|---|---|
| Product | **Web-based SaaS / installable PWA** for owners' associations and compounds. "No app store download" is required. I found no Play Store listing under that name. |
| Target | Owners' associations, buildings of various sizes, compounds, multi-building management companies |
| Countries | Egypt and Saudi Arabia, plus UAE, Kuwait, Qatar, Oman, Bahrain, Jordan (prices in local currency) |
| Contact | info@saknna.com, **+20 122 653 9203** (WhatsApp, an Egyptian number) |
| Traction claim | "أكثر من 500+ مبنى" (500+ buildings). Self-reported and unverified. No named customers or testimonials. |
| Founders / funding | Not disclosed; not found in search |

**Pricing (Egypt, EGP/month; annual = 2 months free; 14-day free trial; promo SAKN30 = 30% off 3 months):**

| Plan | EGP / month | Units | Notes |
|---|---|---|---|
| البيت (Bayt) | **450** | up to 5 | finance + maintenance |
| الدار (Dar) | **900** | up to 10 | "most popular" |
| القصر (Qasr) | **2,200** | up to 20 | all features, phone support |
| المجمع (Mujamma) | **7,500** | unlimited, multi-building | custom |

That works out to roughly **90–110 EGP per unit per month** (Saknna's own figure). For a typical Egyptian 10–20-flat building, whose monthly maintenance fee per flat is often of the same order, this is **very expensive**. **ESTIMATE:** this pricing structurally excludes the mass market of ordinary عمارات, and that is the gap a free product can take.

**Features:**
- Invoices, payments, income/expense statements.
- Maintenance tickets with priority, status and photos.
- Owners and tenants in one file, including multi-owner units.
- Automatic payment reminders.
- **Arabic AI assistant** ("اسأل عن مبناك بالعربي") that summarises building status and answers questions.
- Excel/CSV import.
- Payments: Egypt = InstaPay, Vodafone Cash, bank transfer (handled manually after signup).

**Strengths:** the only one of the three with an AI assistant and a sales-led B2B model; Egyptian phone/WhatsApp support; multi-country.
**Weaknesses:** paid-only after trial and priced per building; no native app; residents are passive (no resident network); no marketplace; WhatsApp only as a support channel, which it frames as the chaos it replaces.

---

## 3. Other building-level (عمارة) apps found on Google Play Egypt

All fetched 2026-10-12 from `play.google.com/store/apps/details?id=<package>&gl=EG`.

| # | App (package) | Developer | Downloads | Rating (reviews) | Last update | Model / price | Key features & notable points |
|---|---|---|---|---|---|---|---|
| 1 | **عمارتي – ادارة اتحاد الملاك** (`com.omaraty.app`) | Youssef Mohamed Ramzy / **Techiato** (techiato.org) | 100+ | 5.0 (7) | Sep 30, 2026 | "Free to use" | v2.0: 3-tab redesign; **residents without phones** (manager keeps their data and cash payments, and they take over the account later); building income from shop/roof/garage rent; recurring and one-off fees; receipt-photo proof approved in one tap; announcements and polls; Google sign-in. Egyptian dialect in reviews. |
| 2 | **عمارتي – إدارة إتحاد الملاك** (`com.ammarty.ammarty`) | HopenWorks LTD | 1K+ | 4.8 (9) | Oct 5, 2026 | **Free 1 month, then subscription** (per a 3★ review, 2026-10-05) | Manager records payments, e-receipts shared via WhatsApp; residents log in with apartment number and password; offline and cloud sync; reminders; exports. HopenWorks also publishes a single-building white-label (`com.building1310.app`, "اتحاد ملاك عمارة 1310", 50+). |
| 3 | **Amarti \| Building Expenses** (`com.tarek.imarati`) | Alfahd Alaswad Co. | 100+ | 4.6 | Sep 6, 2026 | n/a | Apartment status (occupied/vacant/rented/**exempt**); invite codes; expense items (electricity, water, **pumps**, staff, elevator, emergency fund); numbered digital receipts; Arabic/English. |
| 4 | **صندوق العمارة** (`com.amrem.sandooqelamara`) — https://sandoqalemara.com | Amr Emam | 500+ | 4.8 (16) | **Oct 12, 2026** | **49.99 EGP/month or 499.99 EGP/year**, free trial; in-app purchases | The richest treasurer feature set in Egypt. **Voice entry in Egyptian Arabic via assistant "عم أمين"**; Excel import with **AI column mapping**; WhatsApp reminders and receipts; partial and prepaid payments; special project funds (elevator, roof insulation, cameras); **custody for doorman/technicians (عهدة البواب)**; cash and bank treasuries; **mosque fund**; owner loans as liabilities; PDF/Excel reports; offline-first; dark mode. Site claims v137 releases. |
| 5 | **ملاك المرافق** (`com.njik.molakmarafeq`) | Njik Labbak Inc | 100+ | 4.0 | Oct 10, 2026 | n/a | Annual claims, emergency and reserve funds; bank-transfer receipt upload ("No electronic payments are processed within the app"); common-area maintenance tickets with photos; 4 roles. Saudi-style terminology. |
| 6 | **MulakHub – مُلّاك هَب** (`com.mulakhub.app`) — https://mulakhub.com | Codupia Inc | 100+ | – | Apr 27, 2026 | n/a | Units, residents, income/expense, outstanding dues, meetings and minutes (per site title). |
| 7 | **اتحاد الملاك** (`com.elgoktech.buildingmanagement`) | Abdelrahman Taha / elgoktech | 10+ | – | Oct 8, 2026 | n/a | Auto-generated monthly fees; residents upload bank-transfer receipts; maintenance requests with photos; notifications. |
| 8 | **العمارة – إدارة ذكية للعمارات** (`com.beemind.alemara`) | Eyad Ramzy | 10+ | – | Sep 28, 2026 | n/a | Offline-only; occupancy history; overdue tracking. |
| 9 | **العمارة** (`com.taqween.emarti`) | Glow Studio 1998 | 10+ | – | Oct 4, 2026 | n/a | Positions itself against "انعدام الثقة" (lack of trust) between residents and management. |
| 10 | **بنايتنا** (`com.binayatna.app`) | Mohamad Mohamad | 10+ | – | Jul 22, 2026 | n/a | Offline, on-device only; color-coded expense categories (elevator, cleaning, guard). Levantine term "بناية". |
| 11 | **عمارتي** (`com.yazan.mybuilding`) | KDY999 | 10+ | – | Jul 25, 2026 | n/a | Landlord/rental-oriented (contracts, rent). |
| 12 | **Ethadna – اتحادنا** (`sa.ethadna.app`) | Ayed Ahmed | 1+ | – | Oct 10, 2026 | n/a | Saudi namespace. |
| 13 | **ELOMARA العُمارة** (web + app) — https://elomara.com/ar | not disclosed | Play listing not found | – | – | not stated | Describes itself as "منصة مصرية ذكية لإدارة العمارات". Connects residents, managers, supervisors, **approved service providers** and a "V3 financial system". Features: invoices, payment proofs, cash logs, utilities, **chat**, **provider marketplace**, **nearby services/local businesses**. Conceptually the closest Egyptian product to the founder's vision; no traction data found. |

**Pattern across all 13.**
- **Low traction:** the largest has 1K+ installs.
- **Solo-developer builds:** many listings use Gmail contact addresses.
- **Same feature core:** ledger, receipts, reminders, expenses.
- **Manual payment proof** (receipt photo) instead of real payment rails.
- **Manager-centric:** residents are viewers.
- **Generic naming:** at least **7 apps are literally called "عمارتي/العمارة"**, so nobody can win on search-by-name. This is a branding opportunity.

---

## 4. Compound-level (gated community) apps: the white-label vendors

### 4.1 Lyve (formerly iCommunity) — the incumbent compound platform

| Field | Data | Source |
|---|---|---|
| Company | New Moonshot for Information Technologies / "Lyve Inc" (Play developer names) | Play listings |
| Founded | August 2016 as iCommunity; rebranded **Lyve** on 26 Jan 2020 | https://egyptinnovate.com/en/news/icommunity-is-now-lyve-a-new-facelift-simplifying-life-in-compounds |
| CEO | Karim Akram | same; Raya 2021 release |
| Funding | Algebra Ventures (June 2018). CB Insights: Series A, ~$600K total raised; no newer round found. | Egypt Innovate; https://www.cbinsights.com/company/icommunity/ |
| Scale | 2020: 50+ compounds, ~40,000 units. June 2021: ~120K households, 100+ compounds. LinkedIn self-report: **200,000+ contracted units** [unverified: LinkedIn not fetchable; self-reported]. | Egypt Innovate; https://enterpriseam.com/egypt/2021/06/01/raya-trade-doing-consumer-finance-with-lyve-hawaya-hits-4-mn-users/ ; https://www.linkedin.com/company/lyve-app |
| Clients | Palm Hills, La Vista, Rooya, MNHD, Katameya Heights (2020); app listings also show Hyde Park, SED, Hassan Allam Properties, Dorra, Al Marasem, Emaar Misr Commercial | Egypt Innovate; Play |
| Monetization signals | Paid by developers/HOAs (B2B). **Third-party services/stores inside the app**. **Raya Trade appliances + consumer finance for residents (2021)**. **"Lyve Benefits"** QR discount validation at partner outlets (Play `com.moonshot.lyvebenefits`, 5+ installs, updated Jun 2026). | Raya: https://rayacorp.com/raya-trade-signs-cooperation-protocol-with-lyve-to-provide-home-appliance-and-electronics-to-residential-compounds/ |

**Lyve's Play Store footprint (Egypt storefront, 2026-10-12):**

| App (package) | Downloads | Rating (reviews) | Last update |
|---|---|---|---|
| Lyve-App (`com.moonshot.icommunity`) | **10K+** | 4.4 (354) | Sep 21, 2026 |
| La Vista (`com.moonshot.lavista`) | **10K+** | 4.3 (106) | Sep 22, 2026 |
| Palm Hills Live (`com.moonshot.palmhills`) | **10K+** | 3.6 (38) | Sep 21, 2026 |
| SED Communities (`com.moonshot.sed`) | 5K+ | 4.4 (36) | Sep 21, 2026 |
| Places by Hyde Park (`com.moonshot.hydePark`) | 1K+ | – | Sep 21, 2026 |
| Hassan Allam Properties (`com.moonshot.hap`) | 1K+ | 4.0 (10) | Sep 21, 2026 |
| DORRA Egypt (`com.moonshot.dorra`) | 1K+ | 4.8 (6) | Sep 22, 2026 |
| Al Marasem Development (`com.moonshot.almarasem`) | 1K+ | 4.6 (15) | Sep 21, 2026 |
| Emaar Misr Commercial Spaces (`com.lyve.emaarcommercial`) | 500+ | – | Jul 20, 2026 |
| Lyve Spaces (commercial) (`com.moonshot.lyveSpaces`) | 100+ | – | Nov 27, 2025 |

**ESTIMATE:** the combined Android lower bound is about 40K+ installs (sum of bucket floors). With iOS and the 10K+ buckets possibly reaching 49K each, Lyve probably touches on the order of 50–150K app users. That is consistent with its own "120K households" (2021) and "200K units" claims.

**Feature set:** announcements; in-home service requests to facility management; reporting common-area issues; **visitor gate passes (QR)**; **identity badge for access control**; community listings and stores; "100% verified users".

**Verbatim reviews (Lyve family):**
- Lyve-App, 1★, 2025-02-19: "The app was introduced to me through my compound with an invitation code. And I've tried many times to register but keep getting an error… Tried to reach out to support with no response. Sent to my community management team and no response either."
- Lyve-App, 1★, 2024-04-12: "It recommends updating the app but it doesn't have any update on the playstore to download?!"
- Lyve-App, 4★, 2025-06-29: "App is useful ... you fixed truncted text in complaints but still needs RTL alignment for arabic text"
- Palm Hills Live (Arabic, 2026-08-07): «عقيييييم. والله عيب بعد كل الفلوس اللي بندفعها تعملوا ابليكاشن عقيم زي ده..»
- DORRA Egypt, 5★, 2023-02-20: "I think the only thing this app needs is a way for **neighbours to talk to each other**…" (a direct request for resident-to-resident social features)
- La Vista, 4★, 2025-01-25: "Cant add new community… contact support no one was helpful to fix my issue and add my unit"

**Strengths:** the largest installed base in compounds; years of developer relationships; marketplace and benefits experiments already done; white-label factory (one codebase, many brands).
**Weaknesses:**
- Fragmented across 10+ branded apps, so there is no network effect between compounds.
- Support is unresponsive.
- Update-loop and RTL bugs.
- **No resident-to-resident social layer.**
- Only reaches gated compounds (a small minority of Egyptian households); does not touch ordinary عمارات.
- Funding appears stale (no round since ~2018 found).

### 4.2 Milango (and its Kijamii lineage)

| Field | Data | Source |
|---|---|---|
| Founded | Spun out as an independent platform in 2019 (Wamda says "founded last February", i.e. Feb 2020). **Amr Mostafa** is CEO; Startup Scene calls him founder, but Wamda and Ventureburn say he was *appointed* CEO at spin-out [corrected]. First used by Kijamii (agency) for its clients in 2016. | https://thestartupscene.me/BehindTheStartup/Milango-Digitising-the-DNA-of-Modern-Residential-Life ; https://ventureburn.com/2020/10/egyptian-tech-startup-secures-six-figure-capital-seed-investment/ |
| Funding | Undisclosed six-figure seed led by **A15** with strategic angels (6 Oct 2020) | https://www.wamda.com/2020/10/milango-raises-seed-investment |
| Clients | Orascom Development (El Gouna), Emaar, SODIC, Almaza Bay, Hyde Park, Smash Sporting Club (2020). Acquired **Circle** in 2022. Expanded to commercial complexes. "Great Pyramids of Giza" project. | Wamda; Startup Scene |
| Product | Resident app, digital guest management, backend dashboard for developers | Startup Scene |

**Milango-built apps on Play (Egypt, 2026-10-12):**

| App (package) | Developer on Play | Downloads | Rating (reviews) | Last update |
|---|---|---|---|---|
| Emaar Misr App (`com.kijamii.emaarcommunities`) | Emaar Misr For Development | **10K+** | 3.9 (261) | Oct 7, 2026 |
| SODIC (`com.kijamii.sodiccommapp`) | Milango APM | 5K+ | 3.3 (51) | Sep 23, 2026 |
| City Edge Developments (`app.milango.cityedge`) | Milango APM | **10K+** | 3.8 (93) | Sep 30, 2026 |
| Morshedy Group (`app.milango.morshedy`) | Milango APM | **10K+** | 3.6 (47) | Aug 5, 2026 |
| MyPorto – Amer Group (`app.milango.amergroup`) | Milango APM | 5K+ | 4.3 (47) | Jul 14, 2026 |
| Al-Ahly Sabbour (`app.milango.alahlysabbour`) | Milango APM | 5K+ | 3.5 (17) | Sep 1, 2026 |
| Misr Italia Engage (`app.milango.misritalia`) | Milango APM | 100+ | 3.6 | Mar 18, 2026 |

**Verbatim reviews:**
- Emaar Misr, 2★, 2026-08-18: "constantly crashes, and is so slow. as a resident, we must depend heavily on this app… constant problems when people are impatient and dependent on the timing for the app to **open gates**"
- Emaar Misr, 2★, 2024-06-23: "IdDbadge doesn't open the gate many times. Says gate out of range. No way to enter my building if app is not working right."
- Emaar Misr, 1★, 2022-08-02: "Generated QR codes are incomplete and refused at the gates and embaresses me infront my guests"
- Emaar Misr, 1★, 2023-08-20: "…at best a Beta entry level minimum viable product… it is not the app that has most of the problems but rather the backend systems supporting it, total disconnect with terrible integration."
- SODIC, 1★, 2024-09-11: "Buggy application… you have to get OTP over sms each time you open it from the very same mobile and after this it takes ages to load"
- SODIC (Arabic), 1★, 2024-07-17: «تطبيق سيئ، لا يمكنك رؤية بعض الميزات بسبب أخطاء التصميم والتطبيق بطيئ للغاية، لا يليق بشركة مثل سوديك»
- SODIC, 1★, 2026-02-18: "It is unacceptable that the barcode issue for the project gate has not been resolved for more than a month"
- City Edge (Arabic), 2★, 2023-07-09 (62 thumbs-up): «الدخول للبرنامج شديد الصعوبه التحميل اكتر من ١٠ الي ١٥ مره حتى يعمل»
- City Edge (Arabic), 1★, 2025-12-15: «…انا ك اونر مش عارف اعمل log in لان الابليكيشن مش عارف حتي يبعت كود!؟؟»
- Morshedy, 1★, 2025-10-28: "A bug in the Verify Code screen… has any tester this app before releasing it?…"

**Strengths:** blue-chip developer contracts; gate/guest management depth.
**Weaknesses:** quality complaints dominate; OTP delivery failures; residents are captive users, not fans; one app per developer, so no cross-community network.

### 4.3 Other developer / compound apps

| App (package) | Builder | Downloads | Rating (reviews) | Last update | Notes & verbatim pain |
|---|---|---|---|---|---|
| **TMG Life** (`com.tmglife.app`) | Talaat Moustafa Group (in-house) | **50K+**, the largest in the category | **4.8 (1.16K)** | Aug 11, 2026 | Madinaty/Rehab/Noor: bill pay, **NFC charging of prepaid electricity cards**, club renewal, services. 3★, 2025-10-20: "Useful for nfc charging your utility cards… booked a plumbing service months ago and i'm still waiting on it to get dispatched". 1★, 2026-08-09: "Payment completes… Money is taken… Electricity card is NOT updated". Arabic 1★, 2025-08-07: «تطبيق عبيط ماسكه صنايعية هواه، مش ملتزمين ولا بيحترموا مواعيدهم» (complaint about the technicians). |
| **Mountain View Community** (`com.congora.mountainview`) | Intcore | 10K+ | 3.7 (34) | Aug 25, 2026 | 2★, 2026-05-06: "I changed my phone device and now I am blocked… 'You are now blocked due to violation of the single device role, Please visit your nearest office'". 1★, 2026-08-12: "can't send SMS or WhatsApp messages for completing authentication." |
| **PALM HILLS** (`com.palmhills.communityapp`) | Palm Hills Development (in-house, replaced the Lyve app) | 5K+ | 3.0 (34) | Oct 7, 2026 | 1★, 2026-02-08: "Owning my unit in PHNC since 2 years… 'your Community App account has been reviewed and was not approved'". 1★, 2026-05-20: "after 6 months they [haven't] accepted my account". 2★, 2024-08-19: "mandatory to take a selfie… camera will never open". |
| **Madinet Masr** (`com.madinetmasr.community`) | Madinet Masr Innovation Labs | 5K+ | **2.5** (23) | Mar 30, 2026 | Registration/OTP failures, international numbers rejected. Arabic 1★, 2026-06-30: «التطبيق لايعمل و مفيش دعم فني تتصل و تبعت ايميل مفيش اي استجابة». 3★, 2025-05-17: maintenance-cheque ledger shows wrong arrears. |
| **Tatweer Misr Communities** (`com.macber.eg.tatweer`) | Comet Innovations IT L.L.C | 1K+ | 3.4 (14) | Sep 23, 2026 | "already on another device" lockouts; rejects international numbers. |
| **ORA Developers** (`com.oradevelopers.users.app`) | ORA (in-house) | 1K+ | 2.7 (7) | Jun 15, 2026 | Gate QR, guests, installments, family members, nearby shops. Arabic 2026-08-26: «في مشكلة في الابليكشن مش بيشتغل علي كل الموبيلات… بيطلع رسالة تحذير امني» |
| **Horizon Egypt** (`com.horizon_egypt_development`) | Horizon Egypt | 100+ | 5.0 (8) | Aug 31, 2026 | Installments, requests, announcements. |
| **DORRA** (`com.dorra.dorracommunity`) | DORRA (in-house; previously Lyve-built) | 100+ | 4.2 (5) | Jul 27, 2026 | Visitor QR, payments, maintenance, **list unit for rent/resale** (a monetization hook). |
| **Sakan Masr** (`com.KonektApps.saknmasr`) | Konekt Apps | 100+ | 4.8 | Oct 4, 2026 | Sakan Masr Al Andalus: QR passes **with plate recognition**, complaints. |
| **Mulak** (`com.compound.mulak`) | Ahmed Radwan | 100+ | 4.8 | **Oct 21, 2024** (stale) | Pure gate-QR app: time-bound one-time visitor QR, self-entry QR. |
| **Misrrea** (`io.missrea.app`) | **BOYOT LLC** for Misr Real Estate Asset Management | 1K+ | 4.9 (9) | Sep 8, 2026 | Rent, utilities, maintenance fees, requests. The company serves 13,000+ clients across "hundreds" of downtown Cairo/Alexandria buildings (https://www.alaqaratalyoum.com/2026/07/misr-asset-management-launches-misrrea-app.html). |
| **Boyot** (`boyot.tenant.app`, `io.boyot.arkan`) | BOYOT LLC | 100+ / 5+ | – | Oct 2025 / Mar 2026 | Egyptian rent-collection/property-management startup, founded ~2020; co-founders Khaled El-Refaei and Mahmoud El-Sabounagy; on ON TV's "Al-Forsa" in Feb 2022 with 150 clients (https://www.youm7.com/story/2022/2/2/…/5641803). Now white-labels developer apps (Arkan Palm, Misrrea). |
| **Unitify** (`com.unitify.client`) — https://unitify.com/egypt | Unitify Ltd (founder Ilia Sotonin; ex-CIS) | 500+ | – | Oct 1, 2026 | Explicit Egypt landing page targeting compound management companies in New Cairo/Zayed/New Capital. **Free plan $0**, Base **$0.5/apt/month**, Pro **$1.5/apt/month** (AI concierge, AI reports, billing). Built around Law 119/2008; reconciles InstaPay/Meeza/EG-ACH. Self-reported case (Avant Park, Baku): app share of payments rose from 19% to 74% in 2 months. **The most sophisticated foreign entrant and a likely future competitor.** |
| **Mudir App** (`com.mudirapplication.app`) — mudirapp.com | Real Estate Technology Solutions Co. (Giza) | **50K+** | 4.0 (68) | Sep 24, 2026 | Landlord/rental management plus listings and e-contracts. Freemium with 4 tiers. Adjacent, not HOA. |
| **Ahl Madinaty** (`com.ahl.madenty`) | "thelegend" (community-run) | **10K+** | 4.6 (199) | Oct 7, 2026 | Community directory for Madinaty: shops, clinics, bus schedules, offers, magazine. **Proof that a grassroots "hyper-local directory + notifications" app can beat official apps on ratings.** |
| **كمبوندى (حدائق الاهرام)** (`com.melsayed25.compoundy`) | Compoundy Solutions | 100+ | – | Sep 11, 2026 | Community and business hub for Hadayek El Ahram residents. |
| Rehab City directories (`com.newsmart.rehab`, `alrehab.city`) | individuals/Shrka | 5K+ / 500+ | 4.2 | 2023 / 2022 (stale) | Local directories. |

**Names from the brief that I checked and could NOT verify as Egyptian building/compound apps:** "Tenanty", "Comunidad", "Bawabty", "Compoundz", "Hayah", "Ezdan", "Mazaya", "Hood". Web and Play searches (Play queries "Bawabty", "Compoundz" and others on the `gl=EG` store) returned no matching product. `com.app.bawabeti` exists but its listing was not confirmed as building-related. NoBroker's "Hood" is an Indian product (see the international competitors file). Ezdan and Mazaya are Qatari/Kuwaiti real-estate groups, not Egyptian apps.

---

## 5. Cross-cutting complaint analysis (what Egyptian residents hate)

Built from roughly 300 Google Play reviews pulled on 2026-10-12 across the 19 Egyptian apps above (Arabic and English feeds). Counts are my coding of the 1–3★ reviews with text over 60 characters across TMG Life, Emaar Misr, SODIC, Palm Hills, Mountain View, Madinet Masr, City Edge, Tatweer, Lyve and Morshedy (n≈95). **ESTIMATE:** the percentages are approximate.

| Pain theme | Approx. share of negative reviews | Representative quote | Product answer |
|---|---|---|---|
| **Login / OTP / registration failures** (SMS not received, international numbers rejected, "not approved", "single-device" lockouts) | **~35%** | "No verification SMS recieved so could not login" (Madinet Masr, 2025-01-07); "You are now blocked due to violation of the single device role" (Mountain View, 2026-05-06) | **WhatsApp-OTP + Google/Apple sign-in, invite-link auto-join, multi-device by default, international numbers supported (expat owners are common).** |
| **Crashes / slowness / broken updates** ("insecure device" false positives after an update) | **~30%** | "App keeps on crashing… says app cannot be used on unsafe device… after update" (Emaar Misr, 2024-12-22) | Quality bar: crash-free rate >99.5%, staged rollouts, no aggressive root checks. |
| **Gate QR / badge doesn't work** | ~10% | "IdDbadge doesn't open the gate many times" (Emaar Misr); "barcode issue… not resolved for more than a month" (SODIC, 2026-02-18) | Offline-capable QR, guard-side app, fallback via WhatsApp. |
| **Service requests ignored / technicians unreliable** | ~10% | "booked a plumbing service months ago and i'm still waiting" (TMG Life); «صنايعية هواه، مش ملتزمين ولا بيحترموا مواعيدهم» (TMG Life) | **The phase-2 marketplace must win on reliability:** SLA, ratings, guarantees, price transparency. |
| **No support / no response** | ~10% | «مفيش دعم فني تتصل و تبعت ايميل مفيش اي استجابة» (Madinet Masr, 2026-06-30) | AI first-line support inside WhatsApp, with escalation. |
| **Payments wrong / not reflected** | ~5% | "Money is taken… Electricity card is NOT updated" (TMG Life, 2026-08-09) | Real-time payment reconciliation; instant receipts. |
| **Arabic/RTL quality** | small | "still needs RTL alignment for arabic text" (Lyve, 2025-06-29) | Arabic-first, Egyptian dialect. |
| **Missing social / neighbour features** | small but telling | "the only thing this app needs is a way for neighbours to talk to each other" (DORRA Egypt, 2023-02-20) | Resident network, which is the core of the founder's strategy. |

**Building-level app reviews (very different tone: users are grateful but ask for flexibility):**
- Unequal fees and exemptions: «مش كل الادوار نفس عدد الشقق ومش كله بيدفع نفس المبلغ» (صندوق العمارة, 3★, 2026-09-25). «…لو شقة تحت التشطيب ومبتدفعش تيجي تضيف للمبلغ صفر ميقبلش» (صندوق العمارة, 4★, 2026-09-27). Amarati review asking for per-service opt-in, one-off levies and hiding sensitive items.
- Elderly / no-smartphone residents: «في ناس كبيره في السن مش هتعرف تستخدم البرنامج ف لازم تبقي البيانات موجوده» (Omaraty, 2026-08-22).
- Other income (shop, roof, garage rent): requested in the Omaraty review and shipped in Omaraty 2.0.
- Price sensitivity / surprise subscription: «التطبيق مجاني لمده شهر واحد فقط وبعد كده باشتراك… حذفته علشان كنت فاكره مجاني» (Ammarty, 3★, 2026-10-05). «ياريت ميبقاش رسوم غاليه» (Amarati).
- Better reports with names and amounts: «يبقى التقارير شامله الأسماء بقيمه الدفع» (صندوق العمارة, 4★).

> **Key insight.** In ordinary buildings, the buyer and champion is the **volunteer treasurer/committee head**, who is overloaded and price-sensitive. Residents punish paywalls by uninstalling. **Being free forever for the building's core workflow is a hard requirement for the founder's phase-1 dominance strategy.**

---

## 6. Business-model map of Egyptian competitors

| Model | Who | Price points | Comment |
|---|---|---|---|
| **B2B white-label paid by developer/FM company** | Lyve, Milango, Intcore, Comet, RAY Labs, Boyot | Not public. **ESTIMATE:** setup fee plus annual licence per community. | Revenue doesn't depend on residents liking the app, which explains the quality issues. |
| **In-house developer apps** | TMG Life, Palm Hills, ORA, DORRA, Horizon | Cost centre | Strongest when tied to utilities (TMG NFC electricity) and club membership. |
| **SaaS per building, paid by committee** | Saknna (450–7,500 EGP/mo), صندوق العمارة (49.99 EGP/mo, 499.99/yr), Ammarty (subscription after 1 month) | 50–7,500 EGP/month | Low conversion risk; reviews show price sensitivity. |
| **Per-apartment SaaS (foreign)** | Unitify | $0 / $0.5 / $1.5 per apt/month | Free tier is a direct threat to any free play. |
| **Free (no visible model)** | Amarati, Omaraty, Imarti, most tiny apps | Free | No path to revenue yet; Imarti hints at provider offers. |
| **Marketplace / commerce in community** | Lyve (stores, Raya appliances plus consumer finance, Lyve Benefits); Imarti (trusted providers with countdown offers); ELOMARA (provider marketplace, local businesses); DORRA (unit rent/resale listings) | Commission / partnership | **This is the founder's phase 2, and it is still embryonic everywhere in Egypt.** |
| Benchmark abroad | MyGate (India): 27,000+ communities, ~5.7M homes (Entrepreneur, Jun 2026) [corrected], FY25 operating revenue ~₹173.5 crore (+80%), ~65–70% from advertising | – | https://inc42.com/buzz/mygate-trims-fy25-loss-by-61-to-%E2%82%B915-4-cr/ ; https://india.entrepreneur.com/business-news/mygate-bags-inr-225-crore-from-dharana-capital |

**Adjacent phase-2 players (home services) the founder will meet later:**
- **FilKhedma:** founded 2014; plumbing, carpentry, electrical, AC; pre-set pricing and one-month guarantee; Cairo Angels funding 2021. https://cairoscene.com/Business/Home-Services-App-FilKhedma-Raises-New-Funds-from-The-Cairo-Angels
- **Fixawy:** video-based diagnosis; from EGP 50. https://www.dailynewsegypt.com/?p=727734
- **Helper:** cleaning; Falak Startups. Tracxn.
- See file 03 for the full list.

---

## 7. Comparison matrix

Legend: ✅ = yes (verified from listing/site) · ◐ = partial/basic · ❌ = not found · ? = unknown

| Competitor | Segment | Android installs (EG) | Resident accounts | Auto monthly dues | Online payment rails | Receipt-photo proof | Expenses & reports | Voting / polls | Maintenance tickets | Gate / visitor QR | Doorman / staff module | WhatsApp integration | AI | Marketplace / services | Social (neighbour-to-neighbour) | Arabic Egyptian-first | Price |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| **Amarati** (com.amarati.app) | Building | 1K+ | ✅ | ✅ | ❌ | ◐ (cash claim) | ✅ | ❌ | ❌ | ❌ | ❌ | ◐ invite link + summary image | ◐ meter-photo OCR | ❌ | ❌ | ◐ (Palestinian) | Free |
| **Imarti** (com.craftfuture.imarti) | Building | 100+ | ✅ | ✅ | ❌ | ◐ | ✅ PDF | ✅ | ◐ complaints | ❌ | ❌ | ❌ | ❌ | ◐ providers + offers | ❌ | ❌ (Saudi terms) | ? |
| **Saknna** (web) | Building/compound | PWA (n/a) | ◐ | ✅ | ◐ manual InstaPay/VF Cash | ? | ✅ | ❌ | ✅ | ❌ | ❌ | ❌ (support only) | ✅ Arabic assistant | ❌ | ❌ | ◐ | 450–7,500 EGP/mo |
| Omaraty (Techiato) | Building | 100+ | ✅ (+offline residents) | ✅ | ❌ | ✅ | ✅ | ✅ polls | ◐ complaints | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | Free |
| Ammarty (HopenWorks) | Building | 1K+ | ✅ | ✅ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ◐ share receipts | ❌ | ❌ | ❌ | ✅ | Sub after 1 mo |
| صندوق العمارة | Building (treasurer) | 500+ | ❌ (manager only) | ✅ | ❌ | – | ✅✅ (best) | ❌ | ❌ | ❌ | ✅ custody | ✅ reminders/receipts | ✅ voice "عم أمين", AI Excel mapping | ❌ | ❌ | ✅ | 49.99 EGP/mo |
| ELOMARA (web/app) | Building | n/a | ✅ | ✅ | ? | ✅ | ✅ | ? | ✅ | ❌ | ◐ supervisors | ❌ | ❌ | ✅ providers + local biz | ◐ chat | ✅ | ? |
| ملاك المرافق / MulakHub / others | Building | ≤100+ | ◐ | ✅ | ❌ | ✅ | ✅ | ◐ | ◐ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ◐ | ? |
| **Lyve** (10+ white-labels) | Compound | ~40K+ combined | ✅ verified | ◐ fee reminders | ◐ | ? | ❌ | ? | ✅ | ✅ | ❌ | ❌ | ❌ | ✅ stores, finance, benefits | ◐ social wall (2021) | ◐ (RTL issues) | B2B |
| **Milango** (Emaar, SODIC, City Edge…) | Compound | ~45K+ combined | ✅ | ◐ | ◐ | ? | ❌ | ? | ✅ | ✅ | ❌ | ❌ | ❌ | ◐ market (SODIC) | ❌ | ◐ | B2B |
| **TMG Life** | Compound/city | 50K+ | ✅ | ✅ bills | ✅ cards + NFC utility | – | – | ❌ | ✅ | ✅ | ❌ | ❌ | ❌ | ◐ club, services | ❌ | ◐ | In-house |
| Mountain View / Palm Hills / ORA / Madinet Masr / Tatweer | Compound | 1K–10K+ each | ✅ | ◐ installments | ◐ | – | – | ❌ | ✅ | ✅ | ❌ | ❌ | ❌ | ◐ nearby shops (ORA) | ❌ | ◐ | In-house/B2B |
| **Unitify** (foreign) | Compound FM | 500+ | ✅ | ✅ | ✅ reconciles InstaPay/Meeza/ACH | ✅ | ✅ | ✅ mini-app | ✅ | ✅ | ✅ technician app | ❌ (Telegram bot) | ✅ AI concierge, reports | ✅ marketplace module | ◐ | ◐ glossary | $0–1.5/apt/mo |
| Ahl Madinaty (grassroots) | City directory | 10K+ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ directory, offers | ❌ | ✅ | Free |

**Reading the matrix:** no Egyptian player has more than three of these at once: **(free) + (resident accounts) + (WhatsApp-native) + (AI) + (marketplace) + (doorman) + (social)**. Unitify comes closest on features, but it is B2B, priced per apartment, Telegram-centric, and aimed at management companies in compounds, not ordinary عمارات.

---

## 8. White space: where a new Egyptian app can win

### 8.1 Segment white space
1. **The ordinary Egyptian عمارة (5–40 flats, no management company).** This is the vast majority of the ~16M-building stock. There is no product above 1K installs, and Saknna's pricing (~90–110 EGP/unit/month) excludes it. **Whoever becomes the default app here owns the largest residential network in Egypt.**
2. **Old Cairo / Alexandria / Giza mid-market neighbourhoods** (Nasr City, Heliopolis, Maadi, Mohandessin, Faisal, Haram, Shoubra, Smouha). Nasr City authorities are actively pushing union registration as of June 2026. Hook: "سجّل اتحاد الشاغلين".
3. **Smaller compounds and "شبه كمبوند" projects** (Hadayek October, Hadayek El Ahram, Shorouk, Obour) that can't afford Lyve/Milango. They are currently served by grassroots apps (Compoundy, Ahl Madinaty-type directories).
4. **Expat owners** (Gulf-based Egyptians): compound apps repeatedly reject international numbers. A product that works abroad wins them, and they are high-value marketplace customers (remote maintenance of the family flat).

### 8.2 Product white space (features nobody in Egypt has combined)

| # | White-space feature | Why it wins | Evidence of gap |
|---|---|---|---|
| 1 | **WhatsApp-native bot inside the existing building group.** It reads the conversation, logs payments ("دفعت الشهرية"), creates tickets ("الأسانسير واقف"), answers "مين لسه مدفعش؟", and posts summaries. | Meets residents where they already are; zero behaviour change; **viral**, because each group carries the brand to 10–40 people. | Every competitor positions *against* WhatsApp groups (Omaraty, Saknna, Amarati). Only share-to-WhatsApp exists (Amarati image summary, Ammarty/صندوق receipts). |
| 2 | **Free forever for the building core** (ledger, dues, receipts, reminders, announcements). | Reviews punish paywalls (Ammarty). Saknna and صندوق العمارة charge. | §5, §6 |
| 3 | **Every resident gets an account automatically.** Invite link in the WhatsApp group, WhatsApp OTP, and offline/"proxy" residents for the elderly, managed by the treasurer or doorman. | Login/OTP failures are ~35% of compound complaints. Omaraty reviewers ask for proxy residents. | §5 |
| 4 | **Doorman (البواب / حارس العقار) app/mode.** Simple voice-first Arabic: collects cash with instant WhatsApp receipt, logs deliveries and visitors, reports issues with photos, manages petty-cash custody. | The doorman is the de-facto operator of most Egyptian buildings. Only صندوق العمارة tracks his custody, and nobody gives him a tool. | §3, §4 matrix |
| 5 | **Real payment rails:** InstaPay deep links / IPN reference matching, wallets, Fawry codes, auto-reconciliation. | Every building app uses receipt-photo upload plus manual approval. TMG shows the value of in-app utility payment. | §3; TMG review |
| 6 | **Flexible Egyptian fee logic:** unequal shares, exemptions (flat under finishing), opt-in services (elevator for ground floor?), one-off levies, project funds (elevator renewal, water tank, roof insulation), external income (shop/roof/garage), mosque fund. | Directly requested in reviews (Amarati, صندوق العمارة, Omaraty). | §5 |
| 7 | **AI everywhere:** voice entry in Egyptian Arabic; receipt/invoice OCR; meter-photo reading; Arabic Q&A over the ledger; auto-drafted assembly invitations and minutes; dispute-free monthly report. | صندوق العمارة (voice), Amarati (meter OCR) and Saknna (assistant) each have *one* piece. Nobody has the full stack. | §2–3 |
| 8 | **Legal union toolkit:** generate the 8-document district registration pack, assembly invitations (15-day notice), attendance, notarisation checklist, minutes archive. | 2026 enforcement campaign; no competitor offers it. | §1 |
| 9 | **Neighbour network:** building and street chat, lost and found, recommendations, "who has a ladder", local marketplace. | Explicitly requested ("a way for neighbours to talk to each other"). Lyve's social wall is gone or limited. | §4.1 |
| 10 | **Trusted services marketplace (phase 2):** vetted plumbers, electricians, elevator companies, water-tank cleaning, pest control, internet/satellite; building-level group-buying (bulk elevator contracts, cleaning contracts). | TMG/Lyve resident complaints show service reliability is the unmet need. Imarti/ELOMARA have only seeds. MyGate proves the ads/services monetization at scale. | §4.3, §6 |
| 11 | **Hyper-local commerce and ads** (pharmacies, supermarkets, laundries near the building), on the Ahl Madinaty / Lyve Benefits model. | A grassroots directory (Ahl Madinaty, 10K+, 4.6★) outperforms official apps. | §4.3 |
| 12 | **Reliability as a feature:** multi-device, international numbers, no false "insecure device" blocks, staged updates. | ~65% of compound complaints are login and crash issues. | §5 |

### 8.3 Competitive threats to monitor
- **Unitify:** has an explicit Egypt page, a free plan, an AI concierge, a marketplace module, and Law 119/2008 knowledge. If it localises WhatsApp and Egyptian dialect, it becomes the strongest rival.
- **Lyve / Milango:** could launch a "Lite" product for ordinary buildings, using their FM relationships to push a services marketplace.
- **صندوق العمارة:** the most active solo developer (v137, updated the day of research). It has the best Egyptian treasurer UX and voice AI, and could add WhatsApp bot features.
- **Saknna:** sales-led, multi-country, with an AI assistant. It could drop prices.
- **Copycat risk:** building-level ledgers are trivially cloneable (13+ clones found). **Defensibility must come from the network** (resident accounts, WhatsApp group presence, provider supply, payment data), not from features.

### 8.4 Strategic conclusions for the founder
1. **Don't fight compounds first.** Developers lock compounds into Lyve/Milango contracts. Win the **unserved عمارة**, then offer smaller compounds a free alternative.
2. **Enter through the treasurer, spread through WhatsApp, retain through residents.** The treasurer gets a free, Egyptian-Arabic, AI-assisted tool. The bot joins the group. Every resident is auto-provisioned.
3. **Use the legal tailwind (union registration) as free PR and a growth hook.** Partner with district tech centres and lawyers who specialise in اتحاد الشاغلين.
4. **Phase 2 monetization is proven but unclaimed in Egypt:** services marketplace commissions, payment float/fees, hyper-local ads (MyGate's ~65–70% ad revenue), building-level group contracts (elevator maintenance, cleaning, insurance), and later fintech (Lyve plus Raya consumer finance).
5. **Brand distinctly.** At least 7 apps are named "عمارتي/العمارة", so a generic name is invisible in search. Use a distinctive brand plus SEO on "اتحاد الشاغلين", "مصاريف العمارة" and "شهرية العمارة".

---

## 9. Sources (primary)

**Google Play listings (all fetched 2026-10-12, `gl=EG`):**
- https://play.google.com/store/apps/details?id=com.amarati.app
- https://play.google.com/store/apps/details?id=com.craftfuture.imarti
- https://play.google.com/store/apps/details?id=com.omaraty.app
- https://play.google.com/store/apps/details?id=com.ammarty.ammarty
- https://play.google.com/store/apps/details?id=com.tarek.imarati
- https://play.google.com/store/apps/details?id=com.amrem.sandooqelamara
- https://play.google.com/store/apps/details?id=com.njik.molakmarafeq
- https://play.google.com/store/apps/details?id=com.mulakhub.app
- https://play.google.com/store/apps/details?id=com.elgoktech.buildingmanagement
- https://play.google.com/store/apps/details?id=com.beemind.alemara
- https://play.google.com/store/apps/details?id=com.taqween.emarti
- https://play.google.com/store/apps/details?id=com.binayatna.app
- https://play.google.com/store/apps/details?id=com.building1310.app
- https://play.google.com/store/apps/details?id=com.moonshot.icommunity (plus `.lavista`, `.palmhills`, `.sed`, `.hydePark`, `.hap`, `.dorra`, `.almarasem`, `.lyveSpaces`, `.lyvebenefits`, `com.lyve.emaarcommercial`)
- https://play.google.com/store/apps/details?id=com.kijamii.emaarcommunities
- https://play.google.com/store/apps/details?id=com.kijamii.sodiccommapp
- https://play.google.com/store/apps/details?id=app.milango.cityedge (plus `.morshedy`, `.amergroup`, `.alahlysabbour`, `.misritalia`)
- https://play.google.com/store/apps/details?id=com.tmglife.app
- https://play.google.com/store/apps/details?id=com.congora.mountainview
- https://play.google.com/store/apps/details?id=com.palmhills.communityapp
- https://play.google.com/store/apps/details?id=com.madinetmasr.community
- https://play.google.com/store/apps/details?id=com.macber.eg.tatweer
- https://play.google.com/store/apps/details?id=com.oradevelopers.users.app
- https://play.google.com/store/apps/details?id=com.horizon_egypt_development
- https://play.google.com/store/apps/details?id=com.dorra.dorracommunity
- https://play.google.com/store/apps/details?id=com.KonektApps.saknmasr
- https://play.google.com/store/apps/details?id=com.compound.mulak
- https://play.google.com/store/apps/details?id=io.missrea.app
- https://play.google.com/store/apps/details?id=boyot.tenant.app
- https://play.google.com/store/apps/details?id=com.unitify.client
- https://play.google.com/store/apps/details?id=com.mudirapplication.app
- https://play.google.com/store/apps/details?id=com.ahl.madenty
- https://play.google.com/store/apps/details?id=com.melsayed25.compoundy

**Websites / press:**
- Saknna: https://saknna.com , https://saknna.com/ar
- صندوق العمارة: https://sandoqalemara.com
- ELOMARA: https://elomara.com/ar/compound-management-app-egypt
- MulakHub: https://mulakhub.com
- Unitify Egypt: https://unitify.com/egypt
- Lyve / iCommunity: https://egyptinnovate.com/en/news/icommunity-is-now-lyve-a-new-facelift-simplifying-life-in-compounds ; https://www.cbinsights.com/company/icommunity/ ; https://enterpriseam.com/egypt/2021/06/01/raya-trade-doing-consumer-finance-with-lyve-hawaya-hits-4-mn-users/ ; https://rayacorp.com/raya-trade-signs-cooperation-protocol-with-lyve-to-provide-home-appliance-and-electronics-to-residential-compounds/ ; https://www.linkedin.com/company/lyve-app
- Milango: https://www.wamda.com/2020/10/milango-raises-seed-investment ; https://ventureburn.com/2020/10/egyptian-tech-startup-secures-six-figure-capital-seed-investment/ ; https://thestartupscene.me/BehindTheStartup/Milango-Digitising-the-DNA-of-Modern-Residential-Life
- Boyot: https://www.youm7.com/story/2022/2/2/…/5641803
- Misrrea: https://www.alaqaratalyoum.com/2026/07/misr-asset-management-launches-misrrea-app.html
- Mudir: https://www.mudirapp.com/blog/أفضل-برنامج-إدارة-العقارات
- Legal/market: https://www.elwatannews.com/news/details/8298565 ; https://www.elwatannews.com/news/details/5864320 ; https://invest-gate.me/features/management-dilemma-occupants-union-or-developer-management/ ; https://www.dostor.org/5657044 ; https://amwalalghad.com/ihtg ; https://english.ahram.org.eg/News/574749.aspx
- MyGate benchmark: https://inc42.com/buzz/mygate-trims-fy25-loss-by-61-to-%E2%82%B915-4-cr/ ; https://india.entrepreneur.com/business-news/mygate-bags-inr-225-crore-from-dharana-capital
- Home services: https://cairoscene.com/Business/Home-Services-App-FilKhedma-Raises-New-Funds-from-The-Cairo-Angels ; https://www.dailynewsegypt.com/?p=727734

**Limitations:**
- iOS App Store data was not systematically collected (Android dominates Egypt).
- Play download buckets are coarse.
- Saknna's "500+ buildings" and Lyve's "200K units" are self-reported.
- Imarti's ownership (Saudi) is inferred from its privacy-policy domain.
- Facebook/X/Reddit complaint mining for this specific angle returned no indexed threads via search. Review evidence here comes from Google Play.
- The Akhbar El-Yom 2026 article was not retrievable (HTTP 403).

---

## Verification log

Adversarial re-check on 2026-10-12. Play data was re-fetched live (`hl=en&gl=EG`), and web claims were re-fetched from their primary pages.

| Claim | Verdict | Evidence URL |
|---|---|---|
| Amarati: 1K+ downloads, 4.7★, 43 reviews, updated Sep 30 2026, built in Palestine | confirmed (developer address Palestine, +970 phone) | https://play.google.com/store/apps/details?id=com.amarati.app |
| Imarti: 100+ downloads, no rating, Craft Future, privacy policy on craftsolutions.com.sa | confirmed (Saudi origin still an inference) | https://play.google.com/store/apps/details?id=com.craftfuture.imarti |
| Saknna pricing 450/900/2,200/7,500 EGP/month; 5/10/20/unlimited units; "500+ buildings" | confirmed as stated on site (the 500+ figure remains self-reported) | https://saknna.com/ar |
| صندوق العمارة: 500+, 4.8★ (16), 49.99 EGP/mo, 499.99 EGP/yr, updated Oct 12 2026 | confirmed | https://play.google.com/store/apps/details?id=com.amrem.sandooqelamara |
| Ammarty (HopenWorks): 1K+, 4.8★ (9); Omaraty 100+, 5.0★ (7) | confirmed | https://play.google.com/store/apps/details?id=com.ammarty.ammarty |
| TMG Life: 50K+, 4.8★, 1.16K reviews (largest app in the category) | confirmed | https://play.google.com/store/apps/details?id=com.tmglife.app |
| Lyve-App 10K+, 4.4★ (354); Emaar Misr app 10K+, 3.9★ (261); City Edge 10K+, 3.8★ (93) | confirmed | https://play.google.com/store/apps/details?id=com.moonshot.icommunity ; https://play.google.com/store/apps/details?id=com.kijamii.emaarcommunities |
| Lyve: founded Aug 2016, rebranded 26 Jan 2020, CEO Karim Akram, Algebra Ventures Jun 2018, 50+ compounds / ~40K units | confirmed | https://egyptinnovate.com/en/news/icommunity-is-now-lyve-a-new-facelift-simplifying-life-in-compounds |
| Lyve: ~120K households, 100+ compounds (2021), Raya Trade consumer finance; $600K total raised | confirmed | https://enterpriseam.com/egypt/2021/06/01/raya-trade-doing-consumer-finance-with-lyve-hawaya-hits-4-mn-users/ ; https://www.cbinsights.com/company/icommunity/ |
| Lyve: 200,000+ contracted units | unverified (LinkedIn self-report) | https://www.linkedin.com/company/lyve-app |
| Milango: founded 2019 by CEO Amr Mostafa; A15 seed Oct 2020 | corrected (A15 seed confirmed; Amr Mostafa was *appointed* CEO per Wamda/Ventureburn, and the founding date is 2019 or Feb 2020 depending on source) | https://www.wamda.com/2020/10/milango-raises-seed-investment ; https://ventureburn.com/2020/10/egyptian-tech-startup-secures-six-figure-capital-seed-investment/ |
| Unitify: Free $0, Base $0.5, Pro $1.5 per apt/month; AI concierge on Pro; 500+ installs | confirmed (billing is an add-on on Base at $0.5/invoice and included in Pro) | https://unitify.com/egypt |
| Law 119/2008: union mandatory for buildings of ≥5 units; no legal basis for electronic voting | confirmed (art. 72 per legal commentary; union exists by force of law per ER 144/2009) | https://unitify.com/egypt ; https://lawyeregypt.net/?p=4455 |
| Nasr City campaign on 9 Jun 2026: 8 documents, legal action threatened | confirmed | https://www.elwatannews.com/news/details/8298565 |
| CAPMAS 2017: 16.185M buildings, 91.2% residential | confirmed | https://amwalalghad.com/ihtg |
| ~212,000 units built in new cities in FY2024/25, about half by private developers | confirmed (107,200 units, 50.6%) | https://english.ahram.org.eg/News/574749.aspx |
| MyGate: FY25 revenue ₹173.5 cr (+80%), 65–70% from ads; "~25–27K communities" | corrected (revenue and ad share confirmed; footprint is 27,000+ communities and ~5.7M homes as of Jun 2026) | https://inc42.com/buzz/mygate-trims-fy25-loss-by-61-to-%E2%82%B915-4-cr/ ; https://india.entrepreneur.com/business-news/mygate-bags-inr-225-crore-from-dharana-capital |
