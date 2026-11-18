# FRIDAY · Profit Dashboard

Live profit dashboard for the private Friday × Marcus channel.

- **`index.html`** — single-file dashboard, no build step.
- **`profit.json`** — the live portfolio feed FRIDAY reads.
- **GitHub Pages** — serves the dashboard at <https://jjoetong.github.io/MFB/>.

`index.html` fetches `profit.json` from the same origin at load time. There is no
simulated path and no hard-coded target. If the fetch fails, the page shows
`LIVE FEED UNAVAILABLE` instead of inventing numbers.

## Live data

`profit.json` carries only the P&L surface:

```json
{
  "initial_capital": 10000,
  "current_value": 12480.22,
  "today_pnl": 180.00,
  "updated_at": "2026-11-19T01:35:00+08:00",
  "history": [
    {"date": "2026-08-22", "value": 10000},
    {"date": "2026-09-15", "value": 10800},
    {"date": "2026-11-19", "value": 12480.22}
  ]
}
```

- `initial_capital` — Marcus's starting capital.
- `current_value` — latest total portfolio value.
- `today_pnl` — optional; the page uses the history curve for its windows.
- `updated_at` — ISO timestamp with timezone.
- `history` — daily/period points used by the 24H, 30D and 365D strips.

The dashboard shows only portfolio value, net P&L, return, 24H / 30D / 365D
change, the curve and daily P&L. It does not show positions, allocation or
strategy.

## Updating

Joe's bots update `profit.json` after a session, then commit. FRIDAY reads the
same file for the Telegram report and screenshots this page as the Profit card.

## Local preview

```powershell
python -m http.server 8765 --directory "Profit Results"
```

Open <http://127.0.0.1:8765/>. The page fetches `profit.json` from the same folder,
so copy the live file next to `index.html` for a local preview.

## Rules

- Keep `profit.json` valid JSON. Invalid JSON makes FRIDAY serve its last cached copy.
- Never commit API tokens or Telegram credentials here.
- Keep `initial_capital` equal to Marcus's actual deposit.
