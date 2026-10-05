# Security and Testing

This document describes the main security boundaries and how they are verified in the private production repository.

## Security Boundaries

### User Data

User-owned data is protected with PostgreSQL Row Level Security.

Authorization is enforced at the database layer so access does not depend only on frontend or API filtering.

### Exchange Access

The research system uses read-only exchange access.

Research and diagnostic code does not have permission to place trades.

### Browser Access

Private credentials are not exposed to browser code.

The browser only receives configuration that is safe to publish.

### Telegram

Telegram credentials are stored outside the browser and are not included in this public repository.

### Research Separation

Research results are stored separately from active application state.

An experimental result cannot directly change live strategy behavior.

## Testing

The private repository uses both application-level and SQL-level tests.

The test suite covers:

- authentication and user identity
- Row Level Security isolation
- API access boundaries
- database migrations
- strategy evaluation
- research workflows
- signal outcome logic
- data freshness
- system health
- regression checks for security-sensitive behavior

## CI

GitHub Actions runs automated checks before changes are accepted.

Application and database checks are kept separate so database security can be tested independently from the web application.

## Public Repository Scope

This showcase intentionally excludes:

- production secrets
- exchange credentials
- private user data
- private trading data
- production database contents
- proprietary strategy implementation
- private production source code
