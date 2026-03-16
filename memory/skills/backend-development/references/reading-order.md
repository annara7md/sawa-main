# Backend Reading Order

## Core Path

1. `../SKILL.md`
2. `memory/agent-skills/backend-skill-evidence.md`
3. `memory/backend/architecture.md`
4. `memory/backend/domain-map.md`
5. `memory/backend/commands.md`

## Branching Rules

- if the task is transaction- or integrity-sensitive, read `memory/backend/patterns.md`
- if the task is migration- or regression-sensitive, read `memory/backend/risks.md`
- if the task affects dashboard-visible behavior, read `memory/backend/integration-touchpoints.md`
- if the task is app-domain specific, also read `memory/agent-skills/apps-operation-map.md`

## Concrete Starting Points

- domain behavior usually starts in `sawa-backend/saleor/<domain>/`
- GraphQL contract work usually starts in `sawa-backend/saleor/graphql/`
- app lifecycle work usually starts in `sawa-backend/saleor/app/` and `sawa-backend/saleor/graphql/app/`

## Derived From

- `memory/agent-skills/backend-skill-evidence.md`
- `memory/backend/architecture.md`
- `memory/backend/domain-map.md`
- `memory/backend/integration-touchpoints.md`
- `memory/agent-skills/apps-operation-map.md`
