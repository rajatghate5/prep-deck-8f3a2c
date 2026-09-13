# prep-deck

Interview prep pages, served as static assets from a Cloudflare Worker.

## Live pages

| Page | Link |
|---|---|
| Ayuradhar CTO Round — 37 questions | https://prep-deck.rajatghate5.workers.dev/ |
| Interview MCQ Drill — 328 questions | https://prep-deck.rajatghate5.workers.dev/mcqs/ |
| Interview Reboot — 54-day plan to 6 Nov | https://prep-deck.rajatghate5.workers.dev/reboot/ |

> Previously these pointed at `rajatghate5.github.io/prep-deck-8f3a2c/`, but
> GitHub Pages will not serve a **private** repo on the free plan, so those
> links always 404'd. Hosting moved to Cloudflare Workers.

## Interview Reboot

A dated revision plan built for a 1 hr/day budget against a fixed date
(6 November 2026). Four tabs:

- **Plan** — 54 dated cards, 14 Sep → 6 Nov, each pairing a tech topic with a DSA
  pattern and that day's problems. Today is outlined and scrolls into view; past
  days left unticked get a red edge so slippage is visible. The last 5 days are
  review and mock only.
- **Tech MCQs** — 100 questions across JavaScript/TypeScript, React, Next.js,
  Node/NestJS, MongoDB, PostgreSQL, auth & security, AWS, real-time, performance,
  system design, AI/LLM and CS fundamentals. Filter by topic; study modes are
  All / Unseen / Wrong.
- **DSA** — 13 patterns, each with when to use it, the *tell* that identifies it in
  a problem statement, complexity, and a commented JS template. 67 curated
  LeetCode problems mapped to their pattern, plus 12 complexity drills.
- **Progress** — accuracy per topic, colour-coded, and every question missed.

The day plan interleaves **30 min tech + 30 min DSA daily** rather than blocking
tech first, because blocking is how DSA ends up untouched until the final fortnight.

Question weighting leans on the work in the resume — the multi-framework split,
SSE vs WebSockets, why Postgres over Mongo for a relational domain, payment
idempotency, the OpenUI Lang streaming renderer — so several are written as the
follow-up an interviewer asks *after* reading a given bullet.

**Storage note:** this page uses `localStorage` (key `reboot.v1`), not
`sessionStorage` like the other decks. A 54-day plan has to survive closing the
tab. Progress is per-device, so phone and laptop track separately, and it is still
never sent anywhere. "Clear all progress" on the Progress tab resets it.

## Interview MCQ Drill

328 multiple-choice questions covering JavaScript/TypeScript, React & Next.js,
Node.js, PostgreSQL & MongoDB, auth & security, AWS, DSA, CS fundamentals,
system design, SEO, and HR rounds.

- Tap an option for instant feedback plus an explanation citing its source section
- Filter by level (Startup / Mid / MNC / India), track, or section
- Study modes: shuffle, unanswered only, my wrong answers
- Results panel ranks your weakest sections first
- Progress is kept in `sessionStorage` — it lasts the browser tab, and is never sent anywhere

Each page is a single self-contained HTML file: no build step, no dependencies,
no network requests.

## Note

`robots.txt` disallows all crawlers and each page sets `noindex`, so these are
not intended to be search-indexed. The Worker serves publicly regardless of the
repo being private — treat these as unlisted, not secret.

## Deployment

```bash
npx wrangler deploy
```

`wrangler.jsonc` points the assets directory at the repo root; `.assetsignore`
keeps git metadata, config and this README from being uploaded. Cloudflare serves
directory-style URLs, so `/reboot/` and `/reboot` both resolve.

There is **no Git integration** on this Worker — pushing to `main` does not deploy.
Run the command above after changing a page.
