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

![Trade Journal](screenshots/journal.jpg)

### Strategy Scenarios

![Strategy Scenarios](screenshots/scenarios.jpg)

### System Overview

![System Overview](screenshots/overview.jpg)

## Engineering Highlights

### Next.js + TypeScript
The web application uses a typed application layer with separate UI, API and domain logic.

### Supabase + PostgreSQL
Supabase provides authentication, PostgreSQL storage and Row Level Security. Database migrations and SQL tests are part of the development workflow.

### API integrations
The platform integrates external market data and trading account data while keeping exchange access read-only.

### Research workers
Background research tooling evaluates strategies and produces reproducible evidence rather than directly placing trades.

### Security
The project includes:
- Row Level Security checks
- request guards and rate limits
- controlled public configuration
- encrypted Telegram credentials
- read-only exchange access
- tests for API and identity boundaries

### CI and testing
The private production repository includes GitHub Actions plus application-level and SQL-level tests covering:
- authentication and identity
- RLS isolation
- API boundaries
- strategy logic
- research workflows
- security hardening
- data freshness and system health

## Architecture

See [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md).

## Security and Testing

See [docs/SECURITY_AND_TESTING.md](docs/SECURITY_AND_TESTING.md).

## Tech Stack

- Next.js
- TypeScript
- React
- Supabase
- PostgreSQL
- Row Level Security
- REST/API integrations
- Telegram Bot API
- GitHub Actions
- Python research worker
- SQL and application-level tests

## Project Status

The platform is under active development and used as a private research and analytics system.

The public showcase intentionally excludes:
- API keys and credentials
- private trading data
- proprietary strategy implementation details
- production database contents
- private source code

## Role

Independent full-stack project.

Focus areas:
- architecture
- Supabase/PostgreSQL
- authentication and RLS
- API integrations
- background research workflows
- testing and CI
- troubleshooting and security
