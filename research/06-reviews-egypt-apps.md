# 06 — Voice of Customer: App-Store Reviews of Egyptian Building, Compound and Home-Service Apps

**Research angle:** What Egyptian users actually say, in their own words, about (a) the new wave of building / owners-association apps (Amarati, Imarti, Ettihad, Sandooq El Emara and others), (b) the compound / developer community apps (TMG Life, Emaar Misr, SODIC, Palm Hills, Mountain View, Lyve, Milango-built apps), and (c) the Egyptian home-services marketplaces we would later compete with or intermediate (FilKhedma, Taskty, Fixawy).
**Date of collection:** 2026-10-12
**Prepared for:** Founder, Egyptian residential building super-app (free adoption first, then a services marketplace)

---

## 0. Executive summary (read this first)

1. **The "building app" category in Egypt is brand new and crowded. Nobody has scale yet.** At least 12 owners-association apps went live on Google Play between **June and September 2026**: Amarati (Jun 21), Amarti/Building Expenses (Jun 7), Imarti (Jul 26), Ettihad (Aug 10), Omaraty (Aug 10), Sandooq El Emara (Aug 25), Homena (Sep 2), Ammarty (Sep 8) and others. **None has more than about 3,000 installs.** The leader by installs is Ettihad at about 3,000; next are Ammarty at 1,684, Amarati at 1,416 and Sandooq at 961. All have fewer than 50 written reviews. The market is wide open, but the race has started. *(Source: Google Play listings, data pulled 2026-10-12; links in §2.)*
2. **Two of the three apps the founder named are not really Egyptian products.** Amarati (`com.amarati.app`) describes itself as *"built by heads of real building committees in Palestine"* and writes its copy in Levantine dialect. Imarti (`com.craftfuture.imarti`) appears to be Saudi (privacy policy hosted on `admin.craftsolutions.com.sa`) [unverified: the policy names only the publisher "Craft Future" and a Gmail contact, with no country or address; Saudi origin is inferred from the .sa domain]. Its only review says *"الاشتراكات غاليه اوي"* ("the subscriptions are very expensive") [unverified: the Play listing declares no in-app purchases, and in this category "الاشتراكات" usually means the building's monthly dues, so the complaint may be about dues, not app pricing]. Saknna (saknna.com) is a web/PWA product with **no store app, so it has no store reviews**. It charges **450 to 7,500 EGP per month**. **The Egyptian-native, free, mass-market position is still open.**
3. **The strongest direct competitor we found is Ettihad (إتّحاد, `com.ittihad.ettihad`).** It is free and supports InstaPay and receipt uploads. It already ships an **AI assistant called "Fary"** that works by text or voice in Arabic and English, plus QR visitor passes, maintenance tickets with photos, and WhatsApp statements. Residents do not need to install the app. One reviewer: *"فكرة اني مش لازم كل السكان ينزل التطبيق ممتازة. وفاري الذكاء الاصطناعي حلم"* ("not every resident needing to install the app is excellent, and Fary the AI is a dream"). The founder's AI idea is therefore **necessary but not differentiating on its own**.
4. **Developer compound apps are hated for reliability, not for missing features.** In 462 Google Play reviews of 13 compound apps, **35% are 1-star** [corrected: recount of the raw CSV gives ~162/462 = 35%, not 44%; 208 of 462 (45%) are ≤3★]. Among negative reviews (≤3 stars), keyword coding gives: **crashes / won't open 41%**, **login / OTP / registration 23%**, **"broke after update" 14%**, **slow 10%**, **support unresponsive 10%**, and **"security alert / blocked device" 8%**. These apps control gate entry, so a bug means *"we stand for ages on the gates not able to go home"*.
5. **Home-service marketplaces are hated for trust, not for the app.** FilKhedma has 178k installs and a 3.07 rating, and its distribution is **621 one-star vs 631 five-star**, which is extremely polarised. **59% of its 2025–2026 reviews are 1-star.** Taskty has 168k installs, a 2.07 rating, and **79% one-star since 2025**. Among negative reviews: **price inflation / overcharging 21%**, **unskilled work or damage 20%**, **no-shows and lateness 17%**, **unresponsive support 16%**, and **explicit "scam / theft" language 14%**. This is the market we plan to enter in Phase 2. **Trust infrastructure is the product.**
6. **The top requests from building-app users are mundane, and they are the wedge.** They ask for unequal fees per unit, zero-fee or exempt units, one-off levies, rent collection, PDF/Excel statements, multiple admins, recording payments for elderly residents who have no smartphone, a complaints channel, and clarity on whether the app is free. **Price anxiety is the number-one pre-adoption question** ("هيبقي مجاني ولا برسوم؟", "will it be free or paid?").
7. **The implication for our strategy:** win on (a) *free forever for the building*, (b) *bulletproof login* (no OTP loops, no single-device bans, works for Egyptians abroad), (c) *works without everyone installing* (WhatsApp-first), and (d) a Phase-2 services layer that fixes the exact trust failures in FilKhedma and Taskty reviews: locked prices, verified technician identity, a warranty that is honoured, and photo evidence. Sections 6 to 8 give details.

**Sample:** 1,511 Google Play reviews from 26 Egyptian apps plus 360 iOS App Store (Egypt storefront) reviews from 15 apps, **1,871 reviews in total**. The raw dataset with source URLs is in `research/data/06-reviews-raw.csv`.

---

## 1. Method and limitations

### 1.1 How the data was collected
- **Google Play:** the open-source `google-play-scraper` library, country `eg`, languages `ar` and `en`, sorted by both *Newest* (up to 400) and *Most relevant* (up to 200), deduplicated by review ID. Metadata collected: installs, exact install count, rating, rating histogram, release date and last update.
- **Apple App Store:** the public iTunes customer-reviews RSS feed for the **Egypt storefront** (`itunes.apple.com/eg/rss/customerreviews/...`), up to 10 pages per app, deduplicated.
- **App discovery:** Play Store search in Arabic and English (عمارتي، اتحاد الشاغلين، إدارة العمارة، مصاريف العمارة، كمبوند، صيانة منزلية، and developer names) plus the iTunes Search API.
- **Web and social:** we searched Reddit (r/Egypt, r/cairo), Facebook and X for Egyptian complaints. **The search tools indexed almost no Reddit, Facebook or X content for these apps, and the Reddit JSON API refused our requests.** This is stated plainly: **the social-media VOC in this file comes from news and forum coverage, not from scraped Reddit, Facebook or X threads.** Section 5 covers what was found.

### 1.2 How the frequency estimates were made
- Every review with **≤3 stars** was tagged by a bilingual keyword classifier covering Egyptian colloquial and English terms. Examples: `مش بيفتح / بيهنج / crash`, `كود / OTP / تسجيل`, `نصب / حرامي / scam`, `ميعاد / متأخر / didn't come`, `غالي / سعر / overcharge`. One review can hit several categories.
- **ESTIMATE caveat:** keyword coding *under-counts*, because many 1-star reviews say only "زباله" ("garbage") or "سيء" ("bad") and get no category. It can also over-count on ambiguous words like "update" or "account". The percentages show **relative weight**, not exact incidence. The building-app group (49 reviews) was coded **manually** because it is small.

### 1.3 Known biases
- **Very small samples for the new building apps** (1 to 14 reviews each). They are all young, and their reviews skew 5-star, as early reviews from the founders' networks usually do.
- **Signs of review inflation.** MyPorto (Amer Group, `app.milango.amergroup`) got **22 five-star reviews on a single day (2026-06-11)** [corrected: raw CSV count is 22, not ~25], and a later reviewer calls this out: *"واضح ان سيلر عامر جروب أعطوا تقييمات ايجابيه للبرنامج"* ("clearly Amer Group's sales staff gave the app positive ratings"). Homena received 9 five-star reviews within 4 days of launch. TMG Life shows 1,067 five-star *ratings* out of 1,159, yet **31% of its 81 written reviews are 1-star**, so star-only ratings differ sharply from written sentiment.
- One FilKhedma and one Emaar review contained personal phone numbers. These were **not** reproduced.

---

## 2. Landscape of the apps sampled

### 2.1 Building / owners-association apps (direct Phase-1 competitors)

| App (package) | Developer / origin | Released | Installs (exact) | Rating (n) | Reviews scraped | Monetisation seen |
|---|---|---|---|---|---|---|
| **Ettihad – إتّحاد** (`com.ittihad.ettihad`) | Ettihad Community, Egypt-focused; payments in EG, SA, AE, JO, QA, IQ, LB | 2026-08-10 | 1,000+ (≈3,000) | 4.5 (8) | 6 | Free; AI assistant "Fary"; does not touch money |
| **عمارتي – إدارة إتحاد الملاك** (`com.ammarty.ammarty`) | HopenWorks LTD | 2026-09-08 | 1,000+ (1,684) | 4.78 (9) | 8 | **1-month free trial, then subscription** [unverified: stated in one 3★ user review; the Play listing declares no in-app purchases] |
| **Amarati – عمارتي** (`com.amarati.app`) | Amarati Technologies / Issa Kasabri, **Palestine** | 2026-06-21 | 1,000+ (1,416) | 4.74 (43) | 5 | "Free to start" |
| **Sandooq El Emara – صندوق العمارة** (`com.amrem.sandooqelamara`) | Amr Emam, Egypt | 2026-08-25 | 500+ (961) | 4.75 (16) | 14 | IAP **49.99–499.99 EGP**, trial |
| **Omaraty – عمارتي** (`com.omaraty.app`) | Techiato, Egypt (Egyptian colloquial copy) | 2026-08-10 | 100+ (365) | 5.0 (7) | 3 | "Free to use" |
| **Imarti – عمارتي** (`com.craftfuture.imarti`) | Craft Future, likely **Saudi** (craftsolutions.com.sa) [unverified] | 2026-07-26 | 100+ (125) | — | 1 | No IAP declared on listing; one review "الاشتراكات غاليه" (ambiguous) [unverified] |
| Amarti / Building Expenses (`com.tarek.imarati`) | Alfahd Alaswad Co. | 2026-06-07 | 100+ (110) | — | 2 | — |
| Homena (`io.homena.app`) | HomenaApp | 2026-09-02 | 50+ (91) | — | 9 | — |
| اتحاد ملاك عمارة 1310 (`com.building1310.app`) | HopenWorks LTD (white-label for one building) | 2026-08-02 | 50+ (67) | — | 0 | — |
| العمارة – إدارة ذكية (`com.beemind.alemara`), دفتر العمارة, العمارة (Glow Studio), اتحاد الملاك (Elgoktech) | indie developers | Jul–Sep 2026 | 10–50 each | — | 0–1 | — |
| **Saknna – سَكَنة** (saknna.com) | Web/PWA, EG + GCC | — | **No store app** | — | **0 (no store presence)** | **450 / 900 / 2,200 / 7,500 EGP per month**, 14-day trial |

Sources: Google Play listing pages `https://play.google.com/store/apps/details?id=<package>&hl=ar&gl=eg` for each package above, and https://saknna.com (fetched 2026-10-12).

**What the descriptions show about where the category is heading:**
- **Everyone positions against "WhatsApp groups plus paper notebooks."** Amarati: *"يحوّل دفتر الحسابات الورقي ومحادثات الواتساب إلى نظام واضح"* ("turns the paper ledger and WhatsApp chats into a clear system"). Omaraty: *"بديل عصري لجروبات الواتساب ودفاتر الورق"* ("a modern alternative to WhatsApp groups and paper notebooks").
- **Everyone avoids holding money.** Ettihad: *"إتّحاد لا يستلم أي أموال ولا يحتفظ بها"* ("Ettihad does not receive or hold any money"). Amarati: *"ما بنلمس فلوسك"* ("we don't touch your money"). Payment happens by InstaPay or bank transfer, then a receipt is uploaded and the admin approves it.
- **Features are converging:** dues ledger, expenses with receipt photos, arrears, WhatsApp-shareable statements, voting, announcements, complaints, and QR visitor passes (Ettihad). Amarati adds **meter reading by camera** (*"صوّر عداد الميه أو الغاز، والتطبيق بحسب الاستهلاك"*, "photograph the water or gas meter and the app calculates consumption"). Ettihad adds the **AI assistant with voice** and a **"residents without the app"** mode. Omaraty adds **residents without a mobile phone** and **building income from outsiders** (shop, roof and garage rent).

### 2.2 Developer compound apps (show what residents expect from a "home" app)

| App (package) | Operator / builder | Installs (exact) | Play rating (n) | 1-star share of scraped reviews | iOS EG rating (n) |
|---|---|---|---|---|---|
| TMG Life (`com.tmglife.app`) | Talaat Moustafa Group (one developer reply gives a support email on the newtonlabs.ai domain) | 50,000+ (55,469) | 4.79 (1,159) | 31% of 81 | 4.61 (1,133) |
| Emaar Misr App (`com.kijamii.emaarcommunities`) | Emaar Misr (built by Kijamii) | 10,000+ (44,478) | 3.94 (261) | 56% of 81 | 3.35 (99) |
| **Ahl Madinaty** (`com.ahl.madenty`) | **Independent resident-built directory** ("thelegend") | 10,000+ (43,668) | 4.62 (199) | 7% of 95 | 4.26 (35) |
| Lyve-App / iCommunity (`com.moonshot.icommunity`) | Moonshot Labs (used by Palm Hills and others) | 10,000+ (36,430) | 4.4 (354) | 36% of 75 | 3.32 (69) |
| Mountain View Community (`com.congora.mountainview`) | Intcore | 10,000+ (14,209) | 3.67 (34) | 64% of 14 | 3.64 (47) |
| Morshedy Group (`app.milango.morshedy`) | Milango | 10,000+ (10,760) | 3.62 (47) | 50% of 26 | — |
| SODIC (`com.kijamii.sodiccommapp`) | Kijamii / Milango | 5,000+ (9,239) | 3.26 (51) | 71% of 24 | **2.22 (81)** |
| Al-Ahly Sabbour (`app.milango.alahlysabbour`) | Milango | 5,000+ (8,921) | 3.47 (17) | 20% of 5 | — |
| MyPorto (`app.milango.amergroup`) | Milango for Amer Group | 5,000+ (8,357) | 4.35 (47) | 14% of 35 (inflated, see §1.3) | — |
| PALM HILLS (`com.palmhills.communityapp`) | Palm Hills Developments | 5,000+ (7,206) | 2.97 (34) | 62% of 13 | **1.38 (47)** |
| Tatweer Misr Communities (`com.macber.eg.tatweer`) | Comet Innovations | 1,000+ (4,631) | 3.38 (14) | 44% of 9 | 4.3 (20) |
| ORA Developers (`com.oradevelopers.users.app`) | ORA | 1,000+ (1,895) | 2.67 (7) | 33% of 3 | 3.25 (4) |
| Hassan Allam Properties (`com.moonshot.hap`), Places by Hyde Park (`com.moonshot.hydePark`) | Lyve / Moonshot | 1–2k | 4.0 (10) / — | 0 reviews | — |

Sources: Google Play listings (above packages) and iTunes Search API, Egypt storefront (iOS IDs 6502700910, 1168425830, 1498413451, 1138437170, 6754685645, 1390362823, 6477568109, 6502767063, 6756376478).

> **Key insight:** **Ahl Madinaty, an unofficial directory built by residents, has 43,668 installs, about 79% of the official TMG Life's 55,469.** It also has far better sentiment (7% one-star against 31%). Residents adopt a *useful, simple, local* app on their own, with no developer mandate and no marketing budget. This is the closest local proof of the founder's zero-marketing thesis.

### 2.3 Home-service marketplaces (Phase-2 reference)

| App | Installs (exact) | Play rating (n) | Rating histogram 1★…5★ | 1-star share since 2025 | iOS EG rating (n) |
|---|---|---|---|---|---|
| FilKhedma (`com.filkhedma.customer`), a SweepSouth company | 100,000+ (178,066) | 3.07 (1,411) | 621 / 20 / 41 / 94 / 631 | **59%** (n=156) | 3.16 (2,133) |
| Taskty (`com.tasktyapp.taskty`) | 100,000+ (168,317) | **2.07** (659) | 460 / 12 / 19 / 6 / 157 | **79%** (n=34) | 2.30 (115) |
| Fixawy (`com.fixawy.servicebooking`), Alexandria | 10,000+ (11,249) | 3.53 (37) | 12 / 1 / 1 / 0 / 22 | 39% (n=18) | **4.36 (798)** |
| Shagheel – شغيل (`com.spiderte8.shgheelapp`) | 1,000+ (3,893) | — | — | — | — |

Sources: Google Play listings above; iOS IDs 1473742608, 1486080094, 1071671875. The Taskty Play listing was last updated 2023-12-11, which suggests an unmaintained app.

*Note: "Elmohandes" (`com.true.elmohandesclients`) turned out to be a points and loyalty app for a building-materials brand ("collect points, and redeem rewards"), and `com.snonosystems.elmohandes` is an internet-provider app. Both were excluded from the home-services analysis.*

---

## 3. Complaint categories: frequency tables

### 3.1 Building / owners-association apps (n = 49 Play + 1 iOS, manually coded)

Rating mix: 40 five-star, 2 four-star, 3 three-star, 3 two-star, 1 one-star. Ten reviews contain a complaint or request.

| # | Category | Count (of 10 substantive reviews) | Example |
|---|---|---|---|
| 1 | **Pricing / "is it free?" anxiety** | 4 | Imarti 2★: "الاشتراكات غاليه اوي" ("the subscriptions are very expensive") |
| 2 | **Login / registration / payment bugs** | 4 | Ettihad: email OTP loop over 10 tries; Amarti: registration error; Amarati iOS won't open after update; Sandooq: subscription purchase error |
| 3 | **Billing flexibility** (unequal fees, exempt or zero units, one-off levies, rent) | 3 | Amarati 2★ (5-point list), Sandooq 3★ and 4★ |
| 4 | **Reports** (PDF, names and amounts) | 2 | Omaraty 5★, Sandooq 4★ |
| 5 | **Admin data entry for non-app residents / elderly** | 1 | Omaraty 5★ |
| 6 | **Roles / multiple admins** | 1 | Omaraty 5★ |
| 7 | **Complaints module** | 1 | Ettihad 5★ |
| 8 | **iOS availability** | 1 | Amarati 5★ |
| 9 | **"You copied the idea"** | 1 | Ettihad 1★ |

### 3.2 Developer compound apps (n = 462 Play reviews, 208 with ≤3★; keyword-coded ESTIMATE)

| Rank | Category | Negative reviews hit | % of negatives |
|---|---|---|---|
| 1 | Crash / won't open / "not working" | 86 | **41%** |
| 2 | Login / OTP / registration / approval | 47 | **23%** |
| 3 | Broke after an update / forced updates | 29 | 14% |
| 4 | Slow / heavy | 21 | 10% |
| 5 | Support unresponsive | 20 | 10% |
| 6 | "Security alert" / rooted-device false positive / single-device ban | 16 | 8% |
| 7 | Utility payments (NFC electricity cards, cards, Apple Pay) | 11 | 5% (much higher on iOS, §4.2) |
| 8 | Gate / QR pass failures | 10 | 5% |
| 9 | One-way communication / management censorship | 8 | 4% |
| 10 | Abroad / non-Egyptian number can't log in | 4 | 2% |
| — | Arabic / RTL support missing | 3 explicit (all star levels) | — |

On the **iOS Egypt storefront** (360 reviews, 251 with ≤3★), the compound-app complaints focus even more on **payments**. TMG Life on iOS has at least 15 reviews about NFC electricity-card charging failing on iPhone, Manas/Menas cards not supported, NBE debit cards rejected, and requests for Apple Pay or saved cards.

### 3.3 Home-service marketplaces (n = 1,000 Play reviews, 527 with ≤3★; keyword-coded ESTIMATE)

| Rank | Category | Negative reviews hit | % of negatives |
|---|---|---|---|
| 1 | **Price inflation / overcharge / spare-part markups / off-app cash** | 111 | **21%** |
| 2 | **Unskilled work / damage to the home / poor cleaning** | 105 | **20%** |
| 3 | **No-show / late / cancelled without notice / cancellation fee charged to the customer** | 89 | **17%** |
| 4 | **Support unresponsive / hotline loops** | 85 | **16%** |
| 5 | **"Scam / thieves / stole"** (explicit fraud or theft) | 74 | **14%** |
| 6 | Complaint closed without action / no follow-up / warranty refused | 33 | 6% |
| 7 | App crash / won't load | 33 | 6% |
| 8 | Card payment problems / unauthorised charges | 32 | 6% |
| 9 | OTP / activation never arrives | 20 | 4% |
| 10 | Coverage ("not in my area": Alexandria, Obour, Salam City, Sharqia) | ~8 (manual) | ~2% |

**Trend:** FilKhedma's 1-star share rose from 47% across its full scraped history to **59% for 2025–2026**. Several long-time users write "they used to be good" (*"كانو في بدايتهم كويسين دلوقتي للاسف من اسوء الصنايعيه"*, "they were good at the start, now sadly among the worst craftsmen"). **Quality decays as the marketplace scales.** This is the main operational risk for our Phase 2.

---

## 4. Verbatim voice of customer (Arabic as written, with English translation)

All quotes are reproduced exactly as posted. Spelling errors are the users' own. The source URL is the store listing where the review appears.

### 4.1 Building / owners-association apps

**Price anxiety before adoption is the number-one question**
- Amarati, 5★, 2026-10-01: *"هيبقي مجاني ولا برسوم وياريت ميبقاش رسوم غاليه علشان في طبيق غالي اوي"*
  "Will it be free or paid? I hope the fees aren't expensive, because there's an app that's very expensive." [play.google.com/store/apps/details?id=com.amarati.app](https://play.google.com/store/apps/details?id=com.amarati.app&hl=ar&gl=eg)
- Amarati, 5★, 2026-09-30: *"تطبيق رائع احييكم عليه، لكن هل هو مجاني ؟"* "Great app, well done. But is it free?" (same URL)
- Imarti, 2★, 2026-10-01: *"الاشتراكات غاليه اوي"* "The subscriptions are very expensive." [com.craftfuture.imarti](https://play.google.com/store/apps/details?id=com.craftfuture.imarti&hl=ar&gl=eg)
- Ammarty, 3★, 2026-10-05: *"التطبيق مجاني لمده شهر واحد فقط وبعد كده باشتراك انا بعد ما نزلت البرنامج حذفته علشان كنت فاكره مجاني بالكامل لكن طلع باشتراك."*
  "The app is free for only one month and then it's a subscription. After I installed it I deleted it, because I thought it was completely free, but it turned out to be a subscription." [com.ammarty.ammarty](https://play.google.com/store/apps/details?id=com.ammarty.ammarty&hl=ar&gl=eg)
- Sandooq El Emara, 4★, 2026-09-27: *"...وعايزين نعرف اشتراكه كام ويا ريت تمدوا الشهر التجربة لاني لسه فاتحه اليوم وفاضل اسبوع"*
  "...and we want to know how much the subscription is. Please extend the trial month, because I only just started and there's one week left." [com.amrem.sandooqelamara](https://play.google.com/store/apps/details?id=com.amrem.sandooqelamara&hl=ar&gl=eg)

**Real Egyptian buildings aren't uniform (billing flexibility)**
- Amarati, 2★, 2026-09-26: *"ينقصه الاتي : ـ تخصيص الدفع لبعض الخدمات اي ان بعض شاغلي الوحدات يدفعون في بعض الخدمات والاخرى لا . ـ اضافة تحصيل الايجار من الوحدات المؤجرة . ـ اضافه امكانية طلب دفع فواتير او خدمات استثنائية لمره واحده او عده مرات. ـ وضع امكانية اخفاء بعض الامكانيات عن السكان لمنع الإحراج مثل تحصيل الايجار . ـ لماذا تختفي الشقه المعفيه من الدفع من قائمه الشقق"*
  "It lacks: per-service payment assignment (some occupants pay for some services and not others); rent collection from rented units; requesting one-off or repeated exceptional bills; hiding some features from residents to avoid embarrassment, such as rent collection; and why does the payment-exempt apartment disappear from the list?" (Amarati URL above)
- Sandooq, 3★, 2026-09-25: *"مش كل الادوار نفس عدد الشقق ومش كله بيدفع نفس المبلغ"* "Not every floor has the same number of flats, and not everyone pays the same amount." (Sandooq URL)
- Sandooq, 4★, 2026-09-27: *"لو شقة تحت التشطيب ومبتدفعش تيجي تضيف للمبلغ صفر ميقبلش"* "If a flat is still being finished and doesn't pay, you try to enter zero and it won't accept it." (Sandooq URL)

**Elderly and non-smartphone residents, reports, roles**
- Omaraty, 5★, 2026-08-22: *"١) تفعيل امكانيه وضع بيانات كل شقه من مدير العماره لان في ناس كبيره في السن مش هتعرف تستخدم البرنامج ف لازم تبقي البيانات موجوده علشان يسجل عليهم الشهريات ويبقي الرصيد مظبوط ٢) تفعيل وضع الايرادات للصندوق لان ممكن يبقي عندي ايراد غير الشهريه ... ٤) اضافه تقرير بالمبالغ علي كل شقه يصدر في شكل PDF ٥) اضافه صلاحيات حيث من الممكن اضافه اكثر من شخص لاداره العقار"*
  "1) Let the building manager enter every flat's data, because there are elderly people who won't know how to use the app, so the data must exist to record their monthly payments and keep the balance correct. 2) Let the fund record income, because I may have income other than the monthly dues... 4) Add a per-flat amount report exported as PDF. 5) Add permissions so more than one person can manage the property." [com.omaraty.app](https://play.google.com/store/apps/details?id=com.omaraty.app&hl=ar&gl=eg)
- Sandooq, 4★, 2026-09-29: *"خانه المصاريف تكون أوضح ويبقى التقارير شامله الأسماء بقيمه الدفع"* "Make the expenses section clearer, and have the reports include names with the amount paid." (Sandooq URL)

**What delights: transparency, no paper, AI, not needing everyone onboard**
- Ettihad, 5★, 2026-08-28: *"فكرة اني مش لازم كل السكان ينزل التطبيق ممتازة. وفاري الذكاء الاصطناعي حلم الصراحة وبيفهم انا عايز ايه بالظبط، انا بعمل كل حاجة من عليه ... ملاحظه: لو يتم إضافة شكاوي يبقي حاجة ممتازة."*
  "The idea that not every resident has to install the app is excellent. Honestly, Fary the AI is a dream. It understands exactly what I want, and I do everything through it... Note: adding complaints would be excellent." [com.ittihad.ettihad](https://play.google.com/store/apps/details?id=com.ittihad.ettihad&hl=ar&gl=eg)
- Ettihad, 5★, 2026-08-28 (English): *"A platform where property owners can communicate, access services, post and discover relevant ads, and even pay their dues .. Bringing property owners, and community services together in one platform is definitely a game changer."* (Ettihad URL). **Users already imagine the services-marketplace layer.**
- Sandooq, 5★, 2026-09-28: *"بقيت بستخدمه وبطلت استخدم الورقه و القلم"* "I started using it and stopped using pen and paper." (Sandooq URL)
- Ammarty, 5★, 2026-10-08: *"مفيد للناس اللي عامله نظام ان كل شقه تدفع مبلغ كل شهر"* "Useful for people who have a system where every flat pays an amount each month." (Ammarty URL)

**Bugs already showing in the new entrants**
- Ettihad, 5★ (sic), 2026-10-11: *"بعد الانتهاء من خطوات عمليه التسجيل يتم ارسال رمز التحقق ع الايميل و عند ادخال رمز التحقق يرجع من البدايه أكثر من ١٠ محاولات!!!!!!!"*
  "After finishing registration, the verification code is sent by email, and when I enter it, it goes back to the start. More than 10 attempts!" The developer reply blamed a specific Huawei model. (Ettihad URL)
- Amarti, 2★, 2026-10-03: *"عطلان مش بيفتح بيدني خطأ عند التسجيل عن طريق التليفون او الاميل"* "Broken, won't open, gives an error when registering by phone or email." [com.tarek.imarati](https://play.google.com/store/apps/details?id=com.tarek.imarati&hl=ar&gl=eg)
- Amarati iOS, 3★, 2026-10-01: *"الابليكشن بعد اخر تحديث مش بفتح نهائيًا"* "After the last update the app doesn't open at all." [apps.apple.com/eg/app/id6791464029](https://apps.apple.com/eg/app/id6791464029)
- Sandooq, 5★, 2026-10-09: *"كلما حاولت الاشتراك تظهر رسالة تقول حدث خطأ من جانبنا"* "Every time I try to subscribe, a message says 'an error occurred on our side'." (Sandooq URL)

### 4.2 Developer compound apps

**Gate access is mission-critical, so reliability is everything**
- Emaar Misr, 2★, 2026-08-18: *"constantly crashes, and is so slow. as a resident, we must depend heavily on this app and its full of bugs and issues. constant problems when people are impatient and dependent on the timing for the app to open gates"* [com.kijamii.emaarcommunities](https://play.google.com/store/apps/details?id=com.kijamii.emaarcommunities&hl=ar&gl=eg)
- Emaar Misr, 2★, 2024-06-23: *"IdDbadge doesn't open the gate many times. Says gate out of range. No way to enter my building if app is not working right."* (Emaar URL)
- Emaar Misr, 1★, 2022-08-02: *"Generated QR codes are incomplete and refused at the gates and embaresses me infront my guests"* (Emaar URL)
- Lyve iOS, 1★, 2019-06-18: *"Fix the bugs!! It doesn't work! And we stand for ages on the gates not able to go home!"* [apps.apple.com/eg/app/id1138437170](https://apps.apple.com/eg/app/id1138437170)
- SODIC, 1★, 2026-02-18: *"It is unacceptable that the barcode issue for the project gate has not been resolved for more than a month"* [com.kijamii.sodiccommapp](https://play.google.com/store/apps/details?id=com.kijamii.sodiccommapp&hl=ar&gl=eg)

**Login, OTP and "security" friction is the number-one self-inflicted wound**
- SODIC, 1★, 2024-09-11: *"you have to get OTP over sms each time you open it from the very same mobile and after this it takes ages to load"* (SODIC URL)
- SODIC, 2★, 2024-02-12: *"مش راضي يقبل الرقم بيقولي expired otp"* "It won't accept the number, it tells me 'expired OTP'." (SODIC URL)
- Mountain View, 2★, 2026-05-06: *"I changed my phone device and now I am blocked of using the app? ... 'You are now blocked due to violation of the single device role, Please visit your nearest office to resolve this ban'"* [com.congora.mountainview](https://play.google.com/store/apps/details?id=com.congora.mountainview&hl=ar&gl=eg)
- Mountain View, 1★, 2025-12-22: *"my user is blocked due to a violation of multiple device bla bla blah.. and i have to head to the nearest office! what a real digital experience!!!"* (MV URL)
- Morshedy, 1★, 2025-10-29: *"A bug in the Verify Code screen ... did you use Vibe Coding to generate this app?!"* [app.milango.morshedy](https://play.google.com/store/apps/details?id=app.milango.morshedy&hl=ar&gl=eg)
- TMG Life, 2★, 2024-11-05: *"opened only one time and then kept complaining that security threat is detected, even though my phone is locked and not rooted"* [com.tmglife.app](https://play.google.com/store/apps/details?id=com.tmglife.app&hl=ar&gl=eg)
- ORA, 1★, 2026-08-26: *"مش بيشتغل علي كل الموبيلات ... بيطلع رسالة تحذير امني"* "It doesn't work on all phones... it shows a security warning message." [com.oradevelopers.users.app](https://play.google.com/store/apps/details?id=com.oradevelopers.users.app&hl=ar&gl=eg)
- Palm Hills iOS, 1★, 2026-03-28: *"I retook the selfie more than 20 times and it always refuses how I open my eyes.. pathetic way of verification"* [apps.apple.com/eg/app/id6477568109](https://apps.apple.com/eg/app/id6477568109)

**Owners locked out by approval workflows**
- Palm Hills, 1★, 2026-02-08: *"Owning my unit in PHNC since 2 years and when I tried to register, the sms I got was 'We're sorry to inform you that your Community App account has been reviewed and was not approved'"* [com.palmhills.communityapp](https://play.google.com/store/apps/details?id=com.palmhills.communityapp&hl=ar&gl=eg)
- Palm Hills, 1★, 2026-05-20: *"I am an owner of a unit in Badya palm hills. No after 6 months they expected my account"* (PH URL)
- TMG Life, 1★, 2025-04-29: *"وقت الانتظار لحين الحصول على موافقه خدمه العملاء كبير واحيانا بالشهور!"* "The wait to get customer-service approval is long, sometimes months!" (TMG URL)
- TMG Life, 1★, 2025-06-16: *"تطبيق لا يحترم الملاك. واضح ان القائمين على التطبيق خريجين مدرسة 'مدام عفاف للمصالح الحكومية'"* "An app that doesn't respect owners. Clearly the people running it graduated from the 'Madame Afaf school of government offices'." (TMG URL) **Users compare bad digital onboarding to Egyptian bureaucracy.**

**Egyptians abroad and non-Egyptian numbers are excluded**
- Tatweer Misr, 1★, 2025-06-04: *"does not accept login from my registered mobile number when it is from outside Egypt as it should be 10 digits"* [com.macber.eg.tatweer](https://play.google.com/store/apps/details?id=com.macber.eg.tatweer&hl=ar&gl=eg)
- TMG Life, 4★, 2025-08-28: *"بسافر كتير، وللأسف مش شغال بره مصر للمتابعة.. رجاء فتحه بره مصر"* "I travel a lot and sadly it doesn't work outside Egypt for follow-up. Please open it outside Egypt." (TMG URL)
- SODIC iOS, 1★, 2024-07-23: *"Cant login using my registered non-Egyptian number"* [apps.apple.com/eg/app/id1390362823](https://apps.apple.com/eg/app/id1390362823)

**Payments and utilities (strong demand, weak execution)**
- TMG Life, 1★, 2026-08-09: *"Put Intelligence electricity card against phone ... Payment completes ... Money is taken ... Electricity card is NOT updated"* (TMG URL)
- TMG Life iOS, 1★, 2025-07-25: *"حتى مع آخر تحديث لا يشحن مع ان نفس الكارت بيشحن عالأندرويد، مش معقول هغير الكارت بـ٤٠٠ جنيه عشان يشحن عالآيفون"* "Even with the latest update it won't charge, though the same card charges on Android. I'm not going to replace the card for 400 EGP just to charge on iPhone." [apps.apple.com/eg/app/id6502700910](https://apps.apple.com/eg/app/id6502700910)
- TMG Life iOS, 4★, 2026-06-29: *"يفضل تفعيل خدمة آبل باي على التطبيق. أو حفظ ارقام بطاقة الدفع على التطبيق."* "Better to enable Apple Pay in the app, or save card numbers in the app." (TMG iOS URL)
- TMG Life, 5★, 2025-09-20: *"Great app specially for Recharge electricity and i wish to have water recharging very soon"* (TMG URL)
- TMG Life, 3★, 2025-08-04: *"شحن عداد المياه والغاز"* "Charging the water and gas meters." (request; TMG URL)
- TMG Life, 2★, 2025-08-13: *"سئ جدا بس ارحم من الوقفه في طابونه العيش اللي اسمها شركه كهرباء مدينتي"* "Very bad, but more merciful than standing in the bread-bakery queue called Madinaty's electricity company." (TMG URL) **Even a bad digital utility top-up beats the queue.** Utility payments are a strong pull feature.

**Services inside the compound app: same trust failures as the marketplaces**
- TMG Life, 3★, 2025-10-20: *"booked a plumbing service months ago and i'm still waiting on it to get dispatched"* (TMG URL)
- TMG Life, 1★, 2025-08-07: *"تطبيق عبيط ماسكه صنايعية هواه، مش ملتزمين ولا بيحترموا مواعيدهم"* "A silly app run by amateur craftsmen who aren't committed and don't respect their appointments." (TMG URL)
- TMG Life, 1★, 2025-07-15: *"مفيش إهتمام او رد بعد تقديم طلب/شكوي من خلال الأبلكيشن!"* "No attention or response after submitting a request or complaint through the app!" (TMG URL)

**Management censorship backfires (lesson for the community feed)**
- Lyve (Palm Hills on iCommunity), 1★, 2019-11-11 (11 helpful votes): *"It used to be effective as a 2 way communication between residents and community manager and among the neighbors. Now this feature is not available. Only the community manager is allowed to post"* [com.moonshot.icommunity](https://play.google.com/store/apps/details?id=com.moonshot.icommunity&hl=ar&gl=eg)
- Lyve, 1★, 2019-11-12: *"ده يعتبر حجر و غلق علي أفكارنا وأصواتنا"* "This is a lockdown and closure on our ideas and voices." (Lyve URL)
- Lyve iOS, 1★, 2019-11-13: *"يخدم طرف واحد (بالم هيلز) ... تفرض حالة من التعتيم وإنعدام التواصل وعدم إطلاع المستخدم علي أي شكوي مقدمة من أي ساكن"* "It serves one party (Palm Hills)... imposes a blackout and lack of communication, and doesn't show users any complaint submitted by any resident." (Lyve iOS URL)
- Lyve, 1★, 2021-03-08: *"only unit owners can sign up & get verified ... Anyone who is just a resident or renting the unit cannot siguup"* (Lyve URL). **Tenants must be first-class users.**

**Family and household members**
- TMG Life, 4★, 2025-04-29: *"يا ريت اضافة الاخوات مش كل الناس متزوجين في ناس عايشة مع اسرهم"* "Please allow adding siblings. Not everyone is married; some people live with their families." (TMG URL)
- Emaar Misr, 1★, 2022-06-27: *"Unable to add properties in a different community and unable to add family members."* (Emaar URL)
- Lyve iOS, 3★, 2022-10-12: *"How to add a family member to Lyve app ?"* (Lyve iOS URL)

**Language**
- Al-Ahly Sabbour, 5★, 2025-06-12: *"عاوزين لغة عربية ضرووووري"* "We need Arabic, urgently." [app.milango.alahlysabbour](https://play.google.com/store/apps/details?id=app.milango.alahlysabbour&hl=ar&gl=eg)
- Morshedy, 3★, 2026-05-31: *"ارجو تفعيل اللغه العربيه اكثر من ذلك"* "Please support Arabic more than this." (Morshedy URL)
- Lyve, 4★, 2025-06-29: *"still needs RTL alignment for arabic text"* (Lyve URL)

**Update fatigue**
- Emaar Misr, 1★, 2026-09-26: *"update every 2 days? that's very annoying"*; 3★, 2026-02-07: *"كل شوية تحديث صعب اوي"* "An update every little while, it's really hard." (Emaar URL)
- Lyve, 1★, 2023-04-22 (7 helpful votes): *"The software asking for update while the only available buttons are not including update"* (Lyve URL)

**What residents love (Ahl Madinaty and TMG Life positives)**
- Ahl Madinaty, 5★, 2025-04-20: *"يجمع كل الخدمات الموجودة في المدينة في مكان واحد، يعني مش محتاج ادور كتير"* "It gathers all the city's services in one place, so I don't need to search much." [com.ahl.madenty](https://play.google.com/store/apps/details?id=com.ahl.madenty&hl=ar&gl=eg)
- Ahl Madinaty, 5★, 2020-08-30: *"it has everything I need in Madinaty more than this the notifications are really helpful :)"* (Ahl Madinaty URL)
- Ahl Madinaty, 5★, 2020-05-03 (13 helpful votes): *"ارجوا إضافة اماكن و مواعيد سيارات الخدمة الوطنية"* "Please add the locations and schedules of the national-service vehicles." (Ahl Madinaty URL)
- Ahl Madinaty iOS, 5★, 2020-05-24: *"ياريت نقدر نشتري كمان من خلاله حيبقى تحفة"* "I wish we could also buy through it; it would be a masterpiece." [apps.apple.com/eg/app/id1498413451](https://apps.apple.com/eg/app/id1498413451). **Organic demand for commerce inside a community directory.**
- Ahl Madinaty, 5★, 2021-12-26: a gas-appliance maintenance company asks to join as a provider (*"عايزين نشارك فى تقديم الخدمات الخاصة بصيانة اجهزة الغاز"*, "we want to take part in providing gas-appliance maintenance services"). **Supply-side providers approach community apps on their own.**
- Lyve, 5★, 2020-08-30 (24 helpful votes): *"they add new stores all the time. The only improvement I'm looking for is to be able to search for an item in a shop, and to sort the items alphabetically or by price."* (Lyve URL)
- TMG Life iOS, 5★, 2025-04-15: *"open gates with a QR code and stay connected with the city hall for important updates."* (TMG iOS URL)

### 4.3 Home-service marketplaces (FilKhedma, Taskty, Fixawy)

**Price is never final: the core broken promise**
- FilKhedma, 1★, 2026-05-15: *"You pick a service and a specific issue with a certain price, the technician comes, charges you extra and the issue was temporarily patched and not fixed."* [com.filkhedma.customer](https://play.google.com/store/apps/details?id=com.filkhedma.customer&hl=ar&gl=eg)
- FilKhedma, 1★, 2025-07-30 (12 helpful votes): *"technician sells u spare parts with extremely high prices than u discover that the company is not aware of it"* (FilKhedma URL)
- FilKhedma iOS, 1★, 2026-07-27: *"الصنايعي باعلي قطعه على ان سعرها١٠٠٠ جنيه وبعد ما مشي سالنا عرفنا انها ب ٤٠٠ جنيه"* "The craftsman sold me a part claiming it cost 1,000 EGP; after he left we asked and found it was 400 EGP." [apps.apple.com/eg/app/id1473742608](https://apps.apple.com/eg/app/id1473742608)
- FilKhedma, 1★, 2025-07-27: *"بياخدو فلوس اكتر ويقولولك متقولش للشركه عشان مياخدوش ٣٠ فالميه"* "They take more money and tell you not to tell the company so it doesn't take its 30%." (FilKhedma URL). **This is disintermediation (leakage) of a roughly 30% take rate, stated outright.**
- Taskty, 1★, 2026-03-31: *"الفنى جه و دفعتله معينة و قالى سعر تلت اضعاف اللى على الابليكشن"* "The technician came, I paid the inspection fee, and he quoted three times the price shown in the app." [com.tasktyapp.taskty](https://play.google.com/store/apps/details?id=com.tasktyapp.taskty&hl=ar&gl=eg)
- Fixawy, 1★, 2025-01-14 (9 helpful votes): *"الاسعار المذكورة غير مطابقة والمناطق المذكورة داخل التغطية بعد عمل الاوردر تقوم موظفة خدمة العملاء بالتواصل للابلاغ انها خارج التغطية وسيقوم الفني بتحصيل مصاريف انتقالات"* "The listed prices don't match, and areas listed as covered: after you place the order, customer service calls to say it's outside coverage and the technician will charge travel fees." [com.fixawy.servicebooking](https://play.google.com/store/apps/details?id=com.fixawy.servicebooking&hl=ar&gl=eg)
- FilKhedma, 1★, 2025-01-30 (27 helpful votes): *"لا يوجد اي فائدة من المعاينة سوى دفع المبلغ المعلن. الفني الذي يأتي للمعاينة ليس هو من سيتم العمل غالبا فما الفائدة ؟؟؟"* "The inspection visit has no benefit except paying the announced fee. The technician who comes to inspect is usually not the one who will do the work, so what's the point?" (FilKhedma URL)

**No-shows and cancellations charged to the customer**
- FilKhedma, 1★, 2026-06-13: *"ordered a cleaner, cleaner didn't come, and then they deduct charges as if I was the one who canceled. Their hotline is an endless loop of being on hold."* (FilKhedma URL)
- FilKhedma iOS, 1★, 2026-09-05: *"when a service provider cancels at the last minute or simply fails to show up at the agreed time, the company has no effective backup or alternative"* (FilKhedma iOS URL)
- FilKhedma, 1★, 2025-09-16: *"جائزة نوبل فى عدم احترام المواعيد... موعد السباك م ١٠ ل ١١ و لم يظهر"* "A Nobel prize in not respecting appointments... the plumber's slot was 10 to 11 and he never showed." (FilKhedma URL)
- Taskty, 1★, 2026-05-25: *"they simply don't send the cleaner after confirming. Nobody answers calls or messages, and it feels like your booking never existed."* (Taskty URL)

**Quality, damage and no compensation**
- FilKhedma iOS, 1★, 2025-10-01: *"طلبت تنظيف عميق ب ١٣٧٥ جنيه و النتيجة تكسير ٣ مرايات تاتش ليد بال٣ حمامات و الدعم الفني مخدتش منهم غير اعتذار"* "I ordered a deep clean for 1,375 EGP and the result was three LED touch mirrors broken in three bathrooms. All I got from support was an apology." (FilKhedma iOS URL)
- FilKhedma, 1★, 2024-07-23: *"كسرولي رخامة المطبخ ... يقول لي هنعوضك ب٥٠٠ جنيه"* "They broke my kitchen marble... and offered 500 EGP compensation." (FilKhedma URL)
- FilKhedma, 1★, 2026-10-11: *"بيجيبو فنيين بدون تدريب من اي مكان ويشغلوهم وخلاص"* "They bring untrained technicians from anywhere and put them to work, that's it." (FilKhedma URL)

**Theft and safety (the heaviest trust failure)**
- Taskty, 1★, 2024-01-03: *"العاملة اللي جت تنضف سرقت خاتم دهب، والشركة تعاملت مع الشكوى بلامبالاة ومماطلة"* "The cleaner stole a gold ring, and the company handled the complaint with indifference and stalling." (Taskty URL)
- FilKhedma iOS, 1★, 2026-09-24: *"بيتي اتسرق اكتر من ٣ مرات من عاملين عندكم"* "My home was robbed more than three times by your workers." (FilKhedma iOS URL)
- FilKhedma, 1★, 2025-07-09: *"التطبيق مافيهوش اي وسيلة للشكوى او لتقييم العامل. العاملة سرقت حاجات من البيت"* "The app has no way to complain or rate the worker. The cleaner stole things from the house." (FilKhedma URL)
- FilKhedma, 1★, 2026-01-27: *"العمالة حضرت بدون إثبات شخصية"* "The workers came without ID." (FilKhedma URL)
- FilKhedma, 5★, 2026-08-21: *"ينقصه تحديد الشخص القائم بالإصلاح و مكان تواجده خاصة حين ينشأ عن بعض المعاملات من مشاكل قانونية"* "It lacks identification of the repair person and their location, especially when legal problems arise from some jobs." (FilKhedma URL)

**What works when it works**
- FilKhedma, 5★, 2025-08-15: *"بيكون شاكر محترم مركز و بينجز المهمه في وقت قليل ...لانه عارف أنه تحت رقابة الابليكيشن وكمان تقييم العميل"* "He's grateful, respectful, focused and finishes quickly... because he knows he's under the app's supervision and the customer's rating." (FilKhedma URL). **Accountability is the product.**
- FilKhedma, 5★, 2025-12-26: *"The best part is that prices are visible from the start."* (FilKhedma URL)
- FilKhedma, 5★, 2025-11-20 (9 helpful votes): *"the third tried to negotiate prices. I filed a complaint, and the team handled it quickly and assigned me a new specialist"* (FilKhedma URL)
- Fixawy, 5★, 2025-09-30: *"بلغوني إن في ضمان علي الخدمة 14 يوم ... السعر طبعا إن اعرفه من الأول و أبعد عن استغلال الصنايعية"* "They told me there's a 14-day warranty... and of course I know the price upfront and avoid being exploited by craftsmen." (Fixawy URL)
- Fixawy, 5★, 2025-10-01: *"صلحها بأقل من نص تكلفة مركز الصيانة"* "He fixed it for less than half the cost of the service centre." (Fixawy URL)
- FilKhedma, 5★: *"Very helpful for foreigners. Would be better if there was an English option"* and *"I like them as expats we need these honest guys in this country"* (FilKhedma URL). **Expats are a high-value segment.**

**Coverage gaps**
- Taskty, 5★: *"ياريت يبقى في في محافظة الشرقية"* "I wish it were available in Sharqia governorate"; 1★: *"ياريت تيجوا مدينة السلام"* "Please come to Salam City"; 5★: *"باقى الخدمات تكون موجودة فى منطقة العبور"* "the rest of the services available in Obour". (Taskty URL)
- FilKhedma, 1★, 2026-06-03: *"فاسكندريه مفيش عندهم عمالة متاحه"* "In Alexandria they have no workers available." (FilKhedma URL)

**Supply-side signal (technicians want in)**
- FilKhedma: *"انا فني كهربائي يشرفني اني اشتغل مع حضرتكم"* "I'm an electrician and would be honoured to work with you"; Taskty: *"انا فني نقاش واسترجي محتاج اشتغل معاكو"* "I'm a painter and plasterer and need to work with you"; Fixawy requests to add *"عمال تكسير وتشوين وموان"* (demolition, haulage and building-supply labourers) and *"قسم الجيبسوم بورد"* (a gypsum-board section). (respective URLs)

---

## 5. Beyond the stores: news and forum signal on Egyptian building pain points

Social-platform scraping was not possible (see §1.1). Egyptian news and legal commentary confirm the *underlying* pains that building apps address:

| Pain point | Evidence | Source |
|---|---|---|
| **Collecting dues is the biggest problem for owners' associations** | Ahram opinion piece calls collection "the biggest problem facing associations". Leaders lack time and legal knowledge, and treasurers lack accounting skills. It cites forged general-assembly minutes. | https://gate.ahram.org.eg/News/2139186.aspx (2019) |
| **No enforcement power** | [corrected] Sada El-Balad (15 Jun 2021) report on a discussion at the Egyptian Businessmen's Association construction committee, attended by a Housing Ministry official: the association lacks power to compel payment, and the fine for late payers is only 100 EGP per year (stated by EBA committee deputy chair Fathallah Fawzy, not by the ministry). There are disputes over who leads the association, and the maintenance deposit (10%) is insufficient. Proposals include electronic and remote general assemblies. | https://www.elbalad.news/4853788 (2021) |
| **Who maintains internal buildings** | Sheikh Zayed residents complain about neglected building maintenance despite their deposits. The city says stairs and drainage are the owners'/occupants' association's job. | https://www.elwatannews.com/news/details/4915334 |
| **Elevators: frequent breakdowns and cost-sharing fights** | Residents' disputes over elevator breakdowns and who pays for and uses a privately installed elevator | https://www.youm7.com/story/2021/6/7/.../5342588 |
| **Elevator safety and liability** | Elevator accidents linked to lack of maintenance and oversight; owners or maintenance companies can be liable | https://www.vetogate.com/5632859 |
| **Building WhatsApp groups are now mainstream** | Youm7 (Sep 2026) publishes a how-to on tagging yourself with your building or flat number inside residential-complex WhatsApp groups. In Jul 2026 a building's residents' WhatsApp group helped uncover a crime in Alexandria. | https://www.youm7.com/story/2026/9/16/.../7545906 ; https://www.youm7.com/story/2026/7/24/.../7491265 |
| **Developer vs resident conflicts over fees** | Rehab residents accuse the city authority of imposing maintenance levies without disclosing details, bypassing the occupants' association | https://gate.ahram.org.eg/News/1231089.aspx |

**What this means:** the legal pain (weak enforcement, low trust in the treasurer, disputed assemblies) makes a **transparent ledger with an audit trail, e-voting and e-assemblies** valuable, and hard for a WhatsApp group to replace. In that 2021 discussion, a Housing Ministry official said proposed amendments would allow electronic and remote general assemblies.

---

## 6. Top complaints and top requests (consolidated)

### 6.1 Top 15 complaints across all three groups (ranked by weight × relevance to our app)

| # | Complaint | Where it dominates | Share / evidence | What we must do |
|---|---|---|---|---|
| 1 | **App crashes / won't open / broke after update** | Compound apps | 41% of compound negatives; 14% blame an update | Crash-free sessions above 99.8% as a launch gate; staged rollouts; never force-update without a working Play/App Store build |
| 2 | **OTP / login / registration loops** | Compound apps, new building apps | 23% of compound negatives; Ettihad, Amarti, Morshedy, SODIC | Multi-channel login (WhatsApp OTP, SMS, email, Google/Apple, passkey); remember device; no OTP on every open |
| 3 | **Technician overcharging / price changes on site** | Service marketplaces | 21% | Locked quotes, a parts-price catalogue, in-app approval of any change, receipts mandatory |
| 4 | **Unskilled work / damage** | Service marketplaces | 20% | Vetting, skills test, probation, damage protection fund |
| 5 | **No-shows, late cancellation, customer charged** | Service marketplaces | 17% | Live tracking, automatic backup technician, auto-compensation when a provider cancels |
| 6 | **Support unresponsive** | Everywhere | 10% compound, 16% services | In-app ticket with SLA timer, WhatsApp support, AI first response |
| 7 | **Scam / theft** | Service marketplaces | 14% | ID verification, face match at arrival, police-record check, theft insurance, permanent bans |
| 8 | **"Security alert" / single-device ban / rooted false positives** | Compound apps | 8% | Don't use aggressive root detection for a consumer app; allow device switching by OTP |
| 9 | **Approval takes weeks or months / owner rejected** | Compound apps | Palm Hills, TMG, Emaar, SODIC (activation "5 days and counting") | Instant join by invite link; admin approves in one tap; provisional access |
| 10 | **Can't use from abroad / non-Egyptian number** | Compound apps | TMG, Tatweer, SODIC | International numbers, email login; owner-abroad mode |
| 11 | **Utility top-ups fail (NFC, iPhone, card types)** | TMG Life (iOS especially) | ~15 iOS reviews | If we do utilities, use partners such as Fawry/aggregators; Apple Pay, wallets and InstaPay |
| 12 | **Subscription price / unclear pricing** | Building apps | 4 of 10 substantive building reviews | Free for buildings, permanently and visibly |
| 13 | **One-way communication / censorship by management** | Lyve (Palm Hills) | Most-upvoted 1★ reviews in that app | Resident voice preserved; moderation by rules, not deletion |
| 14 | **Tenants / family members excluded** | Lyve, TMG, Emaar | Several | Roles: owner, tenant, family, helper, doorman |
| 15 | **Arabic / RTL missing** | Milango apps, Lyve | 3 explicit | Arabic-first, Egyptian colloquial microcopy; English toggle |

### 6.2 Top 15 feature requests (verbatim-backed)

| # | Request | Who asked (source app) | Priority for us |
|---|---|---|---|
| 1 | **Free (or cheap, clearly priced)** | Amarati ×2, Imarti, Ammarty, Sandooq | **P0**, our core strategy |
| 2 | **Flexible billing:** different fee per unit, zero or exempt units, per-service assignment, one-off levies, partial and advance payments | Amarati, Sandooq ×2 | **P0** |
| 3 | **Admin can enter data and payments for residents without the app or a smartphone (elderly)** | Omaraty; Ettihad praised for it | **P0**, critical for 100% building coverage |
| 4 | **Reports:** per-flat PDF and Excel with names and amounts | Omaraty, Sandooq | P0 |
| 5 | **Multiple admins / roles** (president, treasurer, member) | Omaraty | P0 |
| 6 | **Complaints / maintenance tickets with status and history** | Ettihad, Lyve ("can't see history"), TMG ("no response after complaint") | P0 |
| 7 | **Income lines** (shop, roof and garage rent; rent collection from rented units) | Omaraty, Amarati | P1 |
| 8 | **Utility top-ups and bill payment** (electricity, water, gas), plus Apple Pay, saved cards and e-wallets | TMG Life ×6+ | P1 (partner-led) |
| 9 | **Family and household members, tenants, multiple units/communities per account** | TMG, Emaar, Lyve | P0 |
| 10 | **Gate / visitor QR passes that actually work and can be shared to WhatsApp** | SODIC (praise), TMG ("when will you add gate services?") | P1 (compounds) |
| 11 | **Local directory:** bus schedules, restaurants and menus, numbers, services, notifications | Ahl Madinaty ×4 | P1, a viral content hook |
| 12 | **Buy and order through the app / shop search and sort** | Ahl Madinaty iOS, Lyve | P2 (Phase 2 commerce) |
| 13 | **Notification controls** ("restrict notifications") | Emaar 2017 | P0, aligns with the founder's personalised-alerts idea |
| 14 | **Expand service categories** (gypsum board, upholstery, wood floors, demolition and haulage) and **coverage** (Alexandria, Obour, Salam, Sharqia) | Fixawy, FilKhedma, Taskty | Phase 2 |
| 15 | **Technician identity and live location; warranty follow-up** | FilKhedma 5★, Fixawy 5★ (14-day warranty) | Phase 2 P0 |

---

## 7. Implications for our product (mapped to the founder's ideas)

### 7.1 Founder idea 1: powerful personalised notification system
- **VOC support:** *"the notifications are really helpful"* (Ahl Madinaty); reminders are the main value of building apps (Amarati: *"الإشعارات بالعربي مع صوت تنبيه"*, "notifications in Arabic with an alert sound"). **Risk:** fatigue (*"restrict notifications"*, Emaar).
- **Recommendation:** give each person per-category controls (dues, water or electricity cut, elevator out of service, visitor at the gate, building vote, offers). Provide **"critical only" defaults**, quiet hours, and a **WhatsApp fallback** for residents without the app. Never send marketing offers through the "critical" channel. That protects trust before Phase 2.

### 7.2 Founder idea 2: mandatory, pervasive AI
- **The competitive bar is already set.** Ettihad ships "Fary" (Arabic and English, text and voice, prepares actions in a card and requires confirmation). Saknna ships an Arabic AI assistant. Amarati ships **meter reading by camera**.
- **AI uses the reviews point to:**
  1. **Receipt and InstaPay screenshot parsing:** auto-match payments to units. This removes the admin's biggest chore of approving receipts.
  2. **Zero-typing building setup:** photograph the paper notebook or an Excel sheet and the AI builds units, fees and arrears. This answers the "elderly residents" and "setup" pain.
  3. **Complaint triage:** classify, prioritise and route to the doorman, admin or technician, with an SLA timer. This answers "no response after complaint".
  4. **Price-sanity check for services (Phase 2):** compare a technician's quote and parts price to a catalogue and flag markups. This answers the 21% overcharge category and the 1,000-vs-400 EGP part story.
  5. **Meter OCR** for water and gas splitting.
  6. **Voice-first for elders** in Egyptian colloquial.
- **Guardrail from VOC:** AI must **prepare actions, then a human confirms** (the Fary pattern), especially for money.

### 7.3 Founder idea 3: WhatsApp bot inside the building group
- **VOC strongly supports it:** praise for *"not every resident has to install the app"*; every competitor positions against WhatsApp groups but still relies on WhatsApp for invites and statements; WhatsApp groups are mainstream enough for national news how-tos (Youm7, Sep 2026).
- **Design implications from complaints:** the bot must (a) never shame non-payers publicly (Amarati user: *"اخفاء بعض الامكانيات عن السكان لمنع الإحراج"*, "hide some features from residents to avoid embarrassment"), (b) answer "how much do I owe?" privately by DM, (c) post neutral summaries (the "monthly summary image" pattern from Amarati), and (d) log complaints from chat into tickets.
- **Risk to verify (outside this file's scope):** WhatsApp Business Platform policy on bots in *groups* and per-message costs. Flag for the technical feasibility research.

### 7.4 Founder idea 4: every resident has an account
- **VOC shows the trap:** forcing accounts with heavy verification causes the worst reviews (OTP loops, selfie rejections, approval delays of months, single-device bans, owners rejected).
- **Recommendation:** use **progressive identity**. Admin-created "shadow" profiles for every flat on day one (name only, phone optional, as Ettihad does) let 100% of the building appear immediately. Residents **claim** their profile with a one-tap WhatsApp link. Family, tenants, helpers and doormen get their own roles. International numbers and abroad mode are supported.

### 7.5 Phase 2 (services marketplace): turning FilKhedma and Taskty's failures into our moat

| Their failure (VOC) | Our counter-design |
|---|---|
| Price changes on site; parts marked up 2.5× | Fixed-price menu plus **in-app quote approval**; parts at catalogue price with photo of receipt; any change needs the customer's in-app OK |
| Technician says "don't tell the company" (leakage around a 30% cut) | Lower, transparent take rate; warranty and insurance **only** if paid in-app; reward technicians for in-app payment |
| No-shows; customer charged the cancellation fee | Provider-cancel equals automatic credit to the customer plus a backup technician dispatched |
| Unskilled, damage, ~500 EGP compensation | Tiered vetting; damage-protection fund; ratings tied to the **building's** reputation (neighbours see who served their building) |
| Theft; workers without ID | ID plus face check at arrival, shown in the app; doorman / gate verification through our visitor-pass module |
| Support black hole | Ticket with SLA countdown; escalation to the building admin; public building-level provider ratings |
| Coverage gaps outside Cairo | Recruit **building-local** technicians (the doorman's network, the area's trusted plumber) and let buildings "bring their own provider" |

**Strategic insight:** our unique advantage over FilKhedma is **the building as a trust unit**. A plumber who did good work for flat 3 is visible to flats 1 to 20, and the doorman verifies arrivals. That social accountability is exactly what FilKhedma 5-star reviewers credit (*"عارف أنه تحت رقابة الابليكيشن وكمان تقييم العميل"*, "he knows he's under the app's supervision and the customer's rating"), and what 1-star reviewers miss.

---

## 8. Competitive takeaways per app (one-liners for the strategy team)

| App | Strength users cite | Weakness users cite | Takeaway |
|---|---|---|---|
| Ettihad | AI "Fary", no need for all residents to install, responsive team | Email-OTP loop on some devices; "copycat" accusation | **The benchmark to beat**; match it on AI and exceed it on WhatsApp and services |
| Amarati | Simple, Arabic-only, camera meter reading, WhatsApp summary image | Levantine product; billing rigidity; iOS crash after update | Not Egypt-localised; beatable on local fit |
| Imarti | Voting, emergency funds, Arabic and English | Possibly paid and possibly Saudi [unverified]; near-zero traction (125 installs) | Too small to judge its model; do not over-read the single "expensive" review |
| Ammarty | Simple, offline mode | 1-month trial then paid, so users uninstall [unverified: one user review; listing shows no IAP] | Shows the cost of paywalling early |
| Sandooq El Emara | Fast developer responses, frequent updates, personal care | Paywall (49.99–499.99 EGP IAP); purchase errors | Strong indie; its reply style (fast, warm, in colloquial) is worth copying |
| Omaraty | Residents without mobiles, outside income, Google sign-in | Tiny base | Good feature ideas to absorb |
| Saknna | Full suite, AI, Excel import | 450–7,500 EGP/month; PWA only; no reviews or social proof | Targets paid compounds; leaves the mass market open |
| TMG Life | Gate QR, NFC electricity top-up, club renewals | iOS payments, approvals, security false positives, services not dispatched | Utilities are a killer feature, but only if they work |
| Ahl Madinaty | Directory "everything in one place", notifications | Stale info, newly required sign-up angered users | **The zero-marketing proof**: useful local content leads to organic installs |
| Emaar / SODIC / Palm Hills / Mountain View | Gate passes, service requests | Crashes, OTP, bans, approvals | Residents of premium compounds are under-served even with official apps |
| FilKhedma | Upfront prices, some great technicians, quick replacements | Overcharging, no-shows, theft, support | Opening for a trust-first marketplace |
| Taskty | Some excellent cleaners | Abandoned app (last update 2023), 79% 1★ since 2025 | Effectively a dying competitor |
| Fixawy | 14-day warranty, upfront price, iOS 4.36 | Coverage claims false, high prices | Warranty plus upfront price is the right promise |

---

## 9. Gaps and what could not be found

- **Saknna:** no store app, so there are **no reviews to analyse**. Its site claims "500+ buildings" (unverified, and the counters on the page render "0").
- **Imarti, Omaraty, Homena and the smaller apps:** 0 to 9 reviews each, too few for statistics.
- **Reddit, Facebook, X:** no indexed threads were found by the search tools for these apps, and the Reddit API blocked our requests. **We did not invent social quotes.** A manual follow-up is recommended: search the Facebook groups "اتحاد ملاك ..." and compound resident groups (e.g., "Madinaty Residents", "Rehab City", "Sheikh Zayed" groups) for "تطبيق" ("app"), "الصيانة" ("maintenance"), "الاشتراك" ("subscription"), "البواب" ("doorman").
- **Hassan Allam, Hyde Park, EGI Residents and Misr Italia apps:** 0 to 4 reviews.
- **Amarati's 43 Play ratings vs 5 written reviews:** the rating breakdown is mostly star-only (36 five-star) and cannot be analysed for content.

---

## 10. Sources (primary)

**Google Play listings** (all `https://play.google.com/store/apps/details?id=<id>&hl=ar&gl=eg`), data pulled 2026-10-12:
com.amarati.app · com.craftfuture.imarti · com.ittihad.ettihad · com.ammarty.ammarty · com.amrem.sandooqelamara · com.omaraty.app · com.tarek.imarati · io.homena.app · com.building1310.app · com.beemind.alemara · com.mrizk.emara.building · com.taqween.emarti · com.elgoktech.buildingmanagement · com.melsayed25.compoundy · com.egerp.bellagio · com.KonektApps.saknmasr · com.tmglife.app · com.kijamii.emaarcommunities · com.kijamii.sodiccommapp · com.palmhills.communityapp · com.congora.mountainview · com.oradevelopers.users.app · com.macber.eg.tatweer · com.moonshot.icommunity · com.moonshot.hap · com.moonshot.hydePark · app.milango.alahlysabbour · app.milango.amergroup · app.milango.morshedy · alrehab.city · com.ahl.madenty · com.collo.egi · com.filkhedma.customer · com.tasktyapp.taskty · com.fixawy.servicebooking · com.spiderte8.shgheelapp · com.true.elmohandesclients · com.snonosystems.elmohandes

**Apple App Store (Egypt storefront)** `https://apps.apple.com/eg/app/id<id>`, reviews via `https://itunes.apple.com/eg/rss/customerreviews/id=<id>/sortby=mostrecent/json`:
1390362823 (SODIC) · 6477568109 (Palm Hills) · 6502700910 (TMG Life) · 1168425830 (Emaar Misr) · 6754685645 (Mountain View) · 1473742608 (FilKhedma) · 1138437170 (Lyve) · 6791464029 (Amarati) · 1071671875 (Fixawy) · 1486080094 (Taskty) · 6739183152 (Hyde Park) · 6756376478 (ORA) · 1498413451 (Ahl Madinaty) · 6502767063 (Tatweer Misr) · 6462085044 (Misr Italia Engage)

**Web**
- Saknna: https://saknna.com
- Amarati site: https://amarati-site.web.app/
- Ettihad: https://www.ettihad.org (per Play listing)
- Ahram, occupants' association law problems: https://gate.ahram.org.eg/News/2139186.aspx
- Elbalad, Housing Ministry amendments: https://www.elbalad.news/4853788
- Elwatan, Sheikh Zayed maintenance: https://www.elwatannews.com/news/details/4915334
- Youm7, elevator dispute: https://www.youm7.com/story/2021/6/7/هل-يحق-لمالك-العقار-الجديد-استخدام-أسانسير-خاص-بالسكان-جبرا/5342588
- Vetogate, elevator accidents: https://www.vetogate.com/5632859
- Youm7, WhatsApp residential-group how-to (2026-09-16): https://www.youm7.com/story/2026/9/16/شعار-عمارة-أو-رقم-شقة-كيف-تضيف-علامة-تعريفية-لنفسك-داخل-مجموعات-المجمعات-السكنية/7545906
- Youm7, building WhatsApp group in Alexandria case (2026-07-24): https://www.youm7.com/story/2026/7/24/جروب-يكشف-السر-رسائل-الجيران-تفضح-جريمة-تقطيع-مسنة-على-يد-ابنتها-بالإسكندرية/7491265
- Ahram Gate, Rehab residents vs city authority levies: https://gate.ahram.org.eg/News/1231089.aspx
- CB Insights / company profiles (FilKhedma acquired by SweepSouth, founded 2014; Fixawy Alexandria 2016; Taskty 2012): https://www.cbinsights.com/company/filkhedma , https://www.cbinsights.com/company/fixawy

**Raw dataset:** `/opt/Myprojects/newproject/research-app/research/data/06-reviews-raw.csv` (1,904 rows including 33 reviews from the two excluded "Elmohandes" apps; columns: store, app_id, title, stars, date, thumbs-up, text, developer reply, source URL).

---

## Verification log

Adversarial re-check on 2026-10-12: fresh fetches of the Google Play listings (`hl=en&gl=eg`, parsed from the embedded ds:5 data), the iTunes Lookup API (`country=eg`), saknna.com, the cited news articles, and a recount of `research/data/06-reviews-raw.csv`.

| # | Claim | Verdict | Evidence URL |
|---|---|---|---|
| 1 | Ettihad: 1,000+ (≈3,000 exact) installs, 4.5 rating (8), released 2026-08-10; free; "money never flows through Ettihad"; InstaPay proof review; QR visitor passes; AI "Fary" (Arabic/English, text or voice, prepares a card and waits for confirmation); manual invite with name only | confirmed | https://play.google.com/store/apps/details?id=com.ittihad.ettihad&hl=en&gl=eg |
| 2 | Amarati: 1,416 installs, 4.74 (43), released 2026-06-21; "built by heads of real building committees in Palestine"; camera meter reading; "ما بنلمس فلوسك"; "free to start" | confirmed | https://play.google.com/store/apps/details?id=com.amarati.app&hl=en&gl=eg |
| 3 | Imarti is from a Saudi company | unverified (inferred from .sa domain only; publisher "Craft Future", Gmail contact, no country) | https://admin.craftsolutions.com.sa/privacy-policy.html |
| 4 | Imarti charges "very expensive" subscriptions | unverified (125 installs, no IAP declared; the one review is ambiguous) | https://play.google.com/store/apps/details?id=com.craftfuture.imarti&hl=en&gl=eg |
| 5 | Saknna: no store app (PWA); 450 / 900 / 2,200 / 7,500 EGP per month; 14-day trial; Arabic AI assistant; Excel import; claims 500+ buildings | confirmed (500+ figure is the site's own claim) | https://saknna.com |
| 6 | Ammarty: 1,684 installs, 4.78 (9), released 2026-09-08; offline mode | confirmed | https://play.google.com/store/apps/details?id=com.ammarty.ammarty&hl=en&gl=eg |
| 7 | Ammarty: 1-month trial then subscription | unverified (single user review; no IAP on listing) | https://play.google.com/store/apps/details?id=com.ammarty.ammarty&hl=en&gl=eg |
| 8 | Sandooq El Emara: 961 installs, 4.75 (16), IAP 49.99–499.99 EGP; supports different fee per unit | confirmed | https://play.google.com/store/apps/details?id=com.amrem.sandooqelamara&hl=en&gl=eg |
| 9 | FilKhedma: 178,066 installs, 3.07 (1,411), histogram 621/20/41/94/631; 59% 1★ in 2025–26 (n=156), 47% full history | confirmed | https://play.google.com/store/apps/details?id=com.filkhedma.customer&hl=en&gl=eg |
| 10 | FilKhedma is a SweepSouth company | confirmed (100% acquisition, Dec 2021) | https://www.naspers.com/news-insights/group-updates/2021/sweepsouth-acquires-egyptian-startup-filkhedma |
| 11 | Taskty: 168,317 installs, 2.07 (659), last updated 2023-12-11; 79% 1★ since 2025 (n=34) | confirmed | https://play.google.com/store/apps/details?id=com.tasktyapp.taskty&hl=en&gl=eg |
| 12 | TMG Life 55,469 installs, 4.79 (1,159), 1,067 five-star; Ahl Madinaty 43,668 installs (≈79% of TMG), 4.62 (199), developer "thelegend" | confirmed | https://play.google.com/store/apps/details?id=com.tmglife.app&hl=en&gl=eg ; https://play.google.com/store/apps/details?id=com.ahl.madenty&hl=en&gl=eg |
| 13 | iOS EG ratings: Fixawy 4.36 (798), Palm Hills 1.38 (47), SODIC 2.22 (81), FilKhedma 3.16 (2,133), TMG Life 4.61 (1,133), Taskty 2.30 (115) | confirmed | https://itunes.apple.com/lookup?id=1071671875&country=eg (and same endpoint for each ID) |
| 14 | 44% of 462 compound-app Play reviews are 1★ | corrected → 35% (≈162/462) | research/data/06-reviews-raw.csv (recount) |
| 15 | MyPorto got about 25 five-star reviews on 2026-06-11 | corrected → 22 | research/data/06-reviews-raw.csv (recount) |
| 16 | Late-payer fine is 100 EGP/year; 10% maintenance deposit; e-assemblies proposed, attributed to a "Ministry of Housing discussion" | corrected (facts confirmed; venue was an EBA construction-committee discussion with a ministry official; fine figure stated by EBA's Fathallah Fawzy) | https://www.elbalad.news/4853788 |
| 17 | Youm7 (16 Sep 2026) how-to on WhatsApp member tags in residential-compound groups | confirmed | https://www.youm7.com/story/2026/9/16/شعار-عمارة-أو-رقم-شقة-كيف-تضيف-علامة-تعريفية-لنفسك-داخل-مجموعات-المجمعات-السكنية/7545906 |

**Not re-checked here:** WhatsApp Business Platform rules for bots in groups (§7.3 already flags this for the technical-feasibility file); keyword-category percentages in §3 (method-dependent estimates, not facts).
