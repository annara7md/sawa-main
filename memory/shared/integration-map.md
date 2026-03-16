# Shared Integration Map

- scope: shared
- purpose: Describe how `sawa-dashboard/` and `sawa-backend/` interact, with emphasis on GraphQL contracts and generated artifacts.
- read_when: Read before schema-related work, cross-project debugging, or any task where frontend behavior may depend on backend contract changes.
- source_paths: `sawa-dashboard/docs/multi-schema.md`, `sawa-dashboard/package.json`, `sawa-dashboard/src/graphql/`, `sawa-backend/saleor/graphql/`, `sawa-backend/pyproject.toml`
- last_reviewed: 2026-03-14

## Summary

The integration center of gravity is GraphQL:

- `sawa-backend/saleor/graphql/` defines the backend schema, resolvers, mutations, and DataLoaders.
- `sawa-dashboard/` consumes that contract and generates TypeScript hooks and types into `sawa-dashboard/src/graphql/`.
- `sawa-dashboard/docs/multi-schema.md` shows that the dashboard supports both main and staging schemas, which increases the number of generated files and integration paths.
- The analyzed dashboard GraphQL layer currently includes generated hooks, types, fragment types, type policies, a staging entrypoint, and schema version helpers under `sawa-dashboard/src/graphql/`.

## Key Paths

- `sawa-backend/saleor/graphql/`
- `sawa-backend/pyproject.toml`
- `sawa-dashboard/schema-main.graphql`
- `sawa-dashboard/schema-staging.graphql`
- `sawa-dashboard/src/graphql/`
- `sawa-dashboard/codegen-main.ts`
- `sawa-dashboard/codegen-staging.ts`
- `sawa-dashboard/src/graphql/hooks.generated.ts`
- `sawa-dashboard/src/graphql/hooksStaging.generated.ts`
- `sawa-dashboard/src/graphql/types.generated.ts`
- `sawa-dashboard/src/graphql/typesStaging.generated.ts`
- `sawa-dashboard/src/graphql/schemaVersion.ts`

## Rules and Patterns

- Backend schema changes can require dashboard type regeneration.
- Dashboard behavior may depend on schema selection through `FF_USE_STAGING_SCHEMA`.
- Generated files in `sawa-dashboard/src/graphql/*.generated.ts` should be treated as outputs, not hand-edited sources.
- The backend GraphQL tree is not flat; analyzed subtrees with the most files include `product`, `account`, `order`, `discount`, and `checkout`, so contract investigation should usually start there after locating the owning domain.
- If a frontend query or mutation breaks after backend work, inspect `sawa-backend/saleor/graphql/` and then verify `pnpm run generate` expectations in `sawa-dashboard/`.

## Risks

- A schema change can silently invalidate generated dashboard hooks until codegen is re-run.
- Main vs staging schema differences can produce confusing mismatches when reading the wrong generated file.
- Integration bugs can look like UI bugs even when they originate in backend resolver or mutation changes.
