# Dashboard Reading Order

## Core Path

1. `../SKILL.md`
2. `memory/agent-skills/dashboard-skill-evidence.md`
3. `memory/dashboard/architecture.md`
4. `memory/dashboard/module-map.md`
5. `memory/dashboard/commands.md`

## Branching Rules

- if the task touches shared UI or cross-feature patterns, read `memory/dashboard/patterns.md`
- if the task is risky or broad, read `memory/dashboard/risks.md`
- if the task touches extension screens, also read `memory/agent-skills/extensions-surface-map.md`
- if the task crosses the GraphQL contract boundary, also read `memory/shared/integration-map.md`

## Concrete Starting Points

- feature-local work usually starts in `sawa-dashboard/src/<feature>/`
- generated contract work usually touches `sawa-dashboard/src/graphql/`
- extension management work usually starts in `sawa-dashboard/src/extensions/`

## Derived From

- `memory/agent-skills/dashboard-skill-evidence.md`
- `memory/dashboard/architecture.md`
- `memory/dashboard/module-map.md`
- `memory/agent-skills/extensions-surface-map.md`
