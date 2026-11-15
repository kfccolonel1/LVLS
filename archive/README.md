# LVLS History Archive

A browsable, organized dump of every past **levels** set and every **tweet** this
system has published, mined from the full git history of `main`
(2999 commits). Generated 2026-11-15.

This branch (`history`) exists to make the past easy to read as plain files,
instead of digging through git. `main` keeps only the *current* `today.json`
(overwritten daily) and a rolling 24h `tweet.json`; everything older lived only
in commit history until now.

## What's here

### `levels/` — 118 trading days (2026-05-26 to 2026-11-16)
One file per session: `levels/<YYYY-MM-DD>.json` — the final published `today.json`
for that day (daily pivot, regime, significant lows, bull/bear levels, notes).
- `levels/INDEX.csv` — one row per day: date, pivot, regime, # sig lows, # bull, # bear, source commit.

### `tweets/` — 2475 unique tweets across 152 days (2026-05-28 to 2026-11-14)
One file per calendar day (ET): `tweets/<YYYY-MM-DD>.json` — every @AdamMancini4
tweet captured that day, de-duplicated by tweet id, with text, timestamps, any
levels it added, and the extractor's notes.
- `tweets/INDEX.csv` — one row per day: date, # tweets, # tweets that added levels.
- `tweets/new-levels.csv` — flat log of all 442 level-add events
  (date, time, side, price, tweet id) across history.

## How it was built
Every historical version of `today.json` and `tweet.json` was read from git
(`git cat-file --batch`), parsed, and de-duplicated — levels by session date
(latest wins), tweets by tweet id. Source: `main` as of 2026-11-15.

## Note on cookies
`cookie.json` history is **intentionally excluded** — those are past login
session cookies (credentials), not data worth archiving in the clear.

## Refreshing
Re-run the builder against an updated `main` clone and commit the regenerated
`archive/` to refresh this branch.
