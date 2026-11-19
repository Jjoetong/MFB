# FRIDAY · Profit Page

- **`index.html`** — FRIDAY’s Profit page. It starts at **$3,000**, targets
  **$1,000,000 over 3 years**, and renders the planned portfolio path.
- **`live.html`** — live-feed variant of the same dashboard, reading `profit.json`.
- **`profit.json`** — FRIDAY’s portfolio feed.

## URLs

- Profit page: <https://jjoetong.github.io/MFB/>
- Live-feed variant: <https://jjoetong.github.io/MFB/live.html>

`FRIDAY_GITHUB_PAGE_URL` points at **`index.html`**, so the Telegram Profit card
is the page above.

## Configuration

The page layout lives in `index.html`; its numbers are set in the `CONFIG` block:

- `startBalance` — **3000**
- `targetBalance` — **1000000**
- `start` / `end` — **20 Nov 2026 → 20 Nov 2029** (3 years)

## Live feed

`profit.json` is kept for the live-feed variant:

```json
{
  "initial_capital": 3000,
  "current_value": 3000,
  "today_pnl": 0,
  "updated_at": "2026-11-19T19:25:00+08:00",
  "history": [
    {"date": "2026-11-18", "value": 3000},
    {"date": "2026-11-19", "value": 3000}
  ]
}
```

- `initial_capital` — Marcus's starting capital.
- `current_value` — latest total portfolio value.
- `today_pnl` — optional.
- `updated_at` — ISO timestamp with timezone.
- `history` — points used by the 24H, 30D and 365D strips.

## Rules

- Keep `profit.json` valid JSON.
- Never commit API tokens or Telegram credentials here.
- Keep `initial_capital` equal to Marcus's deposit.
