# Shared Workflows

- scope: shared
- purpose: Capture repeatable cross-project flows so agents can start without re-deriving the sequence every time.
- read_when: Read when work spans frontend and backend, when a task begins with uncertain scope, or when GraphQL contracts may change.
- source_paths: `sawa-dashboard/docs/multi-schema.md`, `sawa-dashboard/docs/configuration.md`, `sawa-dashboard/package.json`, `sawa-backend/AGENTS.md`, `sawa-backend/pyproject.toml`
- last_reviewed: 2026-03-14

## Summary

This file captures three common cross-project flows: contract changes, cross-layer debugging, and initial scope discovery.

## Key Paths

- `sawa-dashboard/docs/multi-schema.md`
- `sawa-dashboard/package.json`
- `sawa-dashboard/src/graphql/`
- `sawa-backend/saleor/graphql/`
- `sawa-backend/pyproject.toml`

## Rules and Patterns

### Updating GraphQL schema contracts

1. Inspect the affected backend contract under `sawa-backend/saleor/graphql/`.
2. Confirm whether the change affects main schema, staging schema, or both.
3. In `sawa-dashboard/`, check `schema-main.graphql`, `schema-staging.graphql`, and codegen scripts from `package.json`.
4. Regenerate frontend artifacts when the contract changes.
5. Verify affected frontend queries, hooks, or feature modules.

### Investigating a bug that spans frontend and backend

1. Start from the visible failure: UI behavior, GraphQL response, or backend error.
2. Map the request path through the relevant frontend feature under `sawa-dashboard/src/`.
3. Inspect the corresponding backend resolver or mutation area in `sawa-backend/saleor/graphql/` and the owning domain module.
4. Verify whether the issue is contract mismatch, generated code drift, or domain logic.

### Starting a new task when scope is uncertain

1. Read `memory/shared/overview.md`.
2. Identify whether the first touched source file will likely live under `sawa-dashboard/` or `sawa-backend/`.
3. If the answer depends on GraphQL shape or backend capability, treat it as shared until proven otherwise.

## Risks

- Cross-project work often fails when only one side of the contract is updated.
- Ambiguous scope can waste time if agents dive into UI code before checking the owning backend domain.
