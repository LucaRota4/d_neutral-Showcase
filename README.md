# d_neutral: delta-neutral funding rate scanner

**Live app:** [deltaneutral-dex-funding.streamlit.app](https://deltaneutral-dex-funding.streamlit.app/) · Personal project · [LucaRota4](https://github.com/LucaRota4) & [ElioMargiotta](https://github.com/ElioMargiotta)

> This repository is a showcase. The source code is not public. Only this description is published. The live app is the best way to see the result.

## What is it about?

Perpetual futures have no expiry. To keep their price close to the spot price, longs and shorts pay each other a **funding rate** at regular intervals, and this rate differs from one exchange to another for the same asset.

The strategy: open a **long** where funding is lowest and a **short** of the same size where funding is highest. Price moves cancel each other out (the position is delta-neutral), and you collect the difference in funding.

The app scans 12 exchanges in real time and ranks the best opportunities.

## Features

- **Opportunities table:** for every pair listed on at least two exchanges, the best long / short venues, both hourly rates and the annualized spread, sortable by any column.
- **Funding matrix:** the annualized rate of every pair on every exchange, colored by sign.
- **Filters:** choice of exchanges, pair search, minimum number of venues, and a cap to hide unrealistic spreads (illiquid or newly listed pairs).
- **Overview:** best pair, its spread and the position to open.

## Exchanges

| Type | Exchanges |
|---|---|
| DEX | Hyperliquid, Vest, dYdX, Paradex, Aster, Lighter, Backpack, Extended, Orderly |
| CEX | Gate, Bybit, Binance |

## Technical choices

| Topic | Choice |
|---|---|
| Stack | Python, Streamlit, pandas |
| Data | Public market-data APIs only, fetched in parallel with `aiohttp`; a failing exchange does not block the others |
| Normalization | Every exchange pays funding on its own schedule (1, 2, 4 or 8 h, sometimes per market): all rates are converted to an hourly rate, then annualized |
| Caching | Results cached for 5 minutes |
| Hosting | Streamlit Community Cloud |

## Disclaimer

Trading fees, liquidity, slippage and the price gap between exchanges are not taken into account. For information only, not investment advice.

## Contact

For any further information about this project, feel free to contact me by e-mail: **lu.rota@sunrise.ch**
