# Backend Skill Evidence

- scope: shared
- purpose: Preserve confirmed local evidence for what the backend-development skill must cover and what it must not claim without support.
- read_when: Read immediately before authoring or revising `skills/backend-development/SKILL.md`.
- source_paths: `memory/backend/architecture.md`, `memory/backend/domain-map.md`, `memory/backend/commands.md`, `memory/backend/patterns.md`, `memory/backend/risks.md`, `memory/backend/integration-touchpoints.md`, `sawa-backend/AGENTS.md`, `sawa-backend/pyproject.toml`, `sawa-backend/skills/pytest-runner/SKILL.md`, `sawa-backend/skills/saleor-django-migration/SKILL.md`
- last_reviewed: 2026-03-14

## Confirmed Evidence

- `sawa-backend` is a Django, GraphQL, Celery, and PostgreSQL backend organized around many domain modules under `sawa-backend/saleor/`.
- The heaviest analyzed backend area is `sawa-backend/saleor/graphql/`, followed by domains such as `order`, `product`, `payment`, `checkout`, and `account`.
- Local backend guidance explicitly emphasizes `F()` expressions, `select_for_update()`, transaction boundaries, DataLoader usage, and migration discipline.
- Commands confirmed locally include `uv sync`, `python manage.py runserver`, `uvicorn saleor.asgi:application --reload`, `pytest`, `ruff check .`, and `python manage.py get_graphql_schema`.
- Existing backend skills already encode strong operational expectations for pytest usage and Django schema migration generation.

## Open Gaps

- No single root skill currently unifies backend architecture, command selection, local helper skills, and GraphQL/backend boundary guidance.
- The current evidence is rich for backend development itself, but not identical to app-building or extension-management flows that cross into app infrastructure.

## Local Paths Reviewed

- `memory/backend/architecture.md`
- `memory/backend/domain-map.md`
- `memory/backend/commands.md`
- `memory/backend/patterns.md`
- `memory/backend/risks.md`
- `memory/backend/integration-touchpoints.md`
- `sawa-backend/AGENTS.md`
- `sawa-backend/pyproject.toml`
- `sawa-backend/skills/pytest-runner/SKILL.md`
- `sawa-backend/skills/saleor-django-migration/SKILL.md`
