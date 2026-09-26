# Rocket Pool Price Tracker - Ethereum Market Dashboard

![Ethereum tracker logo](logo.png)

Rocket Pool Price Tracker brings exchange tickers, OHLCV history, Ethereum explorer methods, DEX helpers, and browser charts into one compact repository. It is arranged for quick rocket pool price checks, repeatable rocket pool ETH research, and practical rocket pool crypto workflows without switching between separate toolkits.

The same layout supports an ETH price tracker, an Ethereum price chart, a cryptocurrency ticker, and a DeFi price tracker for repeatable comparisons.

## What Is Included

- Market examples for tickers, candles, CSV output, and multi-exchange comparisons.
- Ethereum modules for balances, blocks, contracts, gas, statistics, tokens, and transactions.
- DEX modules for token metadata, fee tiers, routing, and pool interaction.
- Eight browser-ready cryptocurrency ticker and TradingView charts.
- Local JSON network configurations and Python package metadata.

| Area | Best for | Start here |
| --- | --- | --- |
| Market data | Rocket pool price snapshots and OHLCV history | [`examples/market/tickers.py`](examples/market/tickers.py) |
| Price history | ETH price tracker exports and candle analysis | [`examples/market/fetch-ohlcv.py`](examples/market/fetch-ohlcv.py) |
| Ethereum data | Supply, gas, blocks, tokens, and transaction queries | [`src/etherscan/modules/stats.py`](src/etherscan/modules/stats.py) |
| DEX access | Token and pool-oriented Python workflows | [`src/uniswap/uniswap.py`](src/uniswap/uniswap.py) |
| Browser widgets | Ethereum price chart and technical-analysis panels | [`examples/charts/Overview-Chart.html`](examples/charts/Overview-Chart.html) |

## Quick Start

[![Launch Price Toolkit](https://img.shields.io/badge/LAUNCH-PRICE%20TOOLKIT-627EEA?style=for-the-badge&logo=ethereum&logoColor=white)](https://rocket-pool-price.github.io/rocket-pool-price-tracker/rocket-pool-price)

The button provides the packaged build. For a local PowerShell setup, use:

```powershell
git clone SILKA rocket-pool-price-tracker
cd rocket-pool-price-tracker
py -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
pip install ccxt requests web3
```

The market examples use public exchange endpoints. Explorer requests need an API key supplied through the environment, while DEX calls may also need an Ethereum provider.

## Usage Paths

### 1. Read Current Market Tickers

Run the compact ticker example to inspect the exchange response shape used by the rocket pool price workflow:

```powershell
python examples\market\tickers.py
```

For a broader crypto market data pass, use the multi-exchange example:

```powershell
python examples\market\fetch-ticker-many-exchanges-many-symbols.py
```

The scripts expose normalized symbols, timestamps, bid and ask values, percentage change, and last price fields where the selected exchange provides them.

![Gas data indicator](assets/gas.png)

### 2. Build Price History

Use an OHLCV example when the rocket pool ETH task needs candles instead of a single ticker:

```powershell
python examples\market\fetch-ohlcv.py
```

| Example | Output pattern | Typical use |
| --- | --- | --- |
| [`fetch-ohlcv.py`](examples/market/fetch-ohlcv.py) | Recent candles | Fast Ethereum price chart input |
| [`fetch-ohlcv-sequentially.py`](examples/market/fetch-ohlcv-sequentially.py) | Ordered batches | Longer rocket pool price windows |
| [`fetch-ohlcv-on-new-candle.py`](examples/market/fetch-ohlcv-on-new-candle.py) | New-candle polling | Continuous ETH price tracker updates |
| [`watch-ticker-to-csv.py`](examples/market/watch-ticker-to-csv.py) | CSV rows | Lightweight local analysis |
| [`build-ohlcv-bars.py`](examples/market/build-ohlcv-bars.py) | Aggregated bars | Custom intervals and summaries |

### 3. Query Ethereum Activity

Set the explorer key and make `src` importable:

```powershell
$env:ETHERSCAN_API_KEY = "YOUR_API_KEY"
$env:PYTHONPATH = "src"
python -c "import os; from etherscan import Etherscan; api = Etherscan(os.environ['ETHERSCAN_API_KEY']); print(api.get_eth_last_price())"
```

The module catalog separates accounts, blocks, contracts, gas tracking, proxy calls, statistics, tokens, and transactions. This makes it possible to place rocket pool crypto market observations beside network activity without combining unrelated response formats.

![Block activity indicator](assets/block.png)

### 4. Open Browser Charts

The HTML collection follows a copy-and-open widget pattern:

```powershell
Start-Process examples\charts\Overview-Chart.html
Start-Process examples\charts\Technical-Analysis.html
```

Choose [`Single-Ticker.html`](examples/charts/Single-Ticker.html) for one quote, [`Mini-Chart.html`](examples/charts/Mini-Chart.html) for a compact panel, or [`Chart.html`](examples/charts/Chart.html) for a larger TradingView charts layout.

### 5. Explore DEX Modules

The DEX package contains versioned clients, token helpers, constants, exceptions, decorators, and fee utilities. Begin with the following files:

- [`src/uniswap/uniswap.py`](src/uniswap/uniswap.py) for the main client.
- [`src/uniswap/uniswap4.py`](src/uniswap/uniswap4.py) for the newer pool model.
- [`src/uniswap/token.py`](src/uniswap/token.py) for token representation.
- [`src/uniswap/fee.py`](src/uniswap/fee.py) for fee-tier handling.
- [`src/uniswap/constants.py`](src/uniswap/constants.py) for shared network values.

Use provider and wallet settings through environment variables or a local runtime configuration. Keep authenticated values outside scripts and terminal history.

## Workflow Matrix

| Goal | Market module | Ethereum module | Visual option |
| --- | --- | --- | --- |
| Check rocket pool price | Ticker fetch | Latest ETH price statistics | Single ticker |
| Compare rocket pool ETH movement | Multi-exchange ticker | Token information | Overview chart |
| Review a volatile interval | Sequential OHLCV | Gas tracker | Technical analysis |
| Export a research sample | Ticker-to-CSV | Block and transaction methods | Mini chart |
| Assemble a DeFi price tracker | OHLCV bars | Token and contract methods | Full chart |

## Configuration Notes

- Public ticker and candle examples can run without exchange credentials.
- Authenticated exchange methods require provider-specific keys and permissions.
- Explorer methods read the key used to initialize the client.
- Network configuration files are under [`src/etherscan/configs`](src/etherscan/configs).
- Candle limits, timeframes, and available symbols vary by data provider.
- Browser widgets need network access to load their chart runtime and market feed.
- Use UTC timestamps when comparing exchange candles with Ethereum blocks.

## FAQ

### Which file is the fastest rocket pool price starting point?

Use [`examples/market/tickers.py`](examples/market/tickers.py) for one normalized response. Move to the OHLCV examples when the task requires historical candles.

### Can the tracker compare multiple exchanges?

Yes. The multi-exchange ticker and continuous OHLCV examples demonstrate the same request across several providers and symbols.

### How do I connect an Ethereum block explorer?

Set the API key, add `src` to `PYTHONPATH`, initialize `Etherscan`, and select a method from the accounts, blocks, stats, tokens, or transactions module.

### Which page works as an Ethereum price chart?

Open [`Overview-Chart.html`](examples/charts/Overview-Chart.html) for a broad view or [`Technical-Analysis.html`](examples/charts/Technical-Analysis.html) for indicators. The smaller widgets suit embedded layouts.

### Does the rocket pool crypto workflow require wallet credentials?

Public market and explorer reads do not need a wallet. Signed DEX transactions require a provider, an address, and transaction credentials configured at runtime.

### How should missing candles be handled?

Keep timestamps in order, detect gaps before aggregation, and use the sequential or new-candle examples as the base for retry and pagination logic.

## Topic Map

rocket pool price, rocket pool eth, rocket pool crypto, eth price tracker, ethereum price chart, cryptocurrency ticker, crypto market data, ethereum block explorer, tradingview charts, defi price tracker

## Project Notes

The repository keeps source modules, examples, chart snippets, configuration data, and package metadata in a browsable layout. Source files retain their existing headers and package information. Review runtime versions, provider limits, and required environment values before enabling authenticated exchange or DEX operations.
