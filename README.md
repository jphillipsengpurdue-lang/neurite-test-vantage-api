# [neurite-test] Vantage API

The Vantage Analytics Platform backend API. Built with FastAPI (Python 3.11).

## Architecture

**Primary datastore:** MySQL 8.0 (RDS, us-east-1)
> Note: there is an ongoing discussion about migrating to PostgreSQL. See ADR in Notion.

**Authentication:** API key (v1) and OAuth 2.0 client credentials (v2, in progress)

**Message queue:** Background jobs use Celery + Redis. A migration to a dedicated
message queue (Kafka or RabbitMQ — decision pending) is in progress.

## API Versions

- **v1** — Stable, maintenance mode. Deprecated June 1 2026.
- **v2** — In development. Target launch: March 30 2026. Currently blocked on security audit.

## Current Sprint (Sprint 14 — March 10-24 2026)

| Issue | Status | Owner |
|---|---|---|
| [P1] OAuth auth endpoint failing in staging | Blocked | Ryan Chen |
| Security audit HIGH-01 remediation | In Progress | Sarah Kim |
| Security audit HIGH-02 remediation | In Progress | Sarah Kim |
| Dashboard load time optimization | In Progress | Dana Torres |
| Null pointer in cohort calculation | In Progress | Sarah Kim |

## Setup

```bash
pip install -r requirements.txt
uvicorn app.main:app --reload
```

## Environment Variables

```
DATABASE_URL=postgresql://...   # or mysql:// for v1 compatibility
REDIS_URL=redis://...
SECRET_KEY=...
```

## Contact

Engineering: ryan.chen@vantage.io | Platform team: #vantage-engineering (Slack)
