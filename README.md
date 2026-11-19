# FRIDAY · Profit Pages

This repository hosts two separate pages plus the live feed.

- **`index.html`** — Claude's **$3,000 → $1,000,000 / 3-year simulation**.
  It is explicitly marked `SIMULATED PORTFOLIO` and `SIMULATION · NOT REAL RESULTS`.
  It does not read `profit.json` and is never sent to Marcus as a real report.
- **`live.html`** — the **live Profit card** that FRIDAY screenshots for Telegram.
  It reads `profit.json` and shows only actual portfolio value and P&L.
- **`profit.json`** — the live portfolio feed.

## URLs

- Simulation: <https://jjoetong.github.io/MFB/>
- Live card: <https://jjoetong.github.io/MFB/live.html>

`FRIDAY_GITHUB_PAGE_URL` must point at **`live.html`**, not the simulation root.

## Live data

`profit.json` carries only the P&L surface:

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
- `today_pnl` — optional; the page uses the history curve for its windows.
- `updated_at` — ISO timestamp with timezone.
- `history` — daily/period points used by the 24H, 30D and 365D strips.

The live page shows portfolio value, net P&L, return, 24H / 30D / 365D change,
the curve and daily P&L. It does not show positions, allocation or strategy.

## Rules

- Keep `profit.json` valid JSON. Invalid JSON makes FRIDAY serve its last cached copy.
- Never commit API tokens or Telegram credentials here.
- Keep `initial_capital` equal to Marcus's actual deposit.
- Never point the Telegram card at the simulation root.
