# Markov-Switching GARCH for Crisis Volatility Modeling

Bachelor's thesis (VKR) project: modeling financial volatility during crisis periods with a Markov-Switching GARCH model, which lets the volatility process itself switch between hidden regimes ("calm" / "crisis") instead of assuming one fixed dynamic for the whole sample.

## Why two assets

The project runs the same methodology on two very different assets, as a robustness check rather than a comparison between them:

- **S&P 500** (traditional equity index): case study is the COVID-19 crash, March 2020.
- **Bitcoin (BTC-USD)** (high-volatility crypto asset): case study is a series of crypto-specific crashes: 2018, COVID-19 (March 2020), Terra/Luna collapse (May 2022), FTX collapse (November 2022).

The two series do not share a calendar window and are not compared directly against each other. Each asset uses the maximum available daily history for that asset individually. If the same model can cleanly separate "calm" and "crisis" regimes on both a moderately volatile equity index and a much more volatile crypto asset, that is evidence the method generalizes rather than being tuned to one specific series.

## Status

Work in progress, updated as the thesis progresses.

- Block 1: data collection and exploratory analysis (returns, descriptive statistics, stationarity, ARCH effects)
- Block 2: baseline models (ARCH, GARCH, GJR-GARCH)
- Block 3: Markov chains and Markov-Switching GARCH implementation
- Block 4: case studies (S&P 500 / COVID, Bitcoin / crypto crashes)
- Block 5: model comparison and VaR backtesting
- Block 6: write-up and final assembly

## Data

Daily close prices, downloaded manually from Yahoo Finance (the automated route is blocked in some working environments, so data is fetched once and cached locally). Each asset uses its own maximum available history rather than a shared window; see notes above.

Cached as CSV files in `data/`:
- `data/sp500_prices.csv`
- `data/btc_prices.csv`

## Repository structure

Currently a single notebook while the analysis is still being built. As each block's code stabilizes it gets split into reusable modules and per-block notebooks:

```
ms-garch/
├── README.md
├── requirements.txt
├── data/
├── notebooks/          (planned: one notebook per block)
├── src/                (planned: reusable functions once they stop changing)
└── vkr_msgarch.ipynb   (current working notebook)
```

## Setup

```bash
pip install -r requirements.txt
```

Then open `vkr_msgarch.ipynb` and run cells top to bottom. Data is downloaded once and cached; later runs read from the local CSV files.

## Author

Nadezhda Kudinova
