**English** | [Español](README.es.md)

# Analytics Starter — Student Workspace

This is your workspace for the **Analytics Starter** project: your first
end-to-end data warehouse.

- **Working path:** `/workspaces/student-analytics-starter` (Codespaces or VM)
- **Project page:** https://z2h-academy.com/es/roadmap/analytics-starter
- **Reference content:** private. TUTOR reads it and guides you; you do not
  need to clone it.

## What is this repo

This repo ships the **synthetic dataset** of the project and the workspace
where you build the pipeline:

- `data/`: the Melodix sources (160 song JSON files and 30 daily log files).
- everything else is built during the project with TUTOR's guidance: the
  PostgreSQL star schema (`songplays` + four dimensions), the idempotent
  Python ETL and the verification notebook.

The reference implementation is not distributed here: TUTOR reads it and
helps you construct your own version, step by step.

### The dataset

| Source | Path | Files | Grain |
|---|---|---|---|
| Song catalog | `data/song_data/<A>/<B>/<C>/<song_id>.json` | 160 | one song per file |
| App activity | `data/log_data/2025/01/2025-01-01-events.json` | 30 | one event per line (JSONL) |

The dataset is fully synthetic (CC0), built in UTC from a fixed seed and
versioned: it is part of the repository, so you do not generate it. Do not
edit it. Every count in the project (8,248 events, 7,061 `NextSong`, 4,544
matched) comes from these exact files.

## How to start

### Option A: GitHub Codespaces (recommended)

GitHub Codespaces gives you a ready-to-use cloud environment, so you do not
need to install Python, Git or Docker on your machine.

Open the repository in a codespace:

[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/z2h-academy/student-analytics-starter)

Or start one from the terminal, if you have the GitHub CLI installed:

```bash
gh codespace create -r z2h-academy/student-analytics-starter
```

The first launch takes a few minutes while GitHub builds the container. When
the editor opens, wait for the terminal prompt to appear and confirm the
repository is there:

```bash
pwd        # /workspaces/student-analytics-starter
ls data    # log_data  song_data
```

Then start the agent from the repository root:

```bash
opencode
```

> The repository does not ship a `.devcontainer/` configuration, so the
> codespace uses the default image. If the environment detail matters for your
> session, run `devcontainer-info` in the terminal to see which image is in
> use.

To reuse the codespace later, open it again from
<https://github.com/codespaces> or with `gh codespace code`. Free accounts have
a monthly quota of core hours and storage; stopping the codespace when you are
done keeps it from being consumed. Codespaces are deleted automatically after
a retention period (30 days by default), and you can delete one early with
`gh codespace delete`.

### Option B: local environment

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

> The database setup (PostgreSQL) is not covered here: TUTOR walks you through
> it from the project docs when the session reaches that step.

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

- Never commit `.env` or `.venv`.
- `data/` is versioned: keep it unmodified, so `git status` stays clean.
- The workspace is yours: build the scripts during the sessions.
- Keep the project at `/workspaces/student-analytics-starter`.
