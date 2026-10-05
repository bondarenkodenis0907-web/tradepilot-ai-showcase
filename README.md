
# TradePilot AI — Technical Showcase

TradePilot AI is a private trading research and analytics platform built with Next.js, TypeScript, Supabase/PostgreSQL and automated research tooling.

This repository is a public technical showcase. The production source code remains private.

> Note: the current production UI is in Russian. The screenshots below show the real application as it exists today. An English UI locale is planned.

## What the system does

- Authenticates users with Supabase Auth
- Isolates user data with Row Level Security
- Reads portfolio and execution data from Bybit in read-only mode
- Maintains a trade journal and strategy evaluation workflow
- Runs automated research and diagnostic jobs
- Integrates Telegram notifications
- Stores and processes market and strategy data in PostgreSQL
- Uses CI and automated tests for application, database and security checks

## Screenshots

### Trade Journal

![Trade Journal](journal.jpg)

### Strategy Scenarios

![Strategy Scenarios](scenarios.jpg)

### System Overview

![System Overview](overview.jpg)

## Engineering Highlights

### Next.js + TypeScript

The web application uses a typed application layer with separate UI, API and domain logic.

### Supabase + PostgreSQL

Supabase provides authentication, PostgreSQL storage and Row Level Security.

Database migrations and SQL tests are part of the development workflow.

### API Integrations

The platform integrates external market data and trading account data while keeping exchange access read-only.

### Research Workers

Background research tooling evaluates strategy hypotheses and produces reproducible evidence rather than directly placing trades.

### Security

The project includes:

- Row Level Security checks
- Request guards and rate limits
- Controlled public configuration
- Encrypted Telegram credentials
- Read-only exchange access
- API and identity boundary tests
- Separation between research logic and trade execution

### CI and Testing

The private production repository includes GitHub Actions plus application-level and SQL-level tests covering:

- Authentication and identity
- Row Level Security isolation
- API boundaries
- Database migrations
- Strategy evaluation
- Research workflows
- Signal outcomes
- Security hardening
- Data freshness
- System health

## Architecture

See [ARCHITECTURE.md](ARCHITECTURE.md).

## Security and Testing

See [SECURITY_AND_TESTING.md](SECURITY_AND_TESTING.md).

## Tech Stack

- Next.js
- TypeScript
- React
- Supabase
- PostgreSQL
- Row Level Security
- REST / API integrations
- Telegram Bot API
- GitHub Actions
- Python research worker
- SQL and application-level tests

## Project Status

The platform is under active development and is used as a private research and analytics system.

The public showcase intentionally excludes:

- API keys and credentials
- Private trading data
- Exchange credentials
- Proprietary strategy implementation details
- Production database contents
- Private production source code

## Role

Independent full-stack project.

Main focus areas:

- Architecture
- Supabase / PostgreSQL
- Authentication and RLS
- API integrations
- Background research workflows
- Testing and CI
- Troubleshooting
- Security

## Key Engineering Decisions

- Exchange integrations are read-only. Research and trade execution are intentionally separated.
- PostgreSQL Row Level Security is used as a database-level authorization boundary.
- Research workers store experimental results separately from live application state.
- Strategy changes are evaluated before promotion rather than modifying live behavior directly.
