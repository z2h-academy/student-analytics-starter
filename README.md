# Analytics Starter — Student Workspace

This is your workspace for the **Analytics Starter** project: your first
end-to-end data warehouse.

- **Working path:** `/workspaces/student-analytics-starter` (Codespaces or VM)
- **Project page:** https://z2h-academy.dev/es/roadmap/analytics-starter
- **Reference content:** private. TUTOR reads it and guides you; you do not
  need to clone it.

## What is this repo

This repo starts **empty on purpose**. During the project you will build,
with TUTOR's guidance:

- a PostgreSQL star schema (`songplays` + four dimensions);
- an idempotent Python ETL for the synthetic Melodix dataset;
- the verification notebook that proves the row counts and match coverage.

The reference implementation is not distributed here: TUTOR reads it and
helps you construct your own version, step by step.

## How to start

```bash
cd /workspaces/student-analytics-starter
opencode
```

Ask TUTOR to start the **Analytics Starter** project. The first response is
the theoretical base (Melodix, star schema, grain, keys), followed by a
checkpoint. After the checkpoint, TUTOR presents the project plan and asks
whether you want to execute it automatically or manually.

> Do not clone or copy the reference content: it is private and is accessed
> only through the harness.

## Requirements

| Requirement | How to check |
|---|---|
| Python 3.9+ (3.11+ for pandas 3.x) | `python3 --version` |
| PostgreSQL 12+ (validated on 16) | `psql --version` or `pg_isready` |
| Git | `git --version` |
| Docker (optional, to run PostgreSQL locally) | `docker --version` |

## What you will learn

- Model a star schema and choose the fact table grain.
- Use natural keys and an identity surrogate key without breaking idempotency.
- Build an ETL that can be re-run safely.
- Verify a load with counts, match coverage and referential integrity.
- Defend every modeling decision with evidence.

## Repo rules

- Never commit `.env`, `.venv`, `data/` or generated artifacts.
- The workspace is yours: build the files during the sessions.
- Keep the project at `/workspaces/student-analytics-starter`.
