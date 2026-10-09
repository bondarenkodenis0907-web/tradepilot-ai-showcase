# Security and testing

These notes describe boundaries and checks in the private TradePilot repository. This public showcase contains no executable test suite, so the checks below cannot be reproduced from this repository alone.

## Access boundaries

| Boundary | Implementation | Verification |
|---|---|---|
| User-owned records | PostgreSQL Row Level Security with ownership checks | SQL tests with different user identities, including cross-user access attempts |
| Exchange operations | Read-only Bybit access for the current application | Checks for the read-only connection and research execution constraints |
| Private integration credentials | Backend handling; the browser receives public configuration | Configuration validation, API boundary tests and repository secret scanning |
| Research results | Separate job/result records and explicit promotion decisions | Tests for research states, data boundaries and evaluation behavior |

Secret scanning catches known patterns. A passing scan is not proof that every possible secret or sensitive record is absent.

## Checks in CI

Application checks cover lint, TypeScript, production compilation and regression tests. Supabase checks rebuild an isolated database from migrations and run SQL tests against it. Database tests use local test identities rather than production accounts.

Examples of behavior covered in the private repository:

- one user cannot read or alter another user's owner-scoped records;
- a temporary health-check timeout gets a bounded retry, while an authentication error does not;
- research calculations respect the defined data boundary and execution assumptions;
- migration replay and database-level permissions are checked independently of the frontend.

Checks report the result for a particular revision. They do not make every branch protected, guarantee a successful production release or replace verification of deployed settings.

## Interpreting research results

Negative evaluations remain in the research history. Development results and future holdout evaluation are kept distinct, and a result cannot by itself grant trading authority.

This is a description of the engineering process, not a claim of profitable trading or a security certification.

## Public material

Only interface screenshots and explanatory notes are included here. Source code, strategy implementation, credentials, user records and exchange datasets remain outside the showcase.
