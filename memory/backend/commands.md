# Backend Commands

- scope: backend
- purpose: Capture the backend commands most likely to matter during development, validation, and schema work.
- read_when: Read before running backend setup, server, worker, test, lint, migration, or schema commands.
- source_paths: `sawa-backend/AGENTS.md`, `sawa-backend/pyproject.toml`
- last_reviewed: 2026-03-14

## Summary

Primary backend commands:

- `uv sync`: install Python dependencies
- `python manage.py runserver`: run Django development server
- `uvicorn saleor.asgi:application --reload`: run ASGI app with reload
- `celery --app saleor.celeryconf:app worker -E`: run Celery worker
- `pytest`: run tests
- `ruff check .`: lint and static checks
- `python manage.py get_graphql_schema`: build GraphQL schema file

Useful task aliases also appear in `sawa-backend/pyproject.toml` under `tool.poe.tasks`, including `start`, `worker`, `scheduler`, `build-schema`, `migrate`, and `test`.

## Key Paths

- `sawa-backend/AGENTS.md`
- `sawa-backend/pyproject.toml`
- `sawa-backend/manage.py`
- `sawa-backend/saleor/asgi/`

## Rules and Patterns

- Use schema build commands when GraphQL contracts change.
- Prefer the documented commands from `sawa-backend/AGENTS.md` and `sawa-backend/pyproject.toml` over guesswork.
- Remember that some flows depend on Celery workers or schedulers, not only the web server.

## Risks

- Backend work can look correct in request handling while still failing in worker-driven follow-up paths.
- Schema and runtime behavior can drift if GraphQL-related changes are not verified against the right command.
