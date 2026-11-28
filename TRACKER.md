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
| 3 | Stripe | `stripe` | ✅ live | 2026-11-09 | ✅ | ✅ | ⚠️ manual | docs.stripe.com/rate-limits | **Title rewritten 2026-11-28**: names the trap (5 types of 429); 8-question schema |
| 4 | GitHub | `github` | ✅ live | 2026-11-10 | ✅ | ✅ | ⚠️ manual | docs.github.com | **Title rewritten 2026-11-28**: 403 = permission OR rate limit; 8-question schema |
| 5 | AWS S3 | `aws-s3` | ✅ live | 2026-11-11 | ✅ | ✅ | ⚠️ manual | docs.aws.amazon.com | No fixed ceiling; 503 SlowDown has no Retry-After; 8-question schema |
| 6 | Twilio | `twilio` | ✅ live | 2026-11-11 | ✅ | ✅ | ⚠️ manual | twilio.com/docs/api/errors | Concurrency, not rate; 8-question schema |
| 7 | Slack | `slack` | ✅ live | 2026-11-11 | ✅ | ✅ | ⚠️ manual | docs.slack.dev | **Title rewritten 2026-11-28**: names the trap (2025 change, 3,300× slower); 8-question schema |
| 8 | Discord | `discord` | ✅ live | 2026-11-11 | ✅ | ✅ | ⚠️ manual | docs.discord.com | 429 funds the ban; 8-question schema |
| 9 | SendGrid | `sendgrid` | ✅ live | 2026-11-12 | ✅ | ✅ | ⚠️ manual | twilio.com/docs/sendgrid | No published numeric table; IP warm-up is the real ceiling; 8-question schema |
| 10 | **Firestore** | `firestore` | ✅ live | 2026-11-28 | ✅ | ✅ | ⚠️ manual | firebase.google.com/docs/firestore/quotas | **RESOURCE_EXHAUSTED has 2 meanings**; hot-spot trap; 8-question schema |
| 11 | Vercel | `vercel` | ⬜ | — | ⬜ | ⬜ | ⬜ | — | **next** |
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

| Date | Channel | Result |
|---|---|---|
| 2026-11-05 | Dev.to | 1 technical comment (Karolis) — replied, TPM correction accepted |
| 2026-11-05 | HN Show HN | ⛔ blocked, new-account gate |
| 2026-11-08–11 | GSC manual URL Inspection × 3 + Stripe + GitHub + AWS S3 | ✅ queued |
| 2026-11-11 | Bing import from GSC | ✅ verified |
| 2026-11-11 | Bing Sitemaps | ✅ 8 URLs discovered |
| 2026-11-11 | Bing URL Submission | ✅ 9/9 accepted |
| 2026-11-11 | IndexNow (browser GET + GitHub Action) | ✅ live |
| 2026-11-11 | HN | 2 comments, no self-promo |
| 2026-11-11 | Perplexity baseline | ⚠️ not cited (expected at day 7) |
| 2026-11-12 | SendGrid page + schema validation | ✅ 0 errors, 8 FAQ items |
| 2026-11-28 | **GSC Performance report (Nov 7–25)** | **2,305 impressions, 22 clicks, 0.95% CTR** |
| 2026-11-28 | **Title rewrites: Stripe, Slack, GitHub** | ✅ applied — trap-name pattern |
| 2026-11-28 | **Firestore page 10** | ✅ live |

---

## 4. Distribution Calendar

| Week of | Channel | Gate to submit | Status |
|---|---|---|---|
| Nov 9–15 | HN participation, `llms.txt`, IndexNow, meta descriptions, FAQ schema | — | ✅ done |
| **Nov 28–Dec 2** | **DevHunt + LibHunt + Indie Hackers** (the 3 that never shipped) | 10 pages | 🔴 **NOW** |
| Nov 28–Dec 2 | Firestore page (page 10) | — | ✅ done 2026-11-28 |
| Nov 28–Dec 2 | Title rewrites: Stripe, Slack, GitHub | — | ✅ done 2026-11-28 |
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

**Full directory list to submit (11 free, 2026-verified):**
DevHunt (`devhunt.org`), LibHunt (`libhunt.com`), Indie Hackers (`indiehackers.com/products`), BetaList (`betalist.com/submit`), SaaSHub (`saashub.com/submit`), Uneed (`uneed.best/submit-a-tool`), Peerlist Launchpad (`peerlist.io/launchpad`), MicroLaunch (`microlaunch.net`), Fazier (`fazier.com/submit`), PeerPush (`peerpush.com`), Tiny Startups (`tinystartups.com`).

---

## 5. Weekly Signals

| Week ending | Pages live | GSC impressions | GSC clicks | CTR | Perplexity citation? | External links | Notes |
|---|---|---|---|---|---|---|---|
| 2026-11-15 | 9 | — | — | — | N / N / N | 0 | 9 pages. All 9 have 8-question FAQ schema, meta descriptions 145-155 chars. |
| **2026-11-22** | **9** | **2,305** | **22** | **0.95%** | **N / N / N** | **0** | **First real traffic signal.** SendGrid leads CTR at 2.31% (title names the trap). Stripe: 92 imp / 0 clicks at position 6-9 (biggest opportunity). GitHub differentiator queries at position 46-48. Organic pace ≈ 130 imp/day → on track for 5K by mid-December. |
| 2026-11-29 | 10 | — | — | — | — | 0 | **Firestore page 10 live.** Title rewrites applied to Stripe, Slack, GitHub. |
| 2026-12-06 | 11 | | | | | | |
| 2026-12-13 | 12 | | | | | | |
| **2027-02-06** | **Day 90 kill check** | **≥ 5,000 organic?** | | | **any citation?** | **≥ 1?** | **verdict: continue / stop** |

**How to check Perplexity citation:** ask `"Stripe API rate limit"` verbatim, look at the citation list. Screenshot. Y/N. Once a week, 3 queries, 2 minutes.

**How to check Bing AI Performance:** Bing Webmaster Tools → AI Performance (BETA). Check Nov 22, Dec 6, Dec 13.

**How to check ChatGPT citation:** ask "Stripe API rate limit" in ChatGPT with web search on. Look at Sources. Y/N.

**The CTR benchmark from the GSC data:**
- SendGrid (trap-name title): **2.31%**
- OpenAI (trap-name title): **2.38%**
- Anthropic (trap-name title): **2.50%**
- Slack (old title: give-the-answer): **0.65%**
- Stripe (old title: give-the-answer): **0.51%**
- GitHub (old title: give-the-answer): **0.59%**
- **Pattern: trap-name titles average 2.4% CTR; give-the-answer titles average 0.58%.**

---

## 6. Sponsor Pipeline

**Gate to start:** 30 pages + one real traffic month. Not yet.

---

## 7. Infrastructure Blockers

| Date found | Issue | Workaround | Permanent fix | Status |
|---|---|---|---|---|
| 2026-11-08 | GSC "Could not be read" — GitHub Pages Content-Type bug | Manual URL Inspection per page | Custom domain (Day 60) | ⚠️ active |
| 2026-11-08 | `robots2.txt` inert at project path | Accept; sitemap + manual indexing | Custom domain (Day 60) | ⚠️ active |
| — | No crawler analytics on GitHub Pages | GSC + Bing are the only signals | Cloudflare Pages (Day 60) | ⚠️ active |
| 2026-11-11 | Open Graph tags missing on all sub-pages | Homepage complete; sub-pages pending | Roll out on next verification pass | ⚠️ active |
| **2026-11-28** | **Page cadence stalled Nov 12→28 (16 days)** | **Firestore shipped 2026-11-28** | — | ✅ resolved 2026-11-28 |
| **2026-11-28** | **Directory listings (DevHunt, LibHunt, IH) never shipped** | **Submitting this week** | — | 🔴 active |

---

## 8. Corrections Log

| Date | Page | What was reported | By | Verdict | Action taken |
|---|---|---|---|---|---|
| 2026-11-05 | openai.html | TPM vs `Retry-After` — request bigger than remaining budget fails regardless of wait | Karolis (Dev.to) | ✅ valid, page gap | Reply accepted; token-count check added |

---

## 9. Monetization Gates

| Rung | Gate | Status | Notes |
|---|---|---|---|
| 1. Sponsored line | 30 pages + one real traffic month | ⬜ | traffic month active (Nov 7–25); 20 more pages needed |
| 2. Change alerts | 60 pages + change-detection | ⬜ | loss-aversion product |
| 3. MCP / API tier | 100 pages + MCP prototype | ⬜ | `last_verified_at` in every response |
| 4. Data licensing | 12 months of dated history | ⬜ | only rung that appreciates with age |
| — | First sponsor email | ⬜ | 20 named companies |

**Frozen rule:** no newsletter, no cookie banner, no hero image, no "premium" tag, no related-articles block, no share widget.

---

## 10. Streak

| Week | Mon | Tue | Wed | Thu | Fri | Sat | Sun | Pages this week |
|---|---|---|---|---|---|---|---|---|
| Nov 9–15 | ✅ | ✅ | ✅ | ✅ | | | | 7 |
| Nov 16–22 | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | ⬜ | 0 |
| Nov 23–29 | ⬜ | ⬜ | ⬜ | ⬜ | ✅ | | | 1 (Firestore) |

**Honest note:** the streak broke between Nov 13 and Nov 27 — 14 consecutive nights with zero pages. Firestore broke the silence on Nov 28. The next test is whether Dec 1–2 produces Vercel, or whether the pattern repeats.

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
| 2026-11-11 | Answer blocks under every `<h2>` | Princeton/IIT-Delhi: answer blocks lift AI visibility up to 40% |
| 2026-11-11 | `llms.txt` shipped | Coding-agent index, not search |
| 2026-11-11 | Bing verified via GSC import | XML and meta tag both returned Bing-side "Unexpected error" |
| 2026-11-11 | IndexNow via GitHub Action | CORS blocks fetch; Action on push = permanent automation |
| 2026-11-11 | FAQ schema expanded to 8 questions on all 8 pages | 4 surface + 4 differentiator |
| 2026-11-12 | SendGrid page live — no published numeric table + IP warm-up | SendGrid publishes no per-endpoint number; the real ceiling is warm-up |
| 2026-11-12 | Monetization alignment check | 9 pages ahead of cadence; 0 traffic was expected but unproven |
| **2026-11-28** | **Firestore page 10 live — RESOURCE_EXHAUSTED has 2 meanings** | **The trap: one variant resets at midnight Pacific (daily quota), the other scales in minutes (ramp-up). Hot-spots from sequential IDs are the silent scaling killer.** |
| **2026-11-28** | **Title rewrites: Stripe, Slack, GitHub** | **GSC data proves trap-name titles average 2.4% CTR vs give-the-answer titles at 0.58%. Applied the SendGrid pattern to the 3 highest-impression low-CTR pages.** |
| **2026-11-28** | **Directory submissions this week (DevHunt, LibHunt, IH, + 8 more)** | **External-link criterion at Day 90 is still 0. Traffic month is active. The only remaining work to pass the gate is 20 more pages + 1 external link.** |
| **2026-11-28** | **Viral mechanic = docs-led growth, not social sharing** | **Research: for dev tools, docs are the highest-leverage marketing channel; API reference pages with error codes and copy-paste examples rank for long-tail queries with purchase intent. The viral loop is: 429 → search exact error → land on page → get fix → bookmark → return → tell colleague. No share button needed.** |
