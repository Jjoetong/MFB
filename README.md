# FRIDAY · Profit Update

A simulated portfolio dashboard: **$10,000 → $1,000,000 over 18 months**
(19 Nov 2026 → 19 May 2028, Singapore time). This is a simulation, not real trading results.

Open `index.html` in a browser, or host it with GitHub Pages. It is a single file with no build step.

## How the numbers work

- The whole path comes from a fixed seed, so everyone who opens the page sees the same numbers.
- Each calendar month has a planned return in `CONFIG.monthPlan`. The positive months are scaled together so the path lands exactly on $1,000,000.00 on 19 May 2028.
- Five months are losing months: Jan 2027, Apr 2027, Aug 2027, Dec 2027 and Mar 2028. About a third of all days are red.
- Inside each day the value moves smoothly and updates every 2 seconds. It always closes on the planned daily figure.
- After 19 May 2028 the value stays at $1,000,000.00.

| Month | Result | Month-end value |
|---|---|---|
| Nov 2026 (from 19th) | +3.6% | $10,355 |
| Dec 2026 | +16.9% | $12,108 |
| Jan 2027 | −5.5% | $11,442 |
| Feb 2027 | +24.9% | $14,291 |
| Mar 2027 | +33.1% | $19,014 |
| Apr 2027 | −8.0% | $17,493 |
| May 2027 | +43.1% | $25,025 |
| Jun 2027 | +49.9% | $37,502 |
| Jul 2027 | +38.0% | $51,762 |
| Aug 2027 | −11.0% | $46,068 |
| Sep 2027 | +58.5% | $73,022 |
| Oct 2027 | +65.5% | $120,883 |
| Nov 2027 | +46.4% | $177,026 |
| Dec 2027 | −6.0% | $166,405 |
| Jan 2028 | +72.7% | $287,347 |
| Feb 2028 | +62.0% | $465,541 |
| Mar 2028 | −4.0% | $446,920 |
| Apr 2028 | +78.1% | $795,949 |
| May 2028 (to 19th) | +25.6% | $1,000,000 |

## Settings

All settings are in the `CONFIG` block near the top of the script:

- `start` / `end`: simulation dates
- `startBalance` / `targetBalance`
- `monthPlan`: the planned % per month (negative values are losing months)
- `seed`: change it for a different day-to-day path with the same monthly plan

## Page parts

- **Gauge**: portfolio value with 365D / 30D / 24H rings (each 1% return = 12° of arc, up to 300°)
- **24H / 30D / 365D cards**: change over that period, with sparklines
- **Profit curve**: full history since start, $10K base line, highlighted last 30 days, and daily P&L bars
