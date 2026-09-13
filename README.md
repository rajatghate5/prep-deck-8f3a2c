# prep-deck

Interview prep pages, published via GitHub Pages.

## Live pages

| Page | Link |
|---|---|
| Ayuradhar CTO Round — 37 questions | https://rajatghate5.github.io/prep-deck-8f3a2c/ |
| Interview MCQ Drill — 328 questions | https://rajatghate5.github.io/prep-deck-8f3a2c/mcqs/ |
| Interview Reboot — 54-day plan to 6 Nov | https://rajatghate5.github.io/prep-deck-8f3a2c/reboot/ |

Mirror, same content: [prep-deck.rajatghate5.workers.dev](https://prep-deck.rajatghate5.workers.dev/)

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
- **JS Drills** — all 41 questions from
  [Array-and-Javascript-practice-questions](https://github.com/rajatghate5/Array-and-Javascript-practice-questions),
  grouped into 8 categories (strings, array basics, dedupe & Sets, filter &
  partition, sorting, math & recursion, nested data, reduce & aggregation).
  Each category carries a worked JS template and the interview angle; each
  question deep-links to its exact line in that repo. Plus 12 JS-mechanics
  drills on the gotchas those questions expose (default sort comparator,
  reduce with no seed, spread-in-reduce being quadratic, Set identity).
- **Progress** — accuracy per topic, colour-coded, and every question missed.

The day plan interleaves **30 min tech + 30 min JS drills daily** rather than
blocking tech first, because blocking is how the coding half ends up untouched
until the final fortnight. 41 days carry a new question, 8 are consolidation
(redo the previous one from memory), and the last 5 are review and mock.

> **Scope note:** the drill set is JavaScript fundamentals and array/object
> manipulation, deliberately sourced from Rajat's own repo rather than LeetCode.
> It does **not** cover algorithm patterns — no binary search, trees, graphs,
> dynamic programming, heaps or backtracking. If a round turns out to be
> LeetCode-style, this deck is not preparation for it.

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
not intended to be search-indexed. The repo is public and both hosts serve
publicly — treat these as unlisted, not secret.

## Deployment

**GitHub Pages** (primary) builds automatically from `main` on every push.
Pages requires the repo to stay public on the free plan; making it private again
takes the site down.

**Cloudflare Worker** (mirror) is manual — there is no Git integration, so run it
after changing a page:

```bash
npx wrangler deploy
```

`wrangler.jsonc` points the assets directory at the repo root; `.assetsignore`
keeps git metadata, config and this README from being uploaded. Both hosts serve
directory-style URLs, so `/reboot/` and `/reboot` resolve.
