---
name: apps-development
description: Use when the task is about the existing app domain in this workspace, including the Saleor app backend domain, app GraphQL schema and mutations, app installation and token flows, or dashboard app-related extension routes
---

# Apps Development

## When To Use

Use this skill when the task is clearly about confirmed app-related surfaces already present in this workspace.

## Package Files

- `references/operations-map.md`
- `references/boundaries.md`
- `references/verification.md`

## First Files To Read

1. `skills/shared-agent-skill-foundation/SKILL.md`
2. `references/operations-map.md`
3. `references/boundaries.md`
4. `memory/agent-skills/apps-skill-evidence.md`
5. `memory/shared/integration-map.md`

## Allowed Scope

- backend app domain work confirmed under `sawa-backend/saleor/app/`
- app GraphQL schema, dataloaders, mutations, and tests under `sawa-backend/saleor/graphql/app/`
- dashboard routes and surfaces that already expose app-related extension management

## Disallowed Scope

- assuming a complete local app-authoring lifecycle that is not documented by the confirmed evidence
- treating app work as identical to generic extension work
- inventing external deployment or packaging workflows without local support

## Workflow

1. Read `memory/agent-skills/apps-skill-evidence.md`.
2. Use `references/operations-map.md` to route the task to the correct app lifecycle or dashboard touchpoint.
3. Use confirmed backend app and dashboard app-related sources first.
4. If the request goes beyond those confirmed surfaces, analyze the listed paths before acting.

## Verification

- Use `references/verification.md`.

## Open Gaps

Read `memory/agent-skills/apps-skill-evidence.md` before broadening this skill. Do not guess beyond confirmed local evidence.
