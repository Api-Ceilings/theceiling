# The Ceiling — Operating Tracker

**Rule:** archive stays free forever. Revenue sits beside it, never inside it.
**Cadence:** 1 page per night, 5 nights/week. Every page = HTML + data.json + homepage row + sitemap entry.

---

## 1. Page Ledger

| # | API | Slug | Status | HTML date | data.json | Home row | Sitemap | Source checked | Notes |
|---|---|---|---|---|---|---|---|---|---|
| 1 | OpenAI | `openai` | ✅ live | 2026-11-04 | ✅ | ✅ | ⚠️ sitemap2 | platform.openai.com | 503 + ramp rule included |
| 2 | Anthropic | `anthropic` | ✅ live | 2026-11-08 | ✅ | ✅ | ⚠️ sitemap2 | platform.claude.com | spend-cap 429 is the differentiator |
| 3 | Stripe | `stripe` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | **next** |
| 4 | GitHub | `github` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | secondary limits + abuse detection |
| 5 | AWS S3 | `aws-s3` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | |
| 6 | Twilio | `twilio` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | |
| 7 | Slack | `slack` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | tier-based + per-method |
| 8 | Discord | `discord` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | |
| 9 | SendGrid | `sendgrid` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | |
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

---

## 2. Distribution Log

| Date | Channel | URL | Format | Result | Follow-up |
|---|---|---|---|---|---|
| 2026-11-05 | Dev.to | dev.to/apiceilings | "I built X" story | 1 comment (Karolis) | replied — TPM correction accepted |
| 2026-11-05 | HN Show HN | — | — | ⛔ blocked, new-account gate | silent until ~Nov 14, then comment-only |
| — | DevHunt | — | — | ⬜ open | week of Nov 16 |
| — | LibHunt | — | — | ⬜ open | week of Nov 16 |
| — | Indie Hackers | — | — | ⬜ open | week of Nov 16 |
| — | r/webdev | — | Showoff Saturday | ⬜ wait | first Saturday after 10 pages |
| — | HN regular submission | — | link to one page | ⬜ **only after 20 pages + 2–3 comments of history** | Day 14+ |

**Rules:** one channel per week. Never two links to the archive in one thread. Never mention the archive in an HN comment unless directly asked.

---

## 3. Weekly Signals (fill every Sunday, once)

| Week ending | Pages live | GSC impressions | GSC clicks | Perplexity citation? (OpenAI / Stripe / GitHub) | External links | Notes |
|---|---|---|---|---|---|---|
| 2026-11-15 | 7 | — | — | — / — / — | 0 | |
| 2026-11-22 | 10 | | | | | |
| 2026-11-29 | 15 | | | | | |
| 2026-12-06 | 20 | | | | | |
| 2026-12-13 | 25 | | | | | |
| 2026-12-20 | 28 | | | | | |
| 2026-12-27 | 30 | | | | | |
| **2027-02-06** | **Day 90 kill check** | **≥ 5,000 organic?** | | **any citation?** | **≥ 1?** | **verdict: continue / stop** |

**How to check Perplexity citation:** ask it `"Stripe API rate limit"` verbatim, look at the citation list. Screenshot. Y/N. Once a week, 3 queries, 2 minutes.

---

## 4. Monetization Gates

| Rung | Gate | Status | Notes |
|---|---|---|---|
| 1. Sponsored line | 30 pages + one real traffic month | ⬜ | one vendor per category, below content only |
| 2. Change alerts | 60 pages + change-detection routine | ⬜ | loss-aversion product |
| 3. MCP / API tier | 100 pages + MCP prototype | ⬜ | `last_verified_at` in every response, honest |
| 4. Data licensing | 12 months of dated history | ⬜ | only rung that appreciates with age |
| — | **First sponsor email** | ⬜ | 20 named companies, no `info@`, no `sales@` |

**Frozen rule:** no newsletter, no cookie banner, no hero image, no "premium" tag, no related-articles block, no share widget. Any one of these inverts the citation signal.

---

## 5. Decisions (append-only — never delete)

| Date | Decision | Reason |
|---|---|---|
| 2026-11-05 | Archive free forever | Paywalling kills citation, ranking, trust |
| 2026-11-08 | Canonical sitemap = `sitemap2.xml` | CDN negative cache on original path; revisit in 7 days |
| 2026-11-08 | `robots2.txt` stays at project path, inert | Crawlers read host-root robots only; becomes real on custom domain |
| 2026-11-08 | Migrate to Cloudflare Pages at ~Day 60 | GitHub Pages gives zero crawler analytics; thesis requires visibility |
| 2026-11-08 | Moat = provenance + freshness discipline, not page volume | AI can generate volume; it cannot keep dated lines honest |
