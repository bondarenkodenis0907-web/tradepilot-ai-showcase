# TradePilot AI

TradePilot helps review exchange activity and test trading ideas. It brings account data, a trade journal, market observations and research results into one application.

The source repository is private. This public showcase contains screenshots of the Russian-language interface and implementation notes; it has no runnable application or test suite.

## What the application does

Users can review imported Bybit data, inspect journal entries, record a trade review and configure strategy scenarios. Background tasks refresh data and run research separately from the web interface. Telegram provides notifications.

The exchange connection is read-only. Research output does not authorize an order or activate a strategy.

## Screenshots

These mobile captures were taken on 3 October 2026. They document that interface revision and are not live account views.

### Strategy scenarios

A user selects a strategy, market and direction to inspect its conditions. Scenario checks do not place trades.

<img src="scenarios.jpg" width="390" alt="TradePilot strategy-scenario screen, captured 3 October 2026" />

### Trade journal

The journal shows imported trading activity and opens individual trade reviews. Figures visible in this historical capture are not independently verified performance results.

<img src="journal.jpg" width="390" alt="TradePilot trade journal, historical capture from 3 October 2026" />

### Overview and system health

The overview capture includes a limited-operation warning. It records the state displayed at capture time, not a current system-health check.

<img src="overview.jpg" width="390" alt="TradePilot overview with a limited-operation warning, captured 3 October 2026" />

## Implementation

PostgreSQL Row Level Security restricts user-owned records. SQL tests check access under different user identities, including attempts to read another user's data.

Research runs in a separate Node.js/Python worker, with its own job and result records. Research history retains negative results alongside the dataset and execution assumptions used for each evaluation.

## Technology and boundaries

The web layer uses React, TypeScript and Next.js-style routing through Vinext/Vite. Supabase provides authentication, PostgreSQL and Edge Functions. Bybit supplies exchange data; Telegram handles notifications; a separate research worker runs Node.js/Python jobs.

[Architecture and data flow](ARCHITECTURE.md) · [Security boundaries and checks](SECURITY_AND_TESTING.md)

The public repository contains no integration credentials or exported account datasets. Research results are not a claim of profitable trading.
