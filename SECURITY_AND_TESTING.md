# Security and Testing

The production project uses several layers of protection and automated verification.

## Security controls

- Supabase Row Level Security for user-owned data
- read-only exchange access
- request guards and per-user rate limits
- controlled exposure of public Supabase configuration
- encrypted Telegram credentials
- separation between advisory/research logic and trade execution
- identity and API boundary checks

## Automated testing

The private production repository contains both application-level and SQL-level tests.

Coverage includes:
- account identity
- API boundaries
- RLS isolation
- database migrations
- strategy evaluation
- research workflows
- signal outcomes
- data freshness
- system health
- security hardening

## Public showcase policy

This repository does not contain production secrets, private user data, exchange credentials, or proprietary strategy source code.
