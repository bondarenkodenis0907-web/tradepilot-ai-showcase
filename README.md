# TradePilot AI

TradePilot helps review exchange activity and test trading ideas. It brings account data, a trade journal, market observations and research results into one application.

The source repository is private. This public showcase contains screenshots of the English interface and implementation notes; it has no runnable application or test suite.

## What the application does

Users can review imported Bybit data, inspect journal entries, record a trade review and configure strategy scenarios. Background tasks refresh data and run research separately from the web interface. Telegram provides notifications.

The exchange connection is read-only. Research output does not authorize an order or activate a strategy.

## Screenshots

Desktop captures from the running application, taken on 20 October 2026 with the interface set to English. Saved strategy names can retain their original language. These images document the interface at capture time; they are not live market data or evidence of trading performance.

### Market and indicators

A watchlist shows closed-candle prices, EMA, RSI, ATR and volume relative to its average. Each card identifies its timeframe and scanner state.

<img src="https://github.com/user-attachments/assets/ebb1bb8a-2e06-4795-8f96-fbfce1825424" width="960" alt="TradePilot market watchlist and indicators in English, captured 20 October 2026" />

### Strategy scenarios

A user selects a strategy, symbol and direction to inspect conditions and scenario history. Shadow evaluations record subsequent price observations, not executed trades or profit. Scenario checks do not place orders.

<img src="https://github.com/user-attachments/assets/7bf42482-1e9f-48af-a402-98c3a9787f55" width="960" alt="TradePilot scenario checks in the English interface, captured 20 October 2026" />

### Manual entry plan

The form accepts a planned entry, stop, target and risk percentage for a context and risk check. The balance field is blank in this capture. No calculation was submitted to create this screenshot.

<img src="https://github.com/user-attachments/assets/3c92d4c5-8e20-42bc-bafa-c099f609da35" width="960" alt="TradePilot manual entry plan in English with the balance field blank, captured 20 October 2026" />

## Implementation

PostgreSQL Row Level Security restricts user-owned records. SQL tests check access under different user identities, including attempts to read another user's data.

Research runs in a separate Node.js/Python worker, with its own job and result records. Research history retains negative results alongside the dataset and execution assumptions used for each evaluation.

## Technology and boundaries

The web layer uses React, TypeScript and Next.js-style routing through Vinext/Vite. Supabase provides authentication, PostgreSQL and Edge Functions. Bybit supplies exchange data; Telegram handles notifications; a separate research worker runs Node.js/Python jobs.

[Architecture and data flow](ARCHITECTURE.md) · [Security boundaries and checks](SECURITY_AND_TESTING.md)

The public repository contains no integration credentials or exported account datasets. Research results are not a claim of profitable trading.
