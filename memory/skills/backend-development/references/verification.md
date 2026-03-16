# Backend Verification

## Primary Commands

- `pytest`
- `ruff check .`
- `python manage.py get_graphql_schema`
- the relevant helper skills under `sawa-backend/skills/` when the task directly matches them

## Verification Rules

- use the backend command that matches the actual change type
- rebuild schema when GraphQL contracts change
- re-check transaction, locking, migration, and worker-driven paths before claiming completion

## Derived From

- `memory/backend/commands.md`
- `memory/backend/patterns.md`
- `memory/backend/risks.md`
