# 19 — WhatsApp in Egypt, October 2026: Reality Check for the "Bot in the Building Group" Idea

**Type:** Gap-filling update to file `10-whatsapp-bot.md` (and to `09-legal-regulatory.md` §11, `11-ai-opportunities.md` §5 and `13-growth-zero-budget.md` §6).
**Research date:** 2026-10-12. **Market:** Egypt only. Other markets appear only as sources of ideas.
**Conventions:** Every fact carries a source URL. **ESTIMATE** marks my own calculations, with the reasoning shown. "Not found" means I searched and found nothing reliable. Meta documentation is quoted word for word wherever it settles a question.

---

## 0. Executive summary (one page)

| # | Open item from file 10 | What I found on 12 Oct 2026 | Change vs file 10 |
|---|---|---|---|
| 1 | Can a business number or AI agent join a **user-created** WhatsApp group? | **Still no.** Meta's Groups API docs still say groups are "invite-only", allow "Max group participants: 8" and are "open to all businesses with an Official Business Account (OBA)". No 2025–2026 changelog entry or newsroom item lets a business number or a third-party AI join consumer groups. **Meta AI** (Meta's own assistant, launched in Egypt in Feb 2025) is the only AI that can be summoned inside a consumer group, by typing "@Meta AI". | Confirmed. No change. |
| 2 | Do Groups API webhooks deliver all group messages? | **Partly answered.** Meta lists a "Receive group messages" feature, and vendors say group messages "arrive by webhook as they happen". Meta's page does not say in so many words that *every* message is delivered, and no history can be pulled. This only matters for groups of 8 or fewer that the business itself created. | Narrowed. Irrelevant for big building groups. |
| 3 | The 1 Oct 2026 service-message charge | **Now confirmed on a Meta page.** "Effective October 1, 2026, Meta will charge on a per-message basis for service messages." Service rates equal the utility/authentication rates, with "Volume tiers: None". Utility templates inside the 24-hour window were "Free until October 1, 2026". The allowance of **1,000 free service messages per business phone number per month** shows up in Meta's pricing page as indexed by search and in every BSP source. I could not open it on a live Meta page (§3). | Upgraded from "BSP-only" to "Meta-confirmed". |
| 4 | Egypt rate card | **Marketing $0.0644, Utility $0.0036, Authentication $0.0036, Service $0.0036** per delivered message (USD list price, before 14% VAT). Three independent BSP and calculator sources agree, and one of them was checked on 25 Sep 2026 against the Oct 2026 card. Meta's own CSV could not be retrieved, because its link targets are not exposed to the fetcher. One outlier guide gives higher numbers. | Confirmed by a 3rd source. Still not verified in a Meta CSV. |
| 5 | WhatsApp Communities limits | Communities group up to **50 sub-groups**, with an **announcement group of up to 5,000 members**. Each group holds up to **1,024 members**. These figures come from 2026 third-party guides only, because the official FAQ body could not be fetched. | Better, but still secondary sources. |
| 6 | Authoritative WhatsApp user count for Egypt | **Still none from NTRA, Kepios or GWI.** DataReportal 2026 Egypt publishes no WhatsApp figure. Third-party estimates run from **50 to 57 M users**. One Egyptian peer-reviewed survey (n=400) found **98% use WhatsApp and 90% use it daily**. | Better triangulated. Still no official number. |
| 7 | Ban-rate data for unofficial bots | **No public rate exists.** The GitHub issue threads are strong qualitative evidence. The Baileys "High number of bans" thread (Oct 2025) says "the problem with the ban is really in groups". New threads appeared in Jan, Jun, Jul and Oct 2026, including the "Error 463 reachout timelock" bug. | Evidence now stronger and more recent. |
| 8 | OBA eligibility | Meta's page now lists **5 hard criteria**: messaging-policy compliance, at least 30 days on the platform, Business Verification, two-step verification and an approved display name. Notability is assessed at Meta's discretion. A BSP can submit the request but **cannot guarantee approval**. | Clarified. |
| 9 | New in 2026 | (a) **Meta Business Agent**, launched 3 Jun 2026 and billed at **$2.00 per 1M tokens** from 1 Aug 2026. (b) A beta for **user-added "third-party agents"**, 1:1 only, up to 5 per user (WABetaInfo, 4 Sep 2026). (c) **Advanced Chat Privacy**, which lets any member **block chat export and AI use** in a chat. (d) Usernames and BSUIDs. (e) Business AI policy terms updated **23 Sep 2026**. | New risks and opportunities (see §6). |

**Final verdict, unchanged in substance and sharpened in detail:** the founder's "bot joins the building WhatsApp group" can **only** be built today with unofficial clients. Those clients break the Terms of Service, and the 2025–2026 evidence shows that **group bots specifically** are being banned. The compliant design from file 10 ("WhatsApp-native, not WhatsApp-dependent") still holds. The changes in this update are:
1. Every bot reply now costs about **$0.0036** once a number passes 1,000 replies a month. Use **several WABA numbers** and route chat to the **app** when it is cheap to do so.
2. **Do not use Meta Business Agent as the brain.** At $2 per 1M tokens it costs roughly 10–40× our own LLM (§7).
3. Make the **chat-export import** tolerant of chats where Advanced Chat Privacy blocks export.
4. Build an "agent-ready" adapter for WhatsApp's upcoming **user-added third-party agents**, a possible future legitimate route for a personal building assistant.

**Updated cost per 1,000 buildings (ESTIMATE, verified Egypt prices):** about **$1,090 per month** in the base case, **~$570** once 80% of users are on the app, and **~$320** in the lean admin-first design (§7).

---

## 1. Capability table (official / unofficial / not possible)

Legend: ✅ official and supported · ⚠️ possible only unofficially (ToS breach, ban risk) · ❌ not possible · ◐ partial.

| Capability | Status | Detail | Verified on | Source |
|---|---|---|---|---|
| Official API number joins an **existing** consumer group | ❌ | No endpoint. Groups API works only on groups the business creates. "Max Cloud API businesses per group: 1" | 2026-10-12 | [Meta Groups API](https://developers.facebook.com/docs/whatsapp/cloud-api/groups) |
| Official API **creates** a group | ✅ (OBA only) | "The Groups API is now open to all businesses with an Official Business Account (OBA)." | 2026-10-12 | Meta Groups API |
| Group size via API | ◐ | "Max group participants: 8". The business uses one slot ([Unipile, verified against Meta docs Aug 2026](https://www.unipile.com/whatsapp-group-api/)) | 2026-10-12 | Meta Groups API |
| Groups per number | ✅ | "Max groups you can create: 10,000 per business number" | 2026-10-12 | Meta Groups API |
| Adding participants silently | ❌ | "Groups are an invite-only experience where participants join using a group invite link you send them." Unipile: there is a `DELETE /participants` endpoint but no `POST /participants`. | 2026-10-12 | Meta, Unipile |
| Interactive buttons, lists, auth, commerce, calls, view-once or disappearing messages in API groups | ❌ | Listed under "Non-supported message types". Edit, delete and hiding the participant list are also unsupported. | 2026-10-12 | Meta Groups API |
| Receive group messages by webhook (API groups) | ◐ | Meta links a "Receive group messages" feature. Vendors: messages "arrive by webhook as they happen", "no endpoint to pull past history". Group lifecycle, participant, settings and status webhooks are separate subscriptions. | 2026-10-12 | Meta, [Unipile](https://www.unipile.com/whatsapp-group-api/), [Kapso](https://kapso.com/blog/whatsapp-groups-api-state-2026) |
| Group billing | ✅ | "you are charged each time a billable message is delivered to someone in the group". Any member's message opens one window for the whole group. Utility templates in the window are free under the group pricing page. "Group utility messages are not eligible for volume tiers." | 2026-10-12 (page undated; may predate the Oct 2026 change) | [Meta Groups pricing](https://developers.facebook.com/docs/whatsapp/cloud-api/groups/pricing) |
| Meta AI inside consumer groups (@Meta AI) | ✅ for users, ❌ for us | Users type "@Meta AI" in a group. Launched in Egypt in Arabic in Feb 2025. **No business or developer access.** Members can block it with Advanced Chat Privacy. | 2026-10-12 | [Meta newsroom Feb 2025](https://about.fb.com/news/2025/02/meta-ai-launches-in-the-middle-east-empowering-new-era-of-creativity-and-connection), [Economy Middle East](https://economymiddleeast.com/news/meta-ai-launches-mena-region-uae-saudi-arabia-egypt), [Lowyat](https://lowyat.net/2025/349167/whatsapp-releases-advanced-chat-privacy) |
| Meta Business Agent (Meta's own AI for businesses) | ✅ 1:1 | Launched globally 3 Jun 2026. Answers questions, books appointments, qualifies leads, hands off to humans. **No group support mentioned.** Billed at $2.00 per 1M tokens from 1 Aug 2026; moving to paid subscription tiers. | 2026-10-12 | [Meta newsroom](https://about.fb.com/news/2026/06/meta-business-agent/), [TechCrunch](https://techcrunch.com/2026/06/03/metas-ai-agent-for-whatsapp-business-is-now-available-globally/), [Meta pricing](https://developers.facebook.com/documentation/business-messaging/whatsapp/pricing/non-template-messages) |
| User-added **third-party agents** | ◐ (beta, 1:1) | WABetaInfo, 4 Sep 2026: users can add up to 5 agents, and WhatsApp generates an API key. "At the moment, it is only possible to chat with the agent in an individual chat." Testing "with a very limited number of users in select countries." | 2026-10-12 | [WABetaInfo](https://wabetainfo.com/whatsapp-is-rolling-out-chats-with-third-party-agents/) |
| Business-specific AI chatbot on the Cloud API | ✅ | Allowed when AI is "incidental or ancillary". General-purpose AI providers are banned (§4). | 2026-10-12 (terms updated 23 Sep 2026) | [Meta terms](https://www.facebook.com/legal/Meta-Terms-for-WhatsApp-Business-Platform) |
| Posting to a WhatsApp **Channel** via API | ⚠️ | No official Cloud API endpoint. Whapi says the Cloud API "does not support Channels". Whapi and WAHA offer unofficial posting. | 2026-10-12 | [Whapi](https://whapi.cloud/blog/whatsapp-channel-api-automation) |
| Unofficial bot in any group (Baileys, whatsapp-web.js, WAHA, Whapi, Green-API, Periskope) | ⚠️ | Works technically in groups of up to 1,024. Breaks the ToS, and **group activity is a reported ban trigger** (§5). | 2026-10-12 | GitHub issues (§5) |
| Forwarded message to a 1:1 bot carries a "forwarded" flag | ✅ | Webhook `context.forwarded: true` (forwarded 5 times or fewer) or `frequently_forwarded: true` (more than 5). The original author and group are **not** included. | 2026-10-12 (Meta reference updated 21 May 2026) | [Meta text webhook reference](https://developers.facebook.com/documentation/business-messaging/whatsapp/webhooks/reference/messages/text) |
| Chat export (.txt/.zip) by any member | ◐ | Still available on Android and iOS. **Any participant can block it** with Advanced Chat Privacy (Apr 2025), which also blocks AI features in that chat. | 2026-10-12 | [Lowyat](https://lowyat.net/2025/349167/whatsapp-releases-advanced-chat-privacy), [Express & Star](https://www.expressandstar.com/uk-news/whatsapp-launches-privacy-tool-to-stop-users-taking-content-off-the-platform-5705285) |
| Click-to-chat `wa.me/<number>?text=` deep links | ✅ | Standard WhatsApp feature (FAQ "كيفية استخدام خاصية النقر للدردشة"; the body could not be fetched, but the feature is long-standing and documented). | 2026-10-12 | [WhatsApp FAQ](https://faq.whatsapp.com/5913398998672934) |
| Status sharing of links with preview | ✅ (manual) | Rich link previews in Status since 2023. Sharing goes through the OS share sheet ("My Status" target). There is no deep link that prefills a Status. | 2026-10-12 | [Android Police](https://www.androidpolice.com/whatsapp-revamped-rich-link-previews-rolling-out-beta/), [AirDroid](https://www.airdroid.com/de/app-tips/how-to-add-link-in-whatsapp-status/) |
| WhatsApp Pay in Egypt | ❌ | Not available (see file 10 §2.2). | 2026-10-12 (no new evidence) | file 10 |

---

## 2. Groups API as of today: verbatim Meta text that decides the question

From [Meta Groups API docs](https://developers.facebook.com/docs/whatsapp/cloud-api/groups) (fetched 12 Oct 2026):

> "The Groups API is now open to all businesses with an Official Business Account (OBA)."
> "Groups are not available for WhatsApp Business app phone numbers"
> "Max group participants: 8"
> "Max groups you can create: 10,000 per business number"
> "Groups are an invite-only experience where participants join using a group invite link you send them."
> "Max Cloud API businesses per group: 1"
> Supported: "Text, media, text-based templates, and media-based templates"

From the [Meta changelog](https://developers.facebook.com/documentation/business-messaging/whatsapp/changelog), Groups API launch, 6 Oct 2025:
> "Introducing WhatsApp Groups API, which enables programmatic creation and management of groups on WhatsApp."

The changelog as served on 12 Oct 2026 runs through **12 May 2026**. It has **no** later entry raising the 8-participant cap or allowing joins to existing groups. Vendor guides updated in **August 2026** still give the cap as 8 ([Unipile](https://www.unipile.com/whatsapp-group-api/), [imbee](https://www.imbee.io/resource/whatsapp-groups-api-business-guide-2026), [Periskope](https://periskope.app/blog/whatsapp-groups-api-requirements-eligibility-limits)). Kapso (6 Jun 2026) concludes that the API is usable only for OBA-eligible businesses with groups of 8 or fewer, and that most teams should stick to 1:1 ([Kapso](https://kapso.com/blog/whatsapp-groups-api-state-2026)).

**What this means for us:** an Egyptian building group of 20–200 people **cannot** contain an official bot. The only official group use is a **micro-group**: board members plus the bot, or resident plus technician plus admin plus bot per job. Even that needs OBA first.

---

## 3. Pricing: Egypt rate card and the 1 Oct 2026 change

### 3.1 The 1 October 2026 service-message change: now on a Meta page

[Meta, "Upcoming pricing updates for Meta Business Agent, service and utility messages"](https://developers.facebook.com/documentation/business-messaging/whatsapp/pricing/non-template-messages) (fetched 12 Oct 2026):

> "Effective October 1, 2026, Meta will charge on a per-message basis for service messages"
> "By market, rates for service messages are the same as the rates for utility and authentication messages."
> "Volume tiers: None. Meta does not offer volume tiers for service messages."
> "Meta will charge for utility messages sent in response to users within an open 24-hour customer service window." (table: utility in window "Free until October 1, 2026")
> "Effective August 1, 2026, Meta will charge on a per-token basis for Meta Business Agent messages." "One global rate of $2.00 USD per 1M tokens."
> "The 72-hour free entry point window is unchanged for message delivery."

**Free allowance:** search-engine snippets of Meta's main pricing page read: "For each business phone number, Meta provides 1,000 free service messages per month, which do not roll over but reset monthly. Thus, Meta only charges as of the 1,001st service message" (search result for [Meta pricing](https://developers.facebook.com/documentation/business-messaging/whatsapp/pricing)). The same snippet set also says the service-message change does **not** apply to "AI Providers" (separate policy). Several BSPs confirm all of this:
- [YCloud, 4 Sep 2026](https://www.ycloud.com/blog/whatsapp-api-message-pricing-update-effective-october-1-2026): "The quota applies per business phone number".
- [overads](https://overads.io/blog/whatsapp-business-api-pricing-october-2026): quotes Meta, "A group send uses one message for every recipient it is delivered to". It also reports Meta's warning that delivery stops for businesses with no payment method on file.
- [respond.io](https://respond.io/blog/whatsapp-pricing-change-2026) and [1msg](https://1msg.io/blog/whatsapp-pricing-october-2026).

⚠️ **Inconsistency log:** the copy of Meta's main pricing page that my fetcher received on 12 Oct 2026 still said "Utility templates delivered within an open customer service window are free". That looks like a stale cached copy. The dedicated Meta page above, Meta's search-indexed text and all BSPs agree on the change. **Verdict: treat the change as in force.**

### 3.2 Egypt price table (USD per delivered message, list price, Oct 2026)

| Category | USD | EGP @55 (FX ESTIMATE used across this research) | ×Utility | Sources (agreeing) |
|---|---|---|---|---|
| Marketing | **0.0644** | ~3.54 | 17.9× | [Zernio (rate card eff. 1 Oct 2026, checked 25 Sep 2026)](https://zernio.com/whatsapp-api-pricing), [ChatMaxima (Meta card, Jul 2026)](https://chatmaxima.com/whatsapp-api-pricing/egypt/), [ArabyBot](https://arabybot.com/guides/whatsapp-api-pricing-egypt?lang=en) |
| Utility (outside **and now inside** the window) | **0.0036** | ~0.20 | 1× | same three |
| Authentication | **0.0036** | ~0.20 | 1× | same three |
| Service (free-form reply), after 1,000 free per number per month | **0.0036** | ~0.20 | 1× | Zernio, ArabyBot, plus the Meta rule "same as utility" |
| Inbound user messages | 0 | 0 | — | Meta (only delivered business messages are billed) |
| Business-initiated call | $0.0127 per minute | ~0.70 | — | [Zernio](https://zernio.com/whatsapp-api-pricing) |
| Meta Business Agent | $2.00 per 1M tokens | — | — | [Meta](https://developers.facebook.com/documentation/business-messaging/whatsapp/pricing/non-template-messages) |
| VAT | +14% on Egyptian invoices | — | — | [ChatMaxima](https://chatmaxima.com/whatsapp-api-pricing/egypt/) |

**Egypt price history (Meta's pricing page):** authentication-international lowered 1 Apr 2025; "Argentina, Egypt, Saudi Arabia – Lower utility and authentication rates" (1 Oct 2025); "France, Egypt - Lower marketing rates" (1 Jan 2026). Egypt is **not** among the markets whose rates changed on 1 Oct 2026 (Bangladesh, Iraq, Nepal, Sri Lanka, Kazakhstan, Kuwait, Morocco, Oman, Ukraine). Source: [Meta pricing](https://developers.facebook.com/documentation/business-messaging/whatsapp/pricing). The ChatMaxima July 2026 figures are therefore still current.

**Outlier sources:**
- ChatDaddy lists $0.0972 / $0.0096 / $0.0192 ([ChatDaddy](https://chatdaddy.tech/blog/whatsapp-business-api-egypt)). This looks like a BSP resale price with markup, not Meta list price.
- A Salesforce rate card shows Egypt "79.51 / 4.45 / 4.45 / Service 0". That is a non-USD unit, Jul 2025 vintage ([Salesforce PDF](https://www.salesforce.com/en-us/wp-content/uploads/sites/4/documents/PDF/WhatsApp-Business-Messaging-1000.pdf), extracted locally).
- **Action:** read the exact figure in WhatsApp Manager → Billing on day 1.

### 3.3 Chart-ready data: cost of 10,000 messages in Egypt (USD, before VAT)

```csv
category,usd_per_10k
Marketing,644
Utility,36
Authentication,36
Service (after free 1k),36
Service (first 1k/month/number),0
```

---

## 4. Meta's AI policy (Jan 2026) and the 23 Sep 2026 terms

[Meta Terms for WhatsApp Business Platform](https://www.facebook.com/legal/Meta-Terms-for-WhatsApp-Business-Platform) (Arabic version fetched 12 Oct 2026, "تاريخ آخر تحديث: 23 سبتمبر 2026"), §4.7 "AI Providers":
- The prohibition applies «عندما تكون هذه التقنيات هي الوظيفة الأساسية (وليس العرضية أو المساعدة) المتوفرة للاستخدام» ("when such technologies are the primary (rather than incidental or ancillary) functionality"). **Meta decides** what counts as primary.
- Platform data may not be used «لإنشاء أو تطوير أو تدريب أو تحسين أي أنظمة أو نماذج أو تقنيات للتعلُّم الآلي أو الذكاء الاصطناعي» ("to create, develop, train or improve any machine-learning or AI systems, models or technologies"). The exception is «للضبط الدقيق لنموذج الذكاء الاصطناعي الخاص بك» ("to fine-tune your own AI model"), for exclusive own use.
- §4.1(a) separately bans building profiles of WhatsApp users from platform data, except the content of your own threads.

**Scope and timeline:**
- Effective 15 Oct 2025 for new users and **15 Jan 2026** for all ([respond.io](https://respond.io/blog/whatsapp-general-purpose-chatbots-ban), [TechCrunch](https://techcrunch.com/2025/10/18/whatssapp-changes-its-terms-to-bar-general-purpose-chatbots-from-its-platform/)).
- Meta told TechCrunch the move "doesn't affect businesses that are using AI to serve customers on WhatsApp".
- Exceptions exist for the EEA and Brazil, where Meta is legally required to allow AI providers, and the separate AI-provider pricing covers them. **Neither applies to Egypt.**

**Application:** "مساعد العمارة" (dues, tickets, notices, technician booking) is ancillary AI and allowed. Keep the guardrails from file 10 §2.4:
- Topic-locked system prompt.
- No "ChatGPT on WhatsApp" marketing.
- LLM vendors on no-training terms.
- Human escalation.

---

## 5. Unofficial group bots: real-world evidence, 2025–2026

### 5.1 GitHub issue evidence (Baileys = WhiskeySockets, the most-used Node library)

| Issue | Date | What was reported | Group-relevant? |
|---|---|---|---|
| [#1869 "High number of bans on WhatsApp!"](https://github.com/WhiskeySockets/Baileys/issues/1869) | opened 5 Oct 2025, closed by stale-bot 24 Dec 2025 | 5 bots (about 9 groups each) banned in one week, 2 of which had run for 3+ years. One user bought 40+ numbers. Bans on v6.7.x and v7 RCs. **"the problem with the ban is really in groups."** One bot kept offline was banned **right after being added to 3 groups**. A private-only bot lasted about a week. No maintainer statement. | **Yes, directly** |
| [#2309](https://github.com/WhiskeySockets/Baileys/issues/2309) | 30 Jan 2026 | 2 temporary bans, then a permanent ban, from batch Status uploads on a production server | Status, not groups |
| [#2260 "GETTING BANNED"](https://github.com/WhiskeySockets/Baileys/issues/2260) | Jan 2026 | Repeated bans, some about 24 h | General |
| [#2658](https://github.com/WhiskeySockets/Baileys/issues/2658) | 24 Jun 2026 | "Your account may soon be subject to restrictions", with WhatsApp citing **unauthorized tools** | Shows WhatsApp detects the client itself |
| [#2707 "Error 463 (Reachout Timelock)"](https://github.com/WhiskeySockets/Baileys/issues/2707) | 14 Jul 2026, still open | Messaging non-recent contacts → 463 → restrictions → bans. Tied to a missing "trusted contact" privacy token (about 28-day life). Unmerged community forks attempt fixes. | A bot replying to group members in DM triggers this |
| [#2850](https://github.com/WhiskeySockets/Baileys/issues/2850) | 7 Oct 2026 | Rapid or parallel sends → anti-spam ban | General |

**whatsapp-web.js:** I found no 2025–2026 GitHub thread on bans (the only hit was a 2020 PR discussion, [#421](https://github.com/pedroslopez/whatsapp-web.js/pull/421)). The library drives a real WhatsApp Web session, so it is subject to the same detection.

**Vendors:**
- [Periskope's docs](https://docs.periskope.app/get-started/best-practices) (India, a group-management shared inbox on regular numbers): WhatsApp's anti-spam enforcement "can lead to account suspensions or bans", "account status remains under WhatsApp's control", and new numbers are "particularly vulnerable".
- [Whapi support](https://support.whapi.cloud/help-desk/blocking/connecting-a-new-whatsapp-number-after-a-ban-steps-and-recommendations) publishes a "connecting a new number after a ban" playbook.
- Z-API (Brazil) runs an "unbanning request" doc ([Z-API](https://developer.z-api.io/en/mobile/request-unbanning.md)).
- **Each vendor's existence of a ban-recovery playbook is itself evidence.**
- Vendor claim, unverified: Baileys accounts "typically last 2–8 weeks" ([AdviseAI](https://www.adviseai.in/blog/whatsapp-automation-ban-risk)). No method is given.

**Platform-scale context:**
- WhatsApp removed **6.8 M** scam-linked accounts in H1 2025 and added "safety overviews" when users are added to unfamiliar groups ([TechRepublic](https://www.techrepublic.com/article/news-whatsapp-scams-meta), [SC World](https://www.scworld.com/brief/millions-of-whatsapp-accounts-linked-to-scams-removed)).
- India monthly reports: **9.9 M** accounts banned in Jan 2025 ([ProPakistani](https://propakistani.pk/2025/03/24/nearly-10-million-whatsapp-accounts-banned-in-india-for-this-reason/amp/)).
- WhatsApp has been testing a **monthly cap on unanswered messages** to non-contacts since Oct 2025, applied "equally to both individuals and business accounts" ([Business Standard](https://www.business-standard.com/technology/tech-news/whatsapp-explores-message-limit-in-one-sided-chats-to-curb-spam-report-125102100179_1.html), [Green-API](https://green-api.com/en/blog/2025/whatsapp-introduces-new-restrictions-on-unanswered-messages/)). Global rollout status: unverified.

**Ban rate:** **No public number exists.** No vendor, no Meta report and no academic paper gives a ban percentage for group bots. My **ESTIMATE**, judged only from the thread evidence: if one number serves dozens of groups, the chance of a ban within 12 months is **well above 50%**. That is a judgement, not a measurement.

### 5.2 Who runs unofficial group bots at scale?
- **India:** Periskope (group inbox for B2B communities), plus many hobby or "userbot" deployments.
- **Brazil:** Z-API and similar gateways.
- **Global gateways:** Whapi, Green-API, WAHA (self-hosted).
- **Egypt:** freelance marketplaces sell group bots and "monitoring userbots" for about $10–15 per job ([Khamsat listings](https://khamsat.com/programming/chatbots-development/4462957-%D8%B3%D8%A3%D8%B7%D9%88%D8%B1-%D8%A8%D9%88%D8%AA-%D9%88%D8%A7%D8%AA%D8%B3%D8%A7%D8%A8-%D8%A3%D9%88-%D8%AA%D9%8A%D9%84%D9%8A%D8%AC%D8%B1%D8%A7%D9%85-%D8%A7%D8%AD%D8%AA%D8%B1%D8%A7%D9%81%D9%8A-%D9%88%D8%B1%D8%A8%D8%B7%D9%87-%D8%A8%D8%A3%D9%86%D8%B8%D9%85%D8%AA%D9%83-%D9%88%D8%AE%D8%AF%D9%85%D8%A7%D8%AA%D9%83)). **No funded Egyptian proptech or compound developer** (Palm Hills, SODIC, Hassan Allam, Madinaty) appears to run a public WhatsApp group bot. Not found.
- **Big proptech (MyGate, NoBrokerHood, ADDA)** does **not** put bots in resident WhatsApp groups. They either replace the group (MyGate: notices go via app push, email and SMS ([MyGate](https://mygate.com/blog/housing-society/seamless-apartment-communication-with-mygate/))), or use **official 1:1 WhatsApp** (NoBrokerHood, next).

### 5.3 Legitimate alternatives in production

| Pattern | Who | Evidence | Lesson for us |
|---|---|---|---|
| **Admin composes notices via a 1:1 official WhatsApp AI assistant** | **NoBrokerHood "WhatsApp Notice AI Assistant", 7 Oct 2026** | Flow: "Hi" → pick society → send rough notes (English, Hindi, Hinglish) → AI preview → reply "Yes" to publish. The AI "automatically detects categories (Maintenance, Security, Event, Emergency), sets appropriate recipient groups, schedules expiry dates". "No app downloads or web dashboard logins required." ([NoBrokerHood](https://www.nobrokerhood.com/blog/whatsapp-notice-ai/)) | **The exact pattern from file 10, now validated by the #2 Indian player.** Ours adds Egyptian Arabic voice and a "share to group" card. |
| App replaces group | MyGate, ADDA | Vendor claims only. No published adoption percentages ([ADDA](https://blog.ind.adda.io/2025/01/seamless-apartment-communication-with-adda/)) | Replacement needs gate or visitor lock-in (MyGate has guards). Egyptian buildings lack this, so co-exist with the group. |
| Admin-only announcement group plus a separate chat group | Brazilian condo practice | Lawyers advise "WhatsApp cannot be the official channel". They suggest a closed group where only the síndico posts, and note an R$7k damages case over insults in a condo group ([condominiosc](https://condominiosc.com.br/radar/4674-veja-regras-e-dicas-para-usar-o-grupo-de-whatsapp-do-condominio), [Estado de Minas](https://www.em.com.br/app/noticia/nacional/2021/01/12/interna_nacional,1228281/grupos-de-whatsapp-em-condominios-causam-aumento-das-acoes-judiciais.shtml)) | Offer a **"Community template"** (announcements plus chat) set up by the treasurer, with the app as the record. |
| Telegram group bots | Egypt freelance scene | Telegram is technically ideal (bots are first-class group members), but **adoption is poor**: about 10.6% of Egyptian sites embed Telegram against 87.9% for WhatsApp ([WMTips](https://www.wmtips.com/technologies/instant-messaging/country/eg)). No Egyptian Telegram user count found. | Optional "Telegram mode" for tech-savvy compounds only. |

---

## 6. Creative compliant patterns: evaluation

Score each pattern 1–5 on **Compliance**, **Group-like feel** (how close it gets to "bot in the group"), **Virality** and **Cost**.

| # | Pattern | How it works | Comp. | Feel | Viral | Cost | Key risk (2026) |
|---|---|---|---|---|---|---|---|
| P1 | **Forward-to-bot** | Admin or any resident long-presses a group message → Forward → "مساعد العمارة". The bot gets text, media or voice with `context.forwarded`. AI turns it into a ticket, poll, payment record or reminder, then replies with a **share card** to paste back. | 5 | 4 | 4 | 5 | Webhook does **not** give the original sender or group, so ask "مين بعتها؟" or infer it. Each reply is a billable service message after 1k. |
| P2 | **Chat-export import with AI** | Admin exports the group (.txt/.zip) and uploads it in the app or sends it to the bot. AI extracts flats, names, payments, vendors, recurring problems and builds the building profile in minutes. | 4 | 3 | 5 | 5 | **Advanced Chat Privacy** lets any member block export ([Lowyat](https://lowyat.net/2025/349167/whatsapp-releases-advanced-chat-privacy)). Personal data under PDPL: get the admin's attestation, delete raw files within 24–72 h. Meta terms ban building user profiles from *platform* data. An export is user-supplied, not API data, but keep it building-scoped. |
| P3 | **Treasurer-run Community** ("مجتمع العمارة") | Treasurer creates a Community: announcement group (admin-only) plus chat group. The app produces weekly digest cards and the treasurer posts them. The bot is 1:1. | 5 | 3 | 4 | 5 | Depends on the treasurer's discipline. Make posting one tap. Community limits (50 groups, 5,000 announcement members) are ample. |
| P4 | **Share cards plus deep links** | Every app event (paid ✅, elevator fixed, vote open) generates an Arabic image card with a link `app.link/b/123` and a `wa.me/<bot>?text=JOIN-123` fallback. | 5 | 3 | 5 | 5 | Link previews only show when the sender has the link in the message body. Keep the card image plus a short URL. |
| P5 | **Status sharing** | "Our building paid 100% this month 🎉 – عمارتنا على [App]" as a Status card | 5 | 1 | 3 | 5 | No deep link that prefills Status; it is a manual share-sheet flow. Low frequency. Use for milestones only. |
| P6 | **Official micro-groups (Groups API)** | Board group (≤7 people plus bot) and per-job groups (resident, technician, admin, bot) | 5 | 5 | 2 | 3 | **Needs OBA**, invite-link joins, no buttons, billed per recipient. Phase 3. |
| P7 | **"Bring your own agent"** (future) | When WhatsApp's third-party agents leave beta, a resident adds "مساعد العمارة" as a personal agent with an API key | 4 (beta) | 3 | 3 | 4 | 1:1 only, beta, countries unknown ([WABetaInfo](https://wabetainfo.com/whatsapp-is-rolling-out-chats-with-third-party-agents/)). Watch item. |
| P8 | Unofficial bot in the real group | Baileys or WAHA number added by the admin | 1 | 5 | 4 | 4 | Ban waves, an "unauthorized tools" warning, and all buildings going dark at once. **Rejected for the core product.** At most a **closed pilot** on throwaway numbers to learn, never sold as a feature. |

**Ranking for launch:** P1 + P4 + P2 + P3 at launch, then P6 after OBA. P7 is a watch item. P8 is rejected.

---

## 7. Updated cost per 1,000 buildings (ESTIMATE, verified Egypt prices)

**Assumptions** (same as file 10 §9 unless stated):
- 30 flats per building and 1.5 accounts per flat, so **45,000 users**.
- Prices: utility = service = **$0.0036**, marketing = $0.0644, plus 14% VAT.
- **New:** in-window utility is billed. 1,000 free service messages **per number**, and we assume **5 WABA numbers** (for example by region or function; legitimate separation of traffic, each with its own display name). That gives 5,000 free per month.
- LLM: own stack (Gemini Flash-Lite class) at ≈ $0.00046 per turn plus a 10% premium-model uplift, per file 10.

| Scenario | Utility templates / mo | Service replies / mo | Billable after 5k free | Meta USD | +VAT | AI/LLM USD | **Total USD / mo** | Per building |
|---|---|---|---|---|---|---|---|---|
| **A. Base** (50% WhatsApp-only users) | 90,000 | 141,000 | 226,000 | 814 | 928 | ~160 | **≈ $1,090** | $1.09 |
| **B. App-first** (80% on the app, so WhatsApp-only falls to 9,000 users; bot replies fall 60%) | 36,000 | 56,400 | 87,400 | 315 | 359 | ~210* | **≈ $570** | $0.57 |
| **C. Lean admin-first** (residents on push; WhatsApp bot for admins and treasurers plus forwards; 1 utility per resident per month only for those without the app) | 22,500 | 60,000 | 77,500 | 279 | 318 | ~0* (in-app AI counted in C's app budget) | **≈ $320** | $0.32 |
| D. Same as A, but **Meta Business Agent** as the brain (~20k tokens per reply ESTIMATE; Meta says up to ~25k) | 90,000 | 141,000 | 226,000 + tokens | 814 + 141,000×20k×$2/1M = **5,640** | 7,358 | 0 | **≈ $7,400** | $7.40 |
| E. Same as A, but marketing 1 template per user per month | +45,000 mktg | — | — | +2,898 | +3,304 | — | **≈ $4,400** | $4.40 |
| F. Groups API add-on (1,000 board groups × 6 human members × 30 bot messages) | — | — | 180,000 per-recipient sends | 648 | 739 | ~15 | **+≈ $750** | +$0.75 |
| G. Unofficial (Whapi about $30 per number × 50 numbers) | — | — | — | 0 | 0 | ~160 | **≈ $1,660** plus SIMs, **plus ban risk** | $1.66 |

\* Scenario B keeps total LLM spend roughly flat because AI moves into the app (OCR, digests, voice). Scenario C excludes in-app AI.

**Arithmetic check (A):**
- 90,000 + 141,000 = 231,000, minus 5,000 free = 226,000. Only service messages get the free tier, so the precise split is: utility 90,000 × 0.0036 = $324, plus service (141,000 − 5,000) × 0.0036 = $489.6, giving **$813.6**.
- ×1.14 = $927.5. Plus LLM ~$160 (141k turns × $0.00046 × 1.1 ≈ $71, plus voice, OCR and export parsing ≈ $30, plus a buffer). That gives **≈ $1,090**.

**Chart-ready data (monthly USD per 1,000 buildings):**
```csv
scenario,meta_incl_vat,ai,total
A Base,928,160,1088
B App-first,359,210,569
C Lean admin-first,318,0,318
D Meta Business Agent brain,7358,0,7358
E Base + 1 marketing/user,4232,160,4392
G Unofficial (Whapi),0,160,1660
```

**Takeaways:**
1. Even after 1 Oct 2026, official WhatsApp is **about $1 per building per month**. Phase-2 marketplace revenue of one job per building per month (≈ 50 EGP commission, about $0.90) still roughly covers it.
2. The **budget killers** are marketing templates (×18) and Meta Business Agent tokens (×7 the base case). Avoid both.
3. Each extra free-tier number saves only $3.60 per month. That is not a reason to run many numbers. Do it only for operational separation.

---

## 8. Egypt WhatsApp penetration: best available data

| Metric | Value | Type | Source |
|---|---|---|---|
| Internet users | 98.2 M (82.7%), Oct 2025 | Kepios | [DataReportal 2026 Egypt](https://datareportal.com/reports/digital-2026-egypt) |
| Mobile connections | 121 M (102%); 95.4% broadband | GSMA Intelligence via Kepios | same |
| Social media identities | 51.6 M (43.4% of population) | Kepios | same; also [El Watan / IDSC](https://www.elwatannews.com/news/details/8268984) |
| Messenger ad reach | 37.0 M (37.7% of internet users) | Meta ads tool | DataReportal 2026 |
| Messenger audience (NapoleonCat) | 54.27 M, Aug 2025 | Meta ads data | [NapoleonCat](https://stats.napoleoncat.com/messenger-users-in-egypt/2025/08/) |
| **WhatsApp users** | **~50–57 M** (third-party estimates) | Aggregators, methodology unclear | [ChatDaddy (52 M; later 57 M)](https://chatdaddy.tech/blog/whatsapp-marketing-egypt), [ElectroIQ (55 M)](https://electroiq.com/stats/whatsapp-business-statistics/), [SociallyIn (>50 M)](https://sociallyin.com/?p=12769) |
| WhatsApp users, Statista model | Values paywalled. The description says growth to 2025 was "uneven" and the forecast declines to 2035. | Model | [Statista](https://www.statista.com/forecasts/1145037/whatsapp-users-in-egypt/) |
| WhatsApp use, academic survey | **98% use it, 90% daily** (n=400, random Egyptian sample) | Peer-reviewed (EKB) | [EKB journal article 154770](https://journals.ekb.eg/article_154770.html), [SJOCS mirror](https://sjocs.journals.ekb.eg/article_154770.html) (abstract via search; full text not fetchable) |
| Messaging widget share on Egyptian websites | WhatsApp 87.9%, Messenger 12.9%, Telegram 10.6% | Web-tech proxy | [WMTips](https://www.wmtips.com/technologies/instant-messaging/country/eg) |
| Android communication-app rank | WhatsApp #1, Telegram #5 | Similarweb | file 10, [Similarweb](https://www.similarweb.com/top-apps/google/egypt/communication/) |
| NTRA / GWI WhatsApp share | **Not found** | — | — |

**ESTIMATE (triangulation):**
- Smartphone or internet users aged 13+ ≈ 85–95 M. If 90%+ of internet users use WhatsApp (EKB survey, regional norms), that gives **≈ 55–65 M**, consistent with the 50–57 M aggregator range.
- Planning figure: **≈ 55 M Egyptians on WhatsApp**, i.e. essentially **every smartphone-owning building resident**.

**Chart-ready:**
```csv
metric,millions
Population,118.8
Mobile connections,121.0
Internet users,98.2
WhatsApp users (ESTIMATE midpoint),55.0
Messenger ad reach,37.0
Social media identities,51.6
```
(The population figure is derived as 98.2 / 0.827, an ESTIMATE.)

---

## 9. OBA: current criteria and the BSP "shortcut"

[Meta OBA page](https://developers.facebook.com/documentation/business-messaging/whatsapp/official-business-accounts/) (fetched 12 Oct 2026), verbatim criteria:
> "The business must comply with the WhatsApp Business Messaging Policy."
> "The business must be registered on the WhatsApp Business Platform for at least 30 days."
> "The business portfolio that owns the number has been verified through Business Verification."
> "The business phone number has enabled two-step verification."
> "The business phone number's display name has been approved."
> "If a business phone number is not an Official Business Account (OBA), it will not appear in search results"

- If the option is missing, contact "your Meta point-of-contact, Solution Provider support, or Meta Support". A rejected request can be resubmitted after 30 days (search snippet of the same page).
- **Notability** (organic press, brand search volume) is **not** in Meta's text. It comes from BSP guides ([wetarseel](https://wetarseel.ai/whatsapp-official-business-account-requirements-in-2026-the-complete-eligibility-checklist/), [DoubleTick](https://learn.doubletick.io/official-business-accounts-oba/eligibility-criteria-for-official-business-accounts)). In practice Meta still applies discretion.
- **BSP shortcut:** BSPs such as [360dialog](https://docs.360dialog.com/docs/waba-management/official-business-account/how-to-request-an-oba) can file the request, but "the BSP does not control approval". **There is no paid shortcut.** OBA can also be requested via API since 13 Jun 2025 ([Meta changelog](https://developers.facebook.com/documentation/business-messaging/whatsapp/changelog)).
- **Plan:** register on day 0. Apply at **day 30+** once verified. Re-apply after the first press coverage (Egyptian tech media such as Wamda, Enterprise, Cairo360). Groups API stays a Phase-3 feature.

---

## 10. Risk matrix (likelihood × impact, 1–5)

| Risk | L | I | Score | Mitigation |
|---|---|---|---|---|
| Unofficial group bot number banned (if P8 used) | 5 | 5 | **25** | Don't use P8 in production. |
| Meta raises Egypt prices or adds new charges (it "may revise pricing up to once per quarter") | 3 | 3 | 9 | Push-first routing. Per-user WhatsApp budget caps. Monitor the first day of each quarter. |
| Service-message volume larger than modelled (chatty bot) | 3 | 2 | 6 | Short answers. Move long flows to app deep links and WhatsApp Flows. Cap bot turns per user per day. |
| AI-policy reinterpretation ("primary functionality") | 2 | 5 | 10 | Topic lock. Building-specific tools only. Human escalation. Keep a policy file. |
| Advanced Chat Privacy blocks chat export | 3 | 2 | 6 | Fall back to forward-to-bot and a manual roster form. |
| BSUID / usernames hide phone numbers from webhooks (GA in H2 2026) | 4 | 2 | 8 | Link accounts with an in-app token. Store BSUIDs ([Bird docs](https://docs.bird.com/api/channels-api/supported-channels/programmable-whatsapp/business-scoped-user-ids), [Kapso](https://kapso.ai/blog/whatsapp-bsuid-usernames-2026)). |
| Unanswered-message cap hits proactive outreach | 3 | 3 | 9 | Opt-in only. Never message cold numbers. Admin-initiated invites via share cards. |
| OBA denied → no Groups API | 4 | 2 | 8 | Core design does not need it. |
| Meta AI or Business Agent commoditises "summaries" | 3 | 3 | 9 | Moat = ledger, tickets, vendor graph, payments. |
| Payment method missing → service messages stop | 2 | 4 | 8 | Card on file in Billing Hub before launch ([overads](https://overads.io/blog/whatsapp-business-api-pricing-october-2026)). |
| PDPL exposure from chat-export imports | 3 | 4 | 12 | Consent attestation. Egypt-region or approved storage. Short retention. DPO registration (file 09). |

**Chart-ready (risk bubble):**
```csv
risk,likelihood,impact
Unofficial ban,5,5
AI policy drift,2,5
PDPL export,3,4
Price change,3,3
Outreach cap,3,3
Meta AI commoditisation,3,3
BSUID,4,2
OBA denied,4,2
Payment method,2,4
Export blocked,3,2
Service volume,3,2
```

---

## 11. Final verdict and architecture changes since file 10

**Verdict (12 Oct 2026):** **No official path** lets our bot sit in an Egyptian building's WhatsApp group. Nothing has shipped that changes this. The only AI allowed in consumer groups is Meta AI, and the only business groups are OBA-only ones of 8 or fewer created by invite link. The file-10 architecture stands, and NoBrokerHood's Oct 2026 launch independently validates it.

**Architecture changes to file 10:**

| Area | File 10 | Change in this update |
|---|---|---|
| Pricing | "BSPs report service billable from 1 Oct 2026" | **Meta-confirmed.** Model every bot reply at $0.0036 after 1k per number. In-window utility is now billable. |
| Bot brain | Own LLM | Keep it. **Explicitly reject Meta Business Agent** as the brain (about 7× cost). Optionally use it only as a free-tier **front desk** on the WhatsApp Business *app* number of a small pilot building, if the subscription is cheap. |
| Numbers | 1 WABA number | 3–5 numbers by function (resident assistant, admin/treasurer, technician/vendor, notifications). This also isolates quality ratings. |
| Message routing | Push first, WhatsApp fallback | Add **cost-aware routing**: if the user has the app and is active within 7 days, use push and an in-app reply. WhatsApp only for WhatsApp-only users or urgent items. |
| Forward-to-bot | Planned | Add a **"who sent it?" disambiguation** step (webhook lacks the original author). Use the `frequently_forwarded` flag to warn about rumours. |
| Chat-export import | Planned | Handle **export-blocked chats**. Add a PDPL consent screen and auto-delete raw files. |
| Admin notice composer | Implicit | **Make it a headline feature** (NoBrokerHood pattern): admin voice note → AI notice → preview → publish to app, plus a share card for the group. |
| Groups API | Phase 3 after OBA | Unchanged. Apply for OBA at day 30. |
| Future | — | **Agent adapter** for WhatsApp's third-party-agent beta (P7). Monitor quarterly. |
| Identity | BSUID-ready | Unchanged. Username GA is reported for H2 2026, so make it mandatory before launch. |

---

## 12. Sources

**Meta / WhatsApp (primary)**
- Groups API: https://developers.facebook.com/docs/whatsapp/cloud-api/groups
- Groups pricing: https://developers.facebook.com/docs/whatsapp/cloud-api/groups/pricing
- Pricing (main): https://developers.facebook.com/documentation/business-messaging/whatsapp/pricing
- Upcoming pricing (service, utility, Business Agent): https://developers.facebook.com/documentation/business-messaging/whatsapp/pricing/non-template-messages
- Pricing updates: https://developers.facebook.com/docs/whatsapp/pricing/updates-to-pricing
- Changelog: https://developers.facebook.com/documentation/business-messaging/whatsapp/changelog
- OBA: https://developers.facebook.com/documentation/business-messaging/whatsapp/official-business-accounts/
- Text webhook reference: https://developers.facebook.com/documentation/business-messaging/whatsapp/webhooks/reference/messages/text
- Terms (AI Providers §4.7, updated 23 Sep 2026): https://www.facebook.com/legal/Meta-Terms-for-WhatsApp-Business-Platform
- Meta Business Agent: https://about.fb.com/news/2026/06/meta-business-agent/ and https://whatsappbusiness.com/blog/introducing-meta-business-agent-ai/
- Meta AI MENA launch: https://about.fb.com/news/2025/02/meta-ai-launches-in-the-middle-east-empowering-new-era-of-creativity-and-connection
- WhatsApp FAQ click to chat: https://faq.whatsapp.com/5913398998672934 · Communities: https://faq.whatsapp.com/495856382464992
- Platform pricing site: https://whatsappbusiness.com/products/platform-pricing/

**Pricing (secondary)**
- https://zernio.com/whatsapp-api-pricing · https://chatmaxima.com/whatsapp-api-pricing/egypt/ · https://arabybot.com/guides/whatsapp-api-pricing-egypt?lang=en
- https://www.ycloud.com/blog/whatsapp-api-message-pricing-update-effective-october-1-2026 · https://overads.io/blog/whatsapp-business-api-pricing-october-2026 · https://respond.io/blog/whatsapp-pricing-change-2026 · https://1msg.io/blog/whatsapp-pricing-october-2026
- https://chatdaddy.tech/blog/whatsapp-business-api-egypt (outlier)
- https://www.salesforce.com/en-us/wp-content/uploads/sites/4/documents/PDF/WhatsApp-Business-Messaging-1000.pdf (non-USD)

**Groups API analysis:** https://www.unipile.com/whatsapp-group-api/ · https://kapso.com/blog/whatsapp-groups-api-state-2026 · https://www.imbee.io/resource/whatsapp-groups-api-business-guide-2026 · https://periskope.app/blog/whatsapp-groups-api-requirements-eligibility-limits

**AI policy:** https://respond.io/blog/whatsapp-general-purpose-chatbots-ban · https://techcrunch.com/2025/10/18/whatssapp-changes-its-terms-to-bar-general-purpose-chatbots-from-its-platform/ · https://techcrunch.com/2026/06/03/metas-ai-agent-for-whatsapp-business-is-now-available-globally/ · https://wabetainfo.com/meta-introduces-ai-business-agent-for-whatsapp-worldwide/ · https://wabetainfo.com/whatsapp-is-rolling-out-chats-with-third-party-agents/

**Unofficial bots and bans:**
- Baileys issues: https://github.com/WhiskeySockets/Baileys/issues/1869 · /2309 · /2260 · /2658 · /2707 · /2850
- whatsapp-web.js: https://github.com/pedroslopez/whatsapp-web.js/pull/421
- Vendors: https://docs.periskope.app/get-started/best-practices · https://support.whapi.cloud/help-desk/blocking/connecting-a-new-whatsapp-number-after-a-ban-steps-and-recommendations · https://developer.z-api.io/en/mobile/request-unbanning.md · https://www.adviseai.in/blog/whatsapp-automation-ban-risk
- Platform-scale bans: https://www.techrepublic.com/article/news-whatsapp-scams-meta · https://propakistani.pk/2025/03/24/nearly-10-million-whatsapp-accounts-banned-in-india-for-this-reason/amp/
- Unanswered-message cap: https://www.business-standard.com/technology/tech-news/whatsapp-explores-message-limit-in-one-sided-chats-to-curb-spam-report-125102100179_1.html · https://green-api.com/en/blog/2025/whatsapp-introduces-new-restrictions-on-unanswered-messages/

**Alternatives and case studies:** https://www.nobrokerhood.com/blog/whatsapp-notice-ai/ · https://mygate.com/blog/housing-society/seamless-apartment-communication-with-mygate/ · https://blog.ind.adda.io/2025/01/seamless-apartment-communication-with-adda/ · https://condominiosc.com.br/radar/4674-veja-regras-e-dicas-para-usar-o-grupo-de-whatsapp-do-condominio · https://www.em.com.br/app/noticia/nacional/2021/01/12/interna_nacional,1228281/grupos-de-whatsapp-em-condominios-causam-aumento-das-acoes-judiciais.shtml · https://whapi.cloud/blog/whatsapp-channel-api-automation

**Privacy and features:** https://lowyat.net/2025/349167/whatsapp-releases-advanced-chat-privacy · https://www.expressandstar.com/uk-news/whatsapp-launches-privacy-tool-to-stop-users-taking-content-off-the-platform-5705285 · https://docs.bird.com/api/channels-api/supported-channels/programmable-whatsapp/business-scoped-user-ids · https://kapso.ai/blog/whatsapp-bsuid-usernames-2026 · https://www.androidpolice.com/whatsapp-revamped-rich-link-previews-rolling-out-beta/ · https://getkanal.com/blog/community-guide-whatsapp · https://www.gsmarena.com/whatsapp_unveils_communities_feature_raises_group_limit_to_1024_participants-news-56392.php

**Penetration:** https://datareportal.com/reports/digital-2026-egypt · https://www.elwatannews.com/news/details/8268984 · https://stats.napoleoncat.com/messenger-users-in-egypt/2025/08/ · https://www.statista.com/forecasts/1145037/whatsapp-users-in-egypt/ · https://journals.ekb.eg/article_154770.html · https://www.wmtips.com/technologies/instant-messaging/country/eg · https://chatdaddy.tech/blog/whatsapp-marketing-egypt · https://electroiq.com/stats/whatsapp-business-statistics/

---

## 13. Verification log

| # | Claim | Check 1 | Check 2 | Result |
|---|---|---|---|---|
| 1 | Groups API max 8 participants, OBA only, invite only | Meta Groups API page, fetched 12 Oct 2026 | Unipile (verified Aug 2026), Kapso (Jun 2026) | ✅ Confirmed |
| 2 | No mechanism to join existing consumer groups | Meta docs (absence; "1 Cloud API business per group") | Unipile: no POST /participants; BotPenguin 2026 | ✅ Confirmed (by absence) |
| 3 | Service messages charged from 1 Oct 2026 | Meta "non-template-messages" page (verbatim) | YCloud, overads, respond.io, 1msg | ✅ Confirmed |
| 4 | 1,000 free service messages per number per month | Meta pricing page (search-indexed snippet) | YCloud, overads, ArabyBot, Zernio | ✅ Likely (Meta text seen only via snippet; live fetch returned a stale page) |
| 5 | Egypt marketing $0.0644 / utility $0.0036 / auth $0.0036 | Zernio (Oct 2026 card, checked 25 Sep 2026) | ChatMaxima (Meta card Jul 2026), ArabyBot | ✅ 3 sources agree; ❌ Meta CSV not retrieved |
| 6 | Egypt not in the 1 Oct 2026 rate-change list | Meta pricing page | Meta updates-to-pricing page | ✅ Confirmed |
| 7 | Meta Business Agent $2 per 1M tokens from 1 Aug 2026 | Meta pricing page (verbatim) | YCloud | ✅ Confirmed |
| 8 | AI-provider ban scope "primary (rather than incidental or ancillary)" | Meta terms (Arabic, updated 23 Sep 2026) | TechCrunch Oct 2025, respond.io | ✅ Confirmed |
| 9 | OBA five criteria | Meta OBA page (verbatim) | wetarseel, 360dialog | ✅ Confirmed; notability = third-party only |
| 10 | Third-party agents beta, 1:1 only | WABetaInfo 4 Sep 2026 | — | ◐ Single source (beta) |
| 11 | Advanced Chat Privacy blocks export and AI | Lowyat | Express & Star, The Hacker News | ✅ Confirmed |
| 12 | Baileys group-bot ban evidence | GitHub #1869 (read) | #2707 (read), #2850, #2658 | ✅ Qualitative; ❌ no rate exists |
| 13 | Communities 50 groups / 5,000 announcement members | Kanal 2026 | Telecrm 2026 | ◐ Secondary only (official FAQ body not fetchable) |
| 14 | Egypt WhatsApp users ≈ 50–57 M | ChatDaddy, ElectroIQ, SociallyIn | EKB survey 98% (n=400) | ◐ No official source; ESTIMATE ≈ 55 M |
| 15 | NoBrokerHood WhatsApp Notice AI (Oct 2026) | NoBrokerHood blog (read) | — | ✅ Primary source |
| 16 | Forwarded-message flags in webhook | Meta text webhook reference (May 2026) | Older Meta inbound doc; Twilio changelog | ✅ Confirmed |
| 17 | Meta AI in groups in Egypt (Arabic) | Meta newsroom Feb 2025 | Economy Middle East, ANBA | ✅ Confirmed (2025 launch; current status assumed) |

**Not found (explicit):**
- Meta's Egypt CSV values.
- An NTRA or GWI WhatsApp share figure.
- Any measured ban rate for group bots.
- Any 2025–2026 whatsapp-web.js ban thread.
- Any Egyptian developer or compound running a WhatsApp group bot.
- MyGate WhatsApp integration.
- Brazilian condo apps (TownSq, uCondo, Condomob) with WhatsApp group bots.
- A Telegram user count for Egypt.
- Published adoption percentages for app-replaces-group migrations.
