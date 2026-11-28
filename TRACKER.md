# The Ceiling — Operating Tracker

**Rule:** archive stays free forever. Revenue sits beside it, never inside it.
**Cadence:** 1 page per night, 5 nights/week. Every page = HTML + data.json + homepage row + sitemap entry + IndexNow Action URL + 8-question FAQ schema.
**Ritual:** the streak counter is the only metric that matters at 11pm. Everything else is downstream.

---

## 1. Page Ledger

| # | API | Slug | Status | HTML date | data.json | Home row | Sitemap | Source checked | Notes |
|---|---|---|---|---|---|---|---|---|---|
| 1 | OpenAI | `openai` | ✅ live | 2026-11-04 | ✅ | ✅ | ⚠️ manual | platform.openai.com | 503 + ramp rule; 8-question schema |
| 2 | Anthropic | `anthropic` | ✅ live | 2026-11-08 | ✅ | ✅ | ⚠️ manual | platform.claude.com | spend-cap 429 is the differentiator; 8-question schema |
| 3 | Stripe | `stripe` | ✅ live | 2026-11-09 | ✅ | ✅ | ⚠️ manual | docs.stripe.com/rate-limits | Title rewritten 2026-11-28: names the trap (5 types of 429); 8-question schema |
| 4 | GitHub | `github` | ✅ live | 2026-11-10 | ✅ | ✅ | ⚠️ manual | docs.github.com | Title rewritten 2026-11-28: 403 = permission OR rate limit; 8-question schema |
| 5 | AWS S3 | `aws-s3` | ✅ live | 2026-11-11 | ✅ | ✅ | ⚠️ manual | docs.aws.amazon.com | No fixed ceiling; 503 SlowDown has no Retry-After; 8-question schema |
| 6 | Twilio | `twilio` | ✅ live | 2026-11-11 | ✅ | ✅ | ⚠️ manual | twilio.com/docs/api/errors | Concurrency, not rate; 8-question schema |
| 7 | Slack | `slack` | ✅ live | 2026-11-11 | ✅ | ✅ | ⚠️ manual | docs.slack.dev | Title rewritten 2026-11-28: names the trap (2025 change, 3,300× slower); 8-question schema |
| 8 | Discord | `discord` | ✅ live | 2026-11-11 | ✅ | ✅ | ⚠️ manual | docs.discord.com | 429 funds the ban; 8-question schema |
| 9 | SendGrid | `sendgrid` | ✅ live | 2026-11-12 | ✅ | ✅ | ⚠️ manual | twilio.com/docs/sendgrid | No published numeric table; IP warm-up is the real ceiling; 8-question schema |
| 10 | Firestore | `firestore` | ✅ live | 2026-11-28 | ✅ | ✅ | ⚠️ manual | firebase.google.com/docs/firestore/quotas | RESOURCE_EXHAUSTED has 2 meanings; hot-spot trap; 8-question schema |
| 11 | Vercel | `vercel` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | **next** — `X-RateLimit-*` returned as decimal strings |
| 12 | Supabase | `supabase` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | connection pooling per compute size |
| 13 | Cloudflare | `cloudflare` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | zone-wide plan inheritance |
| 14 | Firebase | `firebase` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | |
| 15 | Notion | `notion` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | |
| 16 | Airtable | `airtable` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | |
| 17 | Shopify | `shopify` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | leaky bucket |
| 18 | Auth0 | `auth0` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | |
| 19 | AWS Lambda | `aws-lambda` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | concurrency, not RPM |
| 20 | MongoDB Atlas | `mongodb-atlas` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | |
| 21 | Algolia | `algolia` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | |
| 22 | Mapbox | `mapbox` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | |
| 23 | Pinecone | `pinecone` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | |
| 24 | Replicate | `replicate` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | |
| 25 | Hugging Face | `huggingface` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | |
| 26 | Resend | `resend` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | |
| 27 | Linear | `linear` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | |
| 28 | Railway | `railway` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | |
| 29 | PlanetScale | `planetscale` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | |
| 30 | Coinbase | `coinbase` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | |

**Audit rule:** every page re-checked at 90 days. `last_verified` never ages past 90 days without a re-check, or the citation engine is lying.

**Sitemap column legend:** ✅ = in working sitemap · ⚠️ manual = indexed via GSC URL Inspection / Bing URL Submission / IndexNow (sitemap unavailable) · ⬜ = not yet indexed

---

## 2. Content Gate Checklist

**Every new page must pass all 12 before marking ✅ in the ledger.**

| # | Check | Where it lives |
|---|---|---|
| 1 | `<title>` contains the exact query format and the primary number | `<head>` |
| 2 | `<meta name="description">` — 140–160 characters, includes the number and the date | `<head>` |
| 3 | JSON-LD `FAQPage` present with `dateModified` matching visible date | `<head>` |
| 4 | Hero: number (huge), scope label, `Last verified: YYYY-MM-DD` | Above fold |
| 5 | Full table by tier/scope — no "contact sales" | Below fold |
| 6 | Error shapes — the actual JSON or XML, not a generic description | Below fold |
| 7 | Retry logic in code — honours whatever header that API sends | Below fold |
| 8 | One escape hatch — not "20 alternatives," one | Below fold |
| 9 | `{api}/data.json` at repo root, matches visible numbers | Folder |
| 10 | Answer block (40–60 words) under every `<h2>` | Between heading and table |
| 11 | **8-question FAQ schema** — 4 surface + 4 differentiator | `<head>` |
| 12 | **`.github/workflows/indexnow.yml` `urlList` updated** | `.github/workflows/` |

**The stranger test:** if a developer who hit a throttle landed here cold, could they copy the number and the retry snippet in under 15 seconds? If not, the page is not done.

---

## 3. Distribution Log

| Date | Channel | URL | Format | Result | Follow-up |
|---|---|---|---|---|---|
| 2026-11-05 | Dev.to | dev.to/apiceilings/i-built-a-cross-api-rate-limit-reference | "I built X" story | 1 technical comment (Karolis) | replied — TPM correction accepted, token-count fix committed |
| 2026-11-05 | HN Show HN | — | — | ⛔ blocked, new-account gate | silent until ~Nov 14, then comment-only |
| 2026-11-08 | GSC | search.google.com/search-console | manual URL Inspection × 3 | ✅ 3 pages queued | check Nov 15 |
| 2026-11-09 | GSC | search.google.com/search-console | manual URL Inspection — Stripe | ✅ queued | check Nov 15 |
| 2026-11-10 | GSC | search.google.com/search-console | manual URL Inspection — GitHub | ✅ queued | check Nov 15 |
| 2026-11-11 | GSC | search.google.com/search-console | manual URL Inspection — AWS S3 | ✅ queued | check Nov 15 |
| 2026-11-11 | Bing | bing.com/webmasters | Import from GSC → verified | ✅ Site added | sitemap submitted |
| 2026-11-11 | Bing | bing.com/webmasters → Sitemaps | sitemap2.xml | ✅ Success, 8 URLs | check AI Performance Nov 22 |
| 2026-11-11 | Bing | bing.com/webmasters → URL Submission | 9 URLs | ✅ 9/9 accepted | automated via IndexNow |
| 2026-11-11 | IndexNow | api.indexnow.org + GitHub Action | 9 URLs manual + auto on push | ✅ HTTP 200 / run success | permanent |
| 2026-11-11 | HN | news.ycombinator.com | 3 threads read, 2 comments | ✅ no self-promotion | unlock ~Nov 14 |
| 2026-11-11 | Perplexity (baseline) | perplexity.ai | "Stripe API rate limit" | ⚠️ not cited | expected at day 7 |
| 2026-11-12 | GSC | search.google.com/search-console | manual URL Inspection — SendGrid | ✅ queued | check Nov 22 |
| 2026-11-12 | Bing | bing.com/webmasters → URL Inspection | sendgrid.html | ✅ indexable | check AI Performance Nov 22 |
| 2026-11-12 | Schema.org Validator | validator.schema.org | sendgrid.html | ✅ 0 errors, 8 FAQ items | all 9 pages validated |
| 2026-11-28 | GSC | search.google.com/search-console | Performance report Nov 7–25 | ✅ **2,305 impressions, 22 clicks, 0.95% CTR** | first real traffic signal |
| 2026-11-28 | Title rewrites | stripe / slack / github HTML `<title>` | Trap-name pattern | ✅ applied | watch CTR improvement next 2 weeks |
| 2026-11-28 | Firestore page | firestore.html | Page 10 live | ✅ RESOURCE_EXHAUSTED 2-variant trap | cadence resumed after 14-day gap |
| **2026-11-28** | **LibHunt** | **libhunt.com/r/theceiling** | **Free, open source, MIT** | ✅ **LIVE — auto-approved** | **DR 66 dofollow backlink; Activity score 9.1; already in 7 alternatives lists (FaviconDL, zeal, aws-security-cards, http-status-explorer, opensource.guide, InternalSteamWebAPI, slideops)** |

---

## 4. Distribution Calendar

| Week of | Channel | Gate to submit | Status |
|---|---|---|---|
| Nov 9–15 | HN participation, `llms.txt`, IndexNow, meta descriptions, FAQ schema | — | ✅ done |
| Nov 28 | LibHunt | any | ✅ **LIVE — first external link** |
| Nov 29 | Indie Hackers (DR 79) | any | ⬜ **use `hello@egoecho.cloud` for account email** |
| Nov 30 | PeerPush (DR 71) | any | ⬜ backend email only |
| Dec 1 | Twelve Tools (DR 84) | any | ⬜ ~72h approval |
| Dec 2 | Turbo0 (DR 81) | any | ⬜ ~2 weeks |
| Dec 2 | Fazier + Startup Fame | needs footer badge | ⬜ badge commit first |
| Dec 5 | **GSC Links report check** | 7 days after LibHunt | ⬜ verify backlink crawled |
| Dec 2–8 | Vercel page (11) + r/LocalLLaMA post | 11 pages | ⬜ |
| Dec 8–14 | Supabase page (12) + HN regular submission | 12 pages + 3 HN comments | ⬜ |
| Dec 15–21 | Cloudflare page (13) + r/SaaS post | 13 pages | ⬜ |
| Dec 22–28 | Firebase page (14) + Product Hunt prep | 14 pages | ⬜ |

**Recurring maintenance — every new page:**
- Add URL to `.github/workflows/indexnow.yml` `urlList` (#12)
- Add URL to `sitemap2.xml`
- Add row to `index.html`
- Add entry to `llms.txt`
- Submit via GSC URL Inspection
- Submit via Bing URL Inspection
- Validate schema on validator.schema.org

**Directories remaining (6):** Indie Hackers, PeerPush, Twelve Tools, Turbo0, Fazier, Startup Fame. All free. 5 confirmed dofollow, 1 conditional (Unee).

**Directories skipped:** SaaSHub (nofollow without domain email), Peerlist (nofollow), Tiny Startups (dofollow paid-only), BetaList (free tier removed 2026), DevHunt (free queue ~2031, $49 paid alternative deferred).

---

## 5. Weekly Signals

| Week ending | Pages live | GSC impressions | GSC clicks | CTR | Perplexity citation? | External links | Notes |
|---|---|---|---|---|---|---|---|
| 2026-11-15 | 9 | — | — | — | N / N / N | 0 | 9 pages by Nov 12. GSC sitemap unresolved (Content-Type bug). Bing verified via GSC import, sitemap + 9 URLs submitted, IndexNow GitHub Action live. All meta descriptions 145–155 chars. All 9 pages 8-question FAQ schema (72 Q&A pairs). HN: 2 comments, no self-promo. |
| 2026-11-22 | 9 | 2,305 | 22 | 0.95% | N / N / N | 0 | First real traffic signal. SendGrid leads CTR at 2.31% (title names the trap). Stripe 92 imp / 0 clicks at position 6-9 (biggest opportunity). GitHub differentiator queries at position 46-48. Organic pace ≈ 130 imp/day → on track for 5K by mid-December. |
| 2026-11-28 | 10 | 2,305 | 22 | 0.95% | N / N / N | **1** | **LibHunt live — DR 66 dofollow, first external link.** Day 90 criterion 2 (external links ≥ 1) → RESOLVED. Firestore page 10 live after 14-day gap. Title rewrites applied to Stripe, Slack, GitHub. Activity score 9.1 on LibHunt. |
| 2026-11-29 | | | | | | | |
| 2026-12-06 | | | | | | | |
| 2026-12-13 | | | | | | | |
| 2026-12-20 | | | | | | | |
| 2026-12-27 | | | | | | | |
| **2027-02-06** | **Day 90 kill check** | **≥ 5,000 organic?** | | | **any citation?** | **≥ 1?** | **verdict: continue / stop** |

**How to check Perplexity citation:** ask `"Stripe API rate limit"` verbatim, look at the citation list. Screenshot. Y/N. Once a week, 3 queries, 2 minutes.

**How to check Bing AI Performance:** Bing Webmaster Tools → AI Performance (BETA). Copilot and Bing AI summary citations with Citation Share.

**How to check ChatGPT citation:** ask "Stripe API rate limit" in ChatGPT with web search on. Look at Sources. Y/N.

**CTR benchmark from GSC data (Nov 7–25):**
- SendGrid (trap-name title): **2.31%**
- OpenAI (trap-name title): **2.38%**
- Anthropic (trap-name title): **2.50%**
- Slack (give-the-answer title, pre-rewrite): **0.65%**
- Stripe (give-the-answer title, pre-rewrite): **0.51%**
- GitHub (give-the-answer title, pre-rewrite): **0.59%**
- **Pattern: trap-name titles average 2.4% CTR; give-the-answer titles average 0.58% (4× difference)**

---

## 6. Sponsor Pipeline

**Gate to start:** 30 pages + one real traffic month. Traffic month active (Nov 7–25). Pages are the blocker (10/30).

| Company | Why them | Contact person | Contact role | Sent | Reply | Status |
|---|---|---|---|---|---|---|
| Svix | webhook infra, adjacent | — | — | — | — | ⬜ pre-gate |
| Standard Webhooks | open standard | — | — | — | — | ⬜ pre-gate |
| Hookdeck | webhook relay | — | — | — | — | ⬜ pre-gate |
| Sentry | error monitoring | — | — | — | — | ⬜ pre-gate |
| Datadog | observability | — | — | — | — | ⬜ pre-gate |
| Bearer | API monitoring | — | — | — | — | ⬜ pre-gate |
| Postman | API tooling | — | — | — | — | ⬜ pre-gate |
| Kong | API gateway | — | — | — | — | ⬜ pre-gate |
| Apigee (Google) | API gateway | — | — | — | — | ⬜ pre-gate |
| ReadMe | API documentation | — | — | — | — | ⬜ pre-gate |

**The email template** (once gate is met): names their problem in their language, names their product, removes risk with "payment after first month," ends with a single hook. 143 words. Subject: `Your tool should be the answer to "hit rate limit"`.

---

## 7. Infrastructure Blockers

| Date found | Issue | Workaround | Permanent fix | Status |
|---|---|---|---|---|
| 2026-11-08 | GSC "Could not be read" — GitHub Pages Content-Type bug | Manual URL Inspection per page | Custom domain (Day 60) | ⚠️ active |
| 2026-11-08 | `robots2.txt` inert at project path | Accept; sitemap + manual indexing | Custom domain (Day 60) | ⚠️ active |
| — | No crawler analytics on GitHub Pages | GSC + Bing are the only signals | Cloudflare Pages (Day 60) | ⚠️ active |
| 2026-11-11 | Open Graph tags missing on all sub-pages | Homepage complete; sub-pages pending | Roll out on next verification pass | ⚠️ active |
| 2026-11-28 | Page cadence stalled Nov 12→28 (14 days) | Firestore shipped 2026-11-28 | — | ✅ resolved 2026-11-28 |
| 2026-11-28 | Directory listings never shipped (Week 1 & 2 gap) | LibHunt live 2026-11-28 | 6 more this week | 🔄 in progress |
| 2026-11-28 | LibHunt account tied to personal email shekarconnect2@gmail.com | Exemption granted — public profile shows only Api-Ceilings | Assess case-by-case where email is user-visible (IH, Peerlist) | ⚠️ accepted risk |

---

## 8. Corrections Log

| Date | Page | What was reported | By | Verdict | Action taken |
|---|---|---|---|---|---|
| 2026-11-05 | openai.html | TPM vs `Retry-After` — request bigger than remaining budget fails regardless of wait | Karolis (Dev.to) | ✅ valid, page gap | Reply accepted; token-count check added |

---

## 9. Monetization Gates

| Rung | Gate | Status | Notes |
|---|---|---|---|
| 1. Sponsored line | 30 pages + one real traffic month | ⬜ | traffic month active; 20 more pages needed |
| 2. Change alerts | 60 pages + change-detection | ⬜ | loss-aversion product |
| 3. MCP / API tier | 100 pages + MCP prototype | ⬜ | `last_verified_at` in every response |
| 4. Data licensing | 12 months of dated history | ⬜ | only rung that appreciates with age |
| — | First sponsor email | ⬜ | 20 named companies |

**Frozen rule:** no newsletter, no cookie banner, no hero image, no "premium" tag, no related-articles block, no share widget.

---

## 10. Streak

| Week | Mon | Tue | Wed | Thu | Fri | Sat | Sun | Pages this week |
|---|---|---|---|---|---|---|---|---|
| Nov 9–15 | ✅ | ✅ | ✅ | ✅ | ⬜ | ⬜ | ⬜ | 7 |
| Nov 16–22 | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | 0 |
| Nov 23–29 | ⬜ | ⬜ | ⬜ | ⬜ | ✅ | ⬜ | ⬜ | 1 (Firestore) |

**Honest note:** 14 consecutive nights with zero pages between Nov 13–27. Firestore broke the silence Nov 28. Next test is whether Vercel (page 11) ships before Dec 2, or whether the gap repeats.

**If two ❌ in one week:** stop the cadence, write down why in Decisions, restart at one page.

---

## 11. Decisions (append-only — never delete)

| Date | Decision | Reason |
|---|---|---|
| 2026-11-05 | Archive free forever | Paywalling kills citation, ranking, trust |
| 2026-11-08 | Migrate to Cloudflare Pages at ~Day 60 | GitHub Pages gives zero crawler analytics |
| 2026-11-08 | Moat = provenance + freshness discipline, not page volume | AI can generate volume; it cannot keep dated lines honest |
| 2026-11-09 | Stripe page live — five-way 429 diagnostic | `Stripe-Rate-Limited-Reason` distinguishes 5 rate limits |
| 2026-11-10 | GitHub page live — 403 disambiguation | GitHub returns 403 for both permission and rate limit |
| 2026-11-11 | AWS S3 / Twilio / Slack / Discord pages live | Each adds a distinct trap |
| 2026-11-11 | Answer blocks under every `<h2>` | Princeton/IIT-Delhi: up to 40% lift in AI visibility |
| 2026-11-11 | `llms.txt` shipped | Coding agents, not search |
| 2026-11-11 | Bing verified via GSC import | XML and meta tag both returned Bing-side "Unexpected error" |
| 2026-11-11 | IndexNow via GitHub Action | CORS blocks fetch; Action on push = permanent automation |
| 2026-11-11 | FAQ schema expanded to 8 questions | 4 surface + 4 differentiator |
| 2026-11-12 | SendGrid: no published numeric table + IP warm-up | The real ceiling is warm-up |
| 2026-11-28 | Firestore: RESOURCE_EXHAUSTED has 2 meanings | One resets midnight Pacific, one scales in minutes |
| 2026-11-28 | Title rewrites: Stripe, Slack, GitHub | GSC proves trap-name titles 2.4% CTR vs 0.58% |
| 2026-11-28 | Viral mechanic = docs-led growth, not social | The loop is 429 → search exact error → land on page → fix → bookmark → return → tell colleague |
| 2026-11-28 | LibHunt submitted (MIT LICENSE + personal email exemption) | LibHunt is open-source-only and rejects unlicensed projects. MIT added; submitted with name "The Ceiling", 6 topics, HTML language, 51-word description. Expected approval 1-3 days. First confirmed dofollow backlink attempt. |
| 2026-11-28 | LibHunt approved automatically — first external link | Day 90 criterion 2 (external links ≥ 1) resolved. DR 66 backlink live. Auto-approval signal: complete topics (6), MIT LICENSE, 51-word description. Copy this pattern for remaining 6 directories. Do not suggest an "alternative" on LibHunt — creates outbound links, not backlinks. |

---

## 12. Monetization Sprint (Nov 28 → Dec 19)

**The gap:** 10 pages vs 30 required. Traffic month is active. 20 pages in 21 days = 1 page per night for 20 nights. Achievable but tight.

**Week of Nov 28 – Dec 2 — Foundation**

| Day | Action | Metric |
|---|---|---|
| Fri Nov 28 | ✅ Firestore (page 10) + ✅ title rewrites + ✅ LibHunt | 3 wins |
| Sat Nov 29 | Indie Hackers (use `hello@egoecho.cloud`) | 1 listing live |
| Sun Nov 30 | Vercel page (11) + PeerPush | page + listing |
| Mon Dec 1 | Twelve Tools + check LibHunt page for mentions | 1 listing |
| Tue Dec 2 | Supabase page (12) + Turbo0 | page + listing |

**Week of Dec 3 – 9 — Compound**

| Day | Action | Metric |
|---|---|---|
| Wed Dec 3 | Cloudflare page (13) + Fazier (badge commit) | page + listing |
| Thu Dec 4 | Startup Fame (badge commit) | 1 listing |
| Fri Dec 5 | **GSC Links check** — LibHunt backlink crawled? | Y/N |
| Sat Dec 6 | Firebase page (14) + r/LocalLLaMA post | page + post |
| Sun Dec 7 | Notion page (15) + r/webdev Showoff Saturday | page + post |
| Mon Dec 8 | **Day 30 check** — 15 pages? Impressions growing? | verdict |

**Week of Dec 10 – 16 — Push**

| Day | Action | Metric |
|---|---|---|
| Dec 10–16 | 1 page/night: Airtable (16), Shopify (17), Auth0 (18), AWS Lambda (19), MongoDB Atlas (20), Algolia (21), Mapbox (22) | 7 pages |
| Dec 13 | r/SaaS founder story post | 1 post |
| Dec 15 | **Second Perplexity check** — has anything changed? | Y/N |

**Week of Dec 17 – 23 — Hit 30**

| Day | Action | Metric |
|---|---|---|
| Dec 17–23 | 1 page/night: Pinecone (23), Replicate (24), HuggingFace (25), Resend (26), Linear (27), Railway (28), PlanetScale (29) | 7 pages |
| **Dec 19** | **30 pages live — monetization gate page requirement met** | milestone |

**Kill criteria for the sprint:**
- If by **Dec 15** the archive has **<500 cumulative impressions**: pain-search volume problem. Reconsider API selection (add AI-only APIs with rising volume).
- If by **Dec 15** the archive has **>500 impressions but 0 clicks**: SERP snippet problem. Rewrite titles to lead with the trap-name.
- If by **Dec 19** the archive has **<25 pages**: cadence is dead. Stop, log why in Decisions, do not try to catch up.

**The psychology of the sprint:** the archive has been built by a founder who understands the pain. The sprint assumes 1 page per night + 1 directory per day. That's the actual cost of turning the reference into a business. The distribution is now the same importance as the pages.
