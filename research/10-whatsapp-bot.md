# 10 — WhatsApp Group Bot: Feasibility and a WhatsApp-First Architecture

**Research angle:** Can a bot join an Egyptian building's WhatsApp group, read the chat, and act as a coordinator? If not, what is the closest design that follows WhatsApp's rules and what does it cost?
**Date of research:** 2026-10-12. **Market focus:** Egypt only. Foreign products are included only as sources of ideas.
**Conventions:** Every fact has a source URL. Anything marked **ESTIMATE** is my own calculation, with the reasoning shown. "Not found" means I searched and found nothing reliable.

---

## 0. Executive summary (the answer in one page)

| Question | Short answer | Confidence |
|---|---|---|
| Can an official WhatsApp bot (Cloud API) be **added to an existing building WhatsApp group** like a member? | **No.** The official Groups API only lets a business **create its own** groups, which people join by invite link. It allows at most **8 participants**, and only businesses with an **Official Business Account (OBA)** can use it. | High (Meta docs) |
| Can the official API run a bot in a full-size building group (20–200 people)? | **No.** The 8-participant cap rules it out. | High |
| Can an **unofficial** library (Baileys, whatsapp-web.js, WAHA, Green-API, Whapi) put a bot in any group of up to 1,024 members? | **Technically yes.** It breaks WhatsApp's Terms of Service, and the number can be banned without warning. If the bot number is banned, every building it serves goes dark at once. | High |
| Is an AI chatbot allowed on the WhatsApp Business Platform after Meta's 2026 policy? | **Yes, if it is specific to your business.** The ban covers providers whose AI is the **primary functionality**, meaning general-purpose assistants like ChatGPT. A building-management assistant is an "ancillary" business use and is allowed. | High (Meta terms, Sep 2026) |
| What does WhatsApp messaging cost in Egypt? | About **$0.0036 per utility/authentication message** and **$0.0644 per marketing message** (BSP-published rate cards, 2026). BSPs report that **service (free-form) replies are billable from 1 Oct 2026** after 1,000 free per number per month. I could not confirm this on Meta's own pages. | Medium-High |
| WhatsApp Pay in Egypt? | **Not available.** It is live only in India, Brazil, Singapore and Mexico. Use InstaPay, Fawry, Vodafone Cash or Paymob links instead. | High |
| Recommended path | A **"WhatsApp-native, not WhatsApp-dependent"** design. (1) An official 1:1 AI assistant number for each resident ("مساعد العمارة"). (2) **"Share to group"** cards that the app generates and that residents or admins post into the group themselves. (3) **"Forward to bot"**, which turns any group message into a ticket, poll or payment. (4) **Chat-export import with AI**, which builds a whole building's data from its WhatsApp history in one step. (5) Official **≤8-person Groups API** groups for the board (اتحاد الشاغلين) and per-job threads once OBA is earned. (6) In-app building chat as the long-term home. | Recommendation |
| Cost per 1,000 buildings (~45,000 users) | **ESTIMATE ≈ $1,100 per month base case, ~$750 once 80% install the app** [corrected: aligned with §9 arithmetic] in total for WhatsApp and AI under the recommended design (section 9). Marketing templates are the budget killer at $0.0644 each, so marketing goes through free app push notifications, not WhatsApp. | Estimate |

**The single most important insight:** the founder's idea of a bot that joins the group is the right **goal** but the wrong **mechanism**. The policy-compliant way to get the same effect is to **turn the group into the delivery channel for the app's content** (share cards with deep links back to the app). The bot then lives in 1:1 chat with each resident. In practice the group becomes a free distribution channel for us, which is better for viral growth than a bot sitting silently in the group.

---

## 1. Why WhatsApp matters so much in Egypt

| Metric | Value | Source |
|---|---|---|
| Internet users, Egypt (Oct 2025) | 98.2 M (82.7% penetration) | [DataReportal Digital 2026 Egypt](https://datareportal.com/reports/digital-2026-egypt) |
| Mobile connections (end 2025) | 121 M (102% of population) | [DataReportal Digital 2026 Egypt](https://datareportal.com/reports/digital-2026-egypt) |
| Median mobile download speed | 56.45 Mbps (+120% YoY to Aug 2025) | [DataReportal Digital 2026 Egypt](https://datareportal.com/reports/digital-2026-egypt) |
| Messenger ad reach | 37.0 M | [DataReportal Digital 2026 Egypt](https://datareportal.com/reports/digital-2026-egypt) |
| WhatsApp users in Egypt | ~56 M (2024, third-party aggregator; methodology unclear) | cited in [sqmagazine WhatsApp stats](https://sqmagazine.co.uk/whatsapp-statistics/) / [worldpopulationreview](https://worldpopulationreview.com/country-rankings/whatsapp-users-by-country) |
| WhatsApp rank, Egypt communication apps (Android) | #1. Telegram is #5. | [Similarweb top apps Egypt](https://www.similarweb.com/top-apps/google/egypt/communication/) |
| Egypt WhatsApp Play-Store downloads Q2 2024 | ~4.51 M | via [orderlemon](https://orderlemon.com/en/blog/interviews/most-popular-messaging-apps-2025/) |

**Not found:** an official survey (NTRA, GWI) giving WhatsApp's share of Egyptian smartphone users. The direction is clear, though. WhatsApp is the default, and Telegram is a distant fallback.

**What this means for the product:** Egyptian buildings already run on a WhatsApp group (جروب العمارة). Residents use it for notices, complaints about the elevator (الأسانسير), collecting maintenance fees (مصاريف الصيانة), finding a plumber (سباك) or electrician (كهربائي), and the doorman (البواب). Saknna markets itself explicitly as the replacement for "a disorganized WhatsApp group" ([saknna.com](https://saknna.com)). Our strategy should be the opposite: **work with the group instead of fighting it**.

The legal backdrop also produces group friction. Law 119/2008 makes occupants' unions (اتحاد الشاغلين) mandatory for buildings with more than 5 units. It makes contributions compulsory and allows administrative seizure against people who don't pay ([Youm7](https://www.youm7.com/4664251), [Akhbar El Yom – "مأساة اتحادات الشاغلين"](https://akhbarelyom.com/news/newdetails/4808370/1/مأساة-اتحادات-الشاغلين)). Money disputes play out in the group, so a neutral bot that records payments and answers "who paid?" has real value.

---

## 2. The official route: WhatsApp Business Platform (Cloud API), 2025–2026 facts

### 2.1 Groups API: what it is and what it is not

- **Launch:** the Meta changelog entry dated **6 October 2025** reads: "Introducing WhatsApp Groups API, which enables programmatic creation and management of groups on WhatsApp." ([Meta changelog](https://developers.facebook.com/documentation/business-messaging/whatsapp/changelog))
- **Eligibility:** Official Business Account (OBA) only. It is not available on WhatsApp Business **app** numbers or on numbers onboarded to Multi-solution Conversations ([Meta Groups API docs](https://developers.facebook.com/docs/whatsapp/cloud-api/groups)). Kapso's June 2026 analysis puts it this way: "available, but mostly blocked by OBA". It notes that OBA is separate from business verification, an approved display name, or the ability to send 1:1 messages ([Kapso](https://kapso.com/blog/whatsapp-groups-api-state-2026)).

| Groups API parameter | Value | Source |
|---|---|---|
| Max participants per group | **8**, and the business number uses one slot ([Unipile](https://www.unipile.com/whatsapp-group-api/)) | [Meta docs](https://developers.facebook.com/docs/whatsapp/cloud-api/groups) |
| Max groups per business number | 10,000 | Meta docs |
| How users join | **Invite link only.** "Not the same as silently adding users" | Meta docs, [Kapso](https://kapso.com/blog/whatsapp-groups-api-state-2026) |
| Cloud API businesses per group | Max 1 | Meta docs |
| Supported messages | Text, media, text templates, media templates; receive group messages; pin/unpin | Meta docs, Kapso |
| **Not** supported | Interactive messages (buttons/lists), commerce, auth templates, calling, disappearing / view-once (confirmed on Meta docs, Oct 2026). "Edit/delete" and "hiding participants" are **[unverified]**: they are not in Meta's current non-supported list. | Meta docs |
| Joining an **existing consumer group** | **No documented mechanism.** Every endpoint works on groups the business itself creates. | Meta docs (absence), Kapso, [Chat2desk: "WABA numbers cannot be added to groups"](https://chat2desk.com/en/knowledge-base/messenger-configuration/do-you-work-with-group-chats-on-whatsapp-and-telegram) |

**Groups pricing** ([Meta Groups pricing](https://developers.facebook.com/docs/whatsapp/cloud-api/groups/pricing)):
- Charged **per delivered participant**. One marketing template sent to 5 members means 5 charges.
- When any member messages, it opens **one** service window for the whole group. Free-form replies (`group_service`) are free, and utility templates inside the window are free (`group_utility`).
- Group utility messages **do not count toward volume tiers**.
- *Caveat:* this page may predate the 1 Oct 2026 service-message change (§2.3).

**OBA requirements** ([Meta OBA docs](https://developers.facebook.com/documentation/business-messaging/whatsapp/official-business-accounts/)):
- A verified business with at least 30 days on the platform that follows the messaging policy. If refused, you can reapply after 30 days.
- Third-party guides say "notability" means organic coverage in reputable media ([wetarseel](https://wetarseel.ai/whatsapp-official-business-account-requirements-in-2026-the-complete-eligibility-checklist/)). Meta's own excerpt does not confirm this.
- **Implication:** a new startup will probably **not** get OBA in month 1. Plan Groups API features for after press coverage.

**Verdict:** the official API **cannot** run the founder's "bot inside the building group" vision. It **can** run small, high-value groups (board of 3–7 members plus the bot; a resident, technician, admin and bot thread per job).

### 2.2 1:1 messaging features useful for us

| Feature | Use for a building app | Source / status |
|---|---|---|
| **Utility templates** | Dues reminders, receipts, "the technician is coming at 5pm", water-cut alerts | [Meta pricing](https://developers.facebook.com/docs/whatsapp/pricing) |
| **Interactive messages** (buttons, lists) | "Pay now / Remind me later", "Rate the plumber 1–5" (1:1 only, not in groups) | Meta docs |
| **WhatsApp Flows** (native forms inside the chat, GA 10 Oct 2023) | Maintenance-request form, flat registration, technician booking calendar | [Meta changelog](https://developers.facebook.com/documentation/business-messaging/whatsapp/changelog). I found no documented Egypt restriction. |
| **Free Entry Point window** (72 h, all messages free incl. templates) | Users who arrive from a Click-to-WhatsApp ad or Facebook Page CTA | [Meta pricing](https://developers.facebook.com/docs/whatsapp/pricing) (useful later if we run ads) |
| **Usernames / BSUID** | From 2026 a user who adopts a username may stop sharing their phone number with businesses. The business gets a business-scoped user ID instead (in webhooks from 31 Mar 2026). | [Meta BSUID docs](https://developers.facebook.com/documentation/business-messaging/whatsapp/business-scoped-user-ids), [YCloud](https://www.ycloud.com/ru/blog/whatsapp-usernames-and-business-scoped-user-ids) |
| **WhatsApp Pay** | **Not in Egypt.** Live in India, Brazil, Singapore and Mexico only (consistent across secondary sources; Meta publishes no official 2026 country list, and Egypt is not in any reported list or beta billing list). | [ProPakistani Aug 2026](https://propakistani.pk/2026/08/25/whatsapps-online-payments-could-reach-more-countries-soon/) |
| **Channels** | One-way broadcast. There is no official business API for posting. | WAHA lists Channels automation (unofficial): [waha.devlike.pro](https://waha.devlike.pro/) |

**BSUID design rule:** never use the WhatsApp phone number as the primary key. Link a WhatsApp identity to an app account through an OTP or deep-link handshake, and store the BSUID.

### 2.3 Pricing: how it changed and what Egypt costs

**Timeline (Meta):**
- **1 Nov 2024:** "Service conversations are now free for all businesses, including via AI-enabled conversational experiences" ([changelog](https://developers.facebook.com/documentation/business-messaging/whatsapp/changelog)).
- **1 Jul 2025:** moved from per-conversation to **per-message** pricing. Only templates are charged. Utility templates inside an open 24 h window are free. Utility and auth get **volume tiers** ([Meta pricing](https://developers.facebook.com/docs/whatsapp/pricing)).
- **Egypt-specific changes** ([Meta pricing](https://developers.facebook.com/docs/whatsapp/pricing)):
  - Auth lowered 1 Feb 2025.
  - Auth-international lowered 1 Apr 2025.
  - **Utility and auth lowered 1 Oct 2025.**
  - **Marketing lowered 1 Jan 2026.**
- **16 Feb 2026:** a new pricing policy for "AI Providers" (charges for non-template messages only where Meta is legally required to allow them). EU/EEA charges were dropped on 13 May 2026; Brazil still applies ([changelog](https://developers.facebook.com/documentation/business-messaging/whatsapp/changelog), [TechCrunch](https://techcrunch.com/2026/03/06/after-europe-whatsapp-will-let-rival-ai-companies-offer-chatbots-in-brazil/)). **This does not apply to Egypt or to us.**
- **1 Aug 2026:** **Meta Business Agent** (Meta's own AI agent, launched globally 3 Jun 2026) is billed at **$2 per 1M tokens**, about 4–5 cents per reply (up to ~25k tokens per message). TechCrunch also reports that Meta plans to bundle the agent into some WhatsApp Business Premium subscription tiers, so the exact billing model is still moving [corrected: nuance added] ([Business Today](https://www.businesstoday.in/technology/artificial-intelligence/story/whatsapp-introduces-token-based-pricing-for-ai-agents-from-august-1-540699-2026-07-03), [TechCrunch](https://www.techcrunch.com/2026/06/03/metas-ai-agent-for-whatsapp-business-is-now-available-globally/)). Our own LLM is far cheaper (§9).
- **1 Oct 2026, reported by BSPs:**
  - **Service (free-form) messages become billable** at the recipient market's utility rate, with **1,000 free per business phone number per month**.
  - **Utility templates inside the window also become billable.** They are billed as utility and do **not** use up the 1,000 free service allowance. Service messages are billed at the utility rate **with no volume-tier discount** (ArabyBot, YCloud).
  - Sources: [Twilio notice](https://help.twilio.com/articles/53100480177819), [YCloud](https://www.ycloud.com/blog/whatsapp-api-message-pricing-update-effective-october-1-2026), [Business Today](https://www.businesstoday.in/technology/artificial-intelligence/story/whatsapp-introduces-token-based-pricing-for-ai-agents-from-august-1-540699-2026-07-03), [ArabyBot Egypt](https://arabybot.com/guides/whatsapp-api-pricing-egypt?lang=en).
  - ⚠️ Re-checked 12 Oct 2026: Meta's own pricing page still says "Utility templates delivered within an open customer service window are free". Its 1 Oct 2026 entry lists only rate updates for 9 markets (Egypt not among them). Every BSP source and Business Today describe the change, and Oman Observer reported it as news. **Treat this change as real for budgeting, but it is not yet confirmed on a Meta page.**

**Egypt rate card (USD per delivered message, 2026):**

| Category | Rate | EGP @55 | Source |
|---|---|---|---|
| Marketing | **$0.0644** | ~3.54 | [ArabyBot](https://arabybot.com/guides/whatsapp-api-pricing-egypt?lang=en), [ChatMaxima](https://chatmaxima.com/whatsapp-api-pricing/egypt/) |
| Utility | **$0.0036** | ~0.20 | same |
| Authentication | **$0.0036** | ~0.20 | same |
| Service (free-form reply) from 1 Oct 2026 | $0.0036 after 1,000 free per number per month | ~0.20 | same, plus BSP notices above |
| Inbound user messages | Free | — | [Wati / BSP summaries](https://www.wati.io/en/blog/whatsapp-service-message-pricing/) |

Older or alternative figures exist: Eazybe lists marketing at $0.0708 and utility at $0.0057 (undated, probably pre-Oct 2025) ([Eazybe](https://help.eazybe.com/es/waba/pricing)), and Ominiflow lists $0.1073 (an outlier). Some sources add **14% Egyptian VAT**. **Confirm in WhatsApp Manager before launch.**

**Key ratio:** one marketing message costs as much as about **18 utility messages**. Promotions must go through free push and in-app channels, not WhatsApp.

### 2.4 Meta's AI chatbot policy: exact scope

From the official **Meta Terms for WhatsApp Business Platform**, Section 4.7 "AI Providers", last updated **23 Sep 2026** **[unverified]**: I could not fetch the live terms page to confirm the date or section number; the wording itself is confirmed by TechCrunch and a cached copy of the terms ([Meta terms](https://www.facebook.com/legal/Meta-Terms-for-WhatsApp-Business-Platform), Arabic version):

- AI and machine-learning providers and developers are "strictly prohibited" from using the platform, directly or indirectly, to provide, offer, sell or make available such technologies **"when such technologies are the primary (rather than incidental or ancillary) functionality"**. Original wording: «عندما تكون هذه التقنيات هي الوظيفة الأساسية (وليس العرضية أو المساعدة)».
- You **may** retain an AI provider as your solution provider.
- You may **not** let WhatsApp Business Platform data (even anonymized) be used to create, develop, train or improve AI models. The exception is **fine-tuning your own model for your exclusive use**.
- Effective for new users 15 Oct 2025 and for existing users **15 Jan 2026** ([respond.io](https://respond.io/blog/whatsapp-general-purpose-chatbots-ban), [MediaNama](https://www.medianama.com/2025/10/223-whatsapp-bans-external-ai-providers-business-api/)). ChatGPT, Perplexity, Luzia and Poke left WhatsApp ([Gulf News](https://gulfnews.com/technology/no-more-chatgpt-and-perplexity-on-whatsapp-meta-bans-major-ai-chatbots-from-2026-1.500316016)).

**Application to our bot:** "مساعد العمارة" is a building-services assistant. It handles tickets, dues, notices, technician booking and polls, and AI is **ancillary** to that service. That falls in the allowed category ("support, bookings, order tracking, notifications" per [respond.io](https://respond.io/blog/whatsapp-ai-chatbot-policy)). **Design guardrails so we stay clearly ancillary:**
1. Keep the system prompt to building, home-service and account topics. Politely decline general questions ("اسألني عن عمارتك أو خدمات البيت").
2. Do not market it as "ChatGPT on WhatsApp".
3. Do not send WhatsApp conversation data to an LLM vendor that trains on it. Use zero-retention / no-training API terms (Gemini paid tier, Anthropic and OpenAI API defaults). Fine-tuning our own model is allowed.
4. Give a human escalation path (admin or support).

---

## 3. The unofficial route: group bots via reverse-engineered clients

### 3.1 How they work

| Tool | Mechanism | Group capability | Cost | Source |
|---|---|---|---|---|
| **Baileys** (WhiskeySockets) | TypeScript, direct WebSocket to WhatsApp servers, pairs as a **linked device** (QR / pairing code), no browser | Full: read all group messages, send, create, add/remove, admin | Free (OSS) | [Zylos 2026](https://zylos.ai/research/2026-01-26-whatsapp-api-automation) |
| **whatsapp-web.js** | Puppeteer drives a real WhatsApp Web in Chromium. Heavier but "may be less detectable". | Full group management, events | Free | [Zylos](https://zylos.ai/research/2026-01-26-whatsapp-api-automation), [checkleaked](https://whatsapp.checkleaked.cc/blog/best-open-source-whatsapp-libraries) |
| **WAHA** | Self-hosted REST wrapper with 3 engines: WEBJS (browser), NOWEB (WebSocket, Node), GOWS (WebSocket, Go). Scales "1 to 500 sessions". | Full | Free core; $5/mo community tiers | [WAHA](https://waha.devlike.pro/), [WAHA engines](https://waha.devlike.pro/docs/how-to/engines/) |
| **Green-API** | Hosted, per-instance billing | createGroup, addGroupParticipant, setGroupAdmin… unlimited on Business plan | Free dev (3 chats); Business per instance (~$0.40/day per third-party listing) | [Green-API tariffs](https://green-api.com/en/docs/about-tariffs/), [softwarefinder](https://softwarefinder.com/sales-tools/green-api) |
| **Whapi.Cloud** | Hosted | Groups up to 1,024, add participants, read history, polls, resolve @lid | $35/number/mo (1–5), $30 (6–20), $25 (21–50); annual $29 | [Whapi groups](https://whapi.cloud/whatsapp-groups-api), [Whapi pricing](https://support.whapi.cloud/help-desk/getting-started/pricing) |

All of these log in **as a normal WhatsApp account** (a phone number running as a "linked device"). That is why they can be added to any group of up to **1,024** members ([GSMArena](https://www.gsmarena.com/whatsapp_unveils_communities_feature_raises_group_limit_to_1024_participants-news-56392.php)) like a human.

### 3.2 Terms of Service and ban risk

**WhatsApp Terms of Service** ([whatsapp.com/legal/terms-of-service](https://www.whatsapp.com/legal/terms-of-service)) prohibit:
- "non-personal use of our Services unless otherwise authorized by us"
- "bulk messaging, auto-messaging, auto-dialing"
- accessing or using the service "through automated or other means"
- "reverse engineer… extract code"
- creating "software or APIs that function substantially the same as our Services" for third parties

A building-bot business on Baileys or WAHA violates several of these at once.

**Enforcement scale:** in India alone WhatsApp bans about **9.7–9.9 million accounts a month**, about 1.3–1.4 M of them proactively before any user report. Common causes include "automation through bots or third-party apps" and "adding users to groups without their consent" ([Business Today, Feb 2025 report](https://businesstoday.in/technology/news/story/whatsapp-banned-97-million-indian-accounts-in-february-heres-why-470175-2025-04-01), [Herald Goa](https://www.heraldgoa.in/?p=18380)).

**New friction since Oct 2025:** WhatsApp is testing a **monthly cap on messages to people who don't reply**, for users and businesses ([9to5Mac](https://9to5mac.com/2025/10/17/whatsapp-to-restrict-how-many-messages-users-can-send-without-replies/)).

**Security:** Baileys had a CVE that let an attacker spoof messages and inject fake sync data, fixed in 6.7.22 / 7.0.0-rc12 ([Mondoo CVE-2026-48063](https://mondoo.com/vulnerability-intelligence/vulnerability/CVE-2026-48063)).

Vendors argue that **behaviour, not the library**, triggers bans: complaints, unsolicited adds, unexpected messages ([Whapi](https://whapi.cloud/whatsapp-groups-api), [checkleaked](https://whatsapp.checkleaked.cc/blog/best-open-source-whatsapp-libraries)). This is partly true. A passive bot that only replies when @-mentioned in groups that invited it is lower-risk than a spammer. But it is still a **ToS breach with no appeal channel**, and I found **no public data on ban rates for group bots**.

### 3.3 Risk matrix for our business specifically

| Risk | Likelihood | Impact | Why it is severe for us |
|---|---|---|---|
| Bot number banned | Medium (unknown rate) | **Catastrophic** | One number serving 500 buildings means 500 groups lose the bot at once. Number pools spread the risk but multiply cost. |
| Meta legal / BSP blacklisting | Low–Medium | High | It would block our future path to the **official** API, OBA, the Groups API and Meta Business Agent partnerships. |
| Resident privacy complaint (bot "reads everything") | Medium | High | Egypt's **PDPL (Law 151/2020)** Executive Regulations (Decree 816/2025) were issued 1 Nov 2025, with full enforcement from about **Nov 2026**. They require licensing by the Personal Data Protection Center, consent, records and breach notification ([CMS](https://cms.law/en/are/legal-updates/egypt-s-pdpl-executive-regulations-issued-one-year-compliance-countdown-begins), [Clyde & Co](https://www.clydeco.com/en/insights/2026/01/egypt-regulatory-update-on-data-privacy), [Kennedys](https://www.kennedyslaw.com/en/thought-leadership/article/2026/egypt-s-personal-data-protection-law-the-compliance-countdown-has-begun)). A bot that ingests everyone's group messages without each member's consent is exposed. |
| App-store review | Low | Medium | No direct conflict, but marketing an "unofficial WhatsApp bot" invites takedown complaints. |
| Investor due diligence | High (if we raise) | Medium | Platform-ToS violation at the core of the product is a red flag. |

**Verdict:** do **not** build the core product on an unofficial group bot. At most, run an **opt-in experimental pilot** (§8, option E) with a kill-switch, kept separate from the official number and brand.

---

## 4. Other routes

### 4.1 Telegram group bots (technically ideal, adoption-poor)
- Bots in groups run in **Privacy Mode** by default. They receive only commands addressed to them, replies to their messages and service messages. **Bot admins always receive all messages** ([Telegram Bot features](https://core.telegram.org/bots/features#privacy-mode)).
- The Bot API is free and officially supports exactly what the founder wants: a bot that sits in the group, reads, and acts.
- **Problem:** Telegram ranks #5 in Egyptian communication apps ([Similarweb](https://www.similarweb.com/top-apps/google/egypt/communication/)). Moving a building from WhatsApp to Telegram is a bigger ask than installing our app.
- **Use:** an optional "Telegram mode" for tech-savvy compounds only. Low priority.

### 4.2 In-app building chat (the long-term home)
- We own the data, the AI can read everything (with consent in our ToS), and there is no per-message cost (FCM push is free).
- Every Indian and Brazilian leader eventually built this: MyGate, ADDA helpdesk ([ADDA blog](https://blog.ind.adda.io/2025/01/seamless-apartment-communication-with-adda/)), myKutir "replaces WhatsApp" ([hunted.space](https://hunted.space/dashboard/mykutir)).
- **But** it does not win on day 1. We need a bridge (§8).

### 4.3 Native WhatsApp features we should exploit, not fight
WhatsApp keeps adding group-coordination features:
- **Polls** with end times and anonymous voting, and **@all** (admin-only above 32 members), from Aug 2026 ([WABetaInfo](https://wabetainfo.com/whatsapp-announces-three-new-features-for-group-chats/), [ETV Bharat](https://www.etvbharat.com/en/technology/whatsapp-introduces-all-mentions-anonymous-polls-new-group-chat-creation-feature-enn26080502111)).
- **Event reminders**, **member tags** and **group message history** (earlier 2026) ([Dawan Africa](https://www.dawan.africa/news/meta-announces-new-updates-on-whatsapp-group-chats)).
- **Meta AI "Message Summaries"** for unread group messages, via Private Processing. Opt-in, English/US at launch ([Business Today](https://www.businesstoday.in/amp/technology/news/story/whatsapp-is-using-meta-ai-to-read-your-group-chats-but-your-messages-are-still-private-481906-2025-06-26), [The Hacker News](https://thehackernews.com/2025/06/whatsapp-adds-ai-powered-message.html)).

**Strategic implication:** generic "group summarizer" value will be **commoditized by Meta itself**. Our bot's value must come from **structured building data** (who paid, open tickets, technician history, the dues ledger), which Meta AI does not have.

---

## 5. Case studies and analogues

| Product / country | What they do with WhatsApp | Lesson for us | Source |
|---|---|---|---|
| **Sindia by CondoConta** (Brazil, Sep 2026) | AI financial assistant for the condo manager (síndico) **inside WhatsApp 1:1**. Voice or text: "Sindia, pay this bill." It confirms first, flags unusual expenses and predicts a negative balance. Built on Open Finance. | **1:1 with the admin, voice-first, confirm-before-act** is the proven pattern, not a bot in the group. Our Egyptian equivalent is "مساعد أمين الصندوق" for the union treasurer. | [SíndicoNet (sponsored column)](https://www.sindiconet.com.br/informese/gestao-financeira-inteligencia-artificial-condominio-sindia-mercado-coluna-de-olho-no-mercado/amp) |
| **Immobile Condomínio (Alterdata)** (Brazil) | WhatsApp chatbot sends residents their boleto (dues slip) or balance sheet on request and answers FAQs | "Send me my dues statement" is the #1 bot job | [Alterdata](https://ajuda.alterdata.com.br/ni/condominio-188724123.html) |
| **Trevizan Vieira** (Brazil, administrator) | WhatsApp bot handles duplicate slips, owner changes, no-debt certificate (certidão negativa), human handoff | Owner change / clearance certificate (براءة ذمة) is a strong Egyptian use case for sale and rent transfers | via [Sindiconet search results](https://www.sindiconet.com.br/informese/14811/convivencia/mundo-digital) |
| **AiSensy "Society Helpdesk Bot"** (India) | WhatsApp template: residents log society issues and track status | Ticketing over WhatsApp 1:1 is a ready-made, cheap pattern | [AiSensy](https://aisensy.com/whatsapp-chatbot-template/society-helpdesk-bot) |
| **NoBrokerHood** (India) | WhatsApp used for **visitor invitation cards** (QR/passcode). Approvals happen in the app or by IVR. | WhatsApp is the **distribution artifact**; the app is the system of record | [NoBrokerHood](https://www.nobrokerhood.com/solutions/visitor-management-system) |
| **Nexudus** (coworking, global) | Hosts approve visitors by replying on WhatsApp in natural language. An AI assistant can "approve all pending". | Natural-language approval by the doorman or resident on WhatsApp | [Nexudus docs](https://learn.nexudus.com/platform/operations/visitor-approval-whatsapp) |
| **BMC "Hello A Ward"** (Mumbai) | AI WhatsApp assistant for civic complaints | Large-scale AI complaint intake on WhatsApp works | [Free Press Journal](https://www.freepressjournal.in/mumbai/bmc-launches-hello-a-ward-ai-whatsapp-assistant-for-civic-complaints-in-south-mumbai) |
| **WideBot** (Egypt) | Arabic AI **voice agent for WhatsApp calls** | Egyptian-dialect voice AI on WhatsApp is available locally | [MENA Startup Digest](https://menastartupdigest.com/?p=18278) |
| **Saknna** (Egypt, KSA, UAE, Kuwait, Qatar, Oman, Bahrain, Jordan) [corrected] | No WhatsApp integration (WhatsApp is only a support/sales contact button); positions itself *against* the messy WhatsApp group ("بدون جروب واتساب فوضوي"). Paid: 450 EGP (≤5 units), 900 (≤10), 2,200 (≤20), 7,500 (compound, unlimited) per month; annual = 2 months free. Claims 500+ buildings. | Opening for us: **free plus WhatsApp-native** beats paid and anti-WhatsApp | [saknna.com](https://saknna.com) |
| **Egyptian freelance market** | Requests on Mostaql and Khamsat for "building bills/maintenance app" and "WhatsApp group management bots" | Demand exists, but the supply is fragmented, ad-hoc and unofficial | [Mostaql](https://mostaql.com/project/961073), [Khamsat](https://khamsat.com/programming/chatbots-development/2574648) |

**Not found:** any verified example worldwide of a building app running an AI bot **inside full-size resident WhatsApp groups at scale** through the official API. That is because the API doesn't allow it. The scaled players (Sindia, AiSensy, NoBrokerHood) all use **1:1 plus app**.

---

## 6. Option comparison

| # | Option | Achieves "bot in the group"? | ToS compliant | Ban risk | Cost / 1,000 buildings / month (ESTIMATE) | Time to build | Verdict |
|---|---|---|---|---|---|---|---|
| A | Official 1:1 assistant (Cloud API) | Partly (each resident talks to it) | ✅ | Very low | $700–1,100 (see §9) | 4–6 weeks | **Core** |
| B | Share-to-group cards + deep links (from app or bot) | ✅ The content appears in the group, posted by humans | ✅ (user-initiated sharing) | None | ~$0 | 1–2 weeks | **Core, the main growth engine** |
| C | Forward-to-bot (group message → 1:1 → structured action) | Partly | ✅ | None | Included in A | 1–2 weeks | **Core** |
| D | Chat-export import + AI parsing | Retroactive "bot that read the group" | ✅ if the uploader consents and we minimize data (PDPL) | None | ~$5 (LLM) | 2–3 weeks | **Core onboarding hack** |
| E | Unofficial bot (WAHA/Baileys) inside real groups | ✅ fully | ❌ | Medium–High, correlated | Self-host ~$150–400 servers + SIMs; hosted Whapi $25k–35k if one number per building | 2–4 weeks | **Not for core.** Optional isolated pilot only |
| F | Official Groups API (≤8, OBA) | For **small** groups only (board, per-job) | ✅ | None | Small | 2 weeks + OBA wait | **Phase 2** after OBA |
| G | Telegram group bot | ✅ (in Telegram) | ✅ | None | ~$0 | 1–2 weeks | Optional niche |
| H | In-app building chat with AI | ✅ (in our app) | ✅ | None | Push free | 3–5 weeks | **Phase 1.5**, long-term home |
| I | Meta Business Agent instead of our own AI | 1:1 only | ✅ | None | ~$0.04–0.05 per reply (25k tokens × $2/M) | Fast | No: about 100× costlier than our own LLM and no access to our ledger |

---

## 7. What the founder's vision really needs, and how each part maps

| Founder's wish ("بوت واتساب يدخل الجروب ويفهم وينفذ") | Underlying job | Compliant implementation |
|---|---|---|
| "Joins the group" | Be present where residents are, without a new habit | B: every app action produces a rich WhatsApp share card that the admin or resident posts with one tap. The group sees the "bot" output daily. |
| "Understands the conversation" | Turn chaos into structured data | D (history import) plus C (forward any message) plus a 1:1 bot that understands Egyptian Arabic text, **voice notes** and photos |
| "When asked, executes" | Tickets, payments, polls, reminders, booking a technician | A: 1:1 bot with tools (create_ticket, log_payment, send_poll_card, book_technician, broadcast_notice) and Flows forms |
| "Coordinates people" | Who does what; reminders | Personalized utility templates plus app push; small official groups (F) for board and per-job threads |
| "Every resident has an account" | Identity and data moat | WhatsApp-first sign-up: a resident who messages the bot **gets an account automatically** (phone/BSUID → account), with no app install needed on day 1 |

---

## 8. Recommended architecture: "WhatsApp-native, not WhatsApp-dependent"

### 8.1 Diagram (logical)

```
                ┌──────────────────────────── Existing building WhatsApp group (جروب العمارة) ─────────────────────────┐
                │   Residents / admin paste SHARE CARDS ("📢 إعلان: قطع المياه بكرة 10–2 ← تفاصيل: link")          │
                │   Residents FORWARD messages to the bot ("الأسانسير واقف" → forward → ticket created)          │
                └──────────────▲──────────────────────────────────────────────┬──────────────────────────────────────┘
                               │ (human share, wa.me / share-sheet)            │ (human forward / chat export .txt)
┌──────────────────────┐       │                                              ▼
│  Mobile app + PWA    │◄──────┴───────── Deep links ───────────── ┌───────────────────────────────┐
│  (system of record)  │                                           │ Official WhatsApp Cloud API   │
│  dues ledger, tickets│◄──── same backend / event bus ───────────►│ number "مساعد العمارة" (1:1)  │
│  polls, directory,   │                                           │ - text/voice/photo intake     │
│  in-app chat (H)     │                                           │ - Flows forms, buttons        │
└──────────┬───────────┘                                           │ - utility templates (alerts)  │
           │ FCM/APNs push (free)                                  └──────────────┬────────────────┘
           ▼                                                                      │ webhooks
   Personalized notifications                                        ┌────────────▼─────────────┐
   (push first, WhatsApp only                                        │ AI layer (LLM + tools)    │
    for critical/opt-in)                                             │ Egyptian-Arabic NLU, ASR, │
                                                                     │ OCR (receipts, meters),   │
                                                                     │ export parser, summaries  │
                                                                     └────────────┬─────────────┘
                                                                                  │
                                                         Phase 2 (after OBA): Groups API ≤8
                                                         - Board group (اتحاد الشاغلين + bot)
                                                         - Per-job group (resident+فني+admin+bot)
```

### 8.2 Component specs

**A. "مساعد العمارة": official 1:1 AI assistant (Cloud API, direct with Meta; no BSP fee)**
- **Entry points:**
  - QR sticker in the elevator and at the entrance ("امسح وكلم مساعد العمارة")
  - wa.me link in every share card
  - "Join your building" link the admin sends to the group
- **Identity:**
  - First message → the bot asks for the building code or invite token, then the flat number.
  - It creates an account (phone or BSUID) and links it to the app later through OTP / magic link.
  - **This is how "every resident has an account" happens without forcing an app install.**
- **Capabilities (tool calls):**
  1. Report an issue by **voice note** (Egyptian dialect). The AI transcribes, classifies (elevator / water / electricity / cleaning / security), finds duplicates ("3 neighbours already reported the elevator, I added you") and creates the ticket.
  2. Dues:
     - "How much do I owe?"
     - "I paid": user sends an InstaPay/Vodafone Cash **screenshot** → OCR → amount, reference and date → treasurer approves with one button.
     - Payment link (Paymob / Fawry) **because WhatsApp Pay is not in Egypt**.
  3. Book a technician (سباك/كهربائي/نجار) from the building's **trusted directory** (seeded by D). This is the bridge to the phase-2 marketplace and commission model.
  4. Notices: an admin dictates "اكتب إعلان إن المياه هتتقطع بكرة" → the AI drafts a polished notice → it is sent as a **share card** to the group (B) and as push or utility templates to residents.
  5. Polls: the admin asks "اعمل تصويت على تغيير شركة الأسانسير" → poll card plus results in the app. Native WhatsApp polls are an alternative.
  6. "What happened in the building this week?": a digest drawn from **our structured data**, not from reading the group.
  7. Doorman (البواب) mode: a simplified voice-only flow to log deliveries, visitors and water-tank status.
- **Policy guardrails:** building-scoped prompts, no general Q&A, human handoff, no training on WhatsApp data (§2.4).
- **Language:** Egyptian Arabic first. The bot mirrors whatever language the user writes in.

**B. Share-to-group cards (the zero-cost viral engine)**
- Every important event (new notice, monthly dues summary, completed repair with before/after photo, poll, "Flat 5 paid ✅") generates a **pre-formatted Arabic message plus a short deep link** (`app.link/b/XYZ`). The user posts it into the group with one tap through the Android/iOS share sheet or a `wa.me/?text=` link.
- The posting is **human-initiated, so it is fully compliant and free**. It also turns every building group into an advertising channel: each card says "via [App]" and the link opens a web preview (PWA) with a "join your building" CTA.
- This achieves about 80% of "the bot is in the group" from the residents' point of view.

**C. Forward-to-bot**
- A resident long-presses any group message ("مين معاه رقم سباك كويس؟", "الكهربا قاطعة في الدور التالت") → Forward → مساعد العمارة.
- The bot replies with buttons: "Create ticket / Add to poll / Save technician number / Remind me".
- Free for us: the inbound message is free, and our reply opens or uses a service window (billable after 1,000 free per month per number from Oct 2026).

**D. WhatsApp chat-export import (the onboarding "superpower")**
- The admin exports the group chat: "Without media" gives a `.txt` of up to **about 40,000 messages** ([dev.to guide](https://dev.to/chattopdf/whatsapp-chat-export-complete-guide-iphone-android-zip-pdf-2026-10lo), [maketecheasier](https://maketecheasier.com/?p=333810)). It is shared to the app (share target) or sent to the bot as a document.
- The AI parses it and produces an **auto-built building profile**:
  - Member list (names and phones) mapped to flats where they are mentioned
  - Recurring problems (elevator breakdown frequency)
  - **Technicians' phone numbers and residents' opinions of them**, which seeds the vendor directory for the phase-2 marketplace
  - Payments mentioned ("دفعت 300 للبواب")
  - Open disputes, plus a "building health" report
- One upload replaces hours of data entry. This directly answers the founder's "AI for data entry" idea.
- **PDPL compliance:**
  - The uploader confirms they are an admin and members were notified.
  - Process transiently, keep only structured fields, delete the raw text within 24 h.
  - Show members a notice the first time they open the app, with an opt-out.
  - Under Law 151/2020 and its 2025 regulations, consent and records are mandatory ([CMS](https://cms.law/en/are/legal-updates/egypt-s-pdpl-executive-regulations-issued-one-year-compliance-countdown-begins)).
- **Repeatable:** "Monthly sync". The admin re-exports and the AI produces "what changed".

**E. Optional unofficial group-bot pilot (only if the founder insists; isolated)**
- A separate brand or number, explicit opt-in by the admin, **reply-only** (responds only to @mention or "يا مساعد"), never adds people, never broadcasts.
- One number per ~20–50 groups to cap blast radius, a kill-switch, and no cross-link to the official WABA business portfolio.
- Run it as a **3-month research pilot** to measure demand. The same jobs migrate to B, C and H.
- Expect bans. Document the risk to the admins. **Not recommended**, and not included in the cost base.

**F. Official Groups API (phase 2, after OBA)**
- **Board group:** union president, treasurer, secretary plus the bot (≤8). The bot posts weekly ledger summaries, pending approvals and maintenance quotes. Free-form group service replies are free in the group service window, per Meta's group pricing (check the post-Oct 2026 rules).
- **Per-job groups:** resident, technician, admin and bot. Used for scheduling, photos and payment confirmation. This is the **marketplace transaction channel** with commission tracking.
- **Path to OBA:** press coverage (an Egyptian tech-media launch story), verified business, 30+ days on the platform.

**H. In-app building chat**
- An AI-moderated chat with threads (Announcements / Complaints / Marketplace / Social), auto-ticketing, auto-summaries and translation.
- Grows naturally as the app becomes the place where the "real" data lives.

### 8.3 Personalized notification routing (connects to the founder's idea #1)

| Event | Default channel | WhatsApp template? | Why |
|---|---|---|---|
| Dues due / overdue | Push → if unread 24 h → WhatsApp utility | Yes (utility, $0.0036) | High value, collects money |
| Water/electricity cut, elevator down | Push + share card to the group | Utility for opted-in "critical alerts" | Urgent |
| Ticket status changes | Push; WhatsApp only if the user is WhatsApp-only (no app) | Utility | Needed for WhatsApp-only residents |
| Technician arriving | WhatsApp utility | Yes | Time-sensitive, outside the app |
| Marketplace offers (phase 2) | **Push / in-app only** | **No** (marketing $0.0644) | 18× cost |
| Weekly building digest | Share card (admin posts) plus push | No | Free virality |

The rule engine runs per user and per event, based on: app installed?, push opt-in?, last-seen, quiet hours, role (owner / tenant / board / doorman).

---

## 9. Cost model per 1,000 buildings (ESTIMATE)

**Assumptions (ESTIMATE, reasoning given):**
- Average building of **30 flats**. Egyptian urban buildings commonly range from 10 to 60+ units, and compounds are larger.
- **1.5 accounts per flat**, giving **45,000 users** per 1,000 buildings.
- **50% WhatsApp-only** in year 1 (no app installed), so they get WhatsApp notifications. The other 50% use push.
- Each WhatsApp-only user receives 4 utility templates per month (dues reminder, receipt, two alerts): 22,500 × 4 = **90,000 utility messages**.
- Bot conversations: 30% of all users interact monthly, at about 6 bot replies each: 13,500 × 6 = **81,000 service replies**.
- Admin and treasurer bot use: 1,000 buildings × 2 admins × 30 replies = **60,000 service replies**.
- **One WABA phone number.** The 1,000 free service messages apply per number. Using several numbers (e.g. per governorate) adds 1,000 free each, but don't game this.
- Egypt rate $0.0036 for utility and service ([ArabyBot](https://arabybot.com/guides/whatsapp-api-pricing-egypt?lang=en)). VAT 14% added.
- LLM: Gemini 2.5 Flash-Lite at **$0.10/M input text, $0.30/M audio input, $0.40/M output** ([Google pricing](https://ai.google.dev/gemini-api/docs/pricing)). About 3,000 input and 400 output tokens per turn with tool context ≈ $0.00046 per turn. Use a stronger model for about 10% of hard turns at 10× the cost.

| Line item | Volume / month | Unit cost | Monthly USD |
|---|---|---|---|
| Utility templates (WhatsApp-only users) | 90,000 | $0.0036 | 324 |
| Service replies (residents + admins) | 141,000 − 1,000 free | $0.0036 | 504 |
| Marketing templates | 0 (by design) | $0.0644 | 0 |
| Subtotal Meta | | | 828 |
| VAT 14% (if applicable) | | | 116 |
| LLM turns (141k) | 141,000 | ~$0.00046 + 10% premium-model uplift | ~130 |
| Voice-note ASR (30% of turns, ~20 s, ~650 audio tokens) | ~42,000 | ~$0.0002 | ~10 |
| Receipt OCR (vision, ~15k receipts) | 15,000 | ~$0.0005 | ~8 |
| Chat-export parsing (onboarding about 100 new buildings a month, ~300k tokens each) | 30M tokens | $0.10–0.40/M | ~10 |
| Push notifications (FCM) | unlimited | free | 0 |
| BSP fee | Direct Cloud API | $0 | 0 |
| **Total** | | | **≈ $1,100 / month (≈ $1.10 per building, ≈ $0.024 per user)** |

**Sensitivity:**
- If the app-install share rises to 80% by year 2, utility volume falls about 60%, giving roughly **$750 per month**.
- If we sent **one marketing WhatsApp per user per month**, it would add 45,000 × $0.0644 = **$2,898 per month**, nearly 3× the whole budget. That confirms push-only marketing.

**Unofficial-route comparison (ESTIMATE):**
- Whapi at $25–35 per number per month. With one number per 20 groups that is 50 numbers ≈ **$1,250–1,750 per month** plus SIMs (~50 × 100 EGP).
- Self-hosted WAHA: free software, but about 2–4 VPS at $40–100 each ≈ **$150–400 per month**.
- Cheap in cash, but the expected cost of a ban wave (lost buildings and reputation) dominates.

**Phase-2 revenue lens:** at a 10% commission on an average home service of 500 EGP, one marketplace job brings in 50 EGP (about $0.90). **One job per building per month covers the entire WhatsApp and AI bill.**

---

## 10. Growth mechanics specific to this architecture (zero marketing budget)

1. **Admin-led onboarding:** the admin uploads the chat export → instant building dashboard (wow moment) → the app generates a group message "سجّل في عمارتنا: link" → residents tap → a WhatsApp chat with the bot opens, pre-filled with the building token → account created in 10 seconds.
2. **Every share card is an ad:** 1,000 buildings × ~20 cards per month × ~30 readers each = **ESTIMATE ~600k free impressions per month** inside high-trust groups.
3. **Neighbour pull:** the digest card ("12 of 30 flats paid ✅") creates social pressure on the rest to join and pay. This is a collection feature the treasurer loves.
4. **Technician loop:** technicians get booked through the bot → the technician receives a WhatsApp job card with "join as a verified technician" → supply side of the marketplace grows for free.
5. **Doorman as an agent:** the doorman uses the voice bot (no literacy barrier) → logs deliveries and water → residents get value without opening the app.
6. **Cross-building spread:** union presidents often manage or know neighbouring buildings. An "invite another building" card from the dashboard spreads it further.

---

## 11. Risks and mitigations summary

| Risk | Mitigation |
|---|---|
| Meta pricing changes again (it changes quarterly; Meta "may revise pricing up to once per quarter", [Business Today](https://www.businesstoday.in/technology/artificial-intelligence/story/whatsapp-introduces-token-based-pricing-for-ai-agents-from-august-1-540699-2026-07-03)) | Push-first routing engine. WhatsApp is a fallback with per-user cost caps. |
| AI-policy drift (scope of "ancillary") | Keep the bot narrowly scoped. Maintain a policy-review checklist. Watch Meta's terms page (last updated 23 Sep 2026). |
| BSUID / usernames hide phone numbers | Account linking by token or OTP. BSUID stored as a key. |
| Template rejection or category reclassification (utility → marketing) | Write strictly transactional utility templates. Never mix in offers. |
| Quality rating / messaging limits on our number | Opt-in only. Easy "stop". No cold outreach (the non-reply cap, [9to5Mac](https://9to5mac.com/2025/10/17/whatsapp-to-restrict-how-many-messages-users-can-send-without-replies/)). |
| PDPL licensing and consent (enforced about Nov 2026) | Register with the PDPC, minimize data, use an Egypt or approved-region data store, delete raw chat exports. |
| Meta AI commoditizes summaries | Differentiate on structured data: ledger, tickets, vendors, payments. |
| OBA not granted | Groups API is phase-2 only. Core works without it. |

---

## 12. Implementation roadmap

| Phase | Weeks | Deliverables |
|---|---|---|
| 0 | 0–2 | Meta Business verification, Cloud API number, display name, 6–10 utility templates in Arabic, privacy policy (PDPL) |
| 1 | 2–8 | 1:1 bot (text, voice, photo), account linking, tickets, dues and receipt OCR, payment links, share cards with deep-link web previews, forward-to-bot |
| 1.5 | 6–10 | Chat-export importer with AI building profile and vendor directory seeding; notification routing engine |
| 2 | 10–16 | In-app building chat with AI moderation; Flows forms; doorman voice mode |
| 3 | 16+ (after press/OBA) | Groups API board groups and per-job groups; marketplace commission flows; optional Telegram mode |

---

## 13. Open questions / not found

- **Exact Meta-official Egypt rate card (CSV)** was not retrieved. The figures above come from BSPs; verify them in WhatsApp Manager.
- **The 1 Oct 2026 service-message charge** is confirmed by several BSPs and Business Today. The Meta developer page I fetched did not yet show it.
- **Ban-rate data for unofficial group bots:** none public.
- **Official WhatsApp share of Egyptian smartphone users** (NTRA/GWI): not found.
- **Competitors Amarati / Imarti WhatsApp features:** their Play-Store pages could not be fetched in this session. See the competitor files.
- **WhatsApp Communities limits:** 1,024 per group is confirmed ([GSMArena](https://www.gsmarena.com/whatsapp_unveils_communities_feature_raises_group_limit_to_1024_participants-news-56392.php)). The 100 groups / 5,000 announcement-members figures were not verified from an official source.

---

## Sources (main)
- Meta Groups API: https://developers.facebook.com/docs/whatsapp/cloud-api/groups
- Meta Groups pricing: https://developers.facebook.com/docs/whatsapp/cloud-api/groups/pricing
- Meta pricing: https://developers.facebook.com/docs/whatsapp/pricing
- Meta changelog: https://developers.facebook.com/documentation/business-messaging/whatsapp/changelog
- Meta Terms for WhatsApp Business Platform (§4.7 AI Providers): https://www.facebook.com/legal/Meta-Terms-for-WhatsApp-Business-Platform
- WhatsApp ToS: https://www.whatsapp.com/legal/terms-of-service
- OBA: https://developers.facebook.com/documentation/business-messaging/whatsapp/official-business-accounts/
- BSUID: https://developers.facebook.com/documentation/business-messaging/whatsapp/business-scoped-user-ids
- Kapso Groups API 2026: https://kapso.com/blog/whatsapp-groups-api-state-2026
- Unipile Groups API: https://www.unipile.com/whatsapp-group-api/
- respond.io AI policy: https://respond.io/blog/whatsapp-general-purpose-chatbots-ban
- ArabyBot Egypt pricing: https://arabybot.com/guides/whatsapp-api-pricing-egypt?lang=en
- YCloud Oct 2026 update: https://www.ycloud.com/blog/whatsapp-api-message-pricing-update-effective-october-1-2026
- Business Today, Business Agent pricing: https://www.businesstoday.in/technology/artificial-intelligence/story/whatsapp-introduces-token-based-pricing-for-ai-agents-from-august-1-540699-2026-07-03
- TechCrunch, Business Agent global: https://www.techcrunch.com/2026/06/03/metas-ai-agent-for-whatsapp-business-is-now-available-globally/
- Zylos unofficial libraries: https://zylos.ai/research/2026-01-26-whatsapp-api-automation
- WAHA: https://waha.devlike.pro/ ; engines: https://waha.devlike.pro/docs/how-to/engines/
- Green-API tariffs: https://green-api.com/en/docs/about-tariffs/
- Whapi groups: https://whapi.cloud/whatsapp-groups-api ; pricing: https://support.whapi.cloud/help-desk/getting-started/pricing
- Telegram bot privacy mode: https://core.telegram.org/bots/features#privacy-mode
- DataReportal Egypt 2026: https://datareportal.com/reports/digital-2026-egypt
- Egypt PDPL regs: https://cms.law/en/are/legal-updates/egypt-s-pdpl-executive-regulations-issued-one-year-compliance-countdown-begins
- Sindia/CondoConta: https://www.sindiconet.com.br/informese/gestao-financeira-inteligencia-artificial-condominio-sindia-mercado-coluna-de-olho-no-mercado/amp
- Saknna: https://saknna.com
- Gemini pricing: https://ai.google.dev/gemini-api/docs/pricing
- WhatsApp payments countries: https://propakistani.pk/2026/08/25/whatsapps-online-payments-could-reach-more-countries-soon/
- WhatsApp group features Aug 2026: https://wabetainfo.com/whatsapp-announces-three-new-features-for-group-chats/
- WhatsApp India bans: https://businesstoday.in/technology/news/story/whatsapp-banned-97-million-indian-accounts-in-february-heres-why-470175-2025-04-01
- Non-reply message cap: https://9to5mac.com/2025/10/17/whatsapp-to-restrict-how-many-messages-users-can-send-without-replies/

---

## Verification log

Adversarial re-check, 12 Oct 2026. Each claim was re-fetched or re-searched independently.

| # | Claim | Verdict | Evidence URL |
|---|---|---|---|
| 1 | Groups API: max 8 participants, OBA-only, invite-link join, 10,000 groups per number | Confirmed | https://developers.facebook.com/docs/whatsapp/cloud-api/groups |
| 2 | Groups API announced in Meta changelog on 6 Oct 2025 | Confirmed | https://developers.facebook.com/documentation/business-messaging/whatsapp/changelog |
| 3 | Groups API non-supported types incl. "edit/delete, hiding participants" | Partly unverified (core list confirmed; those two items not in Meta's list) | https://developers.facebook.com/docs/whatsapp/cloud-api/groups |
| 4 | Group pricing: per delivered participant, one group-wide service window, free-form and in-window utility free, group utility not eligible for volume tiers | Confirmed (Meta page shows no Oct 2026 change yet) | https://developers.facebook.com/docs/whatsapp/cloud-api/groups/pricing |
| 5 | Egypt rates: marketing $0.0644, utility/auth $0.0036 | Confirmed (BSP figures; Meta CSV not retrieved) | https://arabybot.com/guides/whatsapp-api-pricing-egypt?lang=en |
| 6 | Egypt rate-change dates (auth 1 Feb 2025, auth-intl 1 Apr 2025, utility+auth 1 Oct 2025, marketing 1 Jan 2026) | Confirmed | https://developers.facebook.com/docs/whatsapp/pricing |
| 7 | From 1 Oct 2026 service messages billable, 1,000 free per number per month, in-window utility billable | Confirmed by BSPs and press; still **not shown** on Meta's pricing page | https://www.ycloud.com/blog/whatsapp-api-message-pricing-update-effective-october-1-2026 ; https://www.omanobserver.om/article/1197025/scitech/technology/met-to-charge-messages-on-whatsapp-business |
| 8 | AI Providers ban: "primary (rather than incidental or ancillary)" test; new users 15 Oct 2025, existing 15 Jan 2026; business-specific bots allowed | Confirmed | https://techcrunch.com/2025/10/18/whatssapp-changes-its-terms-to-bar-general-purpose-chatbots-from-its-platform ; https://respond.io/blog/whatsapp-general-purpose-chatbots-ban |
| 9 | Meta terms last updated 23 Sep 2026, section 4.7 | Unverified | https://www.whatsapp.com/legal/business-solution-terms/ |
| 10 | Meta Business Agent global 3 Jun 2026; $2 per 1M tokens from 1 Aug 2026; Meta "may revise pricing up to once every quarter" | Confirmed, nuance added (Premium-tier bundling per TechCrunch) | https://www.businesstoday.in/technology/artificial-intelligence/story/whatsapp-introduces-token-based-pricing-for-ai-agents-from-august-1-540699-2026-07-03 ; https://www.techcrunch.com/2026/06/03/metas-ai-agent-for-whatsapp-business-is-now-available-globally/ |
| 11 | WhatsApp Pay only in India, Brazil, Singapore, Mexico (not Egypt) | Confirmed (secondary sources only; no official list) | https://propakistani.pk/2026/08/25/whatsapps-online-payments-could-reach-more-countries-soon/ |
| 12 | Consumer WhatsApp groups up to 1,024 members | Confirmed | https://www.unipile.com/whatsapp-group-api/ |
| 13 | Whapi pricing $35 / $30 / $25 per number by tier; $29 annual | Confirmed | https://support.whapi.cloud/help-desk/getting-started/pricing |
| 14 | India bans: 9.7M accounts Feb 2025, 1.4M proactive; causes incl. bot automation and adding users without consent | Confirmed | https://businesstoday.in/technology/news/story/whatsapp-banned-97-million-indian-accounts-in-february-heres-why-470175-2025-04-01 |
| 15 | Egypt PDPL Executive Regulations (Decree 816/2025) issued 1 Nov 2025; one-year grace period to ~Nov 2026 | Confirmed | https://cms.law/en/are/legal-updates/egypt-s-pdpl-executive-regulations-issued-one-year-compliance-countdown-begins ; https://digitalpolicyalert.org/event/36521-executive-regulations-of-the-personal-data-protection-law-decision-no-816-of-2025-including-operational-license-requirement-entered-into-force |
| 16 | Gemini 2.5 Flash-Lite: $0.10 input, $0.30 audio, $0.40 output per 1M | Confirmed | https://ai.google.dev/gemini-api/docs/pricing |
| 17 | Telegram bots in privacy mode by default; admin bots receive all messages | Confirmed | https://core.telegram.org/bots/features#privacy-mode |
| 18 | WhatsApp chat export: up to 40,000 messages without media (10,000 with media) | Confirmed | https://dev.to/chattopdf/whatsapp-chat-export-complete-guide-iphone-android-zip-pdf-2026-10lo |
| 19 | Saknna: "Egypt/KSA", 450–7,500 EGP/month, 500+ buildings, anti-WhatsApp-group positioning | Corrected (serves 8 countries incl. UAE, Gulf states and Jordan; tier details added) | https://saknna.com |
| 20 | Exec-summary cost "$900–1,300/month" | Corrected (made consistent with §9: ≈$1,100 base, ≈$750 at 80% app install) | Internal arithmetic, §9 |

