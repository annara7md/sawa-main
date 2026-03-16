---
name: dashboard-development
description: Use when work is centered on sawa-dashboard, including React UI, dashboard GraphQL client usage, frontend tests, generated dashboard GraphQL artifacts, or existing dashboard extension screens
---

# Dashboard Development

## When To Use

Use this skill for work centered on `sawa-dashboard/`, especially when the task concerns:

- React UI behavior
- frontend feature modules
- dashboard GraphQL client and generated types
- frontend tests
- dashboard extension screens under `sawa-dashboard/src/extensions/`

## Package Files

- `references/reading-order.md`
- `references/boundaries.md`
- `references/verification.md`

## First Files To Read

1. `skills/shared-agent-skill-foundation/SKILL.md`
2. `references/reading-order.md`
3. `references/boundaries.md`
4. `memory/agent-skills/dashboard-skill-evidence.md`
5. `sawa-dashboard/AGENTS.md`

## Allowed Scope

- Work under `sawa-dashboard/src/`
- Dashboard commands from `sawa-dashboard/package.json`
- Generated frontend GraphQL artifact handling
- Existing dashboard extension management views and related frontend routes

## Disallowed Scope

- Django models, migrations, and backend transaction rules
- Celery worker behavior
- inventing app or extension build workflows not confirmed by local evidence

## Workflow

1. Read the dashboard evidence and reading-order reference first.
2. Use `sawa-dashboard/AGENTS.md` for local command and implementation constraints.
3. Follow real feature-module boundaries from the memory files named in `references/reading-order.md`.
4. If the task crosses the GraphQL boundary, also read `memory/shared/integration-map.md`.

## Verification

- Use `references/verification.md`.
