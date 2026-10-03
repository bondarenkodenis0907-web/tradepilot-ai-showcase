# Architecture

```mermaid
flowchart TD
    U[User] --> W[Next.js Web App]
    W --> API[Application API Layer]
    API --> AUTH[Supabase Auth]
    API --> DB[(Supabase PostgreSQL)]
    DB --> RLS[Row Level Security]

    API --> MARKET[Market / Exchange APIs]
    API --> TG[Telegram Integration]

    DB --> RW[Research Worker]
    RW --> EVAL[Strategy Evaluation]
    EVAL --> DB

    CI[GitHub Actions CI] --> TESTS[Application + SQL Tests]
    TESTS --> W
    TESTS --> DB
```

## Main components

### Web application
Next.js + TypeScript UI for portfolio overview, journal, strategy scenarios and settings.

### API layer
Typed application endpoints for market data, strategy evaluation, journal workflows and integrations.

### Supabase
Authentication, PostgreSQL persistence, migrations and Row Level Security.

### Research worker
Background research and diagnostics used to evaluate strategy hypotheses and store evidence.

### External integrations
Read-only market/exchange data and Telegram notifications.

### CI
Automated checks for application logic, database behavior and security boundaries.
