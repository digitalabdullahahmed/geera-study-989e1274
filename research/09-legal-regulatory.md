# 09: Egyptian Legal and Regulatory Landscape for a Residential-Building Super-App

**Research angle:** What Egyptian law says about owners' and occupants' associations (اتحاد الشاغلين), the old-rent reform, data protection, payments, tax, consumer protection, labour classification and WhatsApp/Meta platform rules. Also covers which licences and partners the startup needs, and the main risks.
**Research date:** 12 October 2026
**Market:** Egypt only
**Disclaimer:** This is product and strategy research, not legal advice. Every factual claim carries a source URL. Items marked **ESTIMATE** are my reasoning. Items marked **UNVERIFIED** could not be confirmed from a primary source. Before launch, a licensed Egyptian lawyer should review sections 4 (PDPL), 6 (payments) and 7 (tax).

---

## 0. Executive summary (read this first)

| # | Finding | Why it matters for the app | Urgency |
|---|---|---|---|
| 1 | **The law requires an occupants' union (اتحاد شاغلين) in every building with 5 or more units.** It gains legal personality on registration at the local unit (الحي). It has a **statutory lien (حق امتياز)** over each unit for unpaid dues and can get a **payment order (أمر أداء)** from the urgent-matters judge (Law 119/2008, Arts. 72, 76, 87). | The app's core customer, the union, is a legal entity with real enforcement tools that almost no one uses because the paperwork is painful. **The app can turn the law into its product**: registration wizard, statutory GA invitations, minutes, receipts, arrears ledger and a ready-to-file payment-order dossier. | High (opportunity) |
| 2 | **Districts are actively pushing union registration.** Example: the Nasr City East/West campaign, June 2026, which lists 8 required documents and threatens "legal measures". The Housing Ministry is **drafting amendments** to the union rules (meeting on 3 Aug 2026). | A free government-driven tailwind for zero-budget growth. Partner with districts' technology centres, and be ready to adapt to the amendments. | High (opportunity) |
| 3 | **The PDPL full-compliance deadline is about 31 Oct / 1 Nov 2026, roughly 3 weeks from today.** It brings licensing by record volume, a mandatory registered DPO, 72-hour breach notification, a separate licence for **direct electronic marketing**, and a licence plus consent for **cross-border transfer**, which covers cloud hosting abroad and calls to foreign LLM APIs. Criminal fines reach EGP 5M. | The phase-2 plan of selling services to the user base is **legally "direct electronic marketing"** and needs its own licence and explicit opt-in. The "mandatory AI everywhere" idea sends personal data abroad, which is a cross-border transfer. | Critical |
| 4 | **Collecting money for others is a CBE-licensed activity** (PSP rules of June 2025 under Banking Law 194/2020; Category B capital is EGP 10M). | **Never hold users' money.** Use a ledger-only model plus licensed PSPs (Paymob Marketplace, Kashier, Fawry, Geidea) and InstaPay. Seek your own licence only at scale. | Critical |
| 5 | **The official WhatsApp Groups API allows at most 8 participants, is invite-only, and requires an Official Business Account.** WhatsApp ToS bans "bulk messaging, auto-messaging" and accounts created by "automated means". Unofficial libraries (whatsapp-web.js, Baileys) carry real ban risk. | The founder's idea of a bot that joins the building's WhatsApp group (typically 20 to 200 members) **cannot be done officially**. Redesign it as: (a) an 8-seat board/committee group with the bot (fits the 3 or 4 statutory board seats exactly), (b) a 1:1 "building assistant" number, and (c) template broadcasts. | Critical (design) |
| 6 | **Consumer Protection Law 181/2018 Art. 26:** maintenance, finishing and installation providers must **guarantee their work for at least 1 year** and issue a **written receipt before starting work**. There is a 14-day withdrawal right for distance contracts (Art. 40). Fines run up to EGP 2M. | The phase-2 marketplace must build in digital pre-work receipts, warranty tracking and transparent pricing. Doing so is also a selling point. | High (phase 2) |
| 7 | **The new Labour Law 14/2025** (in force 1 Sep 2025) explicitly recognises **digital platform work**, but its executive regulations are reportedly still pending. | Technicians could later be reclassified as employees. Design for independence: technicians set their own prices and hours, can work on other platforms, and are paid per job. | Medium |
| 8 | **Old-rent Law 164/2025:** about 1.6M units affected, 7-year residential transition to 2032, and a 15% annual rent increase. | It creates a **new wave of landlord-tenant friction** (rent collection, receipts, disputes, units returning to market). This is a strong engagement hook. Listing units for rent touches the **new real-estate brokerage regulation (No. 578 of 2026)**. | Medium (opportunity) |
| 9 | **Tax:** VAT is 14% once turnover reaches EGP 500k. ETA has an e-commerce unit. The simplified regime (Law 6/2025) is available up to EGP 20M turnover. | Structure the commission (agent) model correctly from day one and register for simplified tax. | Medium |

**Bottom line (ESTIMATE):** In phase 1 the app needs no special licence beyond company registration, tax registration and PDPL licensing/DPO, **provided it does not touch money and does not market third-party services**. Every phase-2 money move (payments, commissions, selling services) adds a regulated layer. Each layer can be handled through licensed partners rather than in-house licences.

---

## 1. Owners'/occupants' associations: اتحاد الشاغلين

### 1.1 The legal source

- **Unified Building Law No. 119 of 2008** (قانون البناء الموحد), Book Four, Chapter One, **Arts. 69 to 89** on occupants' unions. Published in the Official Gazette issue 19 bis (a), 11 May 2008. Text: [Wikisource, Law 119/2008](https://ar.wikisource.org/wiki/%D9%82%D8%A7%D9%86%D9%88%D9%86_%D8%A7%D9%84%D8%A8%D9%86%D8%A7%D8%A1_%D8%A7%D9%84%D9%85%D9%88%D8%AD%D8%AF_119_%D9%84%D8%B3%D9%86%D8%A9_2008_(%D9%85%D8%B5%D8%B1)). English translation with the Executive Regulations: [Andersen Egypt](https://eg.andersen.com/translation-of-law-no-119-of-2008/).
- **Executive Regulations:** Ministerial Decree **No. 144 of 2009**. Arts. 155 to 174 cover unions, per [Unitify blog](https://unitify.com/blog/unions-of-occupants-egypt-new-cities-maintenance-fees) and [Andersen](https://eg.andersen.com/translation-of-law-no-119-of-2008/).
- **Civil Code:** The Civil Code has older provisions on ownership of floors and apartments (ملكية الطبقات والشقق). I **could not retrieve the verified article text** (the commonly cited range is Arts. 856 to 869) from an official source. **UNVERIFIED.** Law 119/2008 is the operative special law.

### 1.2 Key provisions (from the published law text)

| Topic | Rule | Article | Source |
|---|---|---|---|
| Who must form one | Occupants of built properties with **at least 5 units** ("لا يقل عدد وحداتها عن خمس وحدات"), whether owned, rented or held in usufruct | Art. 72 | [Wikisource](https://ar.wikisource.org/wiki/%D9%82%D8%A7%D9%86%D9%88%D9%86_%D8%A7%D9%84%D8%A8%D9%86%D8%A7%D8%A1_%D8%A7%D9%84%D9%85%D9%88%D8%AD%D8%AF_119_%D9%84%D8%B3%D9%86%D8%A9_2008_(%D9%85%D8%B5%D8%B1)), [mohamah.net](https://www.mohamah.net/law/?p=178136) |
| Integrated complexes (compounds) | Owners and occupants must form one or more **management-and-maintenance companies** holding the union's powers. Per a secondary source, this applies once power is connected and 60% of units are occupied (ER Art. 158). | Art. 72 / ER 158 | [Wikisource](https://ar.wikisource.org/wiki/%D9%82%D8%A7%D9%86%D9%88%D9%86_%D8%A7%D9%84%D8%A8%D9%86%D8%A7%D8%A1_%D8%A7%D9%84%D9%85%D9%88%D8%AD%D8%AF_119_%D9%84%D8%B3%D9%86%D8%A9_2008_(%D9%85%D8%B5%D8%B1)), [Unitify](https://unitify.com/blog/unions-of-occupants-egypt-new-cities-maintenance-fees) |
| Registration | Local units (الوحدات المحلية) register unions in a special register. The union **gains legal personality on registration** ("يكتسب الاتحاد الشخصية الاعتبارية بمجرد القيد"). | Art. 76 | [Wikisource](https://ar.wikisource.org/wiki/%D9%82%D8%A7%D9%86%D9%88%D9%86_%D8%A7%D9%84%D8%A8%D9%86%D8%A7%D8%A1_%D8%A7%D9%84%D9%85%D9%88%D8%AD%D8%AF_119_%D9%84%D8%B3%D9%86%D8%A9_2008_(%D9%85%D8%B5%D8%B1)) |
| Board | President, treasurer and a member. A vice-president is added if there are more than 7 units. | Art. 78 | same |
| Financial obligations | The general assembly sets occupants' contributions per the ER. Revenue comes from contributions, investment returns and donations. The treasurer collects and prepares the budget and final accounts. | Arts. 80, 81, 85 | same |
| General assembly (GA) | All members. Quorum is an absolute majority; if it fails, a second session proceeds with any attendance. Decisions pass by majority of those present. **Members in arrears do not have a counted vote.** | Art. 81 | same |
| GA notice | Invitations **at least 15 days** in advance | Art. 84 | same; also [El-Watan](https://www.elwatannews.com/news/details/8298565) |
| Enforcement | **Lien (حق الامتياز)** on the unit and its appurtenances. The president can get a **payment order (أمر أداء)** from the urgent-matters judge after notifying the occupant. Non-payment has the **same legal effects as non-payment of rent**. | Art. 87 | same |
| Criminal fine | **EGP 10 to 100 per month of default** for failing to pay contributions; the court may also order payment | Art. 109 | same |
| Contribution weights (secondary) | By each unit's share of land. Commercial/administrative m² count **double** the residential rate. Arrears follow the unit to the successor. | ER (per blog) | [Unitify](https://unitify.com/blog/unions-of-occupants-egypt-new-cities-maintenance-fees) (UNVERIFIED against the ER text) |
| No union formed | The local unit may appoint a temporary management committee | ER (per blog) | [Unitify](https://unitify.com/blog/unions-of-occupants-egypt-new-cities-maintenance-fees) (UNVERIFIED) |
| Paper-only procedures | Per one secondary source, the law and ER have **no provision for electronic voting, remote attendance or in-absentia polling**. They rely on paper minutes books and paper receipts. | ER (per blog) | [Unitify](https://unitify.com/blog/unions-of-occupants-egypt-new-cities-maintenance-fees) |

**Weakness noted in public debate:** The EGP 10 to 100 fine dates from 2008 and is trivial today. Commentators say the law "lacks a binding collection power" ([Al-Dostor](https://www.dostor.org/3483595), older article, 2021).

### 1.3 Registration in practice: the district checklist (Cairo, June 2026)

On 9 June 2026, Nasr City East and West districts launched a campaign urging residents to go to **district technology centres (المراكز التكنولوجية)** to form unions. They called it "التزاماً قانونياً" and warned of continued field inspections ([El-Watan, 9 Jun 2026](https://www.elwatannews.com/news/details/8298565)). The required documents:

1. A building statement: address, description, floors, units, licence number and date
2. A certified member list (owners and tenants) with national ID numbers and unit numbers
3. A copy of the GA invitation (venue and date)
4. Proof of delivery of invitations (by hand, or registered mail with acknowledgment)
5. GA minutes **authenticated at the Real Estate Registry (الشهر العقاري)**
6. The model union statute (from the district technology centre)
7. A criminal-record certificate and ID copy for each elected board member
8. A declaration by the union head that signatures and documents are accurate

Fees were not stated in the article. **UNVERIFIED.**

### 1.4 Pending amendments (2026)

On **3 Aug 2026** the Minister of Housing, Randa El-Menshawy, reviewed draft amendments to the Building Law covering unions. They address registration and data updating by administrative authorities, formation procedures, **developer maintenance responsibilities during the legal period**, board formation, GA powers, and handling of buildings **with no union or non-regularised unions**. The minister ordered the drafting finalised ([Invest-Gate](https://invest-gate.me/news/minister-of-housing-reviews-draft-amendments-to-the-unified-building-law-on-owners-associations/), [Masrawy](https://www.masrawy.com/news/realestate-news/details/2026/8/3/3027283/), [SIS](https://sis.gov.eg/ar/%D8%A7%D9%84%D9%85%D8%B1%D9%83%D8%B2-%D8%A7%D9%84%D8%A5%D8%B9%D9%84%D8%A7%D9%85%D9%8A/%D8%A7%D9%84%D8%A3%D8%AE%D8%A8%D8%A7%D8%B1/%D9%88%D8%B2%D9%8A%D8%B1%D8%A9-%D8%A7%D9%84%D8%A5%D8%B3%D9%83%D8%A7%D9%86-%D8%AA%D8%AA%D8%A7%D8%A8%D8%B9-%D8%AA%D8%B9%D8%AF%D9%8A%D9%84%D8%A7%D8%AA-%D9%82%D8%A7%D9%86%D9%88%D9%86-%D8%A7%D9%84%D8%A8%D9%86%D8%A7%D8%A1-%D9%84%D8%AA%D9%86%D8%B8%D9%8A%D9%85-%D8%B9%D9%85%D9%84-%D8%A7%D8%AA%D8%AD%D8%A7%D8%AF-%D8%A7%D9%84%D8%B4%D8%A7%D8%BA%D9%84%D9%8A%D9%86/)). I found **no confirmation** that the draft has reached Cabinet or Parliament as of today.

**Implication (ESTIMATE):** The amendments are likely to formalise a government register and "data updating" duty. If they add any electronic register or e-procedures, an app that already holds structured union data, such as member lists, boards and minutes, could integrate with or feed that register. **Action:** track the draft and lobby through the Real Estate Development Chamber or the ministry's consultation for allowing electronic notices and e-voting.

### 1.5 Compounds: maintenance deposits and developer-run FM

- A study by Saada & Abu El-Kamsan law firm of 40+ contracts found **maintenance deposits up to 10% of unit price**. Many contracts lack a separate account, periodic statements or a mechanism to hand the deposit to the union ([Masrawy, 19 Sep 2026](https://www.masrawy.com/news/realestate-news/details/2026/9/19/3050278), [Egypt Telegraph](https://www.egypttelegraph.com/article/279824/10-وديعة-صيانة-و30-غرامة-فسخ-مصروفات)).
- The Real Estate Development Chamber head (Tarek Shokry) calls for **separating maintenance from developers**, separate bank accounts, independent audit and activating union rules on non-payment ([Banker News, 29 Sep 2026](https://banker.news/154253)).

**Implication:** Compound owners are distrustful of opaque deposits. The app's "transparency ledger" (every expense with receipt photo, GA-approved budget vs actual, deposit statement) addresses a live, press-covered pain point. Compound management companies (Art. 158) are a separate B2B customer segment.

### 1.6 Product features the law directly justifies (the "law-as-product" list)

| Legal requirement | App feature | Growth effect |
|---|---|---|
| Union mandatory at 5+ units (Art. 72) | "Is your building compliant?" checker, with **union-registration wizard** producing the 8 district documents | Organic, government-aligned acquisition: the whole building must join to build the member list |
| Member list with national IDs (Art. 76 / district list) | Every resident gets an account and verifies unit and role (owner/tenant) | Enforces the "every resident has an account" goal *legally*. **PDPL caution:** national ID is personal data (section 4) |
| 15-day GA invitation with proof of delivery (Art. 84) | Timestamped in-app, WhatsApp-template and SMS notices with delivery/read logs exportable as PDF | Evidence trail. Note: whether electronic delivery is accepted as legal proof is **UNVERIFIED**, so keep the registered-mail option |
| Quorum, majority, arrears-holders' votes not counted (Art. 81) | Automatic quorum tracker; vote eligibility computed from the arrears ledger | Removes disputes |
| Board seats (Art. 78) | Role-based permissions: president, treasurer, member, VP | |
| Treasurer collects and keeps accounts (Arts. 80, 85) | Digital receipts, budget vs actual, annual final account generator | Transparency builds trust and engagement |
| Lien and payment order (Art. 87) | **"Payment-order dossier" (ملف أمر أداء):** auto-generated formal notice, arrears statement, GA decision copy, and a lawyer-referral marketplace (phase 2) | Strong retention: boards finally get a working enforcement path |
| Fine EGP 10 to 100 per month (Art. 109) | Show the legal consequence in reminders, in a neutral tone | Soft nudge |
| Land-share weights, commercial ×2 (ER, per blog) | Contribution calculator with configurable weights | Accuracy |

---

## 2. Old-rent reform: Law No. 164 of 2025 (قانون الإيجار القديم)

### 2.1 Facts

| Item | Detail | Source |
|---|---|---|
| Law | **Law 164/2025**, published in the Official Gazette on **4 Aug 2025**. It repealed old-rent Laws 49/1977 and 136/1981 for the units it covers. | [Jurist](https://www.jurist.org/features/2025/12/09/egypts-rental-reform-balancing-property-rights-and-social-justice-after-decades-of-distortion/), [Amwal Al Ghad](https://amwalalghad.com/2025/08/04/تفاصيل-قانون-الإيجار-القديم-الجديد-2025-ب/) |
| Transition | **7 years** for residential and **5 years** for non-residential (natural persons), after which contracts end unless the parties agree otherwise | [Ahram Online](https://english.ahram.org.eg/News/572864.aspx), [Al-Ain](https://al-ain.com/article/details-anticipated-increase-the-old-rent-law) |
| Rent re-basing | Survey committees classify areas as premium, middle or economic. Reported multipliers: premium ×20 (minimum EGP 1,000), middle ×10 (minimum EGP 400), economic ×10 (minimum EGP 250). Interim payment of **EGP 250/month** until committees finish. | [Masrawy](https://www.masrawy.com/news/news_egypt/details/2025/12/1/2900041/الإيجار-القديم-زيادة-تصل-لـ20-ضعف-ا-والحد-الأدنى-250-جنيه-ا) (figures vary by source) |
| Annual increase | **15% per year**, compounding on the prior year's rent, throughout the transition. Sources differ on the first date (Aug or **Sep 2026**). | [Ahram](https://english.ahram.org.eg/News/572864.aspx), [Al-Khaleej](https://www.alkhaleej.ae/2026-08-17/), [Banker](https://banker.news/150643) |
| Scale | CAPMAS: **about 1.6M residential units** under old rent. The 2017 census counted 1,642,870 households (7.0% of households). | [Ahram](https://english.ahram.org.eg/News/572864.aspx), [Jurist](https://www.jurist.org/features/2025/12/09/egypts-rental-reform-balancing-property-rights-and-social-justice-after-decades-of-distortion/) |
| Alternative housing | Applications via the Digital Egypt platform. Only **about 86,000 families** had applied by mid-July 2026 (under 6% of those targeted). Ahram (16 Jul) cited a 21 July deadline; the Housing Ministry then extended it by three months to **12 Oct 2026** (today) [corrected: sourcing clarified]. No further extension found. | [El-Watan](https://www.elwatannews.com/news/details/8327488), [Ahram](https://english.ahram.org.eg/News/572864.aspx), [Al-Ain](https://al-ain.com/article/egypt-old-rent-alternative-deadline-october-2026) |
| Political risk | 60 MPs requested amendments, and there are court challenges to committee decisions | [Ahram](https://english.ahram.org.eg/News/572864.aspx), [El-Watan](https://www.elwatannews.com/news/details/8177886) |
| Maintenance duties | A legal commentator says exceptional rent laws **did not freeze tenants' maintenance obligations**. General rules apply. | [Akhbar El-Yom, May 2026](https://m.akhbarelyom.com/news/newdetails/4825531/1/إيمان-راشد-تكتب-مساهمة-المستأجر-فى-الصيا) |

### 2.2 Impact on the app

1. **Mixed buildings become more contentious.** Old-rent tenants now pay higher rent, increasing yearly to 2032, and many still sit on union boards and must pay union contributions. Expect disputes over who pays what. A neutral ledger app helps.
2. **Landlord-tenant tools become valuable:** rent-due reminders with the 15% compounding pre-calculated, digital rent receipts (important evidence in disputes), notices log, and an "end-of-transition" countdown.
3. **Unit turnover from about 2030 to 2032 (ESTIMATE):** units returning to owners will be renovated and re-let or sold. That means phase-2 demand for finishing/maintenance services and listings. Listings touch the **real-estate brokerage regulation** (section 9).
4. **Sensitivity:** this is a politically charged topic. The app must stay neutral (calculator plus records), never give legal advice in-app, and refer users to lawyers.

---

## 3. Unit-level personal data in a building app: why PDPL is the #1 compliance item

A building app processes: names, phone numbers, unit numbers, **national ID numbers** (needed for the union member list), payment history and arrears (financial status), visitor logs, possibly CCTV and intercom images, children's data (family members), and location. Phase 2 adds service history and in-home access by technicians. Much of this is personal data, and some is plausibly sensitive data (financial and children's data). Section 4 sets out the rules.

---

## 4. Personal Data Protection Law No. 151 of 2020 and Executive Regulations (Decree 816/2025)

### 4.1 Status and timeline

| Item | Detail | Source |
|---|---|---|
| Law | Law 151/2020 | [Andersen PDF](https://eg.andersen.com/wp-content/uploads/2025/06/Law-No.-151-OF-2020.pdf) |
| Executive Regulations | **MCIT Ministerial Decree 816 of 2025**, dated 1 Nov 2025 and released publicly about 25 Dec 2025 | [Baker McKenzie, Jan 2026](https://connectontech.bakermckenzie.com/egypt-important-data-protection-update/), [RecordingLaw](https://www.recordinglaw.com/world-laws/world-data-privacy-laws/egypt-data-privacy-laws/) |
| Grace period ends | **31 Oct 2026** (AMERELLER, DataGuidance) or **1 Nov 2026** (Baker McKenzie, S&H). Either way, **about 3 weeks from today**. | [AMERELLER, Apr 2026](https://amereller.com/publication/the-egyptian-personal-data-protection-regime-what-you-need-to-know-ahead-of-31-october-2026/), [S&H](https://www.shandpartners.com/insights/briefings/telecoms-media-technology/egypt-personal-data-protection-law-compliance-developments/) |
| Regulator | Personal Data Protection Center (PDPC). Its website pdpc.gov.eg reportedly launched. The licensing portal was "scheduled to go live by May 2026". **Whether it is accepting applications is UNVERIFIED.** | [Chambers 2026](https://practiceguides.chambers.com/practice-guides/data-protection-privacy-2026/egypt), [AMERELLER](https://amereller.com/publication/the-egyptian-personal-data-protection-regime-what-you-need-to-know-ahead-of-31-october-2026/) |

### 4.2 Obligations that bite a building app

| Obligation | Detail | Source |
|---|---|---|
| **Controller/processor licence** | Required before processing. Annual fee tiered by number of records (each data subject is one record). | [Legal500](https://www.legal500.com/developments/thought-leadership/overview-of-the-executive-regulations-of-the-egyptian-personal-data-protection-law/), [AMERELLER](https://amereller.com/publication/the-egyptian-personal-data-protection-regime-what-you-need-to-know-ahead-of-31-october-2026/) |
| Fee tiers (**sources conflict**) | Legal500: 1 to 10,000 records exempt; **10,001 to 200,000 records EGP 200/yr** [corrected: more precise band]; 200,001 to 1M records EGP 300 to 1,000/yr; 1M to 5M records EGP 5,000 to 500,000/yr; over 5M records Legal500 words it as "EGP 2,000,000 per year, payable annually for three years" [corrected], which conflicts with Baker's ~EGP 666,666/yr (i.e. EGP 2M spread over 3 years). Baker McKenzie: **up to 100,000 records exempt**, with a maximum of about EGP 666,666/yr above 5M. Controller-only or processor-only pays 50%. | [Legal500](https://www.legal500.com/developments/thought-leadership/overview-of-the-executive-regulations-of-the-egyptian-personal-data-protection-law/), [Baker McKenzie](https://connectontech.bakermckenzie.com/egypt-important-data-protection-update/) |
| **DPO** | Mandatory for legal entities. Must be **registered with the PDPC after passing its exam** (categories A, B, C; 2-year registration). Per one source, the DPO must be an employee. **DPO appointment is a prerequisite for any licence.** | [AMERELLER](https://amereller.com/publication/the-egyptian-personal-data-protection-regime-what-you-need-to-know-ahead-of-31-october-2026/), [RecordingLaw](https://www.recordinglaw.com/world-laws/world-data-privacy-laws/egypt-data-privacy-laws/) |
| Consent | Documented and auditable consent. Implied consent only for what is strictly necessary for the requested service. **No secondary use.** | [Legal500](https://www.legal500.com/developments/thought-leadership/overview-of-the-executive-regulations-of-the-egyptian-personal-data-protection-law/) |
| **Direct electronic marketing** | **A separate licence.** Explicit, marketing-specific consent. Sender identification, opt-out channel, marketing registers, erasure on withdrawal. Fee is 10% of the main licence fee for own marketing, 25% for third-party marketing (percentages per Baker McKenzie only; Legal500 confirms the separate own/third-party licence categories but gives no percentages [corrected attribution]). | [Legal500](https://www.legal500.com/developments/thought-leadership/overview-of-the-executive-regulations-of-the-egyptian-personal-data-protection-law/), [Baker McKenzie](https://connectontech.bakermckenzie.com/egypt-important-data-protection-update/) |
| **Cross-border transfer** | Licence or permit (50% of the local fee). Data-subject consent for transfers. Adequacy assessment. The PDPC decides within 90 working days, and **silence equals refusal**. | [Legal500](https://www.legal500.com/developments/thought-leadership/overview-of-the-executive-regulations-of-the-egyptian-personal-data-protection-law/), [RecordingLaw](https://www.recordinglaw.com/world-laws/world-data-privacy-laws/egypt-data-privacy-laws/) |
| Children | Always sensitive data. Under 15 requires explicit written guardian consent. Profiling is restricted. | [RecordingLaw](https://www.recordinglaw.com/world-laws/world-data-privacy-laws/egypt-data-privacy-laws/), [Baker McKenzie](https://connectontech.bakermckenzie.com/egypt-important-data-protection-update/) |
| Breach | Notify the PDPC within **72 hours** and individuals within **3 working days** after that | [Baker McKenzie](https://connectontech.bakermckenzie.com/egypt-important-data-protection-update/) |
| Data subject requests | Reply within **6 working days** | [RecordingLaw](https://www.recordinglaw.com/world-laws/world-data-privacy-laws/egypt-data-privacy-laws/) |
| CCTV | Visual surveillance needs a licence or permit (AMERELLER: EGP 1,000 for 3 years or EGP 500/yr). Exception for private residences within property boundaries. Whether a **building's shared common areas** fall under the exemption is **UNVERIFIED**. | [AMERELLER](https://amereller.com/publication/the-egyptian-personal-data-protection-regime-what-you-need-to-know-ahead-of-31-october-2026/), [Baker McKenzie](https://connectontech.bakermckenzie.com/egypt-important-data-protection-update/) |
| Foreign entities | Must appoint a PDPC-approved local representative | [Baker McKenzie](https://connectontech.bakermckenzie.com/egypt-important-data-protection-update/) |

### 4.3 Penalties (criminal, before the Economic Courts)

| Violation | Penalty (EGP) |
|---|---|
| Unauthorised processing | 100,000 to 1,000,000 |
| Aggravated unauthorised processing | ≥6 months prison and/or 200,000 to 2,000,000 |
| Sensitive data / cross-border violations | ≥3 months prison and/or 500,000 to 5,000,000 |
| Processing **without licence** (Art. 45) | 500,000 to 5,000,000 |
| No registered DPO | 200,000 to 2,000,000 |
| **Unauthorised direct electronic marketing** | 200,000 to 2,000,000 |
| Controller/processor/breach-reporting failures | 300,000 to 3,000,000 |
| Repeat offence | Doubled |

Source: [RecordingLaw summary](https://www.recordinglaw.com/world-laws/world-data-privacy-laws/egypt-data-privacy-laws/). Confirm against the law text before relying on these figures.

### 4.4 What PDPL means for each founder idea

| Founder idea | PDPL issue | Compliant design |
|---|---|---|
| **Per-individual personalised notifications** | Operational notices (dues, GA, water cut) fall within the service's necessary processing. **Promotional notices for third-party services are "direct electronic marketing"**, which needs a licence plus explicit opt-in. | Two separate consent toggles from day one: (1) building and service notices, (2) offers and partners. Keep a marketing-consent register. Apply for the marketing licence (10% or 25% fee add-on) **before** phase 2. |
| **Mandatory AI everywhere** | Sending resident data (names, phones, payment data, chat text) to OpenAI, Anthropic or Google APIs hosted abroad is a **cross-border transfer**, which needs a licence or permit plus consent. Automated profiling of residents (for example payment-risk scores) is high-risk. | Minimise and pseudonymise before calls (strip names, IDs and phones; use unit tokens). Prefer zero-retention API terms. List the destination countries in the transfer licence. Get explicit consent at onboarding. Consider in-country hosting for the primary database. No credit-style scoring of residents. |
| **WhatsApp bot in the building group** | Meta, a US/Ireland processor, is a cross-border transfer. Group content includes third parties who never consented to the app. | Process only messages addressed to the bot. Inform members. Keep minimal logs. See section 10 on platform constraints. |
| **Every resident has an account** | National IDs, family members and children | Collect the national ID only for the union member list (purpose-bound), encrypted, visible to the board only. No child accounts under 15 without guardian consent. |
| **Phase 2: sell data-driven services** | Secondary use is prohibited without new consent | Explicit opt-in for "recommendations and offers". Never sell or share lists with vendors. Vendors see only job-specific data. |

### 4.5 Immediate PDPL to-do (ESTIMATE, 30 days)

1. Appoint or nominate a DPO (internal employee). Register for the PDPC exam when it is available.
2. Build a records of processing (RoPA) map: data categories, purposes, retention, recipients, transfers.
3. Estimate record volume. If **under 10,000 or 100,000 records** (depending on which source is right), the controller licence fee may be **zero** in year 1. Still file.
4. Draft an Arabic privacy notice, a consent UX with separate toggles, and a DSR flow (6 working days).
5. Prepare a cross-border transfer application (cloud region and LLM vendors).
6. Write a breach runbook (72 hours and 3 working days).

---

## 5. Cybercrime Law No. 175 of 2018 (service-provider duties)

| Item | Detail | Source |
|---|---|---|
| Who | "مقدم الخدمة" includes anyone who stores or processes information for users (Art. 1). An app operator likely qualifies (**ESTIMATE**). | [lawyeregypt.net](https://lawyeregypt.net/?p=5525) |
| Log retention | Keep system logs (user identification, traffic, device data, and content data where under the provider's control) **for 180 consecutive days** (Art. 2) | same |
| Confidentiality | No disclosure without a reasoned judicial order (Art. 2) | same |
| Penalties | Retention breach: **EGP 5 to 10 million** (Art. 33). Confidentiality breach: ≥1 year prison plus a fine per affected user (Art. 31). Account or site manager negligence: Art. 29. | same |

**Tension with PDPL minimisation:** retain *system logs* for 180 days, but not message content beyond what is needed. Document this split.

---

## 6. Payments: collecting money on behalf of others

### 6.1 The CBE framework

- **Banking Law No. 194 of 2020, Arts. 184 to 200**, plus the **CBE Licensing and Registration Rules for Payment System Operators and Payment Service Providers**, issued **19 June 2025**, with a **12-month transitional grace period for entities already offering payment services** (so that grace ended around June 2026) [corrected: the earlier "in force 17 June 2025" date predates issuance and is unverified]. Governance rules were added 1 Sep 2025 ([Matouk Bassiouny](https://matoukbassiouny.com/egypts-central-bank-issues-the-licensing-framework-for-psos-and-psps/), [Lexis ME](https://www.lexismiddleeast.com/news/2025-06-20_38/en), [Daily News Egypt](https://www.dailynewsegypt.com/2025/06/21/cbe-issues-new-licensing-framework-for-electronic-payment-service-providers/)).
- **Licensable activities** include payment transactions and transfers, issuing payment instruments, e-money, payment accounts and "**electronic acceptance services, such as payment technology, facilitation, and cash collection**". They apply to entities inside or outside Egypt serving Egyptian residents ([Matouk Bassiouny](https://matoukbassiouny.com/egypts-central-bank-issues-the-licensing-framework-for-psos-and-psps/)).
- **Capital:** Category B is **EGP 10M** (below EGP 750M per month in volume). Category A is **EGP 30M** (above EGP 750M average monthly volume); a payment-initiation / account-information licence needs EGP 20M [corrected: added]. Add a bank letter of guarantee of 2% of capital. The process is two-step (No Objection Certificate, then licence), with 90 + 90 days per step ([Matouk Bassiouny](https://matoukbassiouny.com/egypts-central-bank-issues-the-licensing-framework-for-psos-and-psps/)).
- Earlier practice: CBE approvals for **aggregators and facilitators were issued to the sponsoring bank**, not the fintech ([Al Tamimi](https://www.tamimi.com/law-update-articles/fintech-in-egypt-be-aware-of-the-regulatory-landscape/), older).
- **Gap:** no source explicitly says whether a marketplace that only *instructs* a licensed PSP to split funds needs its own licence. **Get a written opinion from counsel or the PSP.**

**Conclusion (ESTIMATE):** a startup with no marketing budget cannot fund EGP 10M or more of capital plus compliance. **The app must never hold, pool or move residents' money itself.** All flows must go into the union's own account, or through a licensed PSP's marketplace or split product.

### 6.2 Partner options

| Partner | Relevant capability (2026) | Published pricing | Notes | Source |
|---|---|---|---|---|
| **Paymob** | **"Marketplace by Paymob": accept payments and distribute payouts automatically.** Payouts and "onboarding merchants under your own partner integration". | 2.75% + EGP 3 standard; weekly settlement | Best fit for phase 2 split commissions. About 390k businesses. | [Paymob](https://www.paymob.com/en/about-us), [Paymob docs](https://developers.paymob.com/paymob-docs/getting-started/overview), [comparison, Aug 2026](https://www.kerolosxgad.com/writing/payment-gateways-egypt-comparison), [Forbes ME](https://www.forbesmiddleeast.com/lists/the-middle-easts-fintech-50-2025/paymob/) |
| **Kashier** | CBE-approved payment facilitator/PSP. Strong on subscriptions and recurring payments. Marketplace offering listed but not detailed. | 2.75% + EGP 3, no setup fee; 3-day settlement | Good for recurring monthly dues | [comparison](https://www.kerolosxgad.com/writing/payment-gateways-egypt-comparison), [KrASIA](https://kr-asia.com/egyptian-payments-platform-kashier-raises-six-figure-seed), [Zawya](https://www.zawya.com/company/5079202035/kashier) |
| **Fawry** | Dominant cash and bill-payment network (retail outlets, ATMs, wallets). First licensed banking agent. | Per merchant (about 1.5 to 2.5% commonly cited) | **Critical for cash-paying older residents.** Becoming a Fawry biller lets residents pay dues in cash at a kiosk. | [comparison](https://www.kerolosxgad.com/writing/payment-gateways-egypt-comparison), [TechCabal 2026](https://techcabal.com/2026/04/20/how-fawry-built-a-profitable-fintech/) |
| **Geidea** | Pay-by-link, Meeza QR, SoftPOS | Per merchant | Useful for technicians collecting on-site (SoftPOS) | [Geidea docs](https://docs.geidea.net/edit/tamara), [Wamda](https://www.wamda.com/2024/11/geidea-extends-softpos-services-egypt) |
| **InstaPay (IPN)** | Instant account-to-account transfers. **22M registered customers, 1.47bn transactions and EGP 4.33tn by Q2 2026.** | Sender pays 0.1% (min EGP 0.50, max EGP 20) since 1 Apr 2025 (one outlet reports a EGP 1 minimum). Monthly cap reported at EGP 400k. Limits EGP 70k per transaction, EGP 120k per day. | Most building treasurers already collect via InstaPay to personal accounts. The app can **reconcile, not collect**. | [Egypt Today](https://www.egypttoday.com/Article/3/149807/Egypt’s-instant-payment-transactions-reach-LE-4-33TN-in-Q2), [Banker](https://banker.news/153864), [Akhbar El-Yom](https://m.akhbarelyom.com/news/newdetails/4823018/1/) |

Onboarding with any PSP typically needs a **commercial register, tax card, bank account and compliance review**, which takes days to weeks ([comparison](https://www.kerolosxgad.com/writing/payment-gateways-egypt-comparison)).

### 6.3 A staged, licence-light money architecture (ESTIMATE / recommendation)

| Stage | Model | Who receives money | Licence exposure |
|---|---|---|---|
| **P1: Ledger only** (launch) | Dues ledger, reminders, "I paid" with InstaPay reference or screenshot, treasurer one-tap confirm, AI OCR of transfer screenshots, receipts | Treasurer or union account directly (InstaPay, cash) | **None** (no funds touched) |
| **P2: Union-owned PSP links** | Each *registered* union (it has legal personality under Art. 76) opens its own Paymob or Kashier merchant account. The app embeds that union's links. | Union's account | Low. The PSP is licensed and the app is a tech integrator. Unregistered buildings stay on P1, which pushes registration. |
| **P3: Marketplace split** (phase 2 services) | Resident pays for a plumber via Paymob Marketplace. The PSP splits technician share and app commission. | PSP settles to the technician and the app | Low to medium. Get PSP and counsel confirmation that **you are not "facilitating"** yourself. |
| **P4: Own PSP licence** | Only at large scale (EGP 10M+ capital) | App | High |

**Unregistered unions** have no legal personality, and opening a merchant or bank account in the union's name is likely impossible. Whether a union can open a bank account and what documents banks require is **UNVERIFIED**. This is a natural growth lever: **"Register your union in the app → unlock online payments."**

---

## 7. Tax: VAT, e-invoicing, and the startup's own tax

| Topic | Rule | Source |
|---|---|---|
| VAT registration | Mandatory once annual sales reach **EGP 500,000** (rolling 12 months). Register within 30 days. | [Andersen](https://eg.andersen.com/e-commerce-and-taxation/), [Tamimi](https://www.tamimi.com/law-update-articles/the-digital-economy-and-recent-taxation-implications-the-case-of-egypt), [Afrotools](https://afrotools.com/blog/egypt-vat-guide-2026/) |
| Rate | **14%** on taxable services | [Chambers](https://gpg-pdf.chambers.com/view/731628805/61/) |
| E-commerce enforcement | The ETA has an **e-commerce unit** targeting platforms and content creators. Online delivery services were added to the taxable list (Decree 285/2021). | [Tamimi](https://www.tamimi.com/law-update-articles/the-digital-economy-and-recent-taxation-implications-the-case-of-egypt) |
| E-invoice / e-receipt | Mandatory phased systems run via the ETA portal. E-receipt phases started under decrees 289, 345 and 588 of 2022. Phase 3 started 15 Jan 2023. | [VATit](https://vatit.com/e-invoicing-guide/egypt/), [Al-Bawaba](https://www.albawabhnews.com/4335587) |
| Simplified regime | **Law 6/2025** (effective 1 Mar 2025): turnover-based tax for businesses with turnover **≤ EGP 20M**, at rates around 0.4% to 1.5% of revenue (sources differ). Exemptions from stamp tax, development fees and dividend withholding. Must apply. | [EY](https://www.ey.com/en_gl/technical/tax-alerts/egypt-introduces-tax-incentives-and-benefits-for-small-enterprises), [Andersen AR](https://eg.andersen.com/ar/egypts-new-tax-reform-2025/), [Egyptian Streets](https://egyptianstreets.com/2025/06/02/egypt-launches-new-tax-incentives-to-boost-investment-and-support-small-businesses/) |

**Commission model (ESTIMATE, confirm with a tax adviser):**

- If the app acts as an **agent** (the technician sells to the resident and the app earns a commission), VAT applies to the **commission** once over the threshold. The technician is responsible for VAT on their own service, and most are under the threshold or informal.
- If the app acts as **principal** (it sells "home maintenance" and subcontracts), VAT and consumer-law liability (section 8) apply to the **full price**.
- **Agent structure is safer on both tax and consumer liability**, but the UX must make the technician the contracting party: name, receipt, warranty.
- Union maintenance contributions collected by the union are not the app's revenue. Keep them off the app's books.

**Company form:** a One-Person Company (OPC, Law 4/2018, minimum capital about EGP 1,000) or an LLC (2+ partners), registered via GAFI in 1 to 2 days ([Al Zayat](https://alzayatfirm.com/practice/sole-proprietorship/), [Legal500](https://www.legal500.com/guides/chapter/egypt-doing-business-in/)). Capital figures differ by source, so verify with GAFI. The company form matters because PSPs and the PDPC require a legal entity.

---

## 8. Consumer Protection Law No. 181 of 2018 (phase 2 marketplace)

| Article | Rule | Relevance | Source |
|---|---|---|---|
| Art. 1(5), 1(6), 1(8) | "Supplier" includes sales "بأي طريقة… بما في ذلك الوسائل الإلكترونية". "Advertiser" includes digital means. Distance contracting includes the internet and phone. | A platform that markets services can be treated as supplier or advertiser | [Al-Beronsy text](https://alberonsy.com/?p=3138) |
| Art. 9 | No misleading conduct on price, features and so on | Display total price, fees and commission | same |
| Art. 25 | Defective service: refund, make good or redo | Needs a dispute and redo flow | same |
| **Art. 26** | **Finishing, maintenance and home-installation providers guarantee work and supplied parts for at least 1 year** (3 years for gross fraud or negligence), and must issue **a written receipt before starting work** | **Core design requirement.** The app should auto-issue a digital work order or receipt and a 1-year warranty card. | same |
| Art. 37 | Pre-contract disclosure: supplier identity, price including fees, warranty, withdrawal terms | Booking screen content | same |
| Art. 38 | Written confirmation immediately (email accepted). Right to modify within 7 working days. | Auto-confirmation | same |
| **Art. 40** | **14-day withdrawal** from receipt of goods. Refund via the same method within 7 days. | Spare-parts sales | same |
| Art. 41 | Withdrawal is lost if the service was fully used, for custom-made goods, misuse and similar cases | Services consumed on the spot are largely exempt | same |
| Penalties | Arts. 64 to 66: EGP 10k to 500k; EGP 30k to 1M **or twice the value of the product concerned, whichever is greater** (Art. 65, covering Arts. 25, 26) [corrected]; EGP 50k to 2M (Art. 9, misleading). Doubled on repeat. **Managers personally liable (Art. 74).** | | same |

The Consumer Protection Agency accepts complaints 24/7 via its own app ([search result summary](https://banker.news/116544)). I found **no Egypt-specific rule** on intermediary-platform liability for home services. Kuwait (2026) and Turkey have moved to tighten marketplace liability ([Kuwait Times](https://kuwaittimes.com/article/46260/kuwait/other-news/ministry-strengthens-e-commerce-oversight-consumer-protection/), [Mondaq TR](https://www.mondaq.com/turkey/dodd-frank-consumer-protection-act/1809336/)). Egypt could follow (**ESTIMATE**).

**Turn compliance into a feature:** "ضمان سنة على كل شغلانة" (1-year warranty on every job, legally required anyway), a digital receipt before work, and price shown upfront. These directly address the top complaints about technicians: overcharging, no accountability, no warranty.

---

## 9. Real-estate brokerage regulation (if the app lists units)

- New regulation **No. 578 of 2026**. Sources inconsistently call it a law or a decision, and one cites 576. It creates a **mandatory register of real-estate brokers**; registration is a prerequisite to practise. Categories cover sale, purchase, dual and rental. For legal entities: Egyptian ownership, minimum paid-up capital EGP 20,000, a training course, written contracts, and classes A to D by deal value. Reported fines up to EGP 1M. The register is reportedly kept by GOEIC ([Sadany & Khalifa](https://sadanykhalifa.com/ar/single-blog/%D8%A7%D9%84%D8%B3%D9%85%D8%B3%D8%B1%D8%A9%20%D8%A7%D9%84%D8%B9%D9%82%D8%A7%D8%B1%D9%8A%D8%A9), [Al-Dostor](https://www.dostor.org/5654722), [Youm7](https://www.youm7.com/story/2026/8/7/)).
- An AML compliance decree for brokers: Ministry of Trade & Industry **Decree 173 of 2026** ([Mesfer Law](https://mesferlaw.com/)).
- **Platforms:** the texts I found do not expressly license platforms. Commentators expect platforms to remove unregistered brokers' ads ([Al-Dostor](https://www.dostor.org/5654722)).

**Implication:** In phase 2, do **not** act as a broker charging commission on rentals or sales without registering. Safer options: let owners list directly (classifieds, flat fee), or partner with registered brokers.

---

## 10. Labour classification: technicians, the building guard (البواب), and the gig model

### 10.1 Labour Law No. 14 of 2025

- Signed 3 May 2025, **in force 1 Sep 2025**. It replaces Law 12/2003 ([Andersen](https://eg.andersen.com/egypts-labour-law-14-2025/), [Mondaq](https://admin.mondaq.com/india/employee-rights-labour-relations/1670356/)).
- It recognises "new work patterns", **including work via digital platforms**, plus remote, part-time and flexible work. These workers get the same core rights (social insurance, minimum wage and so on) **where work is done "for an employer, under its direction or supervision, in return for pay"** ([Masaar summary via search](https://masaar.net/en/modern-work-patterns-in-the-new-labor-law/), [lawyeregypt.net](https://lawyeregypt.net/?p=31341)).
- Platform provisions are "extremely brief" and **depend on executive regulations not yet issued** (per Masaar/Defense, Sep 2025). I found no confirmation that they have been issued by Oct 2026 (**UNVERIFIED**) [unverified: re-checked 12 Oct 2026, no source found].
- The employee/contractor line follows the **subordination test** (تبعية) ([Mellow](https://mellow.io/news-and-articles/hiring-contractors-in-egypt-without-labour-law-violations-4827)).
- Contracts are presumed permanent, and four copies must be issued (employer, employee, social insurance, labour office) ([Andersen](https://eg.andersen.com/egypts-labour-law-14-2025/)).

**Design rules to keep technicians independent (ESTIMATE, review with counsel):**

| Do | Avoid |
|---|---|
| Technician sets their own prices, or quotes per job | Fixed shifts, mandatory acceptance rates |
| Technician can refuse jobs and work on other platforms | Exclusivity, uniforms, app-imposed discipline |
| Per-job, PSP-split payment to the technician | Monthly salary-like payouts |
| Ratings shown to customers | Deactivation as a "disciplinary" tool without process |
| Technician's own tools and own receipt (Consumer Art. 26) | App-issued "employee" IDs |

### 10.2 The building guard (حارس العقار / البواب)

- I found **no clear statute** making the union the guard's statutory employer, and **no source confirming** social-insurance treatment of guards under Law 148/2019 (**UNVERIFIED**). A parliamentary proposal to license the guard profession by amending Law 68/1970 (private guards) was reported but not enacted ([Mobtada](https://www.mobtada.com/print/724844)).
- **App implication:** Give guards a free "staff" role (task list, visitor log, package log, payment confirmation) without the app becoming their employer. Record any salary paid by the union as a union expense, not via the app's payroll.

---

## 11. WhatsApp / Meta: platform rules that act like law

### 11.1 What the rules say

| Rule | Text or detail | Source |
|---|---|---|
| WhatsApp ToS (consumer) | Users must not "involve sending illegal or impermissible communications such as **bulk messaging, auto-messaging, auto-dialing**", "involve any **non-personal use** of our Services unless otherwise authorized by us", or "create accounts… through unauthorized or **automated means**" | [WhatsApp ToS](https://www.whatsapp.com/legal/terms-of-service) |
| Unofficial libraries | whatsapp-web.js and Baileys violate the ToS. Bans are ML-driven and unpredictable. Their READMEs warn they are "not guaranteed you will not be blocked". | [checkleaked guide](https://whatsapp.checkleaked.cc/blog/avoid-whatsapp-ban), [bot.space](https://www.bot.space/blog/whatsapp-api-vs-unofficial-tools-a-complete-risk-reward-analysis-for-2025) |
| **Official Groups API** | Requires an **Official Business Account (OBA)**. **Max 8 participants.** Up to 10,000 groups per number. **Max 1 Cloud API business per group.** **Invite-link only.** No interactive messages, calls, editing or deleting in groups. | [Meta developer docs](https://developers.facebook.com/docs/whatsapp/cloud-api/groups) |
| **AI providers clause** | From **15 Jan 2026**, Meta bars general-purpose AI assistants as the core product on the Business API. **Business-specific bots (customer service and similar) remain allowed.** | [TechCrunch](https://techcrunch.com/2025/10/18/whatssapp-changes-its-terms-to-bar-general-purpose-chatbots-from-its-platform), [Gulf News](https://gulfnews.com/technology/no-more-chatgpt-and-perplexity-on-whatsapp-meta-bans-major-ai-chatbots-from-2026-1.500316016) |
| Business Messaging Policy (updated 23 Sep 2026) | Opt-in required. **"Prompt, clear, and direct escalation paths"** to humans required. Don't request full card or account numbers in chat. Don't reuse Meta data beyond the thread. | [WhatsApp Business Policy](https://whatsappbusiness.com/policy/) |
| Opt-in | Opt-in can be general (not WhatsApp-specific) if it names the business and complies with local law. Can be collected in-app or on paper. | [Meta: Get opt-in](https://developers.facebook.com/documentation/business-messaging/whatsapp/getting-opt-in) |
| Egypt pricing | Meta cut Egypt utility and authentication rates (1 Oct 2025) and the marketing rate (1 Jan 2026). A third party lists **marketing about $0.0644, utility about $0.0036, authentication about $0.0036 per message (+14% VAT)**. Treat as **UNVERIFIED** [unverified: Meta's pricing page confirms the Oct 2025 utility/auth and Jan 2026 marketing cuts for Egypt but publishes USD figures only in a separate rate card]. | [Meta pricing](https://developers.facebook.com/documentation/business-messaging/whatsapp/pricing), [ChatMaxima](https://chatmaxima.com/whatsapp-api-pricing/egypt/) |

### 11.2 Verdict on the founder's idea: a "bot that joins the building's WhatsApp group"

| Approach | Feasible? | Risk | Verdict |
|---|---|---|---|
| Official Cloud API bot in the **existing big residents' group (20 to 200 people)** | **No.** Groups API groups are created by the business, capped at 8, and invite-only. A Cloud API number cannot join an arbitrary consumer group. | n/a | Not possible |
| Unofficial bot (personal number via whatsapp-web.js or Baileys) joining big groups | Technically yes | **ToS breach, unpredictable bans** (a ban kills the bot for every building at once), PDPL exposure for reading all members' messages, reputational damage | **Do not build the core product on this.** At most a short, clearly labelled pilot on throwaway numbers. |
| **Official Groups API "board group" (لجنة الاتحاد)**: bot + president + treasurer + members, ≤8 seats | **Yes**, with an OBA. The statutory board is 3 or 4 people (Art. 78), which fits within 8. | Requires OBA status (green tick), which is hard for a new startup. Eligibility details vary by source. | **Strong target for year 2.** The bot drafts notices, tracks dues and answers the board. |
| **1:1 "building assistant" number** (official Cloud API) | Yes | Low. Business-specific AI is allowed. | **Primary design.** Each resident chats 1:1: "I paid", "water is cut", "book a plumber". |
| **Template broadcasts** to residents who opted in (utility category) | Yes | Cost per message | Use for GA invitations, dues reminders and outages |
| "Share to bot" or a link-in-group pattern: the board pastes the app's deep links or summaries into the existing group | Yes | None | **Growth hack:** the app generates a nicely formatted Arabic message for the board to paste, with links that pull residents into the app or the 1:1 bot |
| In-app group chat (own infrastructure) | Yes | PDPL only | Long-term replacement of the WhatsApp group |

---

## 12. Other telecom and tech rules

| Topic | Rule | Source |
|---|---|---|
| SMS sender ID (OTP and notices) | Alphanumeric sender IDs must be registered with each network. Needs commercial register, tax card and NOC. About 15 business days to 3 weeks. Marketing SMS only to consenting users, during restricted hours (vendor claims). | [D7 Networks](https://d7networks.com/sms/egypt/sender-id-registration), [sent.dm](https://www.sent.dm/resources/egypt-sms-guide) (vendor sources) |
| IoT hardware (smart locks, intercoms, gate controllers) | Wireless or telecom devices need **NTRA type approval** plus per-shipment clearance. 3G-only devices are no longer approved (date disputed: Oct 2025 or Jun 2026). | [Carra Globe](https://carraglobe.com/importer-of-record-egypt/), [CAICT](https://gma.caict.ac.cn/en/update/1/1031) |
| AI regulation | **No AI statute in force.** A draft AI law is being prepared with Parliament's ICT committee. The **Egyptian Charter for Responsible AI** (Apr 2023) and the **National AI Governance Framework** (Mar 2026) are soft law. PDPL applies to AI processing. | [Legal500 AI guide 2026](https://www.legal500.com/guides/chapter/egypt-artificial-intelligence/), [NCAI framework (PDF)](https://ai.gov.eg/SynchedFiles/ar/Resources/Guide%20to%20Egypt%E2%80%99s%20National%20AI%20Governance%20Framework%2015-3-2026.pdf), [Responsible AI Charter](https://aicm.ai.gov.eg/en/Resources/EgyptianCharterForResponsibleAIEnglish-v1.0.pdf) |

**AI design guardrails (ESTIMATE):** follow the Responsible AI Charter now (human oversight, transparency, an "AI-generated" label on bot replies, human escalation per the WhatsApp policy). This will ease compliance when the AI law lands.

---

## 13. Licences, registrations and partners: master checklist

| # | Item | Authority / partner | When | Est. cost (ESTIMATE unless sourced) | Priority |
|---|---|---|---|---|---|
| 1 | Company (OPC or LLC), commercial register, tax card | GAFI / ETA | Pre-launch | Low (minimum capital about EGP 1k per sources, plus fees and lawyer) | Must |
| 2 | Simplified tax regime application (Law 6/2025) | ETA | At registration | Free | Must |
| 3 | VAT registration | ETA | When turnover reaches EGP 500k | n/a | Later |
| 4 | E-invoice / e-receipt onboarding | ETA | When B2B or B2C invoicing starts | Integration cost | Phase 2 |
| 5 | **PDPC controller (or controller/processor) licence** | PDPC | **Now (deadline about 31 Oct / 1 Nov 2026)** | Possibly EGP 0 at low volume; tiered after | **Must** |
| 6 | **Registered DPO** | PDPC exam | Now | Internal salary share | **Must** |
| 7 | **Cross-border transfer licence/permit** (cloud abroad, LLM APIs, Meta) | PDPC | Before using foreign processors | 50% of the main fee | **Must** (if hosting or AI abroad) |
| 8 | **Direct electronic marketing licence** | PDPC | Before phase 2 promotions | 10% (own) or 25% (third-party) of the main fee | Phase 2 must |
| 9 | CCTV / visual surveillance licence (if the app operates cameras) | PDPC | If feature launched | EGP 500/yr or EGP 1,000 per 3 years | Optional |
| 10 | WhatsApp Business Platform (Cloud API) via Meta or a BSP; OBA for Groups API later | Meta | Launch (1:1); later (groups) | Per-message | Must |
| 11 | SMS sender ID registration | Mobile operators / aggregator | Launch | Low | Must |
| 12 | PSP merchant accounts (app: Paymob Marketplace / Kashier; unions: their own) | Paymob, Kashier, Fawry, Geidea | Phase 1b to 2 | 2.75% + EGP 3 per transaction (published) | Must for payments |
| 13 | Fawry biller integration (cash payments) | Fawry | Phase 2 | Negotiated | High value |
| 14 | Own PSP licence | CBE | Only at scale | EGP 10M+ capital | Avoid |
| 15 | Broker registration (if earning commission on rentals or sales) | GOEIC register (per sources) | If listings are monetised | Capital EGP 20k+, class fees | Optional |
| 16 | NTRA type approval (if selling hardware) | NTRA | If hardware is added | Per device | Optional |
| 17 | Lawyer partner network (payment orders, union registration, old-rent disputes) | Private law firms | Phase 2 (referral revenue) | Rev-share | Opportunity |
| 18 | District technology centres / governorates (union registration campaigns) | Local units (الأحياء) | Launch | Relationship | **Growth lever** |

---

## 14. Risk register

| # | Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|---|
| R1 | Operating without a PDPC licence or DPO after the deadline | High (if ignored) | Very high (EGP 0.5 to 5M, criminal) | File now, appoint a DPO, keep records |
| R2 | Phase-2 promotions sent without a marketing licence or opt-in | Medium | High (EGP 0.2 to 2M) | Separate consent toggles, marketing licence, opt-out |
| R3 | Treated as an unlicensed PSP because the app touches funds | Medium | Very high (CBE enforcement, shutdown) | Ledger-only plus licensed PSP splits. Written PSP/counsel opinion. |
| R4 | WhatsApp ban of unofficial bot numbers | High (if unofficial) | High (feature dies for all buildings) | Official Cloud API, 1:1 bot, board group ≤8 |
| R5 | Cross-border data via LLMs without licence or consent | High (AI is mandatory) | High (EGP 0.5 to 5M) | Pseudonymise, transfer licence, consent, consider local or regional models |
| R6 | Technicians reclassified as employees (Law 14/2025 regulations) | Low to medium | Medium to high | Independence design (section 10.1). Monitor executive regulations. |
| R7 | Consumer-law liability for technician defects (Art. 26) | Medium | Medium (EGP 30k to 1M) | Agent model, technician as the named supplier, warranty flow, vetting, dispute handling |
| R8 | Union-law amendments change procedures (for example, a state e-register) | Medium | Medium (or positive) | Modular workflows. Engage in consultation. |
| R9 | Defamation or privacy disputes inside building chat (naming defaulters) | Medium | Medium | Arrears visible only to the board. Neutral automated notices. Never auto-shame in groups. |
| R10 | Cybercrime-law log retention failure | Low | High (EGP 5 to 10M) | 180-day system logs, access control |
| R11 | Old-rent political volatility (amendments, court rulings) | Medium | Low to medium | Keep calculators configurable. No legal advice. |
| R12 | Acting as an unregistered broker on listings | Low (phase 2) | Medium (up to EGP 1M reported) | Classifieds model or registered partner |

---

## 15. Regulation as a growth weapon (zero-budget angle)

1. **"Legal compliance" is a free marketing message.** Districts are already telling residents that forming a union is a legal obligation ([El-Watan](https://www.elwatannews.com/news/details/8298565)). An app that says "Form your union legally in 10 minutes. We prepare all 8 documents." rides that campaign at zero cost. Pitch districts' technology centres to recommend it (**ESTIMATE**: a plausible, low-cost partnership).
2. **Registration forces whole-building onboarding.** The member list must include *every* owner and tenant with ID, so one motivated board member must bring in everyone. That is the virality the founder wants.
3. **Enforcement unlocks payments.** Only registered unions have legal personality (Art. 76), so they can hold PSP accounts and use the payment-order path (Art. 87). The ladder is "register → collect online → enforce", and each step deepens lock-in.
4. **Transparency for compounds.** Deposit and fee opacity is a front-page issue in Sep 2026 ([Banker](https://banker.news/154253)). Offer a free "transparency ledger" to owner groups pressuring developers.
5. **Old-rent turbulence** creates a need for neutral rent calculators and digital rent receipts for 1.6M units.
6. **Consumer-law warranty as brand:** "ضمان سنة بالقانون" makes the phase-2 marketplace instantly more trustworthy than informal WhatsApp technician referrals.
7. **PDPL compliance as a moat.** Most small competitors and informal tools will not be PDPC-licensed. Being licensed is a selling point to compounds, developers and municipalities (**ESTIMATE**).

---

## 16. Compliance budget: ESTIMATE for year 1

| Item | ESTIMATE (EGP) | Reasoning |
|---|---|---|
| Company setup plus lawyer | 15,000 to 40,000 | Typical Cairo small-firm fees. OPC minimum capital is tiny. |
| PDPC licence fee | 0 to 1,000 | Under 10k or 100k records is exempt, depending on source; small tiers above that |
| Cross-border transfer and marketing add-ons | 0 to 500 (year 1) | 50%, 10% or 25% of a near-zero base |
| DPO (part-time role of an employee plus exam or training) | 20,000 to 60,000 | Training or certification costs, internal time |
| Privacy and terms drafting (Arabic and English) | 15,000 to 50,000 | One-off |
| Legal opinion on payments model (PSP and CBE) | 20,000 to 60,000 | One-off. Critical before phase 2. |
| Tax accountant (simplified regime) | 1,500 to 4,000 per month | Market rate |
| WhatsApp messaging | Variable | At about $0.0036 per utility message (unverified), 100k reminders per month is about $360 per month |
| **Total one-off (rough)** | **about 70k to 210k EGP** | Excludes salaries and messaging |

All figures above are ESTIMATES, not sourced quotes.

---

## 17. What I could not verify (open questions for counsel)

1. Exact Civil Code articles on apartment ownership and associations (verified text not retrieved).
2. The union registration fee at districts, and whether **electronic GA invitations and e-voting** are legally valid under the current ER (one source says there is no provision).
3. Whether a registered union can open a **bank account or PSP merchant account** in its name, and the required documents.
4. Whether a marketplace instructing a PSP split needs any CBE registration of its own.
5. PDPC portal operational status, the definitive fee tiers (10k vs 100k exemption) and DPO exam schedule.
6. Whether Law 14/2025's platform-work executive regulations have been issued.
7. The social-insurance status of building guards and the legal employer.
8. The exact legal form and number of the 2026 brokerage regulation (578 vs 576; law vs decree).
9. The current e-receipt obligation for small service providers and the VAT treatment of platform commissions.
10. Official Meta per-message prices for Egypt in USD, and current OBA eligibility criteria for the Groups API.

---

## 18. Sources (primary first)

**Primary or official texts**
- Law 119/2008 text: https://ar.wikisource.org/wiki/قانون_البناء_الموحد_119_لسنة_2008_(مصر)
- Law 119/2008 plus ER (EN translation): https://eg.andersen.com/translation-of-law-no-119-of-2008/
- Law 151/2020 (EN): https://eg.andersen.com/wp-content/uploads/2025/06/Law-No.-151-OF-2020.pdf
- Law 181/2018 consumer protection text: https://alberonsy.com/?p=3138
- Law 175/2018 cybercrime text: https://lawyeregypt.net/?p=5525
- Meta Groups API docs: https://developers.facebook.com/docs/whatsapp/cloud-api/groups
- WhatsApp ToS: https://www.whatsapp.com/legal/terms-of-service
- WhatsApp Business Policy: https://whatsappbusiness.com/policy/
- Meta opt-in docs: https://developers.facebook.com/documentation/business-messaging/whatsapp/getting-opt-in
- Meta pricing: https://developers.facebook.com/documentation/business-messaging/whatsapp/pricing
- NCAI AI Governance Framework (Mar 2026): https://ai.gov.eg/SynchedFiles/ar/Resources/Guide%20to%20Egypt%E2%80%99s%20National%20AI%20Governance%20Framework%2015-3-2026.pdf
- Egyptian Charter for Responsible AI: https://aicm.ai.gov.eg/en/Resources/EgyptianCharterForResponsibleAIEnglish-v1.0.pdf
- SIS (State Information Service) on union amendments: https://sis.gov.eg/ (link in section 1.4)

**Law-firm and professional analyses**
- Legal500 PDPL ER overview: https://www.legal500.com/developments/thought-leadership/overview-of-the-executive-regulations-of-the-egyptian-personal-data-protection-law/
- Baker McKenzie PDPL update: https://connectontech.bakermckenzie.com/egypt-important-data-protection-update/
- AMERELLER PDPL alert: https://amereller.com/publication/the-egyptian-personal-data-protection-regime-what-you-need-to-know-ahead-of-31-october-2026/
- S&H PDPL: https://www.shandpartners.com/insights/briefings/telecoms-media-technology/egypt-personal-data-protection-law-compliance-developments/
- Chambers Data Protection 2026 Egypt: https://practiceguides.chambers.com/practice-guides/data-protection-privacy-2026/egypt
- RecordingLaw PDPL summary: https://www.recordinglaw.com/world-laws/world-data-privacy-laws/egypt-data-privacy-laws/
- Matouk Bassiouny CBE PSP rules: https://matoukbassiouny.com/egypts-central-bank-issues-the-licensing-framework-for-psos-and-psps/
- Lexis ME on PSP rules: https://www.lexismiddleeast.com/news/2025-06-20_38/en
- Daily News Egypt PSP: https://www.dailynewsegypt.com/2025/06/21/cbe-issues-new-licensing-framework-for-electronic-payment-service-providers/
- Al Tamimi fintech: https://www.tamimi.com/law-update-articles/fintech-in-egypt-be-aware-of-the-regulatory-landscape/
- Al Tamimi digital tax: https://www.tamimi.com/law-update-articles/the-digital-economy-and-recent-taxation-implications-the-case-of-egypt
- Andersen e-commerce tax: https://eg.andersen.com/e-commerce-and-taxation/
- EY Law 6/2025: https://www.ey.com/en_gl/technical/tax-alerts/egypt-introduces-tax-incentives-and-benefits-for-small-enterprises
- Andersen Labour Law 14/2025: https://eg.andersen.com/egypts-labour-law-14-2025/
- Masaar on platform work: https://masaar.net/en/modern-work-patterns-in-the-new-labor-law/
- Legal500 Egypt AI guide 2026: https://www.legal500.com/guides/chapter/egypt-artificial-intelligence/
- Sadany & Khalifa brokerage 578/2026: https://sadanykhalifa.com/ar/single-blog/السمسرة%20العقارية
- Unitify (union rules summary): https://unitify.com/blog/unions-of-occupants-egypt-new-cities-maintenance-fees

**News (2025 to 2026)**
- El-Watan, Nasr City union campaign (9 Jun 2026): https://www.elwatannews.com/news/details/8298565
- Invest-Gate, union amendments (3 Aug 2026): https://invest-gate.me/news/minister-of-housing-reviews-draft-amendments-to-the-unified-building-law-on-owners-associations/
- Masrawy, union amendments: https://www.masrawy.com/news/realestate-news/details/2026/8/3/3027283/
- Banker News, maintenance after handover (29 Sep 2026): https://banker.news/154253
- Masrawy, 10% maintenance deposits study (19 Sep 2026): https://www.masrawy.com/news/realestate-news/details/2026/9/19/3050278
- Ahram Online, old rent alternative homes: https://english.ahram.org.eg/News/572864.aspx
- Jurist, rental reform: https://www.jurist.org/features/2025/12/09/egypts-rental-reform-balancing-property-rights-and-social-justice-after-decades-of-distortion/
- Masrawy, old rent multipliers: https://www.masrawy.com/news/news_egypt/details/2025/12/1/2900041/
- Al-Ain, alternative housing deadline: https://al-ain.com/article/egypt-old-rent-alternative-deadline-october-2026
- Egypt Today, IPN Q2 2026: https://www.egypttoday.com/Article/3/149807/
- Banker, InstaPay limits 2026: https://banker.news/153864
- TechCrunch, WhatsApp AI provider ban: https://techcrunch.com/2025/10/18/whatssapp-changes-its-terms-to-bar-general-purpose-chatbots-from-its-platform
- Al-Dostor, brokerage law: https://www.dostor.org/5654722
- Akhbar El-Yom, tenant maintenance duty: https://m.akhbarelyom.com/news/newdetails/4825531/1/

**Vendor or secondary (use with caution)**
- Payment gateways comparison (Aug 2026): https://www.kerolosxgad.com/writing/payment-gateways-egypt-comparison
- Paymob about: https://www.paymob.com/en/about-us
- WhatsApp Groups API vendor guides: https://www.unipile.com/whatsapp-group-api/ , https://periskope.app/blog/whatsapp-groups-api-requirements-eligibility-limits
- ChatMaxima Egypt pricing: https://chatmaxima.com/whatsapp-api-pricing/egypt/
- Unofficial WhatsApp ban risk: https://whatsapp.checkleaked.cc/blog/avoid-whatsapp-ban
- SMS sender ID: https://d7networks.com/sms/egypt/sender-id-registration
- NTRA type approval: https://carraglobe.com/importer-of-record-egypt/

---

## Verification log

Adversarial re-check performed 12 Oct 2026 with fresh searches and fetches.

| # | Claim | Verdict | Evidence URL |
|---|---|---|---|
| 1 | Union mandatory for buildings with at least 5 units (Law 119/2008 Art. 72); legal personality on registration (Art. 76) | confirmed | https://ar.wikisource.org/wiki/قانون_البناء_الموحد_119_لسنة_2008_(مصر) |
| 2 | Board = president, treasurer, member; VP added above 7 units (Art. 78); 15-day GA notice (Art. 84); lien (Art. 87) | confirmed | same as above |
| 3 | Fine EGP 10 to 100 per month of non-payment (Art. 109) | confirmed | same as above |
| 4 | PDPL ER = MCIT Decree 816/2025; grace period ends 31 Oct or 1 Nov 2026 | confirmed (date still split between firms) | https://cms.law/en/are/legal-updates/egypt-s-pdpl-executive-regulations-issued-one-year-compliance-countdown-begins ; https://connectontech.bakermckenzie.com/egypt-important-data-protection-update/ |
| 5 | PDPL fee tiers (10k vs 100k exemption, caps) | corrected (band detail; cap wording conflict kept explicit) | https://www.legal500.com/developments/thought-leadership/overview-of-the-executive-regulations-of-the-egyptian-personal-data-protection-law/ |
| 6 | Direct marketing licence fee 10% own / 25% third-party | corrected (attribution: Baker McKenzie only) | https://connectontech.bakermckenzie.com/egypt-important-data-protection-update/ |
| 7 | 72-hour breach notice to PDPC; individuals within 3 working days; cross-border fee 50%, 90 working days, silence = refusal | confirmed | Baker McKenzie and Legal500 links above |
| 8 | CBE PSP rules 19 Jun 2025; Category B EGP 10M, Category A EGP 30M, 2% LG, EGP 750M/month threshold | confirmed; "in force 17 Jun 2025" corrected (12-month grace for incumbents) | https://matoukbassiouny.com/egypts-central-bank-issues-the-licensing-framework-for-psos-and-psps/ |
| 9 | WhatsApp Groups API: OBA required, max 8 participants, invite-link only, 10,000 groups per number, no interactive/edit/delete | confirmed | https://developers.facebook.com/docs/whatsapp/cloud-api/groups |
| 10 | Meta bars general-purpose AI assistants on Business API from 15 Jan 2026; business-specific bots allowed | confirmed | https://techcrunch.com/2025/10/18/whatssapp-changes-its-terms-to-bar-general-purpose-chatbots-from-its-platform ; https://respond.io/blog/whatsapp-general-purpose-chatbots-ban |
| 11 | Egypt WhatsApp USD per-message prices ($0.0644 / $0.0036) | unverified (rate-cut dates confirmed) | https://developers.facebook.com/documentation/business-messaging/whatsapp/pricing |
| 12 | Consumer Law 181/2018 Art. 26: 1-year warranty (3 for fraud/gross negligence), receipt before work; Art. 40 14-day withdrawal | confirmed; Art. 65 penalty corrected ("or twice product value, whichever greater") | https://alberonsy.com/?p=3138 |
| 13 | Old-rent Law 164/2025: 7y residential / 5y non-residential; 15% annual increase from Sep 2026; 1.6M units; 86k applicants; deadline 12 Oct 2026 | confirmed; deadline sourcing corrected | https://english.ahram.org.eg/News/572864.aspx ; https://www.elwatannews.com/news/details/8327488 |
| 14 | Labour Law 14/2025 in force 1 Sep 2025, recognises platform work; executive regs pending | confirmed (in force); regs issuance unverified | https://www.clydeco.com/en/insights/2025/05/egypt-new-labour-law ; https://masaar.net/en/masaar-and-defense-release-research-paper-on-platform-work-in-egypts-new-labor-law |
| 15 | InstaPay 0.1% fee (min EGP 0.50, max EGP 20) from 1 Apr 2025; limits EGP 70k/txn, 120k/day | confirmed (one outlet says EGP 1 minimum) | https://egyptianstreets.com/2025/04/03/instapay-now-charging-transfer-fees ; https://www.egypttoday.com/Article/3/139250/InstaPay-to-start-applying-fees-on-services-transactions-starting-April |
| 16 | VAT 14%, EGP 500k registration threshold; Law 6/2025 simplified regime up to EGP 20M turnover, ~0.4% to 1.5% | confirmed (top rate 1% vs 1.5% still disputed) | https://eg.andersen.com/value-added-tax-in-egypt/ ; https://www.ey.com/en_gl/technical/tax-alerts/egypt-introduces-tax-incentives-and-benefits-for-small-enterprises |
| 17 | Cybercrime Law 175/2018: 180-day log retention (Art. 2), EGP 5M to 10M fine (Art. 33) | confirmed | https://lawyeregypt.net/?p=5525 |
