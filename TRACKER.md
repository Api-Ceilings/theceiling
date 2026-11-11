# The Ceiling — Operating Tracker

**Rule:** archive stays free forever. Revenue sits beside it, never inside it.
**Cadence:** 1 page per night, 5 nights/week. Every page = HTML + data.json + homepage row + sitemap entry + IndexNow Action URL + 8-question FAQ schema.
**Ritual:** the streak counter is the only metric that matters at 11pm. Everything else is downstream.

---

## 1. Page Ledger

| # | API | Slug | Status | HTML date | data.json | Home row | Sitemap | Source checked | Notes |
|---|---|---|---|---|---|---|---|---|---|
| 1 | OpenAI | `openai` | ✅ live | 2026-11-04 | ✅ | ✅ | ⚠️ manual | platform.openai.com | 503 + ramp rule included; 8-question schema |
| 2 | Anthropic | `anthropic` | ✅ live | 2026-11-08 | ✅ | ✅ | ⚠️ manual | platform.claude.com | spend-cap 429 is the differentiator; 8-question schema |
| 3 | Stripe | `stripe` | ✅ live | 2026-11-09 | ✅ | ✅ | ⚠️ manual | docs.stripe.com/rate-limits | Five 429s by Stripe-Rate-Limited-Reason; 8-question schema (first schema-expansion test) |
| 4 | GitHub | `github` | ✅ live | 2026-11-10 | ✅ | ✅ | ⚠️ manual | docs.github.com | 403 is both permission error and rate limit; 8-question schema |
| 5 | AWS S3 | `aws-s3` | ✅ live | 2026-11-11 | ✅ | ✅ | ⚠️ manual | docs.aws.amazon.com | No fixed ceiling; 503 SlowDown has no Retry-After; 8-question schema |
| 6 | Twilio | `twilio` | ✅ live | 2026-11-11 | ✅ | ✅ | ⚠️ manual | twilio.com/docs/api/errors | Concurrency, not rate; 429 never processed; 8-question schema |
| 7 | Slack | `slack` | ✅ live | 2026-11-11 | ✅ | ✅ | ⚠️ manual | docs.slack.dev | Per-method per-workspace; 2025 change makes one method 3,300× slower; 8-question schema |
| 8 | Discord | `discord` | ✅ live | 2026-11-11 | ✅ | ✅ | ⚠️ manual | docs.discord.com | 429 counts as invalid request; 10K/10min → Cloudflare ban; 8-question schema |
| 9 | SendGrid | `sendgrid` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | **next** — 8-question schema from the start |
| 10 | Google Firestore | `firestore` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | |
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
| 2026-11-05 | Dev.to | dev.to/apiceilings/i-built-a-cross-api-rate-limit-reference | "I built X" story | 1 technical comment (Karolis) | replied — TPM correction accepted, token-count fix committed |
| 2026-11-05 | HN Show HN | — | — | ⛔ blocked, new-account gate | silent until ~Nov 14, then comment-only |
| 2026-11-08 | GSC | search.google.com/search-console | manual URL Inspection × 3 | ✅ 3 pages queued | check Nov 15 |
| 2026-11-09 | GSC | search.google.com/search-console | manual URL Inspection — Stripe | ✅ queued | check Nov 15 |
| 2026-11-10 | GSC | search.google.com/search-console | manual URL Inspection — GitHub | ✅ queued | check Nov 15 |
| 2026-11-11 | GSC | search.google.com/search-console | manual URL Inspection — AWS S3 | ✅ queued | check Nov 15 |
| 2026-11-11 | Bing | bing.com/webmasters | Import from GSC → verified | ✅ Site added | sitemap submitted |
| 2026-11-11 | Bing | bing.com/webmasters → Sitemaps | sitemap2.xml | ✅ Success, 8 URLs discovered | check AI Performance Nov 22 |
| 2026-11-11 | Bing | bing.com/webmasters → URL Submission | 9 URLs (homepage + 8 API pages) | ✅ 9/9 accepted (quota 9/100) | now automated via IndexNow |
| 2026-11-11 | Bing | bing.com/webmasters → URL Inspection | homepage audit | ✅ "URL can be indexed", 1 SEO issue fixed (meta description 213→140) | re-submitted homepage after fix |
| 2026-11-11 | IndexNow | api.indexnow.org (browser GET) | 9 URLs submitted manually | ✅ HTTP 200 (blank page) × 9 | replaced by GitHub Action |
| 2026-11-11 | IndexNow (GitHub Action) | .github/workflows/indexnow.yml | Auto-submit on push to main | ✅ run #2 success, 1m 7s | permanent — no VPS, no quota |
| 2026-11-11 | HN | news.ycombinator.com | 3 threads read, 2 comments posted | ✅ no self-promotion | unlocks Show HN ~Nov 14 |
| 2026-11-11 | Meta descriptions | all 8 sub-page HTML files | 200+ → 145-155 chars | ✅ done | Bing SEO warning cleared |
| 2026-11-11 | Perplexity (baseline) | perplexity.ai | Query "Stripe API rate limit" | ⚠️ not cited | expected at day 7 — see §5 |
| 2026-11-11 | FAQ schema | all 8 sub-page HTML files | 4 → 8 questions per page | ✅ validated 0 errors, 8 items each | schema exposure complete |

---

## 4. Distribution Calendar (what's next)

**Rule:** one channel per week. Never two links to the archive in one thread. Never mention the archive in an HN comment unless directly asked.

| Week of | Channel | Format | Gate to submit | Status |
|---|---|---|---|---|
| Nov 9–15 | HN participation only | comments on others' threads | 0 karma today — read 3, comment 2 by Nov 12 | ✅ done 2026-11-11 (2 comments) |
| Nov 9–15 | `llms.txt` at repo root | plain-text index + dates | none — any week | ✅ shipped 2026-11-11 |
| Nov 9–15 | IndexNow | key file + API submission | any week | ✅ done 2026-11-11 (browser GET + GitHub Action) |
| Nov 9–15 | Meta descriptions | 140-160 chars per page | Bing SEO threshold | ✅ done 2026-11-11 (all 8 sub-pages) |
| Nov 9–15 | FAQ schema expansion | 8 questions per page | schema valid | ✅ done 2026-11-11 (all 8 pages, 64 total Q&A pairs) |
| Nov 16–22 | DevHunt | directory submission | archive has 10 pages | ⬜ |
| Nov 16–22 | LibHunt | directory submission | archive has 10 pages | ⬜ |
| Nov 16–22 | Indie Hackers | "I built X" post, different framing from Dev.to | 10 pages | ⬜ |
| Nov 16–22 | r/webdev Showoff Saturday | tool launch thread | 10 pages + no prior link posts | ⬜ |
| Nov 23–29 | r/LocalLLaMA | AI/LLM relevance angle | 15 pages | ⬜ |
| Nov 23–29 | HN regular submission | link to `openai.html` or `stripe.html`, NOT Show HN | 20 pages + 3 HN comments of history | ⬜ |
| Dec 1–7 | r/SaaS | founder story angle | 25 pages | ⬜ |
| Dec 1–7 | r/devops | rate-limit/infra angle | 25 pages | ⬜ |
| Dec 8–14 | Product Hunt | full launch | 30 pages + custom domain (optional but recommended) | ⬜ |
| Dec 15+ | Twitter/X or Bluesky thread | "here's what's on the ceiling for X" | first citation logged | ⬜ |

**Recurring maintenance — every new page:**
- Add URL to `.github/workflows/indexnow.yml` `urlList` (Content Gate #12)
- Add URL to `sitemap2.xml`
- Add row to `index.html`
- Submit URL via Bing URL Inspection once for the fast lane (optional)

**Channels deliberately NOT on this list:** LinkedIn (wrong audience for rate limits), email cold outreach (kills the domain), Discord cold-posting (gets you banned), Stack Overflow answers (only when directly relevant, never as promotion).

---

## 5. Weekly Signals (fill every Sunday, once)

| Week ending | Pages live | GSC impressions | GSC clicks | Perplexity citation? (OpenAI / Stripe / GitHub) | External links | Notes |
|---|---|---|---|---|---|---|
| 2026-11-15 | 8 | — | — | N / N / N | 0 | 8 pages by Nov 11. GSC sitemap unresolved (Content-Type bug). Bing verified via GSC import, sitemap submitted, 9 URLs submitted manually + IndexNow GitHub Action live. All 8 meta descriptions standardized to 145-155 chars. All 8 pages have 8-question FAQ schema (64 total Q&A pairs, validated 0 errors). HN: 2 comments on existing threads, no self-promo. Perplexity baseline check 2026-11-11: "Stripe API rate limit" — answer matched our facts but was less precise (4 categories vs our 5). Not cited. Expected at day 7 (0 external links, 0 traffic, brand-new domain). Positioning confirmed: our differentiator is the deeper answer (no-header trap, concurrency≠rate), not the surface answer. |
| 2026-11-22 | | | | | | |
| 2026-11-29 | | | | | | |
| 2026-12-06 | | | | | | |
| 2026-12-13 | | | | | | |
| 2026-12-20 | | | | | | |
| 2026-12-27 | | | | | | |
| **2027-02-06** | **Day 90 kill check** | **≥ 5,000 organic?** | | **any citation?** | **≥ 1?** | **verdict: continue / stop** |

**How to check Perplexity citation:** ask it `"Stripe API rate limit"` verbatim, look at the citation list. Screenshot. Y/N. Once a week, 3 queries, 2 minutes.

**How to check Bing AI Performance:** Bing Webmaster Tools → AI Performance (BETA). Shows when your site is cited in Microsoft Copilot and Bing AI summaries, with Citation Share. Data appears ~48h after first crawl. Check on Nov 22.

**How to check ChatGPT citation:** ask "Stripe API rate limit" in ChatGPT with web search on. Look at the Sources list at the bottom. Y/N.

---

## 6. Sponsor Pipeline

**Gate to start:** 30 pages **and** one real traffic month. Before that, this section stays empty. Filling it early is founder impatience.

**Rule:** named individuals only. Never `info@`, `sales@`, or a generic contact form. LinkedIn search takes 3 minutes per name.

| Company | Why them | Contact person | Contact role | Sent | Reply | Status |
|---|---|---|---|---|---|---|
| Svix | webhook infra, adjacent category | — | — | — | — | ⬜ pre-gate |
| Standard Webhooks | open standard, adjacent | — | — | — | — | ⬜ pre-gate |
| Hookdeck | webhook relay, adjacent | — | — | — | — | ⬜ pre-gate |
| Sentry | error monitoring, every throttle is their customer | — | — | — | — | ⬜ pre-gate |
| Datadog | observability, rate limit pain is their product | — | — | — | — | ⬜ pre-gate |
| Bearer | API monitoring (if still active) | — | — | — | — | ⬜ pre-gate |
| Postman | API tooling | — | — | — | — | ⬜ pre-gate |
| Kong | API gateway | — | — | — | — | ⬜ pre-gate |
| Apigee (Google) | API gateway | — | — | — | — | ⬜ pre-gate |
| ReadMe | API documentation infra | — | — | — | — | ⬜ pre-gate |

**The email template** (once gate is met): names their problem in their language, names their product, removes risk with "payment after first month," ends with a single hook. 143 words. Subject: `Your tool should be the answer to "hit rate limit"`.

---

## 7. Infrastructure Blockers (running list)

| Date found | Issue | Workaround | Permanent fix | Status |
|---|---|---|---|---|
| 2026-11-08 | GSC "Couldn't fetch" — sitemap was inside `openai/` folder | Moved to repo root | Done | ✅ resolved |
| 2026-11-08 | GSC "Could not be read" — GitHub Pages omits `Content-Type` header on project subpaths | Manual URL Inspection per page | Custom domain (Day 60) | ⚠️ active |
| 2026-11-08 | `raw.githubusercontent.com` sitemap rejected — GSC field is prefix-locked to property domain | None — cross-host submission impossible | Custom domain (Day 60) | ⚠️ active |
| 2026-11-08 | `robots2.txt` at project path is inert — crawlers read host-root only | Accept; sitemap and manual indexing carry discovery | Custom domain (Day 60) | ⚠️ active |
| — | No crawler analytics on GitHub Pages | None — GSC + Bing are the only signals | Cloudflare Pages (Day 60) | ⚠️ active |
| 2026-11-11 | Bing "Unexpected error" on XML file and meta tag verification | Bypassed via GSC import | None needed — import works | ✅ resolved |
| 2026-11-11 | Bing flags meta descriptions >160 chars (all 9 pages) | All 8 sub-pages shortened to 145-155 chars alongside homepage fix | — | ✅ resolved 2026-11-11 |
| 2026-11-11 | IndexNow CORS blocks browser `fetch()` — no `Access-Control-Allow-Origin` | Browser GET works (blank page = HTTP 200). GitHub Action automates permanently. | — | ✅ resolved 2026-11-11 |

---

## 8. Corrections Log

**Every correction is a trust deposit.** Even when the correction is wrong, record it and reply. This log is the archive's strongest non-numeric signal.

| Date | Page | What was reported | By | Verdict | Action taken |
|---|---|---|---|---|---|
| 2026-11-05 | openai.html | TPM vs `Retry-After` — a request bigger than remaining token budget fails regardless of wait time | Karolis (Dev.to) | ✅ valid, page gap | Reply accepted; token-count check committed to page this week |
| | | | | | |

---

## 9. Monetization Gates

| Rung | Gate | Status | Notes |
|---|---|---|---|
| 1. Sponsored line | 30 pages + one real traffic month | ⬜ | one vendor per category, below content only |
| 2. Change alerts | 60 pages + change-detection routine | ⬜ | loss-aversion product |
| 3. MCP / API tier | 100 pages + MCP prototype | ⬜ | `last_verified_at` in every response, honest |
| 4. Data licensing | 12 months of dated history | ⬜ | only rung that appreciates with age |
| — | First sponsor email | ⬜ | 20 named companies, no `info@`, no `sales@` |

**Frozen rule:** no newsletter, no cookie banner, no hero image, no "premium" tag, no related-articles block, no share widget. Any one of these inverts the citation signal.

---

## 10. Streak

**The only metric that matters at 11 PM is whether a page went live tonight.**

| Week | Mon | Tue | Wed | Thu | Fri | Sat | Sun | Pages this week |
|---|---|---|---|---|---|---|---|---|
| Nov 9–15 | ✅ | ✅ | ✅ | | | | | 6 |

**Rules:** ✅ = night a page went live · 🔄 = audit/verification (not a new page, but a night spent) · ⬜ = skipped · ❌ = broke the pattern (skipped two in a row)

**Honest note on this week:** Mon Nov 9 (Stripe), Tue Nov 10 (GitHub), Wed Nov 11 (AWS S3 + Twilio + Slack + Discord — 4 pages in one session). That's **3 nights, 6 pages.** The checkmark counts nights, not pages. Two-in-one-night is the pattern the tracker warns against — if Nov 12–15 produce zero pages, the week reads as 3 nights of work that burned through 6 pages, not 6 nights of work.

**If two ❌ in one week:** stop the cadence, write down why in Decisions, restart at one page. Do not try to "catch up." Catch-up weeks are how archives get abandoned.

---

## 11. Decisions (append-only — never delete)

| Date | Decision | Reason |
|---|---|---|
| 2026-11-05 | Archive free forever | Paywalling kills citation, ranking, trust |
| 2026-11-08 | Canonical sitemap = `sitemap2.xml` | Original diagnosis: CDN negative cache. **Superseded — see below.** |
| 2026-11-08 | `robots2.txt` stays at project path, inert | Crawlers read host-root robots only; becomes real on custom domain |
| 2026-11-08 | Migrate to Cloudflare Pages at ~Day 60 | GitHub Pages gives zero crawler analytics; thesis requires visibility |
| 2026-11-08 | Moat = provenance + freshness discipline, not page volume | AI can generate volume; it cannot keep dated lines honest |
| 2026-11-08 | Correction: "Couldn't fetch" was file location, not CDN cache | `robots2.txt` and `sitemap2.xml` were inside `openai/` folder. Moved to repo root. |
| 2026-11-08 | Sitemap abandoned on github.io project path | GitHub Pages Content-Type bug (community discussions #159977, #149884). Bing accepts same file. GSC field prefix-locked, cross-host impossible. |
| 2026-11-08 | Manual URL Inspection is the indexing method until Day 60 | 3 live pages queued. For <20 pages this is correct tool. Revisit sitemap at custom domain. |
| 2026-11-09 | Stripe page live — five-way 429 diagnostic | `Stripe-Rate-Limited-Reason` distinguishes 5 rate limits; 429 without it is a lock timeout |
| 2026-11-10 | GitHub page live — 403 disambiguation | GitHub returns 403 for both permission errors and rate limits; retrying the wrong one can get the integration banned |
| 2026-11-11 | AWS S3 page live — no-fixed-ceiling model | First page where the limit is per-prefix and unbounded in aggregate; 503 SlowDown carries no Retry-After |
| 2026-11-11 | Twilio page live — concurrency, not rate | First page where the fix is fewer simultaneous connections, not longer backoff |
| 2026-11-11 | Slack page live — per-method scope + distribution-dependent limits | First page where the same method has three different limits depending on distribution model |
| 2026-11-11 | Discord page live — the retry is the failure | First page where a 429 itself counts toward a ban threshold (10,000 / 10 min → Cloudflare IP ban); shared-scope 429s are the only exempt case |
| 2026-11-11 | Added 40–60 word answer blocks under every `<h2>` on all 8 pages | Princeton/IIT-Delhi study: adding statistics, quotations, and citations to credible sources lifts AI visibility by up to 40%. The answer block is the chunk-level unit RAG pipelines quote. Perplexity cites 13% of the time vs ChatGPT's 0.59% — answer blocks are the highest-leverage change |
| 2026-11-11 | Shipped `llms.txt` at repo root | Ahrefs study: 97% of llms.txt files get zero requests. Cheap bet, zero expectation of traffic. Purpose: coding agents pointed at the docs, not search |
| 2026-11-11 | Verified Bing via GSC import, not XML/meta tag | Both XML and meta tag verification returned "Unexpected error" — confirmed Bing-side bug. GSC import bypasses the failing verification crawler entirely. Caveat: import is contingent on GSC OAuth grant persisting |
| 2026-11-11 | Meta description standard = 140–160 chars | Bing flags >160 as an SEO issue. All 9 pages now compliant (145-155 chars). Content Gate Checklist item #2 |
| 2026-11-11 | IndexNow: browser GET for manual, GitHub Action for automation | CORS blocks `fetch()` by design — no `Access-Control-Allow-Origin` header. Browser navigation to the GET URL works. GitHub Action on push to `main` = permanent free automation, no VPS needed. Run #2 confirmed success (1m 7s). Content Gate Checklist item #12 requires updating the action's `urlList` per new page |
| 2026-11-11 | Positioning: archive answers the deeper question, not the surface one | Baseline check: Perplexity "Stripe API rate limit" returns a less precise answer (4 categories, generic backoff) — our page has 5 categories and distinguishes concurrency≠rate. The archive's differentiator is the specific question Stripe docs skip (no-header 429 trap, concurrency-vs-rate decision), not the general summary the LLMs already produce |
| 2026-11-11 | FAQ schema expanded to 8 questions on all 8 pages | 4 surface questions (already there) + 4 differentiator questions per page, targeting the specific long-tail queries the page wins on. Every answer already lives in visible content — schema exposure, not new content. Validated with Schema.org Validator: 0 errors, 8 items per page. Total machine-readable Q&A pairs: 64 (was ~32). |
