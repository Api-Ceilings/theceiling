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
| 3 | Stripe | `stripe` | ✅ live | 2026-11-09 | ✅ | ✅ | ⚠️ manual | docs.stripe.com/rate-limits | Five 429s by header; 8-question schema |
| 4 | GitHub | `github` | ✅ live | 2026-11-10 | ✅ | ✅ | ⚠️ manual | docs.github.com | 403 is both permission and rate limit; 8-question schema |
| 5 | AWS S3 | `aws-s3` | ✅ live | 2026-11-11 | ✅ | ✅ | ⚠️ manual | docs.aws.amazon.com | No fixed ceiling; 503 SlowDown has no Retry-After; 8-question schema |
| 6 | Twilio | `twilio` | ✅ live | 2026-11-11 | ✅ | ✅ | ⚠️ manual | twilio.com/docs/api/errors | Concurrency, not rate; 8-question schema |
| 7 | Slack | `slack` | ✅ live | 2026-11-11 | ✅ | ✅ | ⚠️ manual | docs.slack.dev | Per-method per-workspace; 8-question schema |
| 8 | Discord | `discord` | ✅ live | 2026-11-11 | ✅ | ✅ | ⚠️ manual | docs.discord.com | 429 funds the ban; 8-question schema |
| 9 | SendGrid | `sendgrid` | ✅ live | 2026-11-12 | ✅ | ✅ | ⚠️ manual | twilio.com/docs/sendgrid | No published numeric table; IP warm-up is the real ceiling; 8-question schema; validated 0 errors |
| 10 | Google Firestore | `firestore` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | **next** |
| 11 | Vercel | `vercel` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | |
| 12 | Supabase | `supabase` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | |
| 13 | Cloudflare | `cloudflare` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | |
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

**Every new page must pass all 12 before marking ✅ in the ledger.** This is the anti-thinness gate — the failure mode that kills citation.

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
| 10 | Answer block (40–60 words) under every `<h2>` — for AI citation | Between heading and table |
| 11 | **8-question FAQ schema** — 4 surface + 4 differentiator, all matching visible content | `<head>` |
| 12 | **`.github/workflows/indexnow.yml` `urlList` updated with the new URL** | `.github/workflows/` |

**The stranger test:** if a developer who hit a throttle landed here cold, could they copy the number and the retry snippet in under 15 seconds? If not, the page is not done.

---

## 3. Distribution Log (what already happened)

| Date | Channel | URL | Format | Result | Follow-up |
|---|---|---|---|---|---|
| 2026-11-05 | Dev.to | dev.to/apiceilings/i-built-a-cross-api-rate-limit-reference | "I built X" story | 1 technical comment (Karolis) | replied — TPM correction accepted |
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

---

## 4. Distribution Calendar (what's next)

**Rule:** one channel per week. Never two links to the archive in one thread. Never mention the archive in an HN comment unless directly asked.

| Week of | Channel | Format | Gate to submit | Status |
|---|---|---|---|---|
| Nov 9–15 | HN participation only | comments | 2 comments by Nov 12 | ✅ done 2026-11-11 |
| Nov 9–15 | `llms.txt` | index + dates | none | ✅ done 2026-11-11 |
| Nov 9–15 | IndexNow | key + API | any week | ✅ done 2026-11-11 |
| Nov 9–15 | Meta descriptions | 140-160 chars | Bing threshold | ✅ done 2026-11-11 |
| Nov 9–15 | FAQ schema | 8 questions/page | schema valid | ✅ done 2026-11-11 (all 8 pages) |
| Nov 16–22 | DevHunt | directory | 10 pages | ⬜ |
| Nov 16–22 | LibHunt | directory | 10 pages | ⬜ |
| Nov 16–22 | Indie Hackers | founder story | 10 pages | ⬜ |
| Nov 16–22 | r/webdev Showoff Saturday | launch thread | 10 pages | ⬜ |
| Nov 23–29 | r/LocalLLaMA | AI angle | 15 pages | ⬜ |
| Nov 23–29 | HN regular submission | one page, NOT Show HN | 20 pages + 3 comments | ⬜ |
| Dec 1–7 | r/SaaS | founder angle | 25 pages | ⬜ |
| Dec 1–7 | r/devops | infra angle | 25 pages | ⬜ |
| Dec 8–14 | Product Hunt | full launch | 30 pages + custom domain | ⬜ |
| Dec 15+ | Twitter/X or Bluesky | thread | first citation | ⬜ |

**Recurring maintenance — every new page:**
- Add URL to `.github/workflows/indexnow.yml` `urlList` (Content Gate #12)
- Add URL to `sitemap2.xml`
- Add row to `index.html`
- Add entry to `llms.txt`
- Submit URL via Bing URL Inspection once for the fast lane (optional)
- Validate schema on validator.schema.org
- Submit via GSC URL Inspection

**Channels deliberately NOT on this list:** LinkedIn (wrong audience), email cold outreach (kills the domain), Discord cold-posting (bans), Stack Overflow answers (only when directly relevant, never as promotion).

---

## 5. Weekly Signals (fill every Sunday, once)

| Week ending | Pages live | GSC impressions | GSC clicks | Perplexity citation? (OpenAI / Stripe / GitHub) | External links | Notes |
|---|---|---|---|---|---|---|
| 2026-11-15 | 9 | — | — | N / N / N | 0 | 9 pages by Nov 12. GSC sitemap unresolved (Content-Type bug). Bing verified via GSC import, sitemap + 9 URLs submitted, IndexNow GitHub Action live. All meta descriptions 145–155 chars. **All 9 pages have 8-question FAQ schema (72 Q&A pairs, validated 0 errors).** HN: 2 comments, no self-promo. Perplexity baseline 2026-11-11: not cited; expected at day 7. SendGrid adds the "no published numeric table + IP warm-up" differentiator. |
| 2026-11-22 | | | | | | |
| 2026-11-29 | | | | | | |
| 2026-12-06 | | | | | | |
| 2026-12-13 | | | | | | |
| 2026-12-20 | | | | | | |
| 2026-12-27 | | | | | | |
| **2027-02-06** | **Day 90 kill check** | **≥ 5,000 organic?** | | **any citation?** | **≥ 1?** | **verdict: continue / stop** |

**How to check Perplexity citation:** ask it `"Stripe API rate limit"` verbatim, look at the citation list. Screenshot. Y/N. Once a week, 3 queries, 2 minutes.

**How to check Bing AI Performance:** Bing Webmaster Tools → AI Performance (BETA). Shows Copilot and Bing AI summary citations with Citation Share. Data appears ~48h after first crawl. Check Nov 22.

**How to check ChatGPT citation:** ask "Stripe API rate limit" in ChatGPT with web search on. Look at Sources. Y/N.

---

## 6. Sponsor Pipeline

**Gate to start:** 30 pages **and** one real traffic month. Before that, this section stays empty. Filling it early is founder impatience.

**Rule:** named individuals only. Never `info@`, `sales@`, or a generic contact form. LinkedIn search takes 3 minutes per name.

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

## 7. Infrastructure Blockers (running list)

| Date found | Issue | Workaround | Permanent fix | Status |
|---|---|---|---|---|
| 2026-11-08 | GSC "Couldn't fetch" — sitemap inside `openai/` | Moved to repo root | Done | ✅ resolved |
| 2026-11-08 | GSC "Could not be read" — GitHub Pages Content-Type bug | Manual URL Inspection per page | Custom domain (Day 60) | ⚠️ active |
| 2026-11-08 | `raw.githubusercontent.com` sitemap rejected — prefix-locked | None — cross-host impossible | Custom domain (Day 60) | ⚠️ active |
| 2026-11-08 | `robots2.txt` inert at project path | Accept; sitemap + manual indexing | Custom domain (Day 60) | ⚠️ active |
| — | No crawler analytics on GitHub Pages | GSC + Bing are the only signals | Cloudflare Pages (Day 60) | ⚠️ active |
| 2026-11-11 | Bing "Unexpected error" on XML/meta verification | Bypassed via GSC import | None needed | ✅ resolved |
| 2026-11-11 | Bing meta descriptions >160 chars | All 9 pages 145–155 chars | — | ✅ resolved |
| 2026-11-11 | IndexNow CORS blocks browser fetch | Browser GET + GitHub Action | — | ✅ resolved |
| 2026-11-12 | **Open Graph tags missing on all pages** — every share shows raw URL | Added to homepage; sub-pages pending | Roll out on next verification pass | ⚠️ active |

---

## 8. Corrections Log

| Date | Page | What was reported | By | Verdict | Action taken |
|---|---|---|---|---|---|
| 2026-11-05 | openai.html | TPM vs `Retry-After` — request bigger than remaining budget fails regardless of wait | Karolis (Dev.to) | ✅ valid, page gap | Reply accepted; token-count check added |
| | | | | | |

---

## 9. Monetization Gates

| Rung | Gate | Status | Notes |
|---|---|---|---|
| 1. Sponsored line | 30 pages + one real traffic month | ⬜ | one vendor per category, below content |
| 2. Change alerts | 60 pages + change-detection | ⬜ | loss-aversion product |
| 3. MCP / API tier | 100 pages + MCP prototype | ⬜ | `last_verified_at` in every response |
| 4. Data licensing | 12 months of dated history | ⬜ | only rung that appreciates with age |
| — | First sponsor email | ⬜ | 20 named companies, no `info@`/`sales@` |

**Frozen rule:** no newsletter, no cookie banner, no hero image, no "premium" tag, no related-articles block, no share widget. Any one of these inverts the citation signal.

---

## 10. Streak

**The only metric that matters at 11 PM is whether a page went live tonight.**

| Week | Mon | Tue | Wed | Thu | Fri | Sat | Sun | Pages this week |
|---|---|---|---|---|---|---|---|---|
| Nov 9–15 | ✅ | ✅ | ✅ | ✅ | | | | 7 |

**Rules:** ✅ = night a page went live · 🔄 = audit/verification · ⬜ = skipped · ❌ = broke the pattern (two in a row)

**Honest note on this week:** Mon Stripe, Tue GitHub, Wed AWS S3 + Twilio + Slack + Discord (4 pages in one session), Thu SendGrid. That is **4 nights, 7 pages.** The checkmark counts nights, not pages. Wednesday was a batch night, which is the pattern the tracker warns against — the test is whether Fri–Sun produce zero pages or one more.

**If two ❌ in one week:** stop the cadence, write down why in Decisions, restart at one page. Do not try to catch up.

---

## 11. Decisions (append-only — never delete)

| Date | Decision | Reason |
|---|---|---|
| 2026-11-05 | Archive free forever | Paywalling kills citation, ranking, trust |
| 2026-11-08 | Canonical sitemap = `sitemap2.xml` | Original diagnosis: CDN negative cache. **Superseded.** |
| 2026-11-08 | `robots2.txt` stays at project path, inert | Crawlers read host-root robots only |
| 2026-11-08 | Migrate to Cloudflare Pages at ~Day 60 | GitHub Pages gives zero crawler analytics |
| 2026-11-08 | Moat = provenance + freshness discipline, not page volume | AI can generate volume; it cannot keep dated lines honest |
| 2026-11-08 | Correction: "Couldn't fetch" was file location, not CDN cache | `robots2.txt` and `sitemap2.xml` were inside `openai/` |
| 2026-11-08 | Sitemap abandoned on github.io project path | GitHub Pages Content-Type bug; Bing accepts same file; GSC field prefix-locked |
| 2026-11-08 | Manual URL Inspection is the indexing method until Day 60 | Correct tool for <20 pages |
| 2026-11-09 | Stripe page live — five-way 429 diagnostic | `Stripe-Rate-Limited-Reason` distinguishes 5 rate limits |
| 2026-11-10 | GitHub page live — 403 disambiguation | GitHub returns 403 for both permission and rate limit |
| 2026-11-11 | AWS S3 page live — no-fixed-ceiling model | Per-prefix limit, unbounded aggregate; 503 SlowDown has no Retry-After |
| 2026-11-11 | Twilio page live — concurrency, not rate | Fix is fewer connections, not longer backoff |
| 2026-11-11 | Slack page live — per-method, distribution-dependent | Same method has three limits depending on distribution |
| 2026-11-11 | Discord page live — the retry is the failure | 429 counts toward a 10K/10min Cloudflare ban; shared-scope exempt |
| 2026-11-11 | Answer blocks under every `<h2>` | Princeton/IIT-Delhi: statistics, quotations, citations lift AI visibility up to 40%; answer block is the RAG chunk |
| 2026-11-11 | `llms.txt` shipped | 97% of llms.txt files get zero requests; purpose is coding agents, not search |
| 2026-11-11 | Bing verified via GSC import | XML and meta tag both returned Bing-side "Unexpected error" |
| 2026-11-11 | Meta description standard = 140–160 chars | Bing flags >160; all pages compliant |
| 2026-11-11 | IndexNow via browser GET + GitHub Action | CORS blocks fetch; Action on push = permanent automation |
| 2026-11-11 | Positioning: deeper question, not surface summary | Perplexity's Stripe answer had 4 categories; ours has 5 |
| 2026-11-11 | FAQ schema expanded to 8 questions on all 8 pages | 4 surface + 4 differentiator; 64 Q&A pairs; validated 0 errors |
| 2026-11-12 | SendGrid page live — no published numeric table + IP warm-up | SendGrid is the only API here that publishes no per-endpoint number; the real ceiling is daily warm-up volume, not 10,000 req/sec |
| 2026-11-12 | Monetization alignment check | 9 pages is ahead of cadence; 0 traffic and 0 citations are expected but unproven. Monetization gate is 30 pages + one real traffic month, so revenue is structurally impossible before mid-December. Next 3 weeks must weight distribution as heavily as page count |
| 2026-11-12 | Added §12 Monetization Sprint — 3-week execution plan | Tracker acknowledged distribution was the bottleneck but had no concrete plan. Sprint maps specific days, channels, and metrics to close the gap |
| 2026-11-12 | Open Graph + Twitter Card tags added to homepage | Every share of every page shows a raw URL. Adding OG tags is the highest-ROI marketing change available (2-3× share CTR). Roll out to sub-pages on next verification pass |

---

## 12. Monetization Sprint (Nov 12 → Dec 2)

**The gap between 9 pages and the gate.** Gate is: 30 pages **and** one real traffic month. We are at 9 pages, 0 traffic, 0 citations. The next 3 weeks must weight distribution as heavily as page production. Below is the concrete plan — specific days, specific actions, specific metrics.

**Why this exists:** the alignment check in §11 named the bottleneck. Without a plan against it, "wait for organic" happens. With this plan, every action has a date and a metric. That is what turns a project into a business.

**Week 1 (Nov 12–18) — Foundation & First Signal**

| Day | Action | Metric to watch |
|---|---|---|
| Tue Nov 12 | ✅ SendGrid ships (9 pages) | Page 9 live |
| Wed Nov 13 | Firestore page (10 pages) — 1–2 hrs | Page 10 live |
| Thu Nov 14 | Submit to DevHunt + LibHunt (2 directories in one sitting) | 2 listings live |
| Fri Nov 15 | Indie Hackers post — "I built a cross-API rate limit reference. 10 pages in. Here's what I learned." | 1 post live |
| Sat Nov 16 | r/webdev Showoff Saturday — link to Stripe page, not homepage | 1 post live |
| Sun Nov 17 | **GSC status check** — first real impressions? | Impression count |

**Week 2 (Nov 18–25) — Second Signal Push**

| Day | Action | Metric to watch |
|---|---|---|
| Mon Nov 18 | Vercel page (11 pages) | Page 11 live |
| Tue Nov 19 | r/LocalLLaMA — AI APIs angle (OpenAI vs Anthropic vs OpenAI diff) | 1 post live |
| Wed Nov 20 | **First Perplexity citation check** — target: "Why does my Stripe 429 have no Stripe-Rate-Limited-Reason header?" | Y / N |
| Thu Nov 21 | Supabase page (12 pages) | Page 12 live |
| Fri Nov 22 | **Bing AI Performance check** — first Copilot citation? | Y / N |
| Sat Nov 23 | r/SaaS founder story post | 1 post live |
| Sun Nov 24 | Second GSC check — impressions growing? | Number vs Nov 17 |

**Week 3 (Nov 25–Dec 2) — Distribution Compound**

| Day | Action | Metric to watch |
|---|---|---|
| Mon Nov 25 | Cloudflare page (13 pages) | Page 13 live |
| Tue Nov 26 | r/devops — rate-limit infra angle | 1 post live |
| Wed Nov 27 | HN regular submission — link to Stripe page (needs 3+ comments of history) | Y / N |
| Thu Nov 28 | Firebase page (14 pages) | Page 14 live |
| Fri Nov 29 | Product Hunt prep — assets, tagline, first comment draft | Prep done |
| Sat Nov 30 | **First traffic month check** — if 0 impressions AND 0 external links, escalate | Go / No-go for PH |
| Sun Dec 1 | **Decision point**: continue cadence or accelerate Cloudflare migration | Decision logged |

**Kill criteria for the sprint:**
- If by **Nov 30** GSC shows **0 impressions AND 0 external links**: escalate — do not wait for Day 60. Migrate to Cloudflare Pages in Week 4, then retry distribution.
- If by **Dec 15** the archive has **<500 cumulative impressions**: the pain-search volume is the problem, not the copy. Reconsider API selection — maybe add AI-only APIs (Pinecone, Replicate, HuggingFace) that have rising search volume.
- If by **Dec 15** the archive has **>500 impressions but 0 clicks**: the SERP snippet is the problem, not the traffic. Rewrite titles to lead with the number.

**The psychology of the sprint:** the archive has been built by a founder who understands the pain. The sprint assumes 5 hours per week of distribution work, on top of page cadence. That is the actual cost of turning the reference into a business. If the founder cannot commit 5 hours per week for 3 weeks, the monetization gate cannot be reached — not because the archive is wrong, but because no one is being told it exists.
