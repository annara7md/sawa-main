---
name: backend-development
description: Use when work is centered on sawa-backend, including Django models, GraphQL resolvers and mutations, backend tests, transactions, locking, migrations, or backend app infrastructure
---

# Backend Development

## When To Use

Use this skill for work centered on `sawa-backend/`, especially when the task concerns:

- Django and domain modules under `sawa-backend/saleor/`
- backend GraphQL schema, resolvers, dataloaders, and mutations
- backend tests and backend tooling
- transaction, locking, migration, and concurrency-sensitive logic

## Package Files

- `references/reading-order.md`
- `references/boundaries.md`
- `references/verification.md`

## First Files To Read

1. `skills/shared-agent-skill-foundation/SKILL.md`
2. `references/reading-order.md`
3. `references/boundaries.md`
4. `memory/agent-skills/backend-skill-evidence.md`
5. `sawa-backend/AGENTS.md`
6. `sawa-backend/skills/pytest-runner/SKILL.md`
7. `sawa-backend/skills/saleor-django-migration/SKILL.md`

## Allowed Scope

- Work under `sawa-backend/saleor/`
- Backend GraphQL and domain logic
- Backend testing and migration flows confirmed by local skills and AGENTS guidance
- Backend app infrastructure when the task is still backend-owned

## Disallowed Scope

- frontend React structure or UI styling
- dashboard-only routing or component decisions
- inventing extension or app authoring workflows beyond confirmed backend evidence

## Workflow

1. Read the backend evidence and reading-order reference first.
2. Use existing helper skills when the task matches them directly, especially pytest execution and Django schema migrations.
3. Trace GraphQL behavior from `sawa-backend/saleor/graphql/` into the owning domain module.
4. If dashboard-visible behavior is involved, also read `memory/shared/integration-map.md`.

## Verification

- Use `references/verification.md`.
