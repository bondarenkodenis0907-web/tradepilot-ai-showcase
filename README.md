# TradePilot AI

TradePilot helps review exchange activity and test trading ideas. It brings account data, a trade journal, market observations and research results into one application.

The source repository is private. This showcase contains screenshots and a description of the implementation; it cannot be used to build or run the application. The screenshots show the Russian-language interface.

## What the application does

Users can review imported Bybit data, inspect journal entries, record a trade review and configure strategy scenarios. Background tasks refresh data and run research separately from the web interface. Telegram provides notifications.

The exchange connection is read-only. Research output does not authorize an order or activate a strategy.

## Screenshots

### Trade journal

![Trade journal](journal.jpg)

### Strategy scenarios

![Strategy scenarios](scenarios.jpg)

### Overview

![Overview](overview.jpg)

## Decisions behind the implementation

**Keep ownership checks in the database.** User-owned records have PostgreSQL Row Level Security policies. A browser filter is useful for the interface, but it cannot be the access boundary. SQL tests exercise access with different user identities.

**Separate research from web requests.** Research jobs use a separate Node.js/Python worker. This keeps longer calculations out of the page request and gives them their own job and result records.

**Keep failed ideas in the research history.** An evaluation uses defined data and execution assumptions. Negative results are retained; a disappointing result does not justify changing the rule and presenting the rerun as an independent test.

**Handle temporary failures without hiding persistent ones.** Market refreshes have a concurrency limit. The health check retries a database timeout once, while authentication errors and repeated failures remain visible. These behaviors have regression tests.

## Technology and boundaries

The web layer uses React, TypeScript and Next.js-style routing through Vinext/Vite. Supabase provides authentication, PostgreSQL and Edge Functions. Bybit supplies exchange data; Telegram handles notifications; a separate research worker runs Node.js/Python jobs.

[Architecture and data flow](ARCHITECTURE.md) · [Security boundaries and checks](SECURITY_AND_TESTING.md)

## What this showcase can demonstrate

The screenshots show the interface, and the notes explain how responsibilities are divided. Automated checks run in the private repository, so visitors cannot reproduce them from this showcase. Screenshots also do not establish strategy profitability or prove that every production scenario has been tested.

The public repository contains no source implementation, production credentials or account datasets.
