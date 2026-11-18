# MFB — FRIDAY profit feed

`profit.json` is the single source of truth for Marcus’s portfolio update in Telegram.

## Schema

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

- `initial_capital` — Marcus’s starting capital for this portfolio.
- `current_value` — latest total portfolio value.
- `today_pnl` — optional; calculated from the last two history points if omitted.
- `updated_at` — ISO timestamp with timezone.
- `history` — date/value points used for the 24H, 30D and 365D strips.

## Rules

- Keep it valid JSON. Invalid JSON makes FRIDAY serve the last cached copy.
- Update `current_value` and append to `history` whenever the bots finish a session.
- Set `initial_capital` to Marcus’s actual deposit once Start is complete.
- Never commit API tokens or Telegram credentials here.

FRIDAY reads this file over HTTPS and sends only P&L to the private Telegram group.