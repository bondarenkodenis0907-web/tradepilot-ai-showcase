# TradePilot AI — Technical Showcase

TradePilot AI is a private trading research and analytics platform built with Next.js, TypeScript, Supabase/PostgreSQL and a separate research worker.

The production repository is private. This repository contains only architecture notes, security/testing information and screenshots from the real application.

> The current production UI is in Russian. The screenshots below are from the actual application.

## System Overview

The platform combines several parts of the workflow in one application:

- portfolio and account data
- trade journal
- market data
- strategy scenarios
- research jobs
- research evidence
- system health
- Telegram notifications

Exchange integration is read-only. Research code does not have permission to place trades.

## Screenshots

### Trade Journal

![Trade Journal](journal.jpg)

### Strategy Scenarios

![Strategy Scenarios](scenarios.jpg)

### System Overview

![System Overview](overview.jpg)

## Architecture

```text
User
  ↓
Next.js application
  ↓
Application API
  ├── Supabase Auth
  ├── PostgreSQL
  │     └── Row Level Security
  ├── Market / exchange APIs
  └── Telegram
          ↓
     Research worker
          ↓
   Strategy evaluation
          ↓
   Research evidence
```

A more detailed diagram is available in [ARCHITECTURE.md](ARCHITECTURE.md).

## Key Engineering Decisions

### Read-only exchange access

Exchange integrations are intentionally read-only.

The research system can inspect account, execution and market data, but research logic is kept separate from trade execution.

### Database-level authorization

User-owned data is protected with PostgreSQL Row Level Security.

Authorization is enforced in the database rather than relying only on frontend or API filtering.

### Research isolation

Experimental research results are stored separately from live application state.

A research result does not automatically change active strategy behavior.

### Reproducible research

Strategy ideas are evaluated using defined datasets, execution assumptions and test criteria before they are considered for promotion.

Negative results are kept as research evidence instead of being silently discarded.

### Separate background worker

Long-running research and diagnostic work is handled outside the web request lifecycle.

The web application is responsible for user interaction and application APIs, while the worker handles research tasks.

## Security and Testing

The private production repository includes application-level and SQL-level tests covering areas such as:

- authentication and identity
- Row Level Security
- API boundaries
- database migrations
- research workflows
- strategy evaluation
- signal outcomes
- data freshness
- system health

Additional notes are available in [SECURITY_AND_TESTING.md](SECURITY_AND_TESTING.md).

## Tech Stack

- Next.js
- React
- TypeScript
- Supabase
- PostgreSQL
- Row Level Security
- REST APIs
- Bybit integration
- Telegram Bot API
- GitHub Actions
- Python research worker
- SQL and application-level tests

## Public Repository Scope

This showcase does not include:

- API keys
- exchange credentials
- private trading data
- production database contents
- proprietary strategy implementation
- private production source code

The purpose of this repository is to show the architecture and engineering approach without publishing sensitive project internals.
