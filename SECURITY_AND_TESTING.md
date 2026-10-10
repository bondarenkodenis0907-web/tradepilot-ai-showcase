# Security and testing

The checks below run in the private TradePilot repository. The public showcase contains no executable test suite.

## Access boundaries

| Boundary                        | Implementation                                               | Verification                                                                   |
| ------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------------------------ |
| User-owned records              | PostgreSQL Row Level Security with ownership checks          | SQL tests with different user identities, including cross-user access attempts |
| Exchange operations             | Read-only Bybit access for the current application           | Checks for the read-only connection and research execution constraints         |
| Private integration credentials | Backend handling; the browser receives public configuration  | Configuration validation, API boundary tests and repository secret scanning    |
| Research results                | Separate job/result records and explicit promotion decisions | Tests for research states, data boundaries and evaluation behavior             |

Secret scanning covers known patterns; credentials and account datasets remain outside this showcase.

## Checks in CI

Application checks cover lint, TypeScript, production compilation and regression tests. Supabase checks rebuild an isolated database from migrations and run SQL tests against it. Database tests use local test identities rather than production accounts.

Examples of behavior covered in the private repository:

- one user cannot read or alter another user's owner-scoped records;
- a temporary health-check timeout gets a bounded retry, while an authentication error does not;
- research calculations respect the defined data boundary and execution assumptions;
- migration replay and database-level permissions are checked independently of the frontend.

## Interpreting research results

Negative evaluations remain in the research history. Development results and future holdout evaluation are kept distinct, and a result cannot by itself grant trading authority.

These checks establish behavior for the tested revision. They do not certify security or demonstrate trading profitability.
