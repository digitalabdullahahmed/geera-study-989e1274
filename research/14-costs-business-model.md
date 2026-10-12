# 14 — Costs, Team, Tech Stack and Monetization Benchmarks (Egypt, Oct 2026)

> Research angle: what it really costs to build and run an Egyptian "عمارتي / سكنّا"-style building and compound super-app with mandatory AI and a WhatsApp bot. Also: how competitors and global peers make money, and which revenue model fits a zero-marketing-budget, free-first growth strategy.
>
> Date of research: 2026-10-12. Every number has a source URL. Any number marked **ESTIMATE** is my own derivation, and the reasoning is shown next to it. Where I could not find data, I say so.

---

## 0. Executive summary (the 12 numbers that matter)

| # | Finding | Value | Source |
|---|---|---|---|
| 1 | USD/EGP exchange rate, Oct 2026 | ~52.3–52.6 EGP per USD (XE 11 Oct: 52.58) | [XE](https://www.xe.com/en-us/currencyconverter/convert/?Amount=1&From=EGP&To=USD), [Nile FM 4 Oct 2026](https://www.nilefm.com/life/article/14098/exchange-rates-us-dollar-trades-at-egp-52-27-against-the-egyptian-pound-4-october-2026) |
| 2 | Urban inflation, Sep 2026 | 13.9% y/y (nationwide 12.8%); monthly +1.3% | [Daily News Egypt](https://www.dailynewsegypt.com/2026/10/10/egypts-annual-urban-inflation-eases-to-13-9-in-september/), [EnterpriseAM](https://enterpriseam.com/egypt/2026/10/11/urban-inflation-eased-to-13-9-in-september-even-as-monthly-prices-continue-to-pick-up/), [Egyptian Streets](https://egyptianstreets.com/2026/10/11/egypts-annual-inflation-rises-to-12-8-percent-in-september-as-food-prices-increase/) |
| 3 | Median software engineer net pay at Egyptian local employers | EGP 27,000/month (P75 47,800; P90 75,000) | egytech.fyi survey via [cvpromaker](https://www.cvpromaker.com/salaries/egypt/software-engineer) |
| 4 | Egyptian app-agency median hourly rate | ~$37/h (161 firms); many at <$25/h | [GoodFirms](https://www.goodfirms.co/directory/country/app-development/egypt) |
| 5 | SMS OTP via Twilio to Egypt vs WhatsApp authentication template | $0.3959 per SMS vs $0.0036 per WhatsApp OTP (~110× cheaper) | [Twilio EG](https://www.twilio.com/en-us/sms/pricing/eg), [ChatMaxima](https://chatmaxima.com/whatsapp-api-pricing/egypt/) |
| 6 | WhatsApp Egypt rates (from 1 Oct 2026) | Marketing $0.0644; Utility/Auth $0.0036; Service messages: first 1,000 per number per month free, then $0.0036; +14% VAT | [ChatMaxima](https://chatmaxima.com/whatsapp-api-pricing/egypt/), [ArabyBot](https://arabybot.com/guides/whatsapp-api-pricing-egypt?lang=en) |
| 7 | Official WhatsApp **Groups API** cap | 8 participants per group (business number included); join by invite link only; OBA required (re-verified on Meta's own Groups docs) | [Meta Groups docs](https://developers.facebook.com/documentation/business-messaging/whatsapp/groups), [Unipile](https://www.unipile.com/whatsapp-group-api/) |
| 8 | Paymob standard fee | 2.75% + EGP 3 per successful transaction; weekly settlement | [Paymob pricing](https://paymob.com/en/pricing) |
| 9 | Saknna (direct Egyptian competitor) SaaS pricing | EGP 450/mo (≤5 units), 900 (≤10), 2,200 (≤20), 7,500 (compound) ≈ **EGP 90–110 per unit per month** | [saknna.com](https://saknna.com) |
| 10 | Urban Company commissions + fees | 28.3% of professionals' gross earnings (9M FY26; Inc42 analysis, not a company-disclosed take rate); forward take rate ~22–23% | [Inc42](https://inc42.com/?p=571319), [S&P Global](https://www.spglobal.com/market-intelligence/en/news-insights/research/2026/04/urban-company-revenue-to-triple-by-2030-as-take-rates-and-platform-monetization-rise) |
| 11 | MyGate (India) revenue per home | ₹173.5 Cr FY25 across "nearly 5M homes" ≈ ₹350/home/yr (~US$4); **65–70% from ads** | [Inc42](https://inc42.com/buzz/mygate-trims-fy25-loss-by-61-to-₹15-4-cr/) |
| 12 | Egypt personal-data licensing (PDPL exec. regs, Decree 816/2025) | Annual licence fee tiered by records: ≤100k records exempt; max EGP 666,666 above 5M records (fee tiers per Tamimi/CMS; Digital Policy Alert page itself does not list them); in force 2 Nov 2025, one-year grace, full enforcement from 31 Oct 2026 — **19 days after this report date** | [Digital Policy Alert](https://digitalpolicyalert.org/event/36521-executive-regulations-of-the-personal-data-protection-law-decision-no-816-of-2025-including-operational-license-requirement-entered-into-force), [Clyde & Co](https://www.clydeco.com/en/insights/2026/01/egypt-regulatory-update-on-data-privacy) |

**Strategic conclusions in brief:**
1. **Build in-house with a small Egyptian team, not an agency.** A 6–7 person team costs about **US$7–9k/month fully loaded (ESTIMATE)**. A 6-month MVP comes to about **US$45–55k**. An agency quote for the same scope is about **US$110–225k (ESTIMATE)**.
2. **Never use SMS for OTP. Use WhatsApp authentication templates, and the user's own WhatsApp share sheet for invites.** This one decision saves six figures at a million users.
3. **The official WhatsApp API cannot sit inside a normal 30–200-member building group** (8-participant cap). The "bot joins the building's group" idea has to be redesigned. See §5.
4. **Payments are not a profit centre at first.** Paymob charges about 3.25% on a EGP 600 dues payment. Holding residents' money yourself needs a CBE licence. Partner with licensed payment providers and earn convenience fees and referral fees, not float.
5. **The phase-2 money is in three places:** the services marketplace (15–20% take rate), compound SaaS (Saknna shows Egyptian buildings already pay about EGP 90/unit/month), and hyper-local ads and sponsored offers (MyGate earns 65–70% of revenue from ads).
6. **Base-case ESTIMATE:** about 200k active households by month 36, giving about **US$70–80k monthly revenue**. That is break-even to profitable on a team that stays below about US$45k/month.

---

## 1. Macro context: FX, inflation, market base

### 1.1 Exchange rate and inflation

| Indicator | Value | Source |
|---|---|---|
| USD/EGP, 11 Oct 2026 | 52.5772 | [XE](https://www.xe.com/en-us/currencyconverter/convert/?Amount=1&From=EGP&To=USD) |
| CBE buy/sell, 7–8 Oct 2026 | 52.32 / 52.46 | (aggregated in search; [banklive](https://banklive.net/en/exchange-rate-USD-to-EGP-today)) |
| USD/EGP, 4 Oct 2026 | 52.27 | [Nile FM](https://www.nilefm.com/life/article/14098/exchange-rates-us-dollar-trades-at-egp-52-27-against-the-egyptian-pound-4-october-2026) |
| Model forecast for Oct 2026 range | 52.45–54.01 (a model forecast, not data) | [CoinCodex](https://coincodex.com/forex/usd-egp/forecast/) |
| Urban CPI, Sep 2026 | 13.9% y/y (Aug: 14.5%) | [Daily News Egypt](https://www.dailynewsegypt.com/2026/10/10/egypts-annual-urban-inflation-eases-to-13-9-in-september/) |
| Nationwide CPI, Sep 2026 | 12.8% y/y | [Egyptian Streets](https://egyptianstreets.com/2026/10/11/egypts-annual-inflation-rises-to-12-8-percent-in-september-as-food-prices-increase/) |
| CBE target path | Stable in Q3 2026, then falling toward 7% ±2pp in H2 2027 | [Rio Times](https://www.riotimesonline.com/egypt-urban-inflation-13-9-percent-september-2026/) |

**Planning rate used in this document: 1 USD = 52.5 EGP.**

**Implications for the budget (ESTIMATE):**
- About 70–80% of the cost base is EGP salaries. Plan salary reviews of about **+12–20% per year** to track 13–14% inflation and keep developers.
- About 20–30% of costs are USD-denominated: cloud, LLM APIs, WhatsApp (Egypt is billed in USD), Apple and Google fees. These costs rise in EGP terms whenever the pound weakens. Keep a **10–15% FX buffer** on USD lines.
- Revenue will be in EGP. Price marketplace fees as **percentages, not fixed EGP amounts**, so revenue inflates automatically.

### 1.2 Market base (for revenue modelling)

| Metric | Value | Source |
|---|---|---|
| Households in Egypt (1 Jan 2025) | 26.5M total; 11.8M urban (44.4%); 14.7M rural | CAPMAS via [Cairo Scene](https://cairoscene.com/buzz/over-half-of-egyptian-households-live-in-rural-areas) |
| New-city housing built FY2024/25 | ~212,000 units (+33% y/y); 50.6% by private developers | [Ahram Online](https://english.ahram.org.eg/News/574749.aspx) |
| Internet users (end 2025) | 98.2M (82.7% penetration) | [DataReportal Digital 2026 Egypt](https://datareportal.com/reports/digital-2026-egypt) |
| Social media identities (Oct 2025) | 51.6M | [DataReportal](https://datareportal.com/reports/digital-2026-egypt) |
| Cellular connections | 121M (102% of population) | [DataReportal](https://datareportal.com/reports/digital-2026-egypt) |
| Egypt home-services market | US$1.88B (2025) → US$5.11B (2034), CAGR 11.6%; repair and maintenance is the largest category | [Deep Market Insights](https://deepmarketinsights.com/vista/insights/home-services-market/egypt) (single vendor, not cross-checked) |
| MENA digital ad spend 2025 | US$8.185B (+17.8%); **Egypt fastest growing at +23.1%** | [Campaign ME / IAB MENA](https://campaignme.com/digital-ad-spend-in-mena-reaches-8b-in-2025-iab-report-reveals/) |

**Serviceable market (ESTIMATE):** The core targets are urban apartment-building households plus new-city and compound households, about **8–10M households**. Reasoning: 11.8M urban households, plus new cities that CAPMAS partly classifies otherwise, minus single-family and informal stock with no building-level management. At a 2% share that is 160–200k households, and at 5% it is 400–500k.

---

## 2. Team costs (salaries in Egypt, 2025–2026)

### 2.1 Salary benchmarks

Salary data in Egypt is noisy. Aggregators mix monthly and annual figures, and net and gross. The most transparent dataset is the **egytech.fyi community survey** (n=2,125 at local employers), as reported by [cvpromaker (July 2026)](https://www.cvpromaker.com/salaries/egypt/software-engineer):

| Level | Typical local company (net EGP/month) | Top product co. / multinational (net EGP/month) | Remote for foreign employer |
|---|---|---|---|
| Junior (0–2 yrs) | 10,000–22,000 | 16,000–32,000 | rare |
| Mid (2–5 yrs) | 18,000–42,000 | 28,000–55,000 | $1,800–3,500/mo |
| Senior (5+ yrs) | 35,000–70,000 | 60,000–105,000 | $2,500–5,000+/mo |
| All, median | 27,000 (P75 47,800; P90 75,000) | — | — |

Supporting data points:
- Mid-level median is EGP 31,666 at product companies vs 26,000 at software houses ([cvpromaker](https://www.cvpromaker.com/salaries/egypt/software-engineer)).
- Flutter developer average is **EGP 40,000** in 2026 according to [Payscale](https://www.payscale.com/research/EG/Job=Flutter_Developer/Salary). Payscale's percentiles contain obvious data errors, so treat this as indicative only.
- Backend developers: the middle 80% earn EGP 6,998–34,634 gross per month ([Paylab](https://paylab.com/eg/salaryinfo/information-technology/backend-developer)). The data is older, lags inflation, and is a floor.
- Android developers: the middle 80% earn EGP 8,005–36,567 gross ([Paylab](https://paylab.com/eg/salaryinfo/information-technology/android-developer)).
- UI/UX designers: a 2–5-year role is listed at EGP 20,000–40,000 per month, and a senior (4–7 yrs) role at EGP 400–750k per year ([designproject](https://designproject.io/jobs/jobs/uxui-designer-at-ahoy-ag0bbj), [designproject senior](https://designproject.io/jobs/jobs/senior-ux-ui-designer-at-adree-79vnro)). Paylab's average is EGP 23,139 ([Paylab UX](https://www.paylab.com/eg/salaryinfo/information-technology/ux-designer)).
- Product managers: **no reliable Egyptian monthly figure found.** Payscale's EGP 285,000 average is ambiguous about the period ([Payscale PM](https://www.payscale.com/research/EG/Job=Product_Manager%2C_Software/Salary/b5eb44cd/User-Experience-UX-Design)).
- QA engineers: **no reliable 2025–26 source found.** ESTIMATE below, based on mid-level engineering bands.
- Customer support and call-centre staff: entry level EGP 7,000–9,000; 1–3 years EGP 10,000–14,000 ([Wuzzuf](https://wuzzuf.net/careers/call-center-agent-salary-in-egypt/)). English-account roles in Cairo pay EGP 14,000–19,000+ ([Wuzzuf e& posting](https://wuzzuf.net/jobs/p/kapwh7urg1og-call-center-agent-english-account-b1-english-speakers-etisalat-egypt-cairo-egypt), [NAOS](https://naostalents.recruitee.com/o/voice-customer-service-agent)).

### 2.2 Planning salary table (ESTIMATE, Oct 2026, net EGP per month)

| Role | Planning net (EGP) | ≈ USD | Basis |
|---|---|---|---|
| Senior backend / tech lead (Node/NestJS or Python + Postgres) | 70,000 | $1,333 | Middle of the senior local–top-product band |
| Mid backend | 40,000 | $762 | Upper mid band (product company) |
| Mid Flutter developer | 40,000 | $762 | Payscale avg 40k; mid band 28–55k |
| Senior Flutter developer | 65,000 | $1,238 | Senior band |
| AI/LLM engineer (senior) | 70,000–90,000 | $1,333–1,714 | Senior band, scarce skill premium (ESTIMATE) |
| UI/UX designer (mid) | 30,000 | $571 | 20–40k posting |
| QA engineer (mid, manual + automation) | 22,000–28,000 | $419–533 | ESTIMATE: ~70% of developer mid |
| Product manager (mid–senior) | 50,000–80,000 | $952–1,524 | ESTIMATE; founder may fill this role |
| DevOps (part-time / contract) | 20,000 | $381 | ESTIMATE |
| Customer support agent (Arabic) | 10,000–12,000 | $190–229 | Wuzzuf ranges |
| Community / field ops (building onboarding, "سفير العمارة") | 9,000–12,000 + bonus per onboarded building | $170–230 | ESTIMATE, at call-centre parity |

**Loaded-cost multiplier (ESTIMATE): ×1.30–1.40 on net pay.** This covers gross-up for income tax, the employer's social-insurance share (about 18.75% of the insured wage under Law 148/2019, subject to the cap; verify with an accountant), medical insurance, laptops, and a co-working seat. Many Egyptian startups hire early staff as contractors to reduce this, but that carries legal risk.

### 2.3 Three build options compared (ESTIMATE)

**Scope assumed for the MVP:**
- Resident app (iOS and Android)
- Building and compound admin dashboard (web)
- Backend with payments
- Notification engine
- AI layer: chat, OCR of receipts and bills, voice notes
- WhatsApp integration
- Basic service-request marketplace

| Option | Team / vendor | Monthly burn | 6-month MVP cost | Pros | Cons |
|---|---|---|---|---|---|
| **A. Lean in-house (recommended for zero-marketing bootstrap)** | Founder as PM, 1 senior full-stack (Supabase/Postgres + Flutter), 1 mid Flutter, 1 mid backend/AI, designer at 50% for 4 months, QA from month 3 | Net ≈ 70k + 40k + 50k + 15k + 22k ≈ EGP 197k → loaded ≈ **EGP 265k ≈ $5,000** | **≈ $30k** (EGP 1.6M) | Cheapest, owns IP, fast iteration | Key-person risk; slower AI work |
| **B. Full in-house product team** | 2 Flutter (mid), 1 senior backend, 1 mid backend, 1 AI engineer, 1 designer, 1 QA | Net ≈ 80k + 70k + 40k + 80k + 30k + 25k = EGP 325k → loaded ≈ **EGP 440k ≈ $8,400** | **≈ $50k** (EGP 2.6M) | Can ship AI, bot and marketplace in parallel | Needs hiring time (4–8 weeks) |
| **C. Egyptian agency** | ~4,500 hours (resident app 1,200h, admin web 600h, backend + payments 900h, WhatsApp/AI 700h, design 400h, QA/PM 700h) | n/a | **$112k at $25/h; $166k at $37/h median; $225k at $50/h** | Predictable delivery | 2–4× cost; weak ownership of product thinking; change requests are expensive; you still need a team afterwards |
| **D. Freelancers (Khamsat/Mostaql)** | Gig pricing "from $5–50" is not representative of a full product | — | Not estimable | Cheap for small pieces | Not viable for a platform of this scope ([Khamsat example](https://khamsat.com/user/mahmoudahmed_eg/services)) |

The agency hourly rates come from [GoodFirms](https://www.goodfirms.co/directory/country/app-development/egypt): $37/h median across 161 verified firms, top firm <$25/h. Abbacus gives seniority bands of $10–25 junior, $25–50 mid and $50–90 senior ([Abbacus](https://www.abbacustechnologies.com/?p=50038)). For a global comparison, Business of Apps puts a simple app at $16–32k ([Zoho citing Business of Apps](https://www.zoho.com/creator/decode/creator/decode/the-cost-of-app-development)).

**Recommendation:** Start with Option A for months 0–6 and move to Option B once traction is proven, around 50+ active buildings. Use contractors (designer, DevOps) for spiky needs. Keep the AI and WhatsApp core in-house because it is the moat.

### 2.4 Post-launch operations staffing (ESTIMATE)

| Stage | Active buildings | Support / ops headcount | Monthly cost (loaded) |
|---|---|---|---|
| Pilot | ≤100 | Founder + 1 community/ops person | EGP 15k (~$290) |
| Growth | 1,000 | 2 support (AI handles about 70% of tickets), 2 field "building ambassadors" | EGP 60–70k (~$1.2–1.3k) |
| Scale | 10,000 | 8 support, 6 ops, 1 support lead; marketplace QA/disputes team of 3 | EGP 250–300k (~$5–6k) |

Reasoning: AI-first support (an LLM triages app chat and WhatsApp) should keep the ratio near **1 agent per 25–40k MAU** for a low-ticket utility app. Marketplace disputes are the main driver of headcount.

---

## 3. Tech stack and unit costs of each building block

### 3.1 Recommended stack (cost-optimised for Egypt)

| Layer | Recommendation | Why (cost angle) |
|---|---|---|
| Mobile | **Flutter** (one codebase for iOS and Android, strong RTL/Arabic support) | Large Egyptian Flutter talent pool; Payscale lists Flutter as a distinct role at about EGP 40k |
| Backend | **Supabase (Postgres + Auth + Realtime + Storage)** early on, then self-host Postgres and a NestJS/FastAPI service layer at 500k+ MAU | Pro plan $25/org with 100k auth MAU included, 250 GB egress, 8 GB DB per project, plus per-project compute (Micro $10, Small $15, Medium $60) ([makerkit](https://makerkit.dev/blog/saas/supabase-pricing), [jetadmin](https://www.jetadmin.io/blog/supabase-pricing-2026-guide-to-plans-limits-and-real-world-costs/)) |
| Push notifications | **Firebase Cloud Messaging (FCM)** | **No cost at any scale** ([Firebase pricing plans](https://firebase.google.cn/docs/projects/billing/firebase-pricing-plans?hl=en)) |
| OTP / login | **WhatsApp authentication template** as primary, local SMS aggregator as fallback, Google/Apple sign-in as a free option | See §3.2 |
| AI | Router: **Gemini 2.5 Flash-Lite** for bulk classification and extraction; **Gemini 2.5 Flash / Claude Haiku 4.5** for reasoning and Arabic chat; **gpt-4o-mini-transcribe** for voice notes | See §3.4 |
| Maps | Native Google Maps SDK in-app plus **OpenStreetMap/Mapbox** fallback; geocode only at building creation (once per building) | 10,000 free billable events per SKU per month for Essentials since Mar 2025 ([Google Maps Mar 2025](https://developers.google.com/maps/billing-and-pricing/march-2025), [FAQ](https://developers.google.com/maps/billing-and-pricing/faq)) |
| Payments | **Paymob** (cards, wallets, ValU and others) plus **Kashier** as backup; InstaPay deep links for peer-to-peer dues | §3.5 |
| Hosting (if self-hosted later) | EU region (Frankfurt) on AWS/GCP, or Hetzner where available | Hetzner raised CPX/CCX prices 2.2–2.75× in June 2026 and CX by 30–40%, and cost-optimised plans are often unavailable ([Northflank](https://northflank.com/blog/hetzner-cloud-server-price-increases), [heise](https://heise.de/-11333037)), so "cheap VPS" assumptions from 2024 no longer hold |

### 3.2 OTP and SMS: the biggest avoidable cost

| Channel | Price per message to Egypt | Cost for 1M sign-ups × 1.3 OTP attempts | Source |
|---|---|---|---|
| Twilio SMS (alphanumeric/international route) | **$0.3959** | **$514,670** | [Twilio Egypt](https://www.twilio.com/en-us/sms/pricing/eg) |
| Quo (range) | $0.17–0.32 | $221k–416k | [Quo](https://www.quo.com/rate/egypt) |
| MoceanAPI (local registered company) | $0.05 (~EGP 2.79) | $65,000 | [MoceanAPI Egypt](https://egypt.moceanapi.com/) |
| D7 Networks (local route) | $0.015 | $19,500 | [D7](https://d7networks.com/sms/egypt/) |
| Carrier-direct (needs 100k+/month commitment) | EGP 0.05–0.10 (~$0.001–0.002) | ~$1,300–2,600 | [sent.dm guide](https://www.sent.dm/en/resources/sms-pricing/egypt-sms-pricing) (secondary estimate) |
| Firebase Phone Auth | Varies by country; "$0.06 other countries" in third-party tables, and some report up to $0.46 | $78k+ | [supertokens](https://supertokens.com/blog/firebase-pricing), [Logto](https://blog.logto.io/de/firebase-authentication-pricing) |
| **WhatsApp authentication template** | **$0.0036** (+14% VAT); volume tiers down to $0.0027 | **$4,680** | [ChatMaxima](https://chatmaxima.com/whatsapp-api-pricing/egypt/) |

**Decision:**
1. Make **WhatsApp OTP** the default. Almost every Egyptian smartphone user has WhatsApp. It is about 110× cheaper than Twilio SMS.
2. Use a **local SMS aggregator** (Cequens, Victory Link or similar; published rates were not found, so get quotes) only as a fallback for users without WhatsApp.
3. Offer **Google and Apple sign-in** (free).
4. Use a **long-lived session** (refresh tokens) so users re-OTP rarely.

### 3.3 WhatsApp Business Platform: real costs and hard constraints

**Pricing (Egypt, from 1 Oct 2026; billed in USD, plus 14% VAT):**

| Category | Rate | Notes |
|---|---|---|
| Marketing template | $0.0644 (~EGP 3.4) | Not volume-tiered. **Never use this for invites.** |
| Utility template | $0.0036 (~EGP 0.19) | Free inside an open 24-hour customer-service window; volume tiers 5–25% off, down to $0.0027 |
| Authentication | $0.0036 | Same tiers |
| Authentication-international | $0.0650 | Applies if the sender is registered abroad |
| **Service (free-form replies)** | **First 1,000 per number per month free, then $0.0036** | **New from 1 Oct 2026.** Confirmed by multiple vendors/press (ChatMaxima, respond.io, YCloud, Oman Observer); the Meta pricing page fetched on 12 Oct 2026 did not yet show the 1,000 threshold — re-check Meta's rate card. Allowance does not roll over and is per phone number. A payment method is required in Billing Hub or delivery stops after 1,000. |

Sources: [ChatMaxima Egypt](https://chatmaxima.com/whatsapp-api-pricing/egypt/), [ArabyBot Egypt](https://arabybot.com/guides/whatsapp-api-pricing-egypt?lang=en), [Meta pricing docs](https://developers.facebook.com/documentation/business-messaging/whatsapp/pricing) (per-message pricing since 1 Jul 2025; Egypt utility and auth rates cut on 1 Oct 2025, marketing cut on 1 Jan 2026). One aggregator ([Ominiflow](https://ominiflow.com/whatsapp-api-pricing/egypt)) shows a higher, older-looking card (marketing $0.1073). **Confirm against Meta's official rate-card CSV before budgeting.**

**Hard constraints that reshape the founder's "WhatsApp bot joins the building group" idea:**
1. **Groups API cap.** Official Cloud API groups are capped at **8 participants including the business number**. The business **cannot add people**; they join by invite link and need approval. There is no history endpoint (webhooks only). Group messages are billed at the same per-message rates. Only Official Business Accounts qualify, and groups are unavailable on WhatsApp Business *app* numbers and on numbers onboarded to Multi-solution Conversations. Cap of 10,000 groups per business number. **Confirmed against Meta's own docs** ([Meta Groups API](https://developers.facebook.com/documentation/business-messaging/whatsapp/groups), [Unipile](https://www.unipile.com/whatsapp-group-api/)). A typical Egyptian building group has 20–200 members, so **an official bot cannot be a member of the existing building group.**
2. **Unofficial "linked-device" bots.** These use a personal number via QR (whatsapp-web style libraries, or vendors such as Unipile). They *can* sit in big groups, but they run on a consumer account and **risk the number being banned**, with no SLA. It is acceptable as an experiment, but it must not be the core of the product.
3. **AI policy.** Since **15 Jan 2026**, Meta bars *general-purpose* AI chatbots (ChatGPT-style assistants as the core product) from the Business API. Task-specific business bots for bookings, support and order tracking remain allowed ([Gulf News](https://gulfnews.com/technology/no-more-chatgpt-and-perplexity-on-whatsapp-meta-bans-major-ai-chatbots-from-2026-1.500316016), [respond.io](https://respond.io/blog/whatsapp-chatbot-policy-2026)). Meta also introduced a separate "AI Providers" pricing policy effective 16 Feb 2026 ([Meta pricing docs](https://developers.facebook.com/documentation/business-messaging/whatsapp/pricing)). **A building-services assistant must be scoped as a task bot** (dues, maintenance tickets, bookings, announcements), not "ask me anything".

**Cost model for the WhatsApp assistant (ESTIMATE):**
- Assumption: a building with 30 households where about 40% interact. That gives roughly 600 bot messages per building per month: replies, reminders and receipts.
- Service messages beyond the free 1,000 per month cost $0.0036 each.

| Active buildings | Bot messages / month | Billable (after 1,000 free on one number) | WhatsApp cost / month |
|---|---|---|---|
| 100 | 60,000 | 59,000 | ~$212 (+VAT) |
| 1,000 | 600,000 | 599,000 | ~$2,160 |
| 10,000 | 6,000,000 | 5,999,000 | ~$21,600 |

**Cost per building ≈ $2.2/month (≈ EGP 115).** That is a large share of what a building would pay Saknna (EGP 450 for 5 units). So:
1. Make the **app plus free FCM push the primary channel.**
2. Use WhatsApp for **high-value moments**: OTP, dues reminders as utility templates (which are free inside an open window), and bookings.
3. Treat the full WhatsApp assistant as a **premium feature for compounds and paid buildings**, or fund it from marketplace commissions.

**Invites and virality cost nothing if done right.** Use the **phone's native share sheet** ("ادعُ جيرانك" → opens the user's own WhatsApp with a deep link into the building's group). These messages are sent by the user, not by your business number, so Meta charges nothing. Business-sent invites would be *marketing* templates at $0.0644 each: 1M invites = $64k.

### 3.4 LLM and AI costs (mandatory AI layer)

| Model | Input $/1M tokens | Output $/1M tokens | Source |
|---|---|---|---|
| Gemini 2.5 Flash-Lite | $0.10 (audio $0.30 [corrected], per Google's official pricing page) | $0.40 | [Google official pricing](https://ai.google.dev/gemini-api/docs/pricing), [modelcompare](https://modelcompare.dev/models/google/gemini-2-5-flash-lite), [SD Times](https://sdtimes.com/ai/gemini-2-5-pro-and-flash-are-generally-available-and-gemini-2-5-flash-lite-preview-is-announced/) |
| Gemini 2.5 Flash | $0.30 (audio $1.00) | $2.50 | [cloudprice](https://cloudprice.net/models/openrouter/google/gemini-2.5-flash), [SD Times](https://sdtimes.com/ai/gemini-2-5-pro-and-flash-are-generally-available-and-gemini-2-5-flash-lite-preview-is-announced/) |
| Claude Haiku 4.5 | $1.00 (cache read $0.10) | $5.00 | [pricepertoken](https://pricepertoken.com/pricing-page/model/anthropic-claude-haiku-4.5) |
| gpt-4o-mini-transcribe (speech-to-text) | $0.003 per audio minute | — | [diyai](https://diyai.io/ai-tools/speech-to-text/openai-whisper-api-pricing-2026/) |
| gpt-4o-transcribe / whisper-1 | $0.006 per minute | — | same |

Batch APIs are typically 50% cheaper for non-urgent jobs, such as nightly summaries of building activity ([secondary tracker](https://www.morphllm.com/gemini-api-pricing)). Verify all prices on the vendors' official pages before contracting.

**Cost per AI action (ESTIMATE; 1,500 input tokens of context + prompt, 300 output tokens):**

| Action | Model | Cost per action |
|---|---|---|
| Classify a WhatsApp or app message into an intent (complaint, dues, booking) | Flash-Lite | $0.00015 + $0.00012 = **$0.00027** |
| Extract fields from a photo of an electricity bill or receipt (≈1,300 image tokens) | Flash-Lite | ≈ $0.0003 |
| Arabic conversational answer with tools | Gemini Flash | $0.00045 + $0.00075 = **$0.0012** |
| Same answer on Claude Haiku 4.5 | Haiku | $0.0015 + $0.0015 = **$0.003** |
| 30-second Egyptian-Arabic voice note → text | gpt-4o-mini-transcribe | $0.0015 |
| Monthly AI digest per building (batch) | Flash, batch | ≈ $0.002 |

**AI cost per active user (ESTIMATE):** About 30 AI actions per MAU per month, roughly 70% on Flash-Lite and 30% on Flash. That works out to **≈ $0.015 per MAU per month**: about $150/month at 10k MAU, $1.5k at 100k and $15k at 1M. With intent caching, on-device templates and summarising instead of re-reading history, the target is **≤ $0.01/MAU/month**.

**Design rule:** Use a model router (cheap model first, escalate on low confidence). Cache the building context, which is reused across messages. Never send whole group histories. Send only the rolling summary and the last N messages.

### 3.5 Payment gateway economics

| Provider | Published merchant fee | Settlement | Notes / source |
|---|---|---|---|
| **Paymob** | **2.75% + EGP 3** per successful transaction; no setup or monthly fee; enterprise custom pricing | Weekly | [Paymob pricing](https://paymob.com/en/pricing), [online payment](https://paymob.com/en/online-payment). 50+ methods incl. wallets, cards, BNPL, QR; 350k+ merchants ([TechCrunch](https://techcrunch.com/2024/09/11/paymob-lands-another-22-million-and-is-profitable-in-egypt)). Per-method rates not published. |
| **Kashier** | **2.85% + EGP 3** **[unverified]** — the only matching source is a ~2020–21 KR-Asia article; paymentproviders.io lists 2.75%; kashier.io was unreachable on 12 Oct 2026; no setup or monthly fee | — | [Kashier FAQ](https://kashier.io/en/faqs), [KR-Asia](https://kr-asia.com/egyptian-payments-platform-kashier-raises-six-figure-seed). The FAQ says it currently supports cards only (may be outdated; Shopify listing mentions wallets and ValU). |
| **Fawry** | **Not publicly published**; set per merchant agreement | — | No official schedule found ([paymentproviders](https://paymentproviders.io/country/eg)) |
| **Geidea** | **Not found publicly** | — | Geidea docs show ValU integration with upfront merchant payment ([Geidea docs](https://docs.geidea.net/docs/valu)) |
| **InstaPay (IPN)** | Consumer transfer fee 0.1%, min EGP 0.50 (Egypt Today reported EGP 1; most outlets say EGP 0.50), max EGP 20 (since 1 Apr 2025); merchant/collection pricing **not found** | Instant | [Business Today Egypt](https://www.businesstodayegypt.com/amp/1/6185/InstaPay-to-Introduce-New-Fee-Structure-Starting-April-2025), [Egyptian Streets](https://egyptianstreets.com/2025/04/03/instapay-now-charging-transfer-fees). InstaPay became profitable a year after fees started ([Zawya](https://www.zawya.com/en/economy/north-africa/egypt-instapay-turns-profitable-a-year-after-transfer-fee-rollout-rt18pyrt)). |

**What it costs to collect a typical maintenance-dues payment (ESTIMATE, EGP 600 dues):**

| Rail | Fee | Effective % |
|---|---|---|
| Paymob card or wallet | 600 × 2.75% + 3 = **EGP 19.5** | 3.25% |
| Kashier card | 600 × 2.85% + 3 = **EGP 20.1** | 3.35% |
| InstaPay P2P to the building treasurer (resident pays) | 0.1% → **EGP 0.60** | 0.1% |

**Implication:** For pure dues collection, cards and gateways cost more than 30× InstaPay. The winning UX in Egypt is:
1. An **InstaPay / wallet deep link with an auto-generated reference.**
2. **AI reconciliation:** the resident uploads a screenshot of the transfer, and the model extracts amount, date and reference and marks the dues paid. This is a strong, cheap AI use case at about $0.0003 per check.
3. Use Paymob only for card users, and pass the fee on as a visible "convenience fee".

This gives you all the payment data (gold for phase 2) **without holding money**.

**Regulation on holding money:**
- The CBE's new licensing rules for payment service providers have been in force since **17 June 2025**, with a **12-month transition** for existing operators. They cover payment execution, payment initiation, account information and more, and set capital and guarantee requirements ([Business Today Egypt](https://www.businesstodayegypt.com/amp/1/6465/Central-Bank-of-Egypt-issues-new-licensing-rules-for-payment), [Baker McKenzie](https://insightplus.bakermckenzie.com/bm/banking-finance_1/egypt-new-regulation-on-payment-solutions), [LaunchBase Africa](https://launchbaseafrica.com/2025/06/19/egypts-fintech-firms-given-12-months-to-get-licensed-or-shut-down/)).
- The older 2019 facilitator regime required a separate account and operation on behalf of a bank ([IBA](https://www.ibanet.org/article/6FC3317B-4F9C-4DFC-BDF1-80CF98B68B21)).
- **Conclusion: do not pool residents' money or earn float yourself.** Use Paymob or another licensed PSP's split and marketplace features, so funds settle directly to the building's or technician's account and your commission is deducted at source.
- **Payment float and interchange economics:** I could not find published Egyptian interchange or float-sharing terms. They are negotiated privately between PSPs and banks. Treat float as **zero** in the business plan.

### 3.6 App stores, maps and other fixed costs

| Item | Cost | Source |
|---|---|---|
| Google Play developer account | $25 one-time | [splitmetrics](https://splitmetrics.com/blog/google-play-apple-app-store-fees/) |
| Apple Developer Program | $99/year | same |
| Store commission on digital goods and subscriptions | 15% (Apple Small Business Program up to $1M; Google 15% on subscriptions) | [appbot](https://appbot.co/blog/app-developers-apple-google-small-business-programs/), [RevenueCat](https://revenuecat.com/blog/engineering/small-business-program) |
| Store commission on **physical services** (plumber, cleaning, maintenance dues) | **0%**: the stores' IAP rules cover digital goods; physical goods and services can use your own payment gateway | Apple/Google IAP rules ([UK CMA appendix](https://assets.publishing.service.gov.uk/media/62a0d1b68fa8f5039b2078e5/Appendix_H_-_In-app_purchase_rules_in_Apples_and_Googles_app_stores.pdf)) |
| Google Maps Platform | 10k free billable events per Essentials SKU per month; 5k Pro; 1k Enterprise; Map Tiles 100k free | [Google FAQ](https://developers.google.com/maps/billing-and-pricing/faq) |

**Design note:** Monetize through **services, not digital subscriptions sold inside iOS**, which avoids the 15–30% store cut. If you sell a "Premium building" plan, sell it to the **building admin or compound on the web dashboard**, B2B, invoiced, and paid via Paymob or InstaPay.

### 3.7 Company setup, legal, tax, accounting, data protection

| Item | Finding | Source |
|---|---|---|
| Company formation (LLC / single-person company via GAFI) | **No official 2025/26 fee table found.** Process: name reservation, then legal form, then GAFI registration | [thelawsa](https://thelawsa.com/%D8%A7%D8%AC%D8%B1%D8%A7%D8%A1%D8%A7%D8%AA-%D8%A7%D9%86%D8%B4%D8%A7%D8%A1-%D8%B4%D8%B1%D9%83%D8%A9-%D9%81%D9%8A-%D9%85%D8%B5%D8%B1/), [sadanykhalifa](https://sadanykhalifa.com/ar/single-blog/423) |
| ESTIMATE formation budget | **EGP 25,000–60,000** all-in (government fees + lawyer + commercial register + tax card), based on typical lawyer packages; get 3 quotes | ESTIMATE |
| Small-business tax regime (Law 6 of 2025) | For turnover ≤ EGP 20M: tax on revenue at about 0.4% (≤ EGP 500k) up to about 1–1.5% (EGP 10–20M), sources conflict on the top rate; exemptions from stamp, registration and development fees; capital-gains and dividend-withholding exemptions | [EY](https://www.ey.com/en_gl/technical/tax-alerts/egypt-introduces-tax-incentives-and-benefits-for-small-enterprises), [Beancount guide](https://beancount.io/blog/2026/07/26/egypt-law-6-2025-sme-simplified-tax-regime-guide), [Andersen](https://eg.andersen.com/ar/egypts-new-tax-reform-2025/), [Egyptian Streets](https://egyptianstreets.com/2025/06/02/egypt-launches-new-tax-incentives-to-boost-investment-and-support-small-businesses/) |
| VAT | 14% (applied, for example, on WhatsApp invoices to Egyptian businesses) | [ChatMaxima](https://chatmaxima.com/whatsapp-api-pricing/egypt/) |
| Accounting (outsourced) | ESTIMATE EGP 3,000–8,000/month for a small startup (monthly bookkeeping, VAT and tax filings) | ESTIMATE; no published benchmark found |
| **Personal Data Protection Law 151/2020 + Exec. Regs (Decree 816/2025)** | Licence or permit required for controllers and processors. **Annual fees tiered by number of records: 1–100,000 records exempt; rising to a maximum of EGP 666,666 above 5M records.** Separate licences for direct electronic marketing, cross-border transfer and visual surveillance. In force Nov 2025, with full enforcement from **31 Oct 2026** per Clyde & Co. | [Digital Policy Alert](https://digitalpolicyalert.org/event/36521-executive-regulations-of-the-personal-data-protection-law-decision-no-816-of-2025-including-operational-license-requirement-entered-into-force), [Tamimi](https://www.tamimi.com/law_update_articles/from-policy-to-practice-egypt-issues-executive-regulations-of-the-personal-data-protection-law/), [Clyde & Co](https://www.clydeco.com/en/insights/2026/01/egypt-regulatory-update-on-data-privacy) |

**PDPL is directly relevant to this app:**
- It holds names, phones, unit numbers, payment history and possibly **gate/visitor camera images** (visual surveillance licence).
- It will **pass 100k records quickly**, so budget for the licence fee.
- It will send **marketing** to residents in phase 2, which needs the direct electronic marketing licence.
- Hosting on EU or US cloud is a **cross-border transfer**.

Budget **EGP 50–150k in year 1** (ESTIMATE) for a privacy lawyer, a DPO function (can be outsourced) and licence fees. Fees then scale with records.

---

## 4. Infrastructure cost model at 10k / 100k / 1M MAU (ESTIMATE)

**Assumptions:**
- 30 AI actions per MAU per month.
- New sign-ups each month equal 20% of MAU during growth, with 1.3 OTP sends each via WhatsApp.
- 30 households per building, with 600 WhatsApp bot messages per active building per month.
- Average 4 MB of uploads per MAU per month (receipts, photos).
- Push via FCM.

| Line item (USD/month) | 10k MAU (~330 bldgs) | 100k MAU (~3,300 bldgs) | 1M MAU (~33k bldgs) | Notes |
|---|---|---|---|---|
| Backend DB + API (Supabase Pro + compute → self-managed Postgres at scale) | 50–100 | 400–1,200 | 4,000–12,000 | 50k–200k MAU apps typically run $100–200 on Supabase ([makerkit](https://makerkit.dev/blog/saas/supabase-pricing)); large scale adds read replicas, queue workers |
| Object storage + CDN/egress | 10–30 | 100–300 | 1,000–3,000 | Egress $0.09/GB above 250 GB on Supabase |
| Push (FCM) | 0 | 0 | 0 | Free |
| OTP via WhatsApp auth | ~10 | ~95 | ~940 | 0.2 × MAU × 1.3 × $0.0036 |
| WhatsApp bot (service messages) — **if enabled for all buildings** | ~710 | ~7,100 | ~71,000 | **Danger line.** Cap it or make it premium; at 10% of buildings → 71 / 710 / 7,100 |
| WhatsApp bot — **premium-only, 10% of buildings** (recommended) | ~70 | ~710 | ~7,100 | |
| LLM (≈ $0.01–0.015/MAU) | 100–150 | 1,000–1,500 | 10,000–15,000 | §3.4 |
| Speech-to-text (voice notes, 2 min/MAU) | 60 | 600 | 6,000 | $0.003/min; reduce by transcribing on demand only |
| Maps | 0 | 0–100 | 100–500 | Geocode once per building |
| Monitoring, logging, error tracking, email | 0–50 | 150–400 | 1,000–3,000 | Free tiers early |
| SMS fallback (5% of OTPs via local aggregator at $0.015) | ~2 | ~20 | ~200 | |
| **Total (bot premium-only)** | **≈ $300–480** | **≈ $3,100–5,000** | **≈ $30,000–48,000** | |
| **Per MAU** | $0.03–0.05 | $0.03–0.05 | $0.03–0.05 | |
| In EGP | ≈ 16–25k | ≈ 160–260k | ≈ 1.6–2.5M | at 52.5 |

**Key takeaway:** Infrastructure is cheap (about $0.04/MAU/month) **as long as WhatsApp is not the primary messaging channel.** If every building gets the full WhatsApp assistant, infrastructure cost roughly doubles or triples.

---

## 5. What the founder's four ideas cost

| Idea | Feasibility | One-time build (ESTIMATE) | Running cost (ESTIMATE) | Cost-side recommendation |
|---|---|---|---|---|
| **1. Personalised notification system** | High | 6–8 developer-weeks (rules engine, per-user preferences, quiet hours, AI priority scoring) | FCM free; in-app inbox ~0 | Push first, WhatsApp utility template only for critical items (water cut, dues overdue), at $0.0036 each |
| **2. Mandatory AI everywhere** (data entry, OCR of bills and receipts, voice notes, auto-categorising complaints, auto-minutes of union meetings, translation) | High | 10–14 developer-weeks for the first 6 AI features | ≈ $0.01–0.02 per MAU per month | Router + caching; Flash-Lite for most calls; batch digests overnight |
| **3. WhatsApp bot that "joins the building group"** | **Official API: not possible for groups over 8 people.** Unofficial linked-device bot: possible but ban-prone | Official 1:1 bot: 6–8 weeks. Unofficial group bot: 4–6 weeks plus ongoing anti-ban maintenance | Official: ~$2.2/building/month at 600 messages. Unofficial: ~$0 messaging but account risk | **Redesign:** (a) bot is a **1:1 assistant** each resident can message ("ابعت للمساعد"); (b) **official small "committee group"** (≤7 humans: treasurer, union head, doorman/بواب) where the bot is a member; (c) a **"forward to bot"** flow: a resident forwards a message from the big group to the bot, which acts on it; (d) bot posts summaries that admins paste into the big group with one tap |
| **4. Every resident has an account** | High | Included in core | Auth: free up to 100k MAU on Supabase Pro; WhatsApp OTP $0.0036 | Allow "household account + members" to reduce friction; Google/Apple sign-in free |

---

## 6. Monetization benchmarks

### 6.1 Global and regional comparables

| Company | Market | Model | Key numbers | Source |
|---|---|---|---|---|
| **Urban Company** | India, UAE, KSA, Singapore | Home-services marketplace: commission + platform fees from professionals, customer convenience fee, membership, product sales to pros | FY25 revenue ₹1,144 Cr (+38%), first profitable year [corrected: reported ₹240 Cr net profit was driven mainly by a ₹211 Cr deferred-tax credit; pre-tax profit ≈ ₹28 Cr, adj. EBITDA ≈ ₹11 Cr]; platform services ₹742 Cr = 64.8% of revenue; NTV ≈ ₹3,115–3,271 Cr → **implied take ≈ 23–24%**; commissions + fees = **28.3% of professionals' gross earnings** (9M FY26); S&P expects take rate held at **22–23%** | [Entrackr](https://entrackr.com/fintrackr/urban-company-posts-rs-1144-cr-revenue-and-rs-285-cr-pbt-in-fy25-9373371), [Inc42](https://inc42.com/?p=571319), [S&P Global](https://www.spglobal.com/market-intelligence/en/news-insights/research/2026/04/urban-company-revenue-to-triple-by-2030-as-take-rates-and-platform-monetization-rise) |
| **MyGate** | India (gated communities) | SaaS to societies + **advertising** + smart-home hardware | FY24 revenue ₹96.2 Cr; FY25 ₹173.5 Cr (+80%), net loss ₹15.4 Cr, adj. EBITDA breakeven; FY26 claimed ₹232 Cr [unverified]; ~5M homes; **65–70% of income from ads**; often low-cost or **free** plans to win societies | [Inc42](https://inc42.com/buzz/mygate-trims-fy25-loss-by-61-to-₹15-4-cr/), [BW Disrupt](https://bwdisrupt.com/article/mygate-crosses-rs-100-cr-revenue-and-achieves-35-operating-revenue-growth-with-82-reduction-in-losses-538480) |
| **MyGate, per home (ESTIMATE)** | | | ₹173.5 Cr / 5M ≈ **₹350/home/year (~$4)**; ads ≈ ₹225–245/home/yr | Derived from Inc42 |
| **NoBrokerHood** | India | Society app used as a **free funnel** for NoBroker's paid services (rent agreements, movers, loans, home services) | NoBroker FY24 op. revenue ₹803 Cr, 99% from subscription plans (parent level); NoBrokerHood not broken out. An older The Ken report cited about ₹10/apartment/month for NoBrokerHood | [markhub24 citing Entrackr](https://www.markhub24.com/post/nobroker-s-direct-property-listing-without-brokerage-model), [Inc42](https://inc42.com/features/nobrokers-future-is-beyond-home-listings-but-will-profits-follow/), [The Ken](https://the-ken.com/story/gate-secured-mygate-now-wants-to-monetise-community/) |
| **Saknna (سَكَنة)** | Egypt + 7 Arab countries | Tiered SaaS per building | EGP 450/mo (≤5 units), 900 (≤10), 2,200 (≤20), 7,500 (multi-building compound); 14-day trial; annual = 2 months free; Egyptian payment via InstaPay, Vodafone Cash, bank transfer; claims 500+ buildings | [saknna.com](https://saknna.com) |
| **ManageCasa** | US HOA | Per-unit SaaS | From $1/unit/month | [ManageCasa](https://managecasa.com/hoa-sales-campaign) |
| **Aldea HQ / category average** | US | Flat SaaS | $49/month flat; category average $47/month | [Capterra](https://www.capterra.com/p/10037220/Aldea-HQ/), [SaaSworthy](https://www.saasworthy.com/product/thehousemonk/pricing) |
| **Daarna (دارنا)** | KSA (owners associations / اتحاد الملاك) | Free app | No price shown | [AppGoblin](https://appgoblin.info/apps/6759947745) |
| **FilKhedma** | Egypt home services | Marketplace; acquired by SweepSouth (South Africa) | Commission rate **not disclosed**; founder once sized Cairo household maintenance at $225–338M (2016) | [Cairo Scene](https://cairoscene.com/Business/Egyptian-Home-Services-App-Filkhedma-Acquired-by-South-African-Giant), [Enterprise](https://enterprise.press/?p=6037) |
| **Egyptian maintenance apps** (Fanni Almanarat, Ninja Home, حسن) | Egypt | Booking / bidding marketplaces | **No public commission data found** | [App Store: Ninja Home](https://apps.apple.com/us/app/id6496852097), [Hassan](https://apps.apple.com/app/id1614449416) |

**Notes:**
- Amarati (com.amarati.app) and Imarti (com.craftfuture.imarti): the Play Store pages could not be fully scraped in this session, and I did **not** find published pricing for either. Other research files should hold their listing data.
- **Egyptian per-unit SaaS benchmark:** Saknna's EGP 450 for 5 units is about **EGP 90/unit/month (~$1.7)**. That is in line with ManageCasa's US $1/unit, so Egyptian building admins do pay for management software. For the founder's free-first strategy, this is the **ceiling** price that a premium tier can be anchored against.

### 6.2 BNPL / consumer-finance partnerships

| Data point | Value | Source |
|---|---|---|
| valU H1 2025 gross revenue | EGP 2.6B; BNPL ≈ 60% of GMV; 3.59M transactions (+133%); market share 25%; loan book EGP 11.4B | [Techpoint Africa](https://techpoint.africa/news/egyptian-fintech-valu-h1-results/) |
| FRA consumer finance (Jan–Sep 2025) | EGP 66B | [Amwal Al Ghad](https://en.amwalalghad.com/?p=222883) |
| Egypt BNPL payment market 2025 (forecast) | US$1.67B (+32.7%) | [BusinessWire / ResearchAndMarkets](https://www.businesswire.com/news/home/20250305099643/en/Egypt-Buy-Now-Pay-Later-Business-and-Investment-Report-2025) |
| Egypt instalment customers | ~10M ("Africa's most fought-over fintech asset") | [LaunchBase Africa](https://launchbaseafrica.com/2026/01/15/why-egypts-10m-instalment-customers-have-become-africas-most-fought-over-fintech-asset/) |
| Merchant economics | Merchant receives the full amount upfront; **merchant discount rate not public** | [Geidea docs](https://docs.geidea.net/docs/valu) |

**How to use BNPL here:**
- Accept valU, Souhoola, Contact, Halan and Aman through Paymob checkout for **big-ticket jobs**: AC installation, kitchen or bathroom renovation, water-tank or pump replacement, and building-level elevator modernisation or façade painting financed by the union (اتحاد الشاغلين).
- Higher order values mean higher absolute commission.
- **Referral or partner fees from BNPL providers** are possible but are negotiated privately and not published. **Model them as upside only.**

### 6.3 Advertising and sponsored placements

- The MENA digital ad market is $8.185B (2025), and Egypt is the fastest-growing at +23.1% ([Campaign ME](https://campaignme.com/digital-ad-spend-in-mena-reaches-8b-in-2025-iab-report-reveals/)).
- **Egypt-specific AdMob eCPM / ARPU: not found** in public sources. Appodeal data is from 2021–22 and not Egypt-specific ([gamedevreports](https://gamedevreports.substack.com/p/appodeal-performance-index-2022)).
- **Do not use programmatic banner ads.** MyGate's model is **direct hyper-local sponsorship**: brands pay to reach verified residents of specific compounds. In Egypt this could be supermarkets, pharmacies, ISPs (WE, Vodafone fibre), gas and electricity smart-meter top-ups, water filters, pest control, insurance and real-estate developers. **ESTIMATE:** $0.5–1.5 per active household per year in Egypt, versus about $2.6–2.8 for MyGate in India. Reasoning: lower purchasing power, but highly targetable compound audiences.

---

## 7. Phase-2 revenue model and scenarios (ESTIMATE)

### 7.1 Revenue lines (ranked by fit with the "free first, intermediary later" strategy)

| # | Revenue line | Who pays | Pricing (ESTIMATE, anchored on benchmarks) | Fit |
|---|---|---|---|---|
| 1 | **Home-services marketplace** (plumber سباك, electrician كهربائي, AC, carpentry, cleaning, pest control, elevator أسانسير maintenance contracts, painting) | Technician commission + optional customer service fee | **15–20% take rate** (below Urban Company's ~23–28%; Egypt's informal market will not bear more at first) | Core |
| 2 | **Building / compound "Pro" SaaS** (advanced accounting, auto-reminders via WhatsApp, AI assistant, audits, multi-building) | Union / developer / facility manager | **EGP 25–50 per unit per month** (well under Saknna's ~EGP 90); free tier stays free forever for residents | Strong |
| 3 | **Sponsored offers and hyper-local ads** | Brands, developers, local shops | CPM / flat monthly sponsorship per compound | Strong at scale |
| 4 | **Payment convenience fee** | Resident paying by card or wallet in-app | Pass-through of PSP cost + EGP 3–5 margin; **InstaPay route free** | Small but sticky |
| 5 | **Financial and utility referrals** (BNPL, home insurance, internet, smart meters) | Partners | Negotiated referral fee | Upside |
| 6 | **B2B supply** (bulk cleaning supplies, water-tank cleaning contracts, security staffing, doorman/بواب payroll) | Unions / compounds | 5–10% margin | Later |

### 7.2 Unit economics of one marketplace order (ESTIMATE)

| Item | EGP | Basis |
|---|---|---|
| Average order value | 700 | ESTIMATE. **No reliable public Egyptian price list for plumber/electrician visits was found**; validate in the pilot |
| Take rate 18% | 126 | |
| Payment cost if paid by card through Paymob (on full order) | −22.3 | 700 × 2.75% + 3 |
| Support / dispute handling (AI-first) | −10 | ESTIMATE |
| Quality guarantee reserve (re-visit or refund) | −21 | 3% of order value, ESTIMATE |
| **Contribution per order** | **≈ 73 (~$1.4)** | |
| If the customer pays the technician in cash and the commission is debited from the technician's prepaid wallet | ≈ 95 | Avoids the PSP fee but carries collection risk |

### 7.3 Three scenarios at month 36 (ESTIMATE)

Assumptions: "Active HH" means households with at least one MAU in the month. Planning rate is 52.5 EGP/USD.

| Driver | Conservative | Base | Upside |
|---|---|---|---|
| Active households | 50,000 | 200,000 | 600,000 |
| Marketplace bookings per active HH per month | 3% | 5% | 7% |
| Average order value (EGP) | 700 | 700 | 700 |
| Take rate | 15% | 18% | 20% |
| **Marketplace revenue / month** | EGP 157.5k (**$3.0k**) | EGP 1.26M (**$24.0k**) | EGP 5.88M (**$112.0k**) |
| Units on paid compound "Pro" plans | 5,000 @ EGP 40 | 30,000 @ EGP 40 | 100,000 @ EGP 40 |
| **SaaS revenue / month** | EGP 200k (**$3.8k**) | EGP 1.2M (**$22.9k**) | EGP 4.0M (**$76.2k**) |
| Ads / sponsorship per active HH per year | $0.5 | $1.0 | $1.5 |
| **Ad revenue / month** | **$2.1k** | **$16.7k** | **$75.0k** |
| HH paying dues in-app with a fee | 20% | 30% | 40% |
| Net margin per fee-bearing payment (EGP) | 5 | 5 | 5 |
| **Payments revenue / month** | EGP 50k (**$1.0k**) | EGP 300k (**$5.7k**) | EGP 1.2M (**$22.9k**) |
| **Referrals (BNPL / insurance / ISP)** | $1.0k | $5.0k | $20.0k |
| **Total revenue / month** | **≈ $10.9k** | **≈ $74.3k** | **≈ $306k** |
| Annual run-rate | ≈ $131k | ≈ $892k | ≈ $3.7M |
| Est. MAU (≈1.7 MAU per active HH) | 85k | 340k | 1.0M |
| Infrastructure (§4, ~$0.04/MAU) | $3.4k | $13.6k | $40k |
| Team + support + ops (loaded) | $12k | $25–30k | $55–70k |
| Legal / PDPL / accounting / tools | $1k | $2.5k | $6k |
| **Monthly operating result** | **≈ −$5.5k** | **≈ +$28–33k** | **≈ +$190–205k** |

**Reading the table:**
- The model breaks even at roughly **100–120k active households** (ESTIMATE).
- Below that, the free-first app must be funded from the founder's dev and ops budget or a pre-seed round.
- Egyptian funding is tight: Egypt funding in 2026 through July was down 62.76% vs 2025 per [Tracxn](https://tracxn.com/d/geographies/egypt/__aRcH8lYOC74CSa9mr7vgyEJG0aUdj3E52SUBjjv4gy0), and investors now focus on collections, margins and retention ([mean.ceo](https://blog.mean.ceo/startups-egypt-news-september-2026/)).
- **So start some revenue line early**: compound Pro SaaS from month 6–9. It does not conflict with "free for residents".

### 7.4 Pricing psychology for the "free to dominate" phase

1. **Residents: free forever** (account, notifications, dues tracking, complaints, community feed, AI assistant in-app).
2. **Buildings (≤ 20 units): free forever** for core features. This undercuts Saknna, which charges EGP 450–2,200/month and is the clearest competitive wedge in Egypt.
3. **Compounds and facility-management companies: paid Pro** (multi-building, accountant export, WhatsApp automation, audit trail, gate and visitor module).
4. **Monetize the intermediary layer** (services, offers, financing) only after network density is reached in a district. Aim for about 30%+ of buildings in a neighbourhood or compound, so technician routing is efficient and response times beat the "بواب's cousin".

---

## 8. 24-month cost budget for the founder (ESTIMATE)

Assumes Option A (lean team) for months 0–6, then Option B (product team) for months 7–24. Zero paid marketing. Ops staff are added as buildings grow.

| Period | Team (loaded) | Infra + APIs | Legal / admin / tools | Field ops & support | Total | Cumulative |
|---|---|---|---|---|---|---|
| M0–M6 (build + pilot 20–100 buildings) | $5.0k × 6 = $30k | $0.3k × 6 = $2k | Setup $1k + $0.4k × 6 = $3.4k | $0.3k × 3 = $1k | **≈ $36k (EGP 1.9M)** | $36k |
| M7–M12 (1,000 buildings, ~30k MAU) | $8.4k × 6 = $50k | $1.2k × 6 = $7k | $0.6k × 6 = $3.6k | $1.3k × 6 = $8k | **≈ $69k (EGP 3.6M)** | $105k |
| M13–M24 (5–10k buildings, 150–300k MAU) | $11k × 12 = $132k (adds a 2nd backend and a marketplace ops lead; salary +15% for inflation) | $8k × 12 = $96k | $1.5k × 12 = $18k (PDPL licence, accounting) | $4k × 12 = $48k | **≈ $294k (EGP 15.4M)** | **≈ $400k** |

**Recommendations:**
- If the founder's budget covers only about **$100k (EGP 5.3M)**, plan to have **paid compound SaaS and the marketplace live by M12** so they offset the M13+ ramp. Otherwise raise a pre-seed round around M9–M12 on the back of building-density metrics.
- Keep a **10–15% contingency** for FX and inflation, given 13.9% urban CPI and USD-billed APIs.

---

## 9. Cost-saving playbook for a zero-marketing launch

1. **Free virality rails only:** use native share-sheet invites via the user's own WhatsApp ($0), QR posters in the elevator or lobby printed by the union (≈ EGP 5 each), and a doorman/بواب referral reward paid in phone credit. Avoid business-sent marketing templates ($0.0644 each).
2. **Authentication:** WhatsApp OTP first ($0.0036), Google and Apple sign-in, long sessions. Never Twilio SMS ($0.3959).
3. **Notifications:** FCM push (free) plus an in-app inbox. Reserve WhatsApp utility templates for must-know alerts.
4. **AI:** route Flash-Lite → Flash → Haiku; summaries instead of full history; batch overnight digests (≈50% off); transcribe voice only on demand.
5. **Payments:** an InstaPay / wallet reference with AI screenshot reconciliation for dues (cost about 0.1% to the payer); Paymob only for cards and BNPL. Use split settlement, never pooled funds.
6. **Infra:** managed Supabase until about 300–500k MAU; avoid premature Kubernetes. EU region; watch Hetzner's 2026 price changes.
7. **Store fees:** sell B2B plans on the web; physical services are outside IAP.
8. **People:** hire product-company-calibre mid-level engineers (EGP 28–55k net) and one senior. Pay field ambassadors per onboarded building rather than a high fixed salary.
9. **Compliance early:** a PDPL licence becomes mandatory as you pass 100k records. Bake in consent and marketing opt-ins from day 1, because phase-2 monetization depends on them.

---

## 10. Data gaps and what to validate next

| Gap | Why it matters | How to close it |
|---|---|---|
| Fawry, Geidea and InstaPay **merchant** pricing | Dues collection cost | Request quotes; ask Paymob for a wallet/InstaPay-specific rate |
| Official Meta Egypt rate card (CSV) | Bot and OTP budget | Download from Meta Business Manager |
| ~~Exact Groups API limits (8 participants)~~ | Bot architecture | **Closed:** confirmed on Meta's Groups docs (8 participants, OBA only, invite-link join) |
| Egyptian technician visit prices (سعر زيارة سباك / كهربائي) | Marketplace AOV | Pilot data from 20 buildings; scrape listings on OLX/Facebook groups |
| Commission rates of Egyptian home-service apps | Take-rate positioning | Sign up as a technician on competitor apps; read technician terms |
| Amarati / Imarti monetization | Competitive pricing | Install the apps and inspect in-app purchases and admin plans |
| Egypt AdMob eCPM | Ad revenue model | Small test with mediation in the pilot |
| BNPL merchant discount and referral fees | Big-ticket financing upside | Partner meetings with valU, Souhoola, Contact, Halan |
| Company formation fee table (GAFI) | Setup budget | Quote from 2–3 corporate lawyers |
| QA and PM salary benchmarks | Team budget | Wuzzuf salary filters; recruiter quotes |

---

## Sources (consolidated)

- FX: [XE](https://www.xe.com/en-us/currencyconverter/convert/?Amount=1&From=EGP&To=USD) · [Nile FM](https://www.nilefm.com/life/article/14098/exchange-rates-us-dollar-trades-at-egp-52-27-against-the-egyptian-pound-4-october-2026) · [CoinCodex](https://coincodex.com/forex/usd-egp/forecast/)
- Inflation: [Daily News Egypt](https://www.dailynewsegypt.com/2026/10/10/egypts-annual-urban-inflation-eases-to-13-9-in-september/) · [EnterpriseAM](https://enterpriseam.com/egypt/2026/10/11/urban-inflation-eased-to-13-9-in-september-even-as-monthly-prices-continue-to-pick-up/) · [Egyptian Streets](https://egyptianstreets.com/2026/10/11/egypts-annual-inflation-rises-to-12-8-percent-in-september-as-food-prices-increase/) · [Rio Times](https://www.riotimesonline.com/egypt-urban-inflation-13-9-percent-september-2026/)
- Market: [Cairo Scene / CAPMAS](https://cairoscene.com/buzz/over-half-of-egyptian-households-live-in-rural-areas) · [Ahram](https://english.ahram.org.eg/News/574749.aspx) · [DataReportal 2026](https://datareportal.com/reports/digital-2026-egypt) · [Deep Market Insights](https://deepmarketinsights.com/vista/insights/home-services-market/egypt) · [Campaign ME](https://campaignme.com/digital-ad-spend-in-mena-reaches-8b-in-2025-iab-report-reveals/) · [Tracxn](https://tracxn.com/d/geographies/egypt/__aRcH8lYOC74CSa9mr7vgyEJG0aUdj3E52SUBjjv4gy0)
- Salaries: [cvpromaker / egytech.fyi](https://www.cvpromaker.com/salaries/egypt/software-engineer) · [Payscale Flutter](https://www.payscale.com/research/EG/Job=Flutter_Developer/Salary) · [Paylab backend](https://paylab.com/eg/salaryinfo/information-technology/backend-developer) · [Paylab Android](https://paylab.com/eg/salaryinfo/information-technology/android-developer) · [Paylab UX](https://www.paylab.com/eg/salaryinfo/information-technology/ux-designer) · [designproject](https://designproject.io/jobs/jobs/uxui-designer-at-ahoy-ag0bbj) · [Wuzzuf call centre](https://wuzzuf.net/careers/call-center-agent-salary-in-egypt/) · [Levels.fyi Egypt](https://www.levels.fyi/t/software-engineer/locations/egypt)
- Agencies: [GoodFirms Egypt](https://www.goodfirms.co/directory/country/app-development/egypt) · [Abbacus](https://www.abbacustechnologies.com/?p=50038) · [Zoho / Business of Apps](https://www.zoho.com/creator/decode/creator/decode/the-cost-of-app-development)
- Messaging: [Twilio EG](https://www.twilio.com/en-us/sms/pricing/eg) · [D7](https://d7networks.com/sms/egypt/) · [MoceanAPI](https://egypt.moceanapi.com/) · [sent.dm](https://www.sent.dm/en/resources/sms-pricing/egypt-sms-pricing) · [Meta WhatsApp pricing](https://developers.facebook.com/documentation/business-messaging/whatsapp/pricing) · [ChatMaxima Egypt](https://chatmaxima.com/whatsapp-api-pricing/egypt/) · [ArabyBot Egypt](https://arabybot.com/guides/whatsapp-api-pricing-egypt?lang=en) · [Unipile Groups API](https://www.unipile.com/whatsapp-group-api/) · [Gulf News AI ban](https://gulfnews.com/technology/no-more-chatgpt-and-perplexity-on-whatsapp-meta-bans-major-ai-chatbots-from-2026-1.500316016) · [respond.io](https://respond.io/blog/whatsapp-chatbot-policy-2026)
- AI: [SD Times Gemini](https://sdtimes.com/ai/gemini-2-5-pro-and-flash-are-generally-available-and-gemini-2-5-flash-lite-preview-is-announced/) · [modelcompare Flash-Lite](https://modelcompare.dev/models/google/gemini-2-5-flash-lite) · [cloudprice Flash](https://cloudprice.net/models/openrouter/google/gemini-2.5-flash) · [pricepertoken Haiku 4.5](https://pricepertoken.com/pricing-page/model/anthropic-claude-haiku-4.5) · [diyai transcription](https://diyai.io/ai-tools/speech-to-text/openai-whisper-api-pricing-2026/)
- Infra: [Supabase pricing (makerkit)](https://makerkit.dev/blog/saas/supabase-pricing) · [jetadmin](https://www.jetadmin.io/blog/supabase-pricing-2026-guide-to-plans-limits-and-real-world-costs/) · [Firebase pricing plans](https://firebase.google.cn/docs/projects/billing/firebase-pricing-plans?hl=en) · [Google Maps Mar 2025](https://developers.google.com/maps/billing-and-pricing/march-2025) · [Northflank Hetzner](https://northflank.com/blog/hetzner-cloud-server-price-increases)
- Payments: [Paymob pricing](https://paymob.com/en/pricing) · [Kashier FAQ](https://kashier.io/en/faqs) · [InstaPay fees](https://www.businesstodayegypt.com/amp/1/6185/InstaPay-to-Introduce-New-Fee-Structure-Starting-April-2025) · [Zawya InstaPay](https://www.zawya.com/en/economy/north-africa/egypt-instapay-turns-profitable-a-year-after-transfer-fee-rollout-rt18pyrt) · [CBE PSP rules](https://www.businesstodayegypt.com/amp/1/6465/Central-Bank-of-Egypt-issues-new-licensing-rules-for-payment) · [Baker McKenzie](https://insightplus.bakermckenzie.com/bm/banking-finance_1/egypt-new-regulation-on-payment-solutions) · [LaunchBase](https://launchbaseafrica.com/2025/06/19/egypts-fintech-firms-given-12-months-to-get-licensed-or-shut-down/)
- BNPL: [Techpoint valU](https://techpoint.africa/news/egyptian-fintech-valu-h1-results/) · [Amwal Al Ghad FRA](https://en.amwalalghad.com/?p=222883) · [BusinessWire BNPL](https://www.businesswire.com/news/home/20250305099643/en/Egypt-Buy-Now-Pay-Later-Business-and-Investment-Report-2025) · [LaunchBase instalments](https://launchbaseafrica.com/2026/01/15/why-egypts-10m-instalment-customers-have-become-africas-most-fought-over-fintech-asset/) · [Geidea ValU docs](https://docs.geidea.net/docs/valu)
- Benchmarks: [Inc42 Urban Company](https://inc42.com/?p=571319) · [Entrackr UC FY25](https://entrackr.com/fintrackr/urban-company-posts-rs-1144-cr-revenue-and-rs-285-cr-pbt-in-fy25-9373371) · [S&P Global UC](https://www.spglobal.com/market-intelligence/en/news-insights/research/2026/04/urban-company-revenue-to-triple-by-2030-as-take-rates-and-platform-monetization-rise) · [Inc42 MyGate FY25](https://inc42.com/buzz/mygate-trims-fy25-loss-by-61-to-₹15-4-cr/) · [BW Disrupt MyGate FY24](https://bwdisrupt.com/article/mygate-crosses-rs-100-cr-revenue-and-achieves-35-operating-revenue-growth-with-82-reduction-in-losses-538480) · [The Ken MyGate](https://the-ken.com/story/gate-secured-mygate-now-wants-to-monetise-community/) · [Inc42 NoBroker](https://inc42.com/features/nobrokers-future-is-beyond-home-listings-but-will-profits-follow/) · [saknna.com](https://saknna.com) · [ManageCasa](https://managecasa.com/hoa-sales-campaign) · [Cairo Scene FilKhedma](https://cairoscene.com/Business/Egyptian-Home-Services-App-Filkhedma-Acquired-by-South-African-Giant)
- Legal / tax: [EY Law 6/2025](https://www.ey.com/en_gl/technical/tax-alerts/egypt-introduces-tax-incentives-and-benefits-for-small-enterprises) · [Beancount guide](https://beancount.io/blog/2026/07/26/egypt-law-6-2025-sme-simplified-tax-regime-guide) · [Andersen](https://eg.andersen.com/ar/egypts-new-tax-reform-2025/) · [Digital Policy Alert PDPL](https://digitalpolicyalert.org/event/36521-executive-regulations-of-the-personal-data-protection-law-decision-no-816-of-2025-including-operational-license-requirement-entered-into-force) · [Tamimi PDPL](https://www.tamimi.com/law_update_articles/from-policy-to-practice-egypt-issues-executive-regulations-of-the-personal-data-protection-law/) · [Clyde & Co](https://www.clydeco.com/en/insights/2026/01/egypt-regulatory-update-on-data-privacy) · [Aqarmap hidden costs](https://aqarmap.com.eg/en/advice/a-checklist-of-hidden-costs-when-buying-property-in-egypt/)
- App stores: [splitmetrics](https://splitmetrics.com/blog/google-play-apple-app-store-fees/) · [appbot](https://appbot.co/blog/app-developers-apple-google-small-business-programs/) · [UK CMA IAP appendix](https://assets.publishing.service.gov.uk/media/62a0d1b68fa8f5039b2078e5/Appendix_H_-_In-app_purchase_rules_in_Apples_and_Googles_app_stores.pdf)

---

## Verification log

Adversarial re-check on 2026-10-12. Each claim was re-fetched from the source or a fresh independent search.

| # | Claim | Verdict | Evidence URL |
|---|---|---|---|
| 1 | Official WhatsApp Groups API: max 8 participants, invite-link join only, OBA required | confirmed (Meta primary docs) | https://developers.facebook.com/documentation/business-messaging/whatsapp/groups |
| 2 | WhatsApp Egypt rates: marketing $0.0644, utility $0.0036, auth $0.0036, auth-intl $0.0650, +14% VAT | confirmed (aggregator; Meta CSV not checked) | https://chatmaxima.com/whatsapp-api-pricing/egypt/ |
| 3 | From 1 Oct 2026 service messages are free only for the first 1,000 per number per month | confirmed (multiple vendors and press); not yet visible on the Meta pricing page fetched | https://www.ycloud.com/blog/whatsapp-api-message-pricing-update-effective-october-1-2026 , https://respond.io/blog/whatsapp-pricing-change-2026 |
| 4 | Meta per-message pricing since 1 Jul 2025; "AI Providers" policy effective 16 Feb 2026 | confirmed (terms of the AI Providers policy not reviewed) | https://developers.facebook.com/documentation/business-messaging/whatsapp/pricing |
| 5 | General-purpose AI chatbots banned from the WhatsApp Business API from 15 Jan 2026; task bots allowed | confirmed | https://respond.io/blog/whatsapp-general-purpose-chatbots-ban , https://gulfnews.com/technology/no-more-chatgpt-and-perplexity-on-whatsapp-meta-bans-major-ai-chatbots-from-2026-1.500316016 |
| 6 | Twilio SMS to Egypt $0.3959 per message | confirmed (per segment; +$0.001 failed-message fee) | https://www.twilio.com/en-us/sms/pricing/eg |
| 7 | Paymob 2.75% + EGP 3, no monthly fee, weekly settlement | confirmed | https://paymob.com/en/pricing |
| 8 | Kashier 2.85% + EGP 3 | unverified (old source; newer comparison site says 2.75%; official site unreachable) | https://kr-asia.com/egyptian-payments-platform-kashier-raises-six-figure-seed , https://paymentproviders.io/compare/kashier-vs-codi-mx?focus=fees |
| 9 | Saknna pricing EGP 450 / 900 / 2,200 / 7,500; 14-day trial; 500+ buildings; 8 countries | confirmed (500+ is a self-claim; on-page counter shows "0") | https://saknna.com |
| 10 | PDPL Decree 816/2025: ≤100k records exempt, max fee EGP 666,666 above 5M records; full enforcement 31 Oct 2026 | confirmed (in force 2 Nov 2025 + 1-year grace) | https://www.tamimi.com/law_update_articles/from-policy-to-practice-egypt-issues-executive-regulations-of-the-personal-data-protection-law/ , https://www.clydeco.com/en/insights/2026/01/egypt-regulatory-update-on-data-privacy |
| 11 | Urban inflation Sep 2026 13.9% y/y (Aug 14.5%), monthly +1.3% | confirmed | https://www.dailynewsegypt.com/2026/10/10/egypts-annual-urban-inflation-eases-to-13-9-in-september/ |
| 12 | InstaPay fee 0.1%, min EGP 0.50, max EGP 20 from Apr 2025 | confirmed (one outlet reports min EGP 1) | https://egyptianstreets.com/2025/04/03/instapay-now-charging-transfer-fees |
| 13 | CBE PSP licensing rules in force 17 Jun 2025 with a 12-month transition | confirmed | https://insightplus.bakermckenzie.com/bm/banking-finance_1/egypt-new-regulation-on-payment-solutions |
| 14 | Urban Company FY25 revenue ₹1,144 Cr, "first profitable year" | corrected (profit mostly a deferred-tax credit; pre-tax ≈ ₹28 Cr) | https://www.outlookbusiness.com/news/urban-company-swings-to-2398-cr-profit-in-fy25-ahead-of-ipo |
| 15 | UC commissions and fees = 28.3% of professionals' gross earnings, 9M FY26 | confirmed (Inc42 analysis, not a company-disclosed take rate) | https://inc42.com/?p=571319 |
| 16 | MyGate FY25 revenue ₹173.5 Cr; 65–70% of revenue from ads | confirmed (₹173.5 Cr from a single secondary source; FY26 ₹232 Cr unverified) | https://inc42.com/buzz/mygate-trims-fy25-loss-by-61-to-₹15-4-cr/ |
| 17 | Gemini 2.5 Flash-Lite $0.10/$0.40 (audio $0.30); Flash $0.30/$2.50 (audio $1.00); batch −50% | confirmed; Flash-Lite audio price corrected from "$0.30–0.50, conflicting" | https://ai.google.dev/gemini-api/docs/pricing |
| 18 | Supabase Pro $25; 100k MAU; 250 GB egress; 8 GB DB; Micro $10 / Small $15 / Medium $60 | confirmed (Pro includes $10 compute credit = one Micro) | https://supabase.com/pricing |

**Net effect on conclusions:** None of the strategic conclusions change. The "bot cannot join the big building group" constraint is now confirmed on Meta's primary docs. The Oct-2026 service-message charge stands, but re-check Meta's rate card. PDPL full enforcement starts on 31 Oct 2026, so licensing is an immediate pre-launch task, not a later one.
