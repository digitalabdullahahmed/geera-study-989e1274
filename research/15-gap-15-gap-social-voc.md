# 15: Social Voice of Customer, Deep Dive (gap-filling for 07)

**What this file is:** a gap-filling study for the building/compound app research pack. Files 02 §11, 03 §13, 06 §9 and 07 §8 all say the same thing: Reddit, Facebook and X were not reachable, and **07 grades "WhatsApp-group chaos" (P13) as Evidence C**. This file goes back to social platforms with different access routes and collects **105 verbatim, cited items**. Every Arabic quote is an exact excerpt of public text. Each one was checked by script against the harvested raw text (see the verification log).
**Date of research:** 2026-10-12 (all relative YouTube dates are converted against this date)
**Market:** Egypt only. Foreign items appear only in §5.4 as analogues and are labelled as such. They are **not** counted in the 105.
**Companion files:** 06 (Play-store reviews), 07 (news and social voice), 10 (WhatsApp bot feasibility), 12 (UX).

---

## 0. TL;DR: what changed after this sweep

1. **The access problem was partly solved.** Reddit's own API and search engines still block us. However, the **Arctic Shift Reddit archive API** returned 262 r/Egypt and r/CAIRO posts plus 8 full comment trees, and **YouTube comment threads** returned **4,010 comments from 38 Egyptian videos**. These videos cover occupants' unions, compounds, neighbours, the bawab, apartment finishing costs, water pressure and electricity cleaning fees. Facebook, X and TikTok remain closed to automated access. Facebook voice appears here only where Egyptian news quotes posts verbatim (§1 lists everything that was tried).
2. **The loudest social pain is about money and trust, not the app.** By tag frequency, the top three are spending transparency and trust (P2, 18 mentions), dues and splitting (P1, 17) and compound management (P3, 16). Residents describe treasurers who refuse to show invoices (V026), threaten an **elevator ban when a resident asks for receipts** (V025), go **three years without a budget** (V023), or put the deposit **in their own name** (V021).
3. **Elevator access is used as a debt-collection weapon.** Residents report the bawab locking the lift "until the full year is paid" (V009), codes being withheld or changed at will (V053, V054), and residents being barred from their own flat for asking to pay in instalments (V008). This is a new, concrete sub-pain. It points to **fair, documented dues collection and instalments** as a phase-1 hook and a phase-2 fintech hook.
4. **Splitting rules are the No.1 practical question.** People ask whether closed flats, the ground floor, unfinished "bare-brick" units or flats with their own meter and pump pay the full share, half or a quarter (V001, V003 to V007). This confirms 06/07: **configurable split rules per unit** are a must-have.
5. **The bawab already takes a cut from technicians.** One Egyptian resident (22 likes, ≈May 2026) explains that when residents call a plumber or electrician, the bawab "agrees a price with him and takes his cut from it", on top of what the resident pays (V042). Together with Ahram's report that the bawab works as a parallel broker (cited in 07), **the building-level commission model for phase 2 already exists informally**. The bawab is the incumbent intermediary to co-opt, not ignore.
6. **Price shock dominates the technician conversation in 2026.** "Prices are on fire" (79 likes, V043), "labour charges have become astronomical" (V044), EGP 120k just to paint a flat (V045). There is also an older Reddit thread where a gate repair with under EGP 100 of parts was billed at 4,000 (V048). The positive mirror image: an electrician wins trust by **showing receipts and the retailer's phone number** (V049), and a SODIC resident praises that "prices are clearly stated for each service" (V105). **Transparent itemized pricing is the trust mechanism people already reward.**
7. **WhatsApp/residents' groups: upgraded from C to B.** There is now direct Egyptian evidence of how groups behave. Compound resident groups (Rehab, Madinaty) are seen as run by bored retirees who police trivia and lobby management (V090 to V094, top comment 468 likes). Members don't respond unless individually @mentioned or called (V097). Leaving a group carries a social cost (V096). Residents forward content to "the building group" as a matter of course (V095). Some groups survive only by allowing **a single message type** (V098). Group posts also carry legal risk under Egypt's cybercrime law (V102). We still found **no verbatim from inside an Egyptian building WhatsApp group about fee-reminder spam**; that specific behaviour remains an ESTIMATE.
8. **Privacy is a live, two-sided issue.** Residents want CCTV for security but also call cameras an invasion if they "expose the neighbours' flats" or are placed without consent (V099 to V101). One Youm7 case ended with 250 stitches (video title). Home-service users fear workers having their **personal number and address** and want **photo/ID before arrival** (V052). Implication: bot and app designs must keep phone numbers masked and make camera and decision governance consensual.
9. **Phase-2 willingness to pay: real but price-anxious.** People spend heavily on finishing and repairs and actively seek trusted guidance on brands and fair prices (V046, V051). They resent percentage-based "levies" (2.5% brokerage called "a protection levy", 43 likes, V070). **ESTIMATE:** a phase-2 marketplace will convert better with **fixed, posted prices plus a small visible booking fee** than with hidden percentage commissions.
10. **Evidence grades updated vs 07:** P6 water (B→A), P8 bawab (B→A), P10 neighbours (B→A), P13 WhatsApp groups (C→B). New pain point P14 "privacy and surveillance" added at B. No downgrades. See §4.

---

## 1. Platform access log: exactly what was tried

| Platform | What was tried (2026-10-12) | Result | What is in this file |
|---|---|---|---|
| **Reddit (official)** | `curl` to `www.reddit.com/r/Egypt/search.json?q=doorman` | **HTTP 403** (blocked) | none directly |
| | `old.reddit.com/.../search.json` | 302 redirect, then **403** | none |
| | WebSearch with "reddit r/Egypt ..." phrasing (3 queries, English) | No Reddit URLs returned; results drifted to Gulf/US news | none |
| **Reddit (archives)** | `api.pullpush.io` | **HTTP 429**: "does not provide free scraping resources for agents" | none |
| | **Arctic Shift API** (`arctic-shift.photon-reddit.com`) | **Works** for post search by subreddit plus keyword and for full comment trees by `link_id`. Comment full-text search returned "Timeout. Maybe slow down a bit" on every attempt (5 tries, including narrow date windows) | **262 unique posts** harvested for 20+ terms in r/Egypt and r/CAIRO; **8 comment trees** read; **13 items** used |
| **X / Twitter** | nitter.net (bot challenge page), xcancel.com (**HTTP 451**), nitter.poast.org and nitter.privacydev.net (no response), nitter.tiekoetter.com (200 but no tweets rendered), nitter.space and lightbrd.com (**403**), nitter.kuuro.net (**404**) | **Inaccessible** | none |
| | WebSearch restricted to x.com/twitter.com for "جروب العمارة" | Only Saudi architecture accounts | none |
| **Facebook** | WebSearch restricted to facebook.com ("اتحاد ملاك العمارة صيانة") | Only page titles (a Saudi union page, a Palestinian facility manager, an October housing-project owners' page); no post text | none directly |
| | DuckDuckGo HTML endpoint with `site:facebook.com "جروب العمارة"` | **Bot challenge** ("Select all squares containing a duck") | none |
| | Bing HTML | No usable result text | none |
| | **Egyptian news that quotes Facebook posts verbatim** | Works | **3 items** (Cairo24 x2, Dostor) |
| **TikTok** | WebSearch restricted to tiktok.com ("البواب العمارة السكان") | Only discover pages and clips of the TV series *Ala Bab El-Omara*; no comments reachable | none |
| **YouTube** | `yt-dlp` search (≈45 Arabic and English queries) plus `youtube-comment-downloader` | **Works** | **4,010 comments** from 38 videos; **82 items** used |
| **Egyptian news** (Youm7, Masrawy, El-Watan, Elbalad, Cairo24, Dostor, Ahram, Shorouk) | WebSearch with domain filter (≈8 queries) plus WebFetch (9 pages). *almasryalyoum.com is blocked by the search tool itself.* | Works | **5 reader-complaint/news items** plus context |
| **Expat forums** | WebFetch and curl of `expat.com/forum/viewtopic.php?id=373741` and `id=293825`; Wayback copy | **HTTP 403**; Wayback 404. InterNations not attempted (member-only) | none |
| **Quora Arabic** | WebSearch restricted to ar.quora.com | One generic Q&A about maintenance funds, with no resident testimony | none |
| **Arabic forums (Fatakat, Ta3lim)** | Not reached: general WebSearch for Arabic building terms never surfaced them | none | none |
| **App Store / Play** (already in 06) | Re-read `data/06-reviews-raw.csv` for WhatsApp/privacy mentions | Works | **2 items** (Taskty privacy, SODIC WhatsApp/pricing) |

**Not attempted on purpose:** driving the founder's own logged-in Chrome session (the `claude-in-chrome` tools) to open Facebook groups or X. That would act through the founder's personal accounts and could expose private group content. It should be a deliberate, manual decision by the founder; see §8.

---

## 2. Method, corpus and biases

**Corpus:**
- **YouTube:** 38 videos chosen because their *topic* is Egyptian building life. Topics: occupants'/owners' unions (Sada El-Balad, Amr Adib's *El Hekaya*, three lawyers' channels), compound-versus-flat debates (Mohamed Zazoaa 2026, Adham Fathallah 2026), ground-floor living, neighbour law, water pressure, the electricity cleaning fee, a viral 2026 bawab-brokerage video, the Rehab residents' group satire (*Wad3anaShow*, 195k views), and the 2026 comedy series *مبينفعش معاه صيانة | إتحاد مُلّاك* (43k views). In total 4,010 comments, keyword-filtered and then read manually.
- **Reddit:** 262 unique posts (r/Egypt, r/CAIRO) from the keyword search, then comment trees for the 8 most relevant threads.
- **News and Facebook-quoted:** 9 fetched pages.

**Selection rule:** an item enters the table only if it is (a) written by an Egyptian resident or user, or quoted verbatim by Egyptian media, (b) about building, compound or home-service life, and (c) specific enough to inform a feature or a phase-2 hypothesis. Pure jokes, legal-advice replies from channel owners, spam and non-Egyptian commenters (for example the Moroccan CCTV thread `Wn-r0qN1Rcs`) were excluded.

**Biases you must keep in mind:**
1. **Topic bias.** We searched for union, maintenance and neighbour videos, so P1/P2/P11 are over-sampled relative to everyday life. The *relative* ranking between pain points is indicative, not a population estimate. Counts below are **ESTIMATE-grade directional signals**.
2. **Platform bias.** YouTube commenters on lawyer channels are people *already in a dispute*, which biases toward conflict. Reddit r/Egypt skews young, English-speaking and urban.
3. **Date precision.** YouTube shows relative dates ("قبل سنة"). We converted them against 2026-10-12, so "≈2025" means roughly 12 to 23 months before the scrape. 75 of 105 items (71%) date from 2024 to 2026, and 35 from 2026.
4. **Likes are low** on most lawyer-channel comments (0 to 3). High-engagement items show in the "Likes" column (for example V090 468, V068 101, V043 79, V082 60).

---

## 3. Verbatim table (105 items)

Legend. **Tags** follow 07's numbering: P1 dues/splitting · P2 spending transparency/trust · P3 compound vs developer/management · P4 technicians/prices/trust · P5 elevator · P6 water · P7 utilities/meters/fees · P8 bawab · P9 garbage · P10 neighbour disputes · P11 governance/legal ignorance · P13 WhatsApp/residents' groups · **P14 privacy/surveillance (new)** · FEAT a feature idea in the user's own words. **Phase:** 1 = adoption/building-management value, 2 = marketplace/intermediary signal.
YouTube links open the exact comment (`&lc=` parameter). Quotes keep the original spelling and typos.

| # | Platform | Source (URL) | Date | Likes | Tag(s) | Quote (Arabic / original) | English translation | Phase |
|---|---|---|---|---|---|---|---|---|
| V001 | YouTube | [yt:zT2dhRIdhp8](https://www.youtube.com/watch?v=zT2dhRIdhp8&lc=Ugxny5siHjlPllrcGA14AaABAg) | ≈2024 | 0 | P1 | ازاي شقة مغلقة تماما تدفع استهلاك مياه وكهرباء العمارة ٢٠٠جنيه والمساكن الفعلي يدفع ٢٥٠ جنيه | How can a completely closed flat pay EGP 200 for the building's water and electricity while the actual occupant pays 250? | 1 |
| V002 | YouTube | [yt:0Hp4MMXlep8](https://www.youtube.com/watch?v=0Hp4MMXlep8&lc=UgyHanbHLObIBuPwLc94AaABAg) | ≈2026-06 | 0 | P1 | انا عندى شقة عندك فى العمارة و مش هدفع بقى انا حر 😂 | I own a flat in your building and I'm not paying, it's my choice 😂 (mocking the closed-flat owner stance) | 1 |
| V003 | YouTube | [yt:0Hp4MMXlep8](https://www.youtube.com/watch?v=0Hp4MMXlep8&lc=UgwqZfy5Mtzif7wb4aV4AaABAg) | ≈2026-09 | 0 | P1 | ااشقق ال لسة على الطوب تدفع صيانة | Do flats still at bare brick [unfinished] pay maintenance? | 1 |
| V004 | YouTube | [yt:GbKb4sCr8b8](https://www.youtube.com/watch?v=GbKb4sCr8b8&lc=UgyJffCyzfnt51O2KU54AaABAg) | ≈2025 | 0 | P1 | العماره نصفها ساكن ونصفها قافل شقته... هل هؤلاء يشاركون في الدفع لاتحاد العماره....وما هي نسبه الدفع نصف مايدفع المالك المقيم في شقته ام ربع | Half the building lives here, half keep their flats closed... do they share in paying the union, and what share: half of what a resident owner pays, or a quarter? | 1 |
| V005 | YouTube | [yt:jI9NDF2_0tM](https://www.youtube.com/watch?v=jI9NDF2_0tM&lc=UgzHuRoNN18MFjMH9cB4AaABAg) | ≈2025-11 | 1 | P1, P5 | هل الدور الارضي ملزم يدفع بدفع صيانة الاسانسير | Is the ground floor obliged to pay for elevator maintenance? | 1 |
| V006 | YouTube | [yt:jI9NDF2_0tM](https://www.youtube.com/watch?v=jI9NDF2_0tM&lc=UgzjoISGK0TFMFiMufp4AaABAg.ACYIsG8gAqOACnSRoMb4EH) | ≈2025 | 0 | P1, P11 | انا ساكنة في الدور الارضي و اللي ماسك اتحاد الملاك الغير رسمي مصمم اني ادفع في كهرباء المصعد و صيانة المصعد و يتم تسجيل ذلك مديونية علي | I live on the ground floor, and whoever runs the informal owners' union insists I pay for elevator electricity and maintenance, and records it as a debt against me. | 1 |
| V007 | YouTube | [yt:jI9NDF2_0tM](https://www.youtube.com/watch?v=jI9NDF2_0tM&lc=UgzzHKNrqNzTfuHKQZJ4AaABAg) | ≈2024 | 0 | P1 | شقتي فيها عداد مياه خاص وماتور مياه خاص ... وأدفع نصف مصاريف الصيانة من حوالي ٨ سنوات وحاليا صاحب العقار عايزني أدفع المبلغ كامل | My flat has its own water meter and pump... I've paid half the maintenance for about 8 years and now the building owner wants the full amount. | 1 |
| V008 | YouTube | [yt:jI9NDF2_0tM](https://www.youtube.com/watch?v=jI9NDF2_0tM&lc=UgwW_jsjGh61t2OIElt4AaABAg) | ≈2025 | 0 | P1 | الساكنين في العماره يمنعوني من دخول شقتي لرغبتي التسديد الخدمات بالتقسيط وأرغامي على دفع كافه المبلغ | The residents are stopping me from entering my flat because I want to pay the service charges in instalments, and are forcing me to pay the whole amount. | 1+2 |
| V009 | YouTube | [yt:jI9NDF2_0tM](https://www.youtube.com/watch?v=jI9NDF2_0tM&lc=UgxHSHNe8nrT8NiyU2J4AaABAg) | ≈2024 | 0 | P1, P5, P8 | مالحل اذا اغلق البواب الاسانسير بناء علي طلب من مجلس الادارة الا بدفع مبلغ السنة كامل | What's the solution if the bawab locks the elevator, on the board's instructions, until the full year's fee is paid? | 1 |
| V010 | YouTube | [yt:jI9NDF2_0tM](https://www.youtube.com/watch?v=jI9NDF2_0tM&lc=UgwnFZ36tzr0qsdt-Mt4AaABAg) | ≈2025 | 1 | P1 | لو انا رئيس اتحاد ملاك واحنا كسكان لمينا مت بعض وشطبنا البرج علي حسابنا هل من حقي ارفع قضيه علي السكان ال مدفعتش | I'm an owners' union head; we residents pooled money and finished the tower at our own cost. Can I sue the residents who didn't pay? | 1 |
| V011 | YouTube | [yt:mrbAwXs3PtI](https://www.youtube.com/watch?v=mrbAwXs3PtI&lc=UgxB6jfs8DkcgGblabF4AaABAg) | ≈2025 | 0 | P1 | كنت أريد أن إيجار الشقة ولكن اتحاد الشاغلين يريد مني أن أدفع ٣ أضعاف مبلغ الصيانة | I wanted to rent the flat out, but the occupants' union wants me to pay three times the maintenance amount. | 1 |
| V012 | YouTube | [yt:yVnH-onX3W8](https://www.youtube.com/watch?v=yVnH-onX3W8&lc=Ugy7FTAQWOAUnH-wldB4AaABAg) | ≈2023 | 2 | P1 | فى ناس مرتبتهم ضعيفة ٢٠٠٠ جنية فى الشهر هتلزمة المحكمة يدفع فلوس اذاى ؟ فى ناس دلوقتى مش لاقية تاكل | Some people earn a weak EGP 2,000 a month; how will a court force them to pay? Some people can't find food now. | 1 |
| V013 | YouTube | [yt:yVnH-onX3W8](https://www.youtube.com/watch?v=yVnH-onX3W8&lc=Ugypu8kaoRlhYGl84v14AaABAg) | ≈2025 | 1 | P1, P7 | الزمونا علي دفع مبلغ ٣٠٠ جنيه نظير نظافه وصيانه وبعد كده قالولنا تعملوا جمعيه عموميه ولازم ندفع كهرباء السلم والاسانسير يبقي هندفع مرتين | They made us pay EGP 300 for cleaning and maintenance, then told us to form a general assembly and pay stair and elevator electricity too; so we'll pay twice. | 1 |
| V014 | YouTube | [yt:zT2dhRIdhp8](https://www.youtube.com/watch?v=zT2dhRIdhp8&lc=UgxTfGh4-3mK0L-badh4AaABAg) | ≈2025-12 | 0 | P2 | ده لو اصلا الوديعه موجوده مش مختفيه. | That's if the deposit even exists and hasn't vanished. | 1 |
| V015 | YouTube | [yt:77GYiWtg2jc](https://www.youtube.com/watch?v=77GYiWtg2jc&lc=UgzxLn1VaJaYFnFbgVV4AaABAg) | ≈2026-07 | 0 | P2, P11 | لابد من تغيير وتعديل القانون وتحديد مدة اتحاد الشاغلين وصلاحياته وعرض المصاريف والصلاحيات والقرارات . هي ليست سبوبة | The law must be amended to set the union's term and powers and to publish expenses, powers and decisions. It is not a money-making racket. | 1 |
| V016 | YouTube | [yt:77GYiWtg2jc](https://www.youtube.com/watch?v=77GYiWtg2jc&lc=UgzOAscRZw_MmAGpQth4AaABAg) | ≈2024 | 1 | P2 | في ناس بتفرض مبالغ باهظه تحت مسمي اتحاظ ملاك برج كذا ومفيش اتحاظ ملاك اساسا | Some people impose huge sums in the name of 'the owners' union of tower X' when there's no union at all. | 1 |
| V017 | YouTube | [yt:0Hp4MMXlep8](https://www.youtube.com/watch?v=0Hp4MMXlep8&lc=Ugw_nff1DbZ28gkttMJ4AaABAg) | ≈2025 | 2 | P2, P1 | حددي إيه الصيانة بالظبط ؟ التي تمت أثناء العام و التكلفة الفعلية و بالنسبة لاجرة الحارس كام في الشهر يجب أن توضحوا الأمور ولا تتركوها عائمة | Specify exactly what maintenance was done during the year and its actual cost, and how much the guard is paid monthly. You must make things clear, not leave them vague. | 1 |
| V018 | YouTube | [yt:GbKb4sCr8b8](https://www.youtube.com/watch?v=GbKb4sCr8b8&lc=UgwE4iBPWuaMrhRBeIh4AaABAg) | ≈2025-12 | 0 | P2, P11 | القانون مش واضح ولايتم عرض بيانات ولا حسابات على حد ؟؟ | The law isn't clear, and no data or accounts are shown to anyone?? | 1 |
| V019 | YouTube | [yt:GbKb4sCr8b8](https://www.youtube.com/watch?v=GbKb4sCr8b8&lc=UgwfPIF0CPOIYzofMu54AaABAg) | ≈2025 | 1 | P2 | اذا كان رئيس الاتحاد ياخذ قرارت منفرده لمصلحته الشخصيه | What if the union head takes unilateral decisions for his personal benefit? | 1 |
| V020 | YouTube | [yt:GbKb4sCr8b8](https://www.youtube.com/watch?v=GbKb4sCr8b8&lc=Ugw38ZolGFUA6z1m7CJ4AaABAg) | ≈2022 | 3 | P2, P11 | لا يوجد لا جمعية عمومية ولا مجلس شاغلين ولا امين صندوق ... بقالهم اكتر من 3 سنوات وهما يمسكون اتحاد ملاك بالعصا والسكين | There's no general assembly, no occupants' board, no treasurer... for over 3 years they've run the owners' union 'with a stick and a knife' (48-flat tower). | 1 |
| V021 | YouTube | [yt:4uoOI2v0Ct8](https://www.youtube.com/watch?v=4uoOI2v0Ct8&lc=UgzZeTP55MCM5c5RAnp4AaABAg) | ≈2024 | 0 | P2 | تم دفع الوديعة وصاحب البرج وضعها باسمه وليس باسم اتحاد الملاك ماذا نفعل | We paid the deposit and the tower owner put it in his own name, not the union's. What do we do? | 1 |
| V022 | YouTube | [yt:4uoOI2v0Ct8](https://www.youtube.com/watch?v=4uoOI2v0Ct8&lc=Ugxao87JZCG-ToxQWSJ4AaABAg) | ≈2022 | 1 | P2 | المسئول عن اتحاد الملاك يستغل منصبه ... التلاعب فى سرقة بعض اموال باتحاد الملاك بالاف الجنيهات وكأن العمارة واموالها ملكا له | The person running the owners' union abuses his position... manipulated and stole thousands of pounds of union money as if the building and its money were his. | 1 |
| V023 | YouTube | [yt:mrbAwXs3PtI](https://www.youtube.com/watch?v=mrbAwXs3PtI&lc=UgwSoYhVD6ox6Z69orx4AaABAg) | ≈2025-12 | 0 | P2 | عندنا اتحاد شاغلين مقدمش ميزانيه سنويه لمدة ثلاث سنوات | Our occupants' union hasn't presented an annual budget for three years. | 1 |
| V024 | YouTube | [yt:e_sDW0P-x3c](https://www.youtube.com/watch?v=e_sDW0P-x3c&lc=Ugx8LesHtCyBUBdn6xN4AaABAg) | ≈2025 | 0 | P2 | بيخربوا العمارة ويستولوا على الوديعة ومش عايزين حد يسالهم علي اي حاجة | They ruin the building, seize the deposit, and don't want anyone asking them about anything. | 1 |
| V025 | YouTube | [yt:yVnH-onX3W8](https://www.youtube.com/watch?v=yVnH-onX3W8&lc=UgznXPqQL-53N1CrzB94AaABAg) | ≈2022 | 3 | P2, P5 | تهديد أحد السكان بحرمانه من الاسانسير برغم دفعه كل مصاريفه وذلك لأن الساكن طلب فواتير وايصالات الكهربا | A union member threatened to ban a resident from the elevator, although he'd paid everything, because he asked for the electricity invoices and receipts. | 1 |
| V026 | YouTube | [yt:yVnH-onX3W8](https://www.youtube.com/watch?v=yVnH-onX3W8&lc=Ugy8Nda-hbtcOZP16C54AaABAg) | ≈2022 | 1 | P2 | قلت لها اريد أن ارى فواتير الكهرباء والمياه وإيصال صيانه الاسنسير تم الرفض من قبل رئيس الاتحاد الملاك وأمين الصندوق | I said I want to see the electricity and water bills and the elevator maintenance receipt; the union head and treasurer refused. | 1 |
| V027 | YouTube | [yt:yVnH-onX3W8](https://www.youtube.com/watch?v=yVnH-onX3W8&lc=UgwDMfF8CqC3SBSVEtV4AaABAg) | ≈2021 | 1 | P2, P1 | رئيس الاتحاد اللى استولى على وديعة الصيانه ورفع ايده من الادارة وبنتعذب عشان نلم فلوس الصيانه | The union head grabbed the maintenance deposit and walked away from management, and we're suffering to collect maintenance money. | 1 |
| V028 | News reader complaint | [elbalad.news](https://www.elbalad.news/5090532) | 2021-12-18 | - | P2, P3 | الوديعة بمبلغ كبير جدا وبدون رقابة من الملاك ... وللاسف الملاك لأتعرف كيفية الصرف من عائد الوديعة | The deposit is a very large sum with no oversight by owners... unfortunately owners don't know how the deposit's returns are spent (Dar Misr compound). | 1 |
| V029 | News reader complaint | [elbalad.news](https://www.elbalad.news/5090532) | 2021-12-18 | - | P3 | مبلغ ١٧٠٠ج من كل وحدة للأمن السيئ جدا | EGP 1,700 from every unit for very bad security. | 1 |
| V030 | Facebook (quoted by news) | [cairo24.com](https://www.cairo24.com/2489391) | 2026-09-05 | - | P3, P9 | إحنا مش عارفين نقعد في البلكونات، ولا نفتح الشبابيك، ولا حتى نخرج نستمتع بالهواء، بسبب الروائح المنبعثة من المكان. | We can't sit on our balconies, open our windows or even go out to enjoy the air because of the smells coming from that spot (Family City, New Cairo; delivery riders using a construction wall as a toilet). | 1 |
| V031 | Facebook (quoted by news) | [cairo24.com](https://www.cairo24.com/2481594) | 2026-08-23 | - | P3, P10 | أنتم إدارة فاشلة عشان تسمعوا لكلام ساكن أو اتنين شبهكم | You're a failed management for listening to one or two residents like you (viral post about a 6th-of-October compound silencing the call to prayer). | 1 |
| V032 | YouTube | [yt:kG_1RjvG7RE](https://www.youtube.com/watch?v=kG_1RjvG7RE&lc=UgwHBuXysXp0qj3VncN4AaABAg) | ≈2026-09 | 0 | P3 | ما٣% مبلغ كبييير جدا كوديعة للصيانة لان السعر غالي جدا | 3% is a huge amount as a maintenance deposit, because the price is so high. | 1 |
| V033 | YouTube | [yt:kG_1RjvG7RE](https://www.youtube.com/watch?v=kG_1RjvG7RE&lc=UgzpW21J-aXrJh_LDgV4AaABAg) | ≈2026-07 | 0 | P3 | اللي يشتري في اي كومبوند ده اشتري الوهم جوه سجن لا من حقة يفتح شباك ولا من حقة يدخل عفش وقت ما يحب ولا من حقة يستقبل ضيوم في اي وقت | Whoever buys in any compound has bought an illusion inside a prison: no right to open a window, move furniture in when he likes, or receive guests any time. | 1 |
| V034 | YouTube | [yt:kG_1RjvG7RE](https://www.youtube.com/watch?v=kG_1RjvG7RE&lc=UgyuxND3oLP9_Ev2bgx4AaABAg) | ≈2026-07 | 21 | P3 | في حد بيدفع ملايين في الزبالة وعلب الصفيح ديه | Does anyone really pay millions for this rubbish and these tin cans? | 1 |
| V035 | YouTube | [yt:00LqRPjkaL0](https://www.youtube.com/watch?v=00LqRPjkaL0&lc=UgxwC844ZsH7-CoI8rd4AaABAg) | ≈2026-08 | 1 | P3 | كمبوند فى المقطم ... مفش اى امن ولا امان و لا اضاءة ... والوديعه ف زمة الله | A compound in Mokattam... no security, no safety, no lighting... and the deposit is 'with God' (gone). | 1 |
| V036 | YouTube | [yt:00LqRPjkaL0](https://www.youtube.com/watch?v=00LqRPjkaL0&lc=UgxmLnX2XmN0Azsryj14AaABAg) | ≈2026-07 | 6 | P3 | عشت في ثلاثة كمبوندات ... انعدام الخصوصية في البلكونات 3- انتشار السرقة بسبب خلاف الامن مع المطور ... 5- صيانة للمنشئات الاساسية مثل الكهرباء والماء على حساب السكان | I lived in three compounds... no balcony privacy; theft spread because security fell out with the developer; basic electricity and water maintenance charged to residents. | 1 |
| V037 | YouTube | [yt:6a1LaaBNVLM](https://www.youtube.com/watch?v=6a1LaaBNVLM&lc=Ugy_4ajtOrIXSWqeJQN4AaABAg) | ≈2025 | 1 | P3 | الكمبوند مهجور ومافيش فيه اي خدمات نهائي | The compound is deserted and has no services at all (Mostathmirin compound, Hadayek October). | 1 |
| V038 | YouTube | [yt:_kOOx3hOm00](https://www.youtube.com/watch?v=_kOOx3hOm00&lc=UgzJ_bFuNlAGn3pTydR4AaABAg) | ≈2023 | 1 | P3, P2 | حاول تتكلم عن حاجة مهمة زي الصيانة ومصروفاته التي اصبحت عبء علي الملاك ... بعد اكثر من اربع سنوات في المحاكم | Talk about something important like maintenance and its costs, which have become a burden on owners... after more than four years in the courts. | 1 |
| V039 | YouTube | [yt:GF3LI4qv71I](https://www.youtube.com/watch?v=GF3LI4qv71I&lc=Ugx-BfQYPXTkuP9KunZ4AaABAg) | ≈2023 | 0 | P3 | دبي 1.3% وديعة صيانة وكلنا عارفين قوة البنية التحتية والخدمات والصيانة الدورية ومافيش فرق صيانة | Dubai: a 1.3% maintenance deposit, strong infrastructure and services, periodic maintenance, and no 'maintenance top-ups'. | 1 |
| V040 | Facebook (quoted by news) | [dostor.org](https://www.dostor.org/5596429) | 2026-06-13 | - | P3 | تضرر عدد من قاطني أحد الكومباوندات السكنية بالجيزة من القائمين على إدارته | (Viral video summarised by the ministry) A number of residents of a Giza compound were harmed by its management; the ministry found a dispute over gate security blocking construction materials and allegedly demanding money. | 1 |
| V041 | Reddit | [reddit:hpk1rlx](https://www.reddit.com/r/Egypt/comments/rldaep/_/hpk1rlx/) | 2021-12-22 | 1 | P3 | Compounds handle their own cleaning/landscaping/security/maintenance so expect a good invoice every few months for running fees which you have to pay. | (English original) | 1 |
| V042 | YouTube | [yt:njkHf6a789o](https://www.youtube.com/watch?v=njkHf6a789o&lc=UgxsGPMWkJ7bVnTFFqt4AaABAg) | ≈2026-05 | 22 | P4, P8 | لو طلبنا سباك كهربائى وفنى بيتفقوا معاه يطلب مبلغ معين ويطلعله منه حسنته بالاضافه للفلوس اللى بيخدوها من الساكن اللى طلب الصنيعى ده | If we ask for a plumber, electrician or technician, they [the bawabs] agree with him on a price and take a cut from it, on top of the money they take from the resident who asked for that workman. | 2 |
| V043 | YouTube | [yt:qfFTXaP1WzE](https://www.youtube.com/watch?v=qfFTXaP1WzE&lc=Ugzc2oQPAYOqkE4-rEN4AaABAg) | ≈2026-09 | 79 | P4 | انا حاليا بشطب شقتي و الاسعار مولعه ادعولي تخلص علي خير | I'm finishing my flat right now and prices are on fire. Pray it ends well. | 2 |
| V044 | YouTube | [yt:qfFTXaP1WzE](https://www.youtube.com/watch?v=qfFTXaP1WzE&lc=Ugxfw1dKr69q0r7jKed4AaABAg) | ≈2026-09 | 1 | P4 | اسعار الشقق والتشطيب والعفش والأجهزة الكهربائية بقت خيالية دة غير المصنعيات اللى بقت فلكية | Prices of flats, finishing, furniture and appliances are unreal, not to mention labour charges, which have become astronomical. | 2 |
| V045 | YouTube | [yt:qfFTXaP1WzE](https://www.youtube.com/watch?v=qfFTXaP1WzE&lc=UgwaoaEBw-iXdu0fNyF4AaABAg) | ≈2026-09 | 1 | P4 | النقاشة عندي مكلمة ١٢٠ الف جنية ( معملتش جبس و دهانات بس للشقة ) 💔 | Painting alone came to EGP 120,000 for my flat (no gypsum, just paint) 💔 | 2 |
| V046 | YouTube | [yt:qfFTXaP1WzE](https://www.youtube.com/watch?v=qfFTXaP1WzE&lc=Ugw9u1gi_dERDpayH3t4AaABAg) | ≈2026-09 | 2 | P4 | وعايزين فيديو تقولنا الماركات الكويسة للخامات بتاعة الكهرباء والسباكة | We want a video telling us the good brands for electrical and plumbing materials. | 2 |
| V047 | Reddit | [reddit:acknowledging_](https://www.reddit.com/r/Egypt/comments/wmfrl0/acknowledging_the_source_of_our_problems/) | 2022-08-12 | 54 | P4 | Technicians charging him 4X the repair cost whilst hiding the company's actual invoice | (English original, r/Egypt post) | 2 |
| V048 | Reddit | [reddit:ijzejwl](https://www.reddit.com/r/Egypt/comments/wmfrl0/_/ijzejwl/) | 2022-08-12 | 15 | P4 | شركة بتعمل بوابات كانوا بيصلحوا بوابة جابوا حاجات مكملتش ١٠٠ جنيه وبيقولي الحساب ٤٠٠٠ | A gate company fixing a gate brought parts worth under EGP 100 and told me the bill was 4,000. | 2 |
| V049 | Reddit | [reddit:prices_arent_j](https://www.reddit.com/r/Egypt/comments/yw1sml/prices_arent_just_increasing_business_owners_have/) | 2022-11-15 | 125 | P4 | he was nervous because he didn't want me to think that he's trying to earn an extra pound here and there so he showed me the receipts and gave me the address and phone number of the retailer | (English original) An electrician 'one of the good ones' proves honesty by showing receipts. | 2 |
| V050 | Reddit | [reddit:iwhhebv](https://www.reddit.com/r/Egypt/comments/yw1sml/_/iwhhebv/) | 2022-11-15 | 7 | P4 | i had a similar experience with my electrician with wires ... the price MORE THAN DOUBLED like how is that possible? | (English original) | 2 |
| V051 | Reddit | [reddit:plumber_in_new](https://www.reddit.com/r/CAIRO/comments/1u539wr/plumber_in_new_cairo_ask_me_anything_free_advice/) | 2026-06-13 | 1 | P4 | Fair prices for plumbing materials in Egypt so nobody rips you off. | (English original; a New Cairo plumber's 'AMA' pitch to expats in New Cairo, Madinaty and Rehab: supply-side signal) | 2 |
| V052 | App Store | [apps.apple.com](https://apps.apple.com/eg/app/id1486080094) | 2026-02-12 | - | P4, P14 | تواصل العاملة معايا بشكل مباشر على رقمي الشخصي ومعاها عنواني، ودا مقلق من ناحية الخصوصية والأمان ... عدم وجود نظام واضح لتعريف العاملة قبل الوصول (زي صورة أو كارت تعريف) | The worker contacted me directly on my personal number and has my address, which is worrying for privacy and safety... no clear system to identify the worker before arrival (photo or ID card). (Taskty) | 2 |
| V053 | YouTube | [yt:jI9NDF2_0tM](https://www.youtube.com/watch?v=jI9NDF2_0tM&lc=Ugx-UyJ7oNunVVHo3cd4AaABAg) | ≈2026-01 | 1 | P5, P10 | طب لو احد السكان هو ال بيمنعنا منه ويغير الشفرات بمزاجه ويقفالالباب المدخل بمزاجه الحل ايه | What if one resident blocks us from it, changes the [elevator] codes whenever he likes and locks the entrance door as he pleases? | 1 |
| V054 | News reader complaint | [dostor.org](https://www.dostor.org/4657268) | 2024-03-12 | - | P5, P2 | يرفضا تسليمها الشفرات الخاصة بالمصاعد دون مسوغ قانوني وبدون سبب | They refuse to hand her the elevator codes without legal justification or reason (lawsuit: owner paid maintenance yet denied 10 elevator codes; won on appeal). | 1 |
| V055 | YouTube | [yt:3KCCKSyT4kk](https://www.youtube.com/watch?v=3KCCKSyT4kk&lc=UgzsrXnELhDVpcN3FK14AaABAg.AXN4qOA1RAbAXOYZPaoEUp) | ≈2026-06 | 3 | P5, P6 | بس ممكن تقابل مشاكل في الأسانسير ومشاكل أخرى في ضغط المياه | But you may face elevator problems and other water-pressure problems (upper floors). | 1 |
| V056 | YouTube | [yt:0nFQ9t5JLaQ](https://www.youtube.com/watch?v=0nFQ9t5JLaQ&lc=UgxfVuFVac7lYyJ-i3p4AaABAg) | ≈2025 | 0 | P6 | الموتور 1 حصان راكب فى الدور الخامس وطول النهار مفيش مياه أنا زهقت والموتور إذا ركبته تحت هيتسرق | The 1-hp pump is installed on the 5th floor and there's no water all day. I'm fed up, and if I install the pump downstairs it'll be stolen. | 1+2 |
| V057 | YouTube | [yt:0nFQ9t5JLaQ](https://www.youtube.com/watch?v=0nFQ9t5JLaQ&lc=UgwrryHnWBaVIXF6Ge94AaABAg) | ≈2023 | 0 | P6 | عندى مشكله ضعف مياه فى الدور العاشر (الدور الاخير) مع العلم ان العماره شغاله على خزان مياه | I have weak water on the 10th (top) floor, and the building runs on a water tank. | 1+2 |
| V058 | YouTube | [yt:O4NEJTHfBG8](https://www.youtube.com/watch?v=O4NEJTHfBG8&lc=UgwRUBC07iASbhfiV014AaABAg) | ≈2026-06 | 2 | P6, P7 | لما كان في تخفيف أحمال وبيقطعوا الكهرباء فطبعا علشان المياه مرتبطة بالمواتير فبتقطع برضو | During load-shedding they cut the electricity, and since water depends on the pumps, it gets cut too (Faisal). | 1 |
| V059 | YouTube | [yt:O4NEJTHfBG8](https://www.youtube.com/watch?v=O4NEJTHfBG8&lc=UgxqA7yEzyAwQaczB_d4AaABAg) | ≈2026-06 | 1 | P6 | اللي اعرفه ان المياه بتقطع ب ال٣ أيام في حدايق اكتوبر | What I know is that the water gets cut for three days at a time in Hadayek October. | 1 |
| V060 | YouTube | [yt:O4NEJTHfBG8](https://www.youtube.com/watch?v=O4NEJTHfBG8&lc=UgwUZ7dKPeP3WpOtqfd4AaABAg) | ≈2026-06 | 1 | P6 | الميه للاسف مش حلوه للشرب الدكتور قالنا بلاش الاطفال يشربوا منها خالص | Unfortunately the water isn't good to drink; the doctor told us not to let the children drink it at all. | 2 |
| V061 | Reddit | [reddit:water_out_in_t](https://www.reddit.com/r/Egypt/comments/171mheo/water_out_in_tagamo3_5_for_2_days/) | 2023-10-06 | - | P6 | They said that a pipe blew up in Re7ab and that’s what caused it ... why the hell is it not fixed yet? | (English original; water out in Tagamo3 5 for 2 days) | 1 |
| V062 | Reddit | [reddit:k3tv39p](https://www.reddit.com/r/Egypt/comments/171mheo/_/k3tv39p/) | 2023-10-07 | 3 | P6 | According to their Facebook page, it's fixed now and just a matter of time until we get water. I don't trust them that much tho. | (English original) Official Facebook updates are not trusted. | 1 |
| V063 | Reddit | [reddit:hpf6dtq](https://www.reddit.com/r/Egypt/comments/rldaep/_/hpf6dtq/) | 2021-12-21 | 11 | P6, P3 | معرضة لان مياة وكهربا تقطع كتير عادي جدا | [In compounds] water and electricity can get cut a lot, it's very normal. | 1 |
| V064 | YouTube | [yt:g4EUPWgyF2s](https://www.youtube.com/watch?v=g4EUPWgyF2s&lc=UgzISHMfIavwVKBDTCZ4AaABAg.AKjIdv8SRAUAKjJSgCWdeZ) | ≈2025 | 0 | P7 | بيخصم من غير سبب واضح العداد كان فيه رصيد ٤٠ج شحنت ب ١٠٠ اصبح الرصيد ٨٤ج | It deducts without a clear reason: the meter had EGP 40, I topped up 100 and the balance became 84. | 1 |
| V065 | YouTube | [yt:g4EUPWgyF2s](https://www.youtube.com/watch?v=g4EUPWgyF2s&lc=UgxIjd42w-3yfiozUll4AaABAg) | ≈2024 | 0 | P7 | ده شغل سرقه واجرام من الحكومة | This is theft and crime by the government (on the cleaning fee added to electricity). | 1 |
| V066 | YouTube | [yt:g4EUPWgyF2s](https://www.youtube.com/watch?v=g4EUPWgyF2s&lc=UgzmapmIropGrXzJXOt4AaABAg) | ≈2025 | 1 | P7, P9 | يعنى رسوم النظافه دى الزبالة ولا ايه | So is this 'cleaning fee' for the garbage, or what? | 1 |
| V067 | YouTube | [yt:KvIEGSsKqvQ](https://www.youtube.com/watch?v=KvIEGSsKqvQ&lc=UgxZfzktV3CYBa4uWxt4AaABAg) | ≈2025 | 0 | P7, P9 | والهى العظيم بدفع شهريا 40 جنية على فاتورة الكهرباء 😢😢😢 | I swear I pay EGP 40 a month [cleaning fee] on the electricity bill 😢 | 1 |
| V068 | YouTube | [yt:njkHf6a789o](https://www.youtube.com/watch?v=njkHf6a789o&lc=UgyPf_gF2wvDYrzzsdh4AaABAg) | ≈2026-05 | 101 | P8 | السمسار و سايس الجراج و البوابين في مصر بلطجيه وعيشين بالدراع | Brokers, parking attendants and bawabs in Egypt are thugs who live by muscle. | 1 |
| V069 | YouTube | [yt:njkHf6a789o](https://www.youtube.com/watch?v=njkHf6a789o&lc=UgxsGPMWkJ7bVnTFFqt4AaABAg) | ≈2026-05 | 22 | P8 | البوابين عندنا ساكنين ببلاش وميه ونور ببلاش غير السمسره ... ولو بقى مش حابب صاحب الشقه يوقف حال الشقه ويطفش اى مشترى | Our bawabs live free, with free water and power, plus brokerage... and if he dislikes a flat owner he blocks the flat and scares off any buyer. | 1+2 |
| V070 | YouTube | [yt:njkHf6a789o](https://www.youtube.com/watch?v=njkHf6a789o&lc=UgwLgiyOp8HoX0YqCtl4AaABAg) | ≈2026-05 | 43 | P8 | ال ٢.٥٪؜ سمسره اصبحت اتاوه مفروضة في جميع انحاء مصر | The 2.5% brokerage fee has become a protection levy imposed all over Egypt. | 2 |
| V071 | YouTube | [yt:3KCCKSyT4kk](https://www.youtube.com/watch?v=3KCCKSyT4kk&lc=Ugw5GFkKbIF45P7DvXV4AaABAg) | ≈2026-09 | 0 | P8, P14 | اول حاجة البواب كانة معاك فى الشقة | [Ground floor] first, the bawab is basically in the flat with you. | 1 |
| V072 | YouTube | [yt:yVnH-onX3W8](https://www.youtube.com/watch?v=yVnH-onX3W8&lc=UgznGijkqBpAbCsKsiV4AaABAg) | ≈2025 | 1 | P8, P1 | هل هناك وجوبية التمسك بحارس للعقار وخصوصا إذا كان سيء الخلق ويتمسك به اربع خمس ملاك من ضمن ١٨ مالك....وهل ممكن المشاركة فى مصاريف الاتحاد كلها فيما عدا راتب الحارس | Must we keep a building guard, especially an ill-mannered one whom 4-5 of 18 owners insist on? Can I pay all union costs except the guard's salary? | 1 |
| V073 | YouTube | [yt:_kOOx3hOm00](https://www.youtube.com/watch?v=_kOOx3hOm00&lc=UgzP6FZ2Y8wKRVtdWO54AaABAg) | ≈2025 | 1 | P8 | جت شركة امن مسكت الحي وقالوا حيحطوا اسوار وبوابات ... وكل ده عشان البوابين مش يروحوا | A security company took over our district [October] promising walls and gates... and it was all blocked so the bawabs wouldn't lose their jobs. | 1 |
| V074 | Reddit | [reddit:ldgihjl](https://www.reddit.com/r/Egypt/comments/1e4hew9/_/ldgihjl/) | 2024-07-16 | 1 | P8 | you are paying her to do a job if she doesn’t do it properly or doesn’t listen then don’t pay | (English original; on the bawab's wife wedging the door open so stray dogs got in) | 1 |
| V075 | Reddit | [reddit:whats_the_best](https://www.reddit.com/r/CAIRO/comments/1we8ull/whats_the_best_way_to_find_renters_for_my_flat/) | 2026-09-12 | 1 | P8 | I need to find renters and our doorman hasn't been able to help (the first advice I received) | (English original) The doorman is the default rental broker. | 2 |
| V076 | Reddit | [reddit:welad_el_bawab](https://www.reddit.com/r/Egypt/comments/1hsta04/welad_el_bawab_beywala3o_fy_5ashab/) | 2025-01-03 | 1 | P8, P10 | welad el bawab beta3 el 3omara el warana beywala3o fy 5ashab kol youm w m4 3aref afte7 el 4obak mn el ree7a | (Franco-Arabic) The bawab's kids in the building behind us burn wood every day and I can't open my window because of the smell. | 1 |
| V077 | YouTube | [yt:njkHf6a789o](https://www.youtube.com/watch?v=njkHf6a789o&lc=UgyecsjIwnzAtRuXCGd4AaABAg.AVzz3hX-fgiAW-_5JUupEg) | ≈2026-05 | 20 | P9 | كنت بدي عامل قمامه بعتبرها صدقه ... قالى وفين باقى الشهور اللى فاتت | I used to give the garbage collector money as charity... [after a break] he said: where are the other months you missed? | 1 |
| V078 | YouTube | [yt:XN3VbXFM_dQ](https://www.youtube.com/watch?v=XN3VbXFM_dQ&lc=UgyVj_BRiEo5pgs7dM94AaABAg) | ≈2024 | 1 | P9, P10 | والجارة الى تسلط عيالها يعملو حمام ع السلم وبترمى زبالة | And the neighbour who lets her kids relieve themselves on the stairs and throws garbage? | 1 |
| V079 | YouTube | [yt:XN3VbXFM_dQ](https://www.youtube.com/watch?v=XN3VbXFM_dQ&lc=UgxNS7rQ-gDXKOE6hCZ4AaABAg) | ≈2025 | 1 | P10, P4 | بقالى 6شهور بعاتن. من الجار الافوقى بسبب أن الحييطان بتسرب ميه | I've suffered for 6 months from the upstairs neighbour because the walls leak water. | 1+2 |
| V080 | YouTube | [yt:XN3VbXFM_dQ](https://www.youtube.com/watch?v=XN3VbXFM_dQ&lc=UgzdmuuWY6FO1g7_q9B4AaABAg) | ≈2022 | 2 | P10, P4 | سقف الحمام وقع علينا بسبب نشع وتسريب الصرف بتاع حمام جاري اللي فوقيا | Our bathroom ceiling fell on us because of seepage from the upstairs neighbour's bathroom drain. | 1+2 |
| V081 | YouTube | [yt:XN3VbXFM_dQ](https://www.youtube.com/watch?v=XN3VbXFM_dQ&lc=Ugx7h2Rvax7wzQUdd9R4AaABAg) | ≈2025 | 5 | P10, P11 | على ماخلص الإجراءات دي كلها يكون الجار مات | By the time I finish all these procedures, the neighbour will be dead. | 1 |
| V082 | YouTube | [yt:3KCCKSyT4kk](https://www.youtube.com/watch?v=3KCCKSyT4kk&lc=Ugw8bsSv10A2DPMRUGR4AaABAg) | ≈2026-06 | 60 | P10 | مشاكل الدور الارضي : ازعاج + قلة خصوصيه+ رطوبة + فيران+ صراصير و حشرات ... + حراميه | Ground-floor problems: noise + no privacy + damp + mice + cockroaches and insects... + thieves. | 1+2 |
| V083 | YouTube | [yt:3KCCKSyT4kk](https://www.youtube.com/watch?v=3KCCKSyT4kk&lc=Ugx1mzzExYUI14lAoe54AaABAg) | ≈2026-06 | 3 | P10 | في ناس بتركن عجل ف مدخل العماره ... غير الجيران اللي بتركن حاجات في المنور | Some people park bikes in the building entrance... plus neighbours who dump stuff in the light-well. | 1 |
| V084 | YouTube | [yt:_kOOx3hOm00](https://www.youtube.com/watch?v=_kOOx3hOm00&lc=UgzSs2VBHAKpllwt3IJ4AaABAg.9pxaVphwhsZ9py5XjpdEJM) | ≈2023 | 9 | P10 | الولد بتاع الدليفري ممنوع يطلع ف الاسانسير وانه يستعمل السلم لان الاسانسير للسكان فقط | The delivery boy is banned from the elevator and must use the stairs because the elevator is 'for residents only' (Rehab group rule). | 1 |
| V085 | YouTube | [yt:jI9NDF2_0tM](https://www.youtube.com/watch?v=jI9NDF2_0tM&lc=UgwDd7qoGBYK-EJwdTZ4AaABAg) | ≈2024 | 1 | P10, P11 | انا رئيس اتحاد ملاك عقار هل من حقى منع ايجار الشقق المفروشة وخصوصا للشباب | I'm a building's owners' union head: do I have the right to ban furnished rentals, especially to young men? | 1 |
| V086 | YouTube | [yt:jI9NDF2_0tM](https://www.youtube.com/watch?v=jI9NDF2_0tM&lc=UgzPb1rFQEdO6qJAVtJ4AaABAg) | ≈2024 | 0 | P11 | تم عمل جمعية عمومية وتحديد المصاريف الشهرية دون علمى ولم يتم اخبارى بالجمعية العمومية ... وفوجئت بوجود مديونية عليا | A general assembly was held and monthly fees set without my knowledge; I wasn't told about the assembly... and was surprised to find a debt against me. | 1 |
| V087 | YouTube | [yt:yVnH-onX3W8](https://www.youtube.com/watch?v=yVnH-onX3W8&lc=UgyuN-eLuhAFh-tvAH54AaABAg) | ≈2024 | 2 | P11 | انا اتفاجئت ان بعض السكان عملوا اتحاد ملاك من غير اعلامي ولا اعلام ٥ شقق اخري | I was surprised that some residents formed an owners' union without telling me or five other flats. | 1 |
| V088 | YouTube | [yt:77GYiWtg2jc](https://www.youtube.com/watch?v=77GYiWtg2jc&lc=Ugy3Ow2Qwvi_VHiGleF4AaABAg) | ≈2025 | 0 | P11, P2 | احنا عندنا حي الهرم عمل اتحاد ملاك لمجموعة من السكان محدش بيثق فيهم | In our Haram district an owners' union was formed by a group of residents nobody trusts. | 1 |
| V089 | YouTube | [yt:XN3VbXFM_dQ](https://www.youtube.com/watch?v=XN3VbXFM_dQ&lc=UgxH547ZgdRjwMw-mFt4AaABAg) | ≈2024 | 2 | P11 | ف كل مره لجنه المعاينه بتكون مرتشيه | Every time, the inspection committee is bribed. | 1 |
| V090 | YouTube | [yt:_kOOx3hOm00](https://www.youtube.com/watch?v=_kOOx3hOm00&lc=UgxqsDUL5VD-lUgAMgN4AaABAg) | ≈2023 | 468 | P13, P10 | اغلب الناس الي بتكتب عن المشاكل التافهة دي هم عبارة عن عجائز متقاعدين معندهمش حاجة يعملوها فبيعملو مشاكل مع الجيران | Most people writing about these trivial problems [in Rehab residents' groups] are retirees with nothing to do, so they make problems with the neighbours. | 1 |
| V091 | YouTube | [yt:_kOOx3hOm00](https://www.youtube.com/watch?v=_kOOx3hOm00&lc=UgxqsDUL5VD-lUgAMgN4AaABAg.9pwmd5tOhQP9pxStzLxBXm) | ≈2023 | 19 | P13 | يعني هما العجائز دول هما ادمنز الجروبس والصفحات دي !!!؟ | So these old people are the admins of these groups and pages?! | 1 |
| V092 | YouTube | [yt:_kOOx3hOm00](https://www.youtube.com/watch?v=_kOOx3hOm00&lc=UgwitVEPdVFJGybYskZ4AaABAg) | ≈2023 | 7 | P13 | فايتك مشاكل جروب ائتلاف سكان مدينتي بقى😂 | You've missed the problems of the 'Madinaty Residents Coalition' group 😂 | 1 |
| V093 | YouTube | [yt:_kOOx3hOm00](https://www.youtube.com/watch?v=_kOOx3hOm00&lc=Ugy0LzqcJDaQrSlHTdV4AaABAg) | ≈2023 | 4 | P13 | خلي بالك جروب مدينة الرحاب لافزر هيعملوا عليك استوريز و حملة ريبورتات 😂😂 | Careful, the Rehab City group lovers will make stories about you and a mass-report campaign 😂 | 1 |
| V094 | YouTube | [yt:_kOOx3hOm00](https://www.youtube.com/watch?v=_kOOx3hOm00&lc=UgwCOx_ODGn-vM4nfKt4AaABAg) | ≈2023 | 34 | P13, P3 | اهم بوست عندهم انهم عايزين اي حد جاي من برا الرحاب ... لازم ب فلوس و انهم بيطلبوا الادارة انهم يعملوا تيكت دخول زائر | Their most important post: anyone coming from outside Rehab... must pay; they're asking management to introduce a visitor entry ticket. | 1 |
| V095 | YouTube | [yt:Fejp-oBY3EU](https://www.youtube.com/watch?v=Fejp-oBY3EU&lc=UgxSQA_6v22AGISI6FR4AaABAg) | ≈2026-09 | 4 | P13 | عايز ابعته لجروب العماره بس في مشكله العماره مفهاش أسانسير | I want to send it [an owners'-union comedy episode] to the building group, but the problem is our building has no elevator. | 1 |
| V096 | YouTube | [yt:PzqrPSWjkx4](https://www.youtube.com/watch?v=PzqrPSWjkx4&lc=Ugy8rrMztOQ_CKStC4J4AaABAg) | ≈2018 | 45 | P13 | والله كل اما اخرج من الجروب عمي يجيبني من قفايا ويدخلني تاني ههههه | Every time I leave the group, my uncle grabs me by the neck and adds me back (family group; exit is socially costly). | 1 |
| V097 | Reddit | [reddit:no_one_respond](https://www.reddit.com/r/Egypt/comments/16g25of/no_one_responds_to_whatsapp_anymore/) | 2023-09-11 | 4 | P13 | Especially in WhatsApp groups, you have either mention each member in the group individually or call them to get them to respond. | (English original, r/Egypt) | 1 |
| V098 | News reader complaint | [youm7.com](https://www.youm7.com/story/2018/8/12/أغرب-جروبات-واتس-آب-من-محبى-السبانخ-لـ-أنا-هنشر/3908172) | 2018-08-12 | - | P13 | هذه الرسالة الوحيدة التى يتم تبادلها على المجموعة درءًا للخلافات بين الجيران | This is the only message exchanged on the group [a building's women: 'I'm about to hang laundry, take yours in'], to avoid disputes between neighbours. | 1 |
| V099 | YouTube | [yt:tbXr79GS_98](https://www.youtube.com/watch?v=tbXr79GS_98&lc=Ugy3-QKSEC7TnSNIj894AaABAg) | ≈2024 | 1 | P14, P10 | الكامرات دي تعدي على خصوصيات الاخرين لايجوز تركيب كلمره تكشف شقق الجيران | These cameras violate others' privacy; you can't install a camera that exposes the neighbours' flats. | 1 |
| V100 | YouTube | [yt:tbXr79GS_98](https://www.youtube.com/watch?v=tbXr79GS_98&lc=UgxjvAiVYaHKxOsGUUB4AaABAg) | ≈2021 | 3 | P14, P10 | انتم اخطأتم بسبب انكم فاكرين العماره بتاعتكم لوحدكم بالاتفاق مع السكان تركب كاميرات مراقبة | You were wrong to think the building is yours alone; CCTV gets installed by agreement with the residents. | 1 |
| V101 | YouTube | [yt:yVnH-onX3W8](https://www.youtube.com/watch?v=yVnH-onX3W8&lc=Ugz-ULlhSlwouJu0Bpd4AaABAg) | ≈2025 | 1 | P14, P1 | حكم القانون في تركيب كاميره بالاسانسير ... ووجود اعتراض من بعض السكان ... هل مصاريف صيانة خزانات المياه وهي تخص الادوار العليا فقط تستقط | What does the law say about a camera in the elevator... some residents object... and should tank maintenance, which serves only the upper floors, be [split differently]? | 1 |
| V102 | News reader complaint | [dostor.org](https://www.dostor.org/5714544) | 2026-09-24 | - | P14, P13 | الجريمة تظل جريمة، سواء ارتكبت أمام مليون شخص، أو أمام ١٥ أمًا داخل جروب «واتساب» | A crime remains a crime whether committed before a million people or before 15 mothers inside a WhatsApp group (cassation lawyer on Law 175/2018). | 1 |
| V103 | YouTube | [yt:3KCCKSyT4kk](https://www.youtube.com/watch?v=3KCCKSyT4kk&lc=UgwWWFpg04Ho1NhdBx54AaABAg) | ≈2026-06 | 35 | FEAT, P8 | نفسي يكون فيه جروبات لناس بتبيع او تشتري بعيد عن السماسره | I wish there were groups for people buying or selling, away from the brokers. | 2 |
| V104 | YouTube | [yt:O4NEJTHfBG8](https://www.youtube.com/watch?v=O4NEJTHfBG8&lc=Ugyr_dw7isRrdxLXK-94AaABAg) | ≈2026-06 | 90 | FEAT | انا مهندس سوفتوير بفكر اعمل ابليكيشن او موقع يجمع كل الشقق الي ايجار و للبيع و الاسعار في مصر كلها | I'm a software engineer thinking of building an app or site gathering all rental and for-sale flats and prices across Egypt. | 2 |
| V105 | App Store | [apps.apple.com](https://apps.apple.com/eg/app/id1390362823) | 2024-10-13 | - | FEAT, P13, P4 | I have been able to generate QR codes for visitors quite easily with the option to share via WhatsApp. I have also requested plumbing, aluminium and carpentry services via the app. I appreciate the fact that prices are clearly stated for each service | (English original, SODIC App review) WhatsApp hand-off and posted prices are valued. | 1+2 |


**Platform mix of the 105 items:** YouTube 82 · Reddit 13 · News reader complaints 5 · Facebook posts quoted by news 3 · App Store 2.
**Year mix:** 2018: 2 · 2021: 6 · 2022: 9 · 2023: 13 · 2024: 15 · 2025: 25 · 2026: 35.
**Phase mix:** phase 1 only: 81 · phase 2 only: 16 · both: 8.

---

## 4. Frequency by pain point vs 07's ranking (with evidence-grade changes)

Each item can carry up to three tags. "All tags" counts every mention; "Primary" counts only the first tag. **These are directional counts from a topic-biased sample (ESTIMATE), not prevalence.**

| 07 rank | Pain point | 07 grade | All-tag mentions (n=105) | Primary-tag items | Mentions dated 2023+ | Social-voice rank (this file) | **New grade** | Why |
|---|---|---|---|---|---|---|---|---|
| 1 | P1 Dues non-payment and unfair splitting | A | **17** | 13 | 16 | 2 | **A (confirmed)** | 17 independent commenters across 7 videos; new specifics on closed flats, ground floor, bare-brick units, own meter/pump, instalments (V001 to V013) |
| 2 | P2 Spending transparency, trust in treasurer | A | **18** | 15 | 12 | **1** | **A (strengthened)** | Refused invoices (V026), elevator-ban threat for asking for receipts (V025), 3 years without a budget (V023), deposit in owner's name (V021) |
| 3 | P3 Compound vs management/developer | A | **16** | 13 | 12 | 3 | **A (confirmed)** | 2026 YouTube compound debates (V032 to V036) plus Facebook posts quoted by Cairo24/Dostor (V030, V031, V040) |
| 4 | P4 Technicians: price, trust, no-shows | A | **14** | 11 | 9 | 4 (tie) | **A (confirmed; new angle)** | Price shock 2026 (V043 to V045), overbilling (V047, V048), receipts as trust signal (V049), bawab's commission (V042) |
| 5 | P5 Elevator breakdowns and safety | A | **6** | 3 | 5 | 10 (tie) | **A (unchanged; social adds "elevator as coercion")** | Social talk is about *access*, not breakdowns: codes withheld or changed, lift locked until fees are paid (V009, V053, V054, V025) |
| 6 | P6 Water: cuts, pressure, pump, tank | B | **9** | 8 | 8 | 9 | **A (upgraded)** | Independent 2023–2026 voices: top-floor pressure (V056, V057), 3-day cuts in Hadayek October (V059), pumps dying with load-shedding (V058), undrinkable water (V060), Tagamo3 outage on Reddit (V061, V062) |
| 7 | P7 Utilities: prepaid meters, fees | A | **6** | 4 | 6 | 10 (tie) | **A (unchanged)** | Balance "deducted without reason" (V064), cleaning fee seen as "theft" (V065 to V067) |
| 8 | P8 Bawab | B | **12** | 9 | 12 | 6 | **A (upgraded)** | 12 recent mentions across YouTube and Reddit: broker behaviour and commissions (V042, V069, V070, V075), "thugs" (V068, 101 likes), enforcer role (V009), privacy (V071), blocking district security reforms (V073) |
| 9 | P9 Garbage | B | **5** | 2 | 5 | 13 | **B (unchanged)** | Cleaning fee on electricity bill (V066, V067), informal collector expectations (V077) |
| 10 | P10 Neighbour disputes | B | **14** | 7 | 12 | 4 (tie) | **A (upgraded)** | Leaks from upstairs (V079, V080), common-area misuse (V083), noise and pests (V082, 60 likes), discriminatory rules (V084, V085), slow legal remedies (V081) |
| 11 | P11 Governance apathy, legal ignorance | A | **10** | 4 | 9 | 8 | **A (confirmed)** | AGMs held without notifying owners (V086), unions formed behind residents' backs (V087), "the law isn't clear" (V018) |
| 12 | P12 Existing apps fail at basics | A | 0 | 0 | 0 | n/a | **A (unchanged; out of scope here)** | Social sources barely discuss specific building apps; 06's primary review data stands |
| 13 | P13 WhatsApp/residents' group chaos | **C** | **11** | 9 | 9 | 7 | **B (upgraded)** | Direct Egyptian evidence on group behaviour and admins (V090 to V098). Still missing: verbatims from inside building groups about fee reminders (ESTIMATE) |
| new | **P14 Privacy and surveillance** (CCTV, numbers, defamation) | – | **6** | 4 | 5 | 10 (tie) | **B (new)** | CCTV consent fights (V099 to V101), worker access to personal number and address (V052), cybercrime liability in groups (V102) |

**Reading the table:**
- The two lists agree on the **top four** (money, trust, compound management, technicians). Social media adds weight to **P8 bawab** and **P10 neighbours**: these are daily, emotional topics that news covers less than courts or fees.
- **P5 elevator** looks smaller socially because people discuss *access disputes* rather than accidents. National-media coverage of fatal accidents (07) still justifies grade A.
- **P12 (bad apps)** is invisible on social media. ESTIMATE: Egyptians don't yet think of building management as "an app problem". That is an opportunity, and also a marketing challenge (category creation).

---

## 5. How residents' WhatsApp/Facebook groups behave in practice

### 5.1 What the Egyptian evidence shows (verbatim-backed)

| Behaviour | Evidence | Strength | Product implication |
|---|---|---|---|
| **Groups exist and are the default distribution channel.** Residents forward content "to the building group" without thinking (V095). New Cairo's development authority itself created an owners' WhatsApp group "to follow residents' problems" ([Ahram, 2020](https://gate.ahram.org.eg/daily/News/203397/148/764494/WhatsApp/%C2%AB%D8%A7%D9%84%D9%88%D8%A7%D8%AA%D8%B3-%D8%A2%D8%A8%C2%BB-%D9%84%D8%AD%D9%84-%D9%85%D8%B4%D9%83%D9%84%D8%A7%D8%AA-%D8%B3%D9%83%D8%A7%D9%86-%D8%A7%D9%85%D8%AA%D8%AF%D8%A7%D8%AF-%D8%BA%D8%B1%D8%A8-%D8%A7%D9%84%D8%AC%D9%88%D9%84%D9%81.aspx)) | V095; Ahram | B | Don't fight the group; **plug into it**. Every app output (receipt, poll, notice) needs a one-tap "share to building group" deep link |
| **Large compound groups are run by a vocal minority of older residents** who police trivia (children shouting, chickens, crows, dogs) and lobby management. Other residents mock and resent them (V090 at 468 likes, V091, V092, V093) | V090 to V093 | B | The app must give **silent majorities a voice** (anonymous polls, quorum-based decisions) so a few admins can't claim to speak for everyone |
| **Group campaigns try to restrict outsiders**: visitor entry tickets of EGP 50 to 100 (V094) and "elevator for residents only" rules against delivery staff (V084) | V084, V094 | B | Visitor and delivery management is a real demand. Rules must be **voted on and transparent**, not imposed by admins |
| **Low responsiveness**: "you have to mention each member individually or call them" (V097) | V097 (r/Egypt) | B | Notices sent to a group are ignored. **Per-person push and 1:1 WhatsApp nudges** (founder idea 1) solve a real problem |
| **Leaving is socially costly**: "every time I leave the group, my uncle adds me back" (V096; family group, 2018) | V096 | C (family, not building) | ESTIMATE: residents stay in noisy building groups out of obligation and mute them. A quieter, structured channel will be welcome if it is not *another* group |
| **Some groups only survive by narrowing to one message type**: a building's women's group where the *only* allowed message is "I'm hanging laundry, take yours in", "to avoid disputes between neighbours" (V098, Youm7 2018) | V098 | C (single, older) | Strong design cue: **typed messages** (notice, payment, request, vote) beat free chat for keeping peace |
| **Groups as a fee-enforcement and shaming venue** | No Egyptian verbatim found. Indirect: union boards threaten lift bans (V025), bawab locks the lift (V009), owners surprised by debts recorded against them (V006, V086) | **ESTIMATE** | Keep "who hasn't paid" **out of the group**. Send private reminders; show only an aggregate "x of y paid" |
| **Legal exposure**: Egyptian lawyers stress that insults or defamation inside a closed WhatsApp group are prosecutable under Law 175/2018 (V102) | V102 (Dostor, Sep 2026) | B | A bot that **summarizes or reposts** messages must avoid re-publishing accusations. Moderation and "cool-down" prompts reduce risk |

### 5.2 Admins, the bawab and money in groups

- **Who admins.** The evidence points to self-appointed union heads, often older and retired residents in compounds (V090, V091), or "whoever runs the informal union" (V006). Residents distrust them when accounts are hidden (V019, V020, V023, V088). ESTIMATE: admin legitimacy is the biggest social risk for any tool that gives admins more power.
- **Fee reminders.** Today they take the form of debt "recorded against" residents (V006), recovered by force (V008, V009) or by a 3x penalty before renting out (V011). No resident asked for "more reminders". They asked for **fairness** (split rules), **evidence** (invoices), and **instalments** (V008).
- **The bawab's role.** He is the physical enforcer (he locks the lift, V009), the rental broker (V075), the technician broker who takes a cut (V042), and, for some residents, a privacy risk (V071) or "thug" (V068). Others are fond of him ("my bawab remembers my name", r/Egypt `gakmfg1`, 2020, not tabled). **ESTIMATE:** the bawab has the information and the physical presence the app lacks. A **bawab role in the app** (task log, verified job referrals with a transparent fee, tips) turns a gatekeeper into a distribution partner.

### 5.3 Attitudes to bots, apps and privacy

| Attitude | Evidence | Implication |
|---|---|---|
| **Positive to "not everyone has to install" plus AI** | Ettihad 5★ review: "فكرة اني مش لازم كل السكان ينزل التطبيق ممتازة. وفاري الذكاء الاصطناعي حلم" (2026-08-28, [Play](https://play.google.com/store/apps/details?id=com.ittihad.ettihad); already in 07; few ratings) | WhatsApp-first onboarding is validated, but it is a single early review |
| **WhatsApp hand-off is valued inside apps** | SODIC App: visitor QR codes "with the option to share via WhatsApp" (V105) | Use WhatsApp for sharing and confirmation even when the core lives in-app |
| **Distrust of official social updates** | "According to their Facebook page, it's fixed now... I don't trust them that much tho." (V062) | Crowd-confirmed status ("12 residents report water back") beats one-way announcements |
| **Privacy fear about service workers** | Taskty: worker has "my personal number and my address... worrying for privacy and safety"; wants photo or ID before arrival (V052) | **Masked calling or relay**, worker photo and ID card, live arrival status |
| **CCTV wanted, but by consent** | "Cameras installed by agreement with the residents" (V100); cameras that "expose the neighbours' flats" are not acceptable (V099); objections to a lift camera put up by an informal union (V101) | Building-level **votes** for cameras, and access logs on who viewed footage |
| **Fear of exposure in groups** | Lawyers: closed group is no shield (V102) | Bot must never auto-post names of non-payers or complaints about named people |
| **Apps by and for residents are in demand** | A software engineer with 90 likes wants to build a rental-listing app (V104); "I wish there were groups to buy and sell away from brokers" (V103, 35 likes) | Phase-2 adjacent: a **building-verified resale/rental board** could disintermediate brokers, but it collides with the bawab's income (see §5.2) |
| **Explicit attitude to a bot *inside* a building group** | **Not found** on any reachable platform | **ESTIMATE / gap.** Must be tested in the 30-group survey proposed in 07 §8 |

### 5.4 Foreign analogues (not counted; for design ideas only)

- **Saudi Arabia (Al Watan, 2024-07-25):** building groups became "ميادين للخلافات والمنازعات التي تصل حتى إلى السب والشتائم". One owner filed a police report and was then removed from the group. A family consultant recommended abolishing groups for paper notices ([alwatan.com.sa](https://www.alwatan.com.sa/ampArticle/1150737)).
- **Kenya (Citizen Digital, 2026-07-15):** "Once you're labelled 'the noisy neighbour', every complaint somehow finds its way to your door." Service-charge questions escalate into attacks on committee members. The fix that works is agreed rules on what belongs in the group and when to move to formal meetings ([citizen.digital](https://citizen.digital/article/how-nairobis-apartment-whatsapp-groups-became-the-new-village-baraza-n386496)).
- **Singapore (Stacked Homes, 2023-03-08):** a manager says the chat "is like our extra eyes and ears... Very effective, compared to last time when people just ignored our emails". Privacy risk: "it's very easy to become a 'star' for the wrong reason" ([stackedhomes.com](https://stackedhomes.com/editorial/the-rise-of-the-telegram-whatsapp-group-chat-how-these-chat-groups-affect-condo-living)).

**Synthesis (ESTIMATE):** across four countries the same pattern holds. Groups are excellent for **fast alerts and collective action** and poor for **money, blame and decisions**. The founder's WhatsApp bot should **take money, blame and decisions out of the group** (into private messages, the ledger and polls) and **leave alerts in the group**.

---

## 6. Feature suggestions in residents' own words

| # | What people literally ask for (verbatim) | Source | Feature it maps to |
|---|---|---|---|
| F1 | "حددي إيه الصيانة بالظبط ؟ التي تمت أثناء العام و التكلفة الفعلية و ... اجرة الحارس كام في الشهر" (specify the maintenance done, its real cost, the guard's wage) | V017 | **Itemized annual statement** auto-generated from the ledger |
| F2 | "عرض المصاريف والصلاحيات والقرارات" (publish expenses, powers and decisions) | V015 | Public **expense feed plus decision log plus role and term display** |
| F3 | "اريد أن ارى فواتير الكهرباء والمياه وإيصال صيانه الاسنسير" (I want to see the bills and the lift receipt) | V026 | **Photo receipts attached to every expense**, visible to all owners |
| F4 | "ما هي نسبه الدفع نصف ... ام ربع" (what share: half or a quarter?) for closed flats; ground floor and lift; own meter | V004, V005, V007 | **Split-rule engine** (occupied/closed/unfinished/ground floor/own meter), with an explanation shown per unit |
| F5 | "التسديد ... بالتقسيط" (pay service charges in instalments) | V008 | **Instalment plans** for arrears and deposits (phase-2 fintech) |
| F6 | "لم يتم اخبارى بالجمعية العمومية" (I wasn't told about the AGM) | V086, V087 | **Mandatory, logged AGM notices** to every owner, including absentee owners abroad (WhatsApp plus email), with e-voting |
| F7 | "تحديد مدة اتحاد الشاغلين وصلاحياته" (set the union's term and powers) | V015, V018 | **Governance templates** (Law 119/2008), term countdowns, election workflow |
| F8 | "بالاتفاق مع السكان تركب كاميرات مراقبة" (install CCTV by agreement with residents) | V100 | **Building votes** for capex such as cameras, plus a camera-access log |
| F9 | "عايزين فيديو تقولنا الماركات الكويسة للخامات بتاعة الكهرباء والسباكة" (tell us good brands for electrical and plumbing materials) | V046 | **Trusted-materials guide** and price benchmarks (content-led phase-2 funnel) |
| F10 | "Fair prices for plumbing materials in Egypt so nobody rips you off" | V051 | **Fair-price calculator** per job type (phase 2) |
| F11 | "عدم وجود نظام واضح لتعريف العاملة قبل الوصول (زي صورة أو كارت تعريف)" (no way to identify the worker before arrival, such as a photo or ID) | V052 | **Worker profile, photo and ID, masked number**, live ETA |
| F12 | "prices are clearly stated for each service" (praise) | V105 | **Posted prices** in the services catalogue |
| F13 | "نفسي يكون فيه جروبات لناس بتبيع او تشتري بعيد عن السماسره" (groups to buy or sell away from brokers) | V103 | **Building-verified resale/rental board** (phase 2; tension with the bawab's brokerage) |
| F14 | "اي حد جاي من برا ... تيكت دخول زائر" (visitor entry tickets) | V094 | **Visitor passes/QR** (already in compound apps; residents want control) |
| F15 | Residents with no water on the 5th or 10th floor ask how to fix pressure or where to put the pump (V056, V057) | V056, V057 | **Water module**: pump schedule, outage reports, vetted pump and tank technicians |

---

## 7. Phase-2 signals: willingness to pay and price complaints

### 7.1 Evidence that people pay (and pay a lot) for home work

| Signal | Evidence | Read-out |
|---|---|---|
| Large 2026 spend on finishing and repairs | "النقاشة عندي مكلمة ١٢٠ الف جنية" (EGP 120k painting, V045); "prices are on fire" (79 likes, V043); "labour charges have become astronomical" (V044) | Ticket sizes are large. Even a small booking fee on finishing jobs is meaningful revenue (ESTIMATE) |
| Recurring, unavoidable repairs | Leaks from upstairs neighbours (V079, V080), pumps and pressure (V056, V057), pests and damp on the ground floor (V082) | Recurring demand for plumbers, insulation, pest control and pump technicians |
| Residents already pay intermediaries | The bawab takes a cut from technicians (V042); the 2.5% brokerage fee is common enough to be called a nationwide "levy" (V070) | **Paying an intermediary is normal**; the anger is about *hidden* and *forced* fees |
| Trust is bought with transparency | The electrician shows receipts and the retailer's number (V049); SODIC praised for posted prices (V105) | Itemized quotes, materials receipts and posted prices are the conversion lever |
| Supply is looking for clients online | A New Cairo plumber advertises on r/CAIRO to expats in New Cairo, Madinaty and Rehab (V051) | Technicians will join a platform that brings clients; supply acquisition can be cheap (ESTIMATE) |
| Ability to pay is uneven | "Some people earn a weak EGP 2,000 a month" (V012); instalment requests (V008) | **Instalments/BNPL** for big jobs and arrears; keep basic services cheap |

### 7.2 Price and fairness complaints that a marketplace must neutralise

- **Overbilling:** a gate repair with under EGP 100 of parts was billed at EGP 4,000 (V048); "technicians charging him 4X the repair cost whilst hiding the company's actual invoice" (V047); an electrician's price "MORE THAN DOUBLED" (V050).
- **Hidden cuts:** the bawab's commission is added on top of the technician's price (V042).
- **Forced fees:** a "cleaning fee" on the electricity bill (V065 to V067); a 3x maintenance charge demanded before renting out (V011); compound deposits of 3% felt as "huge" (V032).

### 7.3 Phase-2 design implications (ESTIMATE)

1. **Price model:** fixed or posted prices for common jobs plus a visible platform fee (for example EGP 20 to 50 per job, or 5 to 10% on large jobs). Avoid opaque percentage commissions that echo the "2.5% levy" resentment. Validate with 10 technician interviews (07 §8).
2. **Bawab partnership:** offer the bawab a **transparent referral fee** paid by the platform. That brings the existing informal commission (V042) into the open instead of fighting it. It also removes the main incentive he has to sabotage the app.
3. **Trust stack:** worker photo and ID, masked numbers (V052), materials receipts (V049), a building-level rating ("used by 6 flats in your building"), and a warranty window.
4. **Fintech:** instalments for dues arrears and large repairs (V008, V012) and an escrow-style "pay after job approved".

---

## 8. What this means for the product, and remaining gaps

**Confirmed priorities for phase 1 (in order of social-voice weight):**
1. **Money with proof.** Ledger, receipts, itemized annual statement, configurable split rules, private reminders, instalments (P1, P2).
2. **Governance with legitimacy.** AGM notices to every owner (including abroad), e-voting with quorum, role and term display, decision log (P11).
3. **Access fairness.** Documented dues status to replace ad-hoc lift locking. ESTIMATE/legal: in-app restrictions for non-payers are risky after the 2024 appeal ruling that the union "may only claim through the courts, not prevent use" ([Dostor](https://www.dostor.org/4657268)). See 09 legal.
4. **Group-friendly, not group-replacing.** Typed messages, a silent-by-default bot, private 1:1 nudges, weekly digest, share-to-group links (P13).
5. **Neighbour issues with a paper trail.** Leak or noise reports with photos and timestamps; a polite anonymous channel; vetted leak technicians (P10 bridges to phase 2).

**Remaining gaps (honest list):**
- **No verbatims from inside Egyptian building WhatsApp groups** about fee-reminder spam, admin wars or reactions to bots. ESTIMATE only.
- **No Facebook group post text** (Ahl Madinaty, سكان التجمع, يلا نغير زايد) and **no X posts**. Only news-quoted Facebook.
- **Fatakat, Ta3lim and InterNations** were not reached.
- **Recommended next step (cheap, manual, 1 week):** the founder or a team member with personal accounts collects 100 posts from 5 Facebook groups and 30 building WhatsApp groups (with members' consent), using the tag scheme in §3. Add three survey questions: "Would you accept a bot in the group that only speaks when @mentioned?", "Who should see who hasn't paid?", "Would you pay EGP X to book a vetted technician with posted prices?"
- **Optional:** the founder may choose to let Claude browse Facebook and X through the `claude-in-chrome` extension in their own browser. That decision belongs to the founder (privacy of group members, platform terms).

---

## 9. Sources

### 9.1 YouTube videos whose comments were used (upload date · channel · views at scrape)

| Video ID | Upload | Channel | Views | Title (abridged) |
|---|---|---|---|---|
| [zT2dhRIdhp8](https://www.youtube.com/watch?v=zT2dhRIdhp8) | 2019-04-29 | Sada Drama | 3,611 | مشكلات اتحاد الشاغلين في عدم دفع الصيانة |
| [77GYiWtg2jc](https://www.youtube.com/watch?v=77GYiWtg2jc) | 2023-07-31 | El Hekaya (Amr Adib) | 5,859 | اتحاد الشاغلين (الملاك).. أهميته وكيف تم تأسيسه؟ |
| [0Hp4MMXlep8](https://www.youtube.com/watch?v=0Hp4MMXlep8) | 2022-09-04 | قهوة سلمى | 772 | لماذا يمتنع اصحاب الشقق المغلقة عند دفع الصيانة |
| [Fejp-oBY3EU](https://www.youtube.com/watch?v=Fejp-oBY3EU) | 2026-08-25 | Bingbong | 43,150 | مبينفعش معاه صيانة · إتحاد مُلّاك |
| [GbKb4sCr8b8](https://www.youtube.com/watch?v=GbKb4sCr8b8) | 2021-01-07 | El7adota | 6,675 | إعرف حقوقك في إتحاد الشاغلين |
| [jI9NDF2_0tM](https://www.youtube.com/watch?v=jI9NDF2_0tM) | 2021-08-20 | Lawyer Ebrahem | 8,324 | منعوك من استخدام الاسانسير |
| [mrbAwXs3PtI](https://www.youtube.com/watch?v=mrbAwXs3PtI) | 2019-01-10 | Opera City Compound | 691 | مجلس إتحاد الشاغلين يخفى الميزانيات |
| [4uoOI2v0Ct8](https://www.youtube.com/watch?v=4uoOI2v0Ct8) | 2019-04-01 | Sada Drama | 9,237 | دور اتحاد الشاغلين إذا امتنع احد المستأجرين |
| [e_sDW0P-x3c](https://www.youtube.com/watch?v=e_sDW0P-x3c) | 2023-11-07 | The Global Hub Development | 3,521 | يعني إيه إتحاد الملاك؟ |
| [yVnH-onX3W8](https://www.youtube.com/watch?v=yVnH-onX3W8) | 2021-06-12 | أحمد رزق عطا (lawyer) | 11,991 | شرح قانون اتحاد الشاغلين |
| [00LqRPjkaL0](https://www.youtube.com/watch?v=00LqRPjkaL0) | 2026-06-29 | Mohamed Zazoaa | 152,659 | كمبوند ولا شقة؟ (2026) |
| [kG_1RjvG7RE](https://www.youtube.com/watch?v=kG_1RjvG7RE) | 2026-07-02 | Adham Fathallah, AF Property | 90,933 | كمبوندات متستاهلش نص سعرها في التجمع |
| [6a1LaaBNVLM](https://www.youtube.com/watch?v=6a1LaaBNVLM) | 2025-04-11 | Kareem Hosni | 15,170 | عيوب كمبوند المستثمرين في حدائق اكتوبر |
| [GF3LI4qv71I](https://www.youtube.com/watch?v=GF3LI4qv71I) | 2022-10-24 | Sada Elbalad 2 | 12,344 | ما هي وديعة الصيانة في القانون؟ |
| [_kOOx3hOm00](https://www.youtube.com/watch?v=_kOOx3hOm00) | 2023-05-20 | Wad3anaShow | 195,458 | مشاكل سكان الرحاب |
| [3KCCKSyT4kk](https://www.youtube.com/watch?v=3KCCKSyT4kk) | 2026-05-28 | Mohamed Zazoaa | 73,610 | مميزات وعيوب الدور الارضي |
| [O4NEJTHfBG8](https://www.youtube.com/watch?v=O4NEJTHfBG8) | 2026-05-15 | Mohamed Zazoaa | 179,854 | تجربتي الكاملة في البحث عن سكن مريح |
| [qfFTXaP1WzE](https://www.youtube.com/watch?v=qfFTXaP1WzE) | 2026-08-17 | Mohamed Zazoaa | 55,563 | تكلفة تأسيس شقة في مصر 2026 |
| [XN3VbXFM_dQ](https://www.youtube.com/watch?v=XN3VbXFM_dQ) | 2022-02-14 | Mohamed Torky (lawyer) | 43,514 | كيفية التعامل مع الجار المؤذي |
| [0nFQ9t5JLaQ](https://www.youtube.com/watch?v=0nFQ9t5JLaQ) | 2023-07-05 | Sayed Ahmed | 7,081 | حل مشكلة ضعف المياه في الأدوار العليا |
| [njkHf6a789o](https://www.youtube.com/watch?v=njkHf6a789o) | 2026-04-24 | Melakher | 84,901 | حارس عقار فيصل و طبيبة الأسنان و سمسرة 75 ألف |
| [tbXr79GS_98](https://www.youtube.com/watch?v=tbXr79GS_98) | 2021-07-11 | Youm7 | 30,749 | بسبب تركيب كاميرات مراقبة.. 250 غرزة |
| [g4EUPWgyF2s](https://www.youtube.com/watch?v=g4EUPWgyF2s) | 2024-08-20 | Al-Majad | 2,790 | رسوم النظافة على فاتورة الكهرباء |
| [KvIEGSsKqvQ](https://www.youtube.com/watch?v=KvIEGSsKqvQ) | 2024-08-06 | ابوكبير لخدمات الدفع | 1,651 | رسوم النظافة على فواتير وكروت الكهرباء |
| [PzqrPSWjkx4](https://www.youtube.com/watch?v=PzqrPSWjkx4) | 2016-11-04 | Lamees El-Hadidy, El Bilateau | 607,575 | لما بتسيب جروب الواتس اب |

Other videos were downloaded but contributed no tabled item: tSJFO64ZISM (owners'-union meeting sketch, comments mostly about the actors), -eqsXx9xnmA, 57XGMLEvscs, bG34iUytJuM, rLfwCxMcyX4, VOUjdw8RFus, kyUEcjIJyYQ, r2eOsxcjnLM (2017, Madinaty protest; too old), Wn-r0qN1Rcs (Moroccan), and others.

### 9.2 Reddit (via Arctic Shift archive; canonical reddit.com URLs)
- r/Egypt "Acknowledging the source of our problems" (2022-08-12): https://www.reddit.com/r/Egypt/comments/wmfrl0/
- r/Egypt "Prices aren't just increasing..." (2022-11-15): https://www.reddit.com/r/Egypt/comments/yw1sml/
- r/Egypt "Living in Compounds العيشة في الكومباوند" (2021-12-21): https://www.reddit.com/r/Egypt/comments/rldaep/
- r/Egypt "Water out in Tagamo3 5 for 2 days" (2023-10-06): https://www.reddit.com/r/Egypt/comments/171mheo/
- r/Egypt "The bawab's wife is an idiot" (2024-07-16): https://www.reddit.com/r/Egypt/comments/1e4hew9/
- r/Egypt "No one responds to WhatsApp anymore?!" (2023-09-11): https://www.reddit.com/r/Egypt/comments/16g25of/
- r/Egypt "welad el bawab..." (2025-01-03): https://www.reddit.com/r/Egypt/comments/1hsta04/
- r/CAIRO "Plumber in New Cairo: AMA" (2026-06-13): https://www.reddit.com/r/CAIRO/comments/1u539wr/
- r/CAIRO "Whats the best way to find renters for my flat?" (2026-09-12): https://www.reddit.com/r/CAIRO/comments/1we8ull/
- Context only: r/Egypt "Bawab" (2020, 997 upvotes): https://www.reddit.com/r/Egypt/comments/jk77im/ · "Property - not in a compound" (2026-08-23): https://www.reddit.com/r/Egypt/comments/1vwjdu0/
- Archive API used: https://arctic-shift.photon-reddit.com/api/posts/search and /api/comments/tree

### 9.3 Egyptian news (verbatim complaints, Facebook posts quoted)
- Elbalad, Dar Misr residents' complaint (2021-12-18): https://www.elbalad.news/5090532
- Cairo24, Family City residents' Facebook post (2026-09-05): https://www.cairo24.com/2489391
- Cairo24, compound adhan post controversy (2026-08-23): https://www.cairo24.com/2481594
- Dostor, Interior Ministry on viral compound-management video (2026-06-13): https://www.dostor.org/5596429
- Dostor, lawsuit over elevator codes, Badr Tower (2024-03-12): https://www.dostor.org/4657268
- Dostor, legal liability in WhatsApp "mamiz" groups (2026-09-24): https://www.dostor.org/5714544
- Youm7, "strangest WhatsApp groups", building laundry group (2018-08-12): https://www.youm7.com/story/2018/8/12/أغرب-جروبات-واتس-آب-من-محبى-السبانخ-لـ-أنا-هنشر/3908172
- Ahram Daily, New Cairo authority WhatsApp group with owners (2020-05-28): see link in §5.1
- Context (not tabled): Cairo24 Promenade Zayed water cut https://www.cairo24.com/2464858 · Al-Wafd Paradise compound https://www.alwafd.news/5975683 · El-Watan Zayed maintenance https://www.elwatannews.com/news/details/4915334 · Masrawy deposits study (2026-09-19) https://www.masrawy.com/news/realestate-news/details/2026/9/19/3050278/

### 9.4 App stores (from 06's raw file)
- Taskty App Store review (2026-02-12): https://apps.apple.com/eg/app/id1486080094
- SODIC App Store review (2024-10-13): https://apps.apple.com/eg/app/id1390362823
- Ettihad Play review (2026-08-28): https://play.google.com/store/apps/details?id=com.ittihad.ettihad

### 9.5 Foreign analogues
- Al Watan (Saudi), 2024-07-25: https://www.alwatan.com.sa/ampArticle/1150737
- Citizen Digital (Kenya), 2026-07-15: https://citizen.digital/article/how-nairobis-apartment-whatsapp-groups-became-the-new-village-baraza-n386496
- Stacked Homes (Singapore), 2023-03-08: https://stackedhomes.com/editorial/the-rise-of-the-telegram-whatsapp-group-chat-how-these-chat-groups-affect-condo-living

---

## 10. Verification log

| Check | Method | Result |
|---|---|---|
| **Quote fidelity (YouTube, Reddit)** | A script splits each Arabic/original quote on "..." and checks every fragment is an exact substring (whitespace-normalised) of the harvested comment or post text. | **95 of 105 items machine-verified, 0 mismatches** after correcting three transcription slips (the typo "ويقفالالباب" restored; curly apostrophes restored in two Reddit quotes) |
| **Quote fidelity (news, App Store)** | The other 10 items (Elbalad x2, Cairo24 x2, Dostor x3, Youm7 x1 checked against WebFetch output; App Store x2 checked against `data/06-reviews-raw.csv`) | Matched. The Dostor 5596429 item is the ministry's summary of a viral video, not the creator's own words, and is labelled as such |
| **Dates** | YouTube relative dates converted against 2026-10-12; video upload dates from `yt-dlp` metadata; Reddit dates from `created_utc`; news dates from article bylines (Cairo24 pages show the *current* date in the header; we used the article byline) | Approximate (≈) for YouTube comments; exact for others |
| **Egypt-only filter** | Excluded the Moroccan CCTV thread (Wn-r0qN1Rcs), the Syrian/Lebanese commenters, and Gulf/US news results | Done |
| **Second-source checks on key claims** | (a) The bawab as broker and commission-taker: V042, V069, V075 here plus Ahram Gate May 2026 (07). (b) Elevator access used as leverage: V009, V025, V053 plus the Dostor lawsuit V054. (c) Water pressure and cuts: V056 to V063 across YouTube and Reddit plus news in 07. (d) Opaque union finances: 10 independent commenters plus Youm7/Al-Wafd in 07 | Each key claim has at least 2 independent sources |
| **Counts** | Frequency table generated by script from the item list (tags split on ";") | Reproducible. Directional only (ESTIMATE) because of topic-biased sampling |
| **Reddit coverage** | Arctic Shift post search ran in the background for 30 terms across 2 subreddits. Server timeouts slowed it, and not all terms completed before writing | Partial; listed in §1 |
| **What was NOT verified** | Commenters' identity and location. Comments are self-reported and could include non-Egyptians writing in Egyptian dialect. Engagement (likes) is as of the scrape date | Stated |

*Raw harvest (session scratchpad, not committed): 38 YouTube JSON files (4,010 comments), `posts.json` (273 Reddit post records, 262 unique), 8 Reddit comment trees, and the item list with its verification script.*
