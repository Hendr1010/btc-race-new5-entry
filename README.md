# Dip-bounce scalper v2 — BTC race round 5

[![make.fun](https://make.fun/badge/btc-race-24h-20261118-1444.svg)](https://make.fun/bounty/btc-race-24h-20261118-1444?utm_source=github&utm_medium=readme&utm_campaign=makefun)
[![Rank](https://make.fun/badge/btc-race-24h-20261118-1444/Hendr1010/btc-race-new5-entry/rank.svg)](https://make.fun/bounty/btc-race-24h-20261118-1444?utm_source=github&utm_medium=readme&utm_campaign=makefun)
[![Reward](https://make.fun/badge/btc-race-24h-20261118-1444/Hendr1010/btc-race-new5-entry/reward.svg)](https://make.fun/bounty/btc-race-24h-20261118-1444?utm_source=github&utm_medium=readme&utm_campaign=makefun)

A long-only dip-bounce scalper for cbBTC on 1-minute Orca bars. It buys a sharp
dip (close ≥105 bps below the 60-bar rolling high) with all cash and sells the
snap-back at +180 bps take-profit or −55 bps stop-loss, then sits in cash until
the next real swing. No randomness, no clock, no network — two runs on the same
bars produce identical orders.

## Tuning

Validated on three published dev windows (local backtest, next-minute-open
fills, 4 bps fee + 2 bps slippage):

| setting | round-5 window | round-4 window | 20261113 window |
| --- | --- | --- | --- |
| TP 150 / SL 55 (round 4) | +$6.70 | +$24.70 | −$40.43 |
| **TP 180 / SL 55 (this bot)** | **+$9.28** | **+$30.98** | −$37.47 |
| TP 200 / SL 55 | +$11.68 | +$19.06 | −$32.97 |

Rejected by the same tests: a shallower second entry trigger (lost money on
every window), scale-ins (never triggered), and trend filters (blocked the
winning trades along with the losers). TP 180 / SL 55 was picked for the best
three-window total, not the best single window — TP 250 won one window with a
single trade and was discarded as overfit.

Dev grade on this round's window (local): PnL +$9.28, 5 trades, max drawdown 1.50%.
