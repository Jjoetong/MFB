# FRIDAY · Profit Update

A simulated portfolio dashboard: **$10,000 → $1,000,000 over 18 months**
(20 Nov 2026 00:00 → 20 May 2028 00:00, Singapore time). This is a simulation, not real trading results.

Open `index.html` in a browser, or host it with GitHub Pages. It is a single file with no build step.

## How the numbers work

- The whole path comes from a fixed seed, so everyone who opens the page sees the same numbers.
- Each calendar month has a planned return in `CONFIG.monthPlan`. The positive months are scaled together so the path lands exactly on $1,000,000.00 on 20 May 2028.
- Five months are losing months: Jan 2027, Apr 2027, Aug 2027, Dec 2027 and Mar 2028. About a third of all days are red.
- Inside each day the value moves smoothly and updates every 2 seconds. It always closes on the planned daily figure.
- Before 20 Nov 2026 00:00 SGT the page shows $10,000 and a launch countdown.
- After 20 May 2028 the value stays at $1,000,000.00.

| Month | Result | Month-end value |
|---|---|---|
| Nov 2026 (from 20th) | +3.2% | $10,325 |
| Dec 2026 | +16.9% | $12,068 |
| Jan 2027 | −5.5% | $11,404 |
| Feb 2027 | +24.8% | $14,238 |
| Mar 2027 | +33.0% | $18,933 |
| Apr 2027 | −8.0% | $17,418 |
| May 2027 | +43.0% | $24,901 |
| Jun 2027 | +49.7% | $37,286 |
| Jul 2027 | +37.9% | $51,431 |
| Aug 2027 | −11.0% | $45,774 |
| Sep 2027 | +58.4% | $72,490 |
| Oct 2027 | +65.4% | $119,883 |
| Nov 2027 | +46.3% | $175,431 |
| Dec 2027 | −6.0% | $164,905 |
| Jan 2028 | +72.5% | $284,453 |
| Feb 2028 | +61.9% | $460,415 |
| Mar 2028 | −4.0% | $441,998 |
| Apr 2028 | +77.9% | $786,293 |
| May 2028 (to 20th) | +27.2% | $1,000,000 |

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

## Animation

- Opening sequence: panels fade in, the FRIDAY letters assemble, rings sweep up, numbers count up, and the profit curve, sparklines and P&L bars draw in.
- Live: numbers glide between updates and flash green or red, the waveform pulses on each change, and today's P&L bar blinks.
- Ambient: radar sweep and orbiting marker on the gauge, ripples on line ends, rising particles in the 30D window, light streaks on the cards and a slow scan across the screen.
- Animations switch off for visitors whose device is set to reduce motion.
