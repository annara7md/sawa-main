# Dashboard Commands

- scope: dashboard
- purpose: Capture the frontend commands most likely to matter during development, testing, and GraphQL synchronization.
- read_when: Read before running or changing frontend tooling, tests, codegen, or local setup.
- source_paths: `sawa-dashboard/AGENTS.md`, `sawa-dashboard/package.json`, `sawa-dashboard/docs/configuration.md`, `sawa-dashboard/docs/running-tests.md`
- last_reviewed: 2026-03-14

## Summary

Primary frontend commands:

- `pnpm install`: install dependencies
- `pnpm run dev`: start local development server
- `pnpm run build`: build production bundle
- `pnpm run lint`: run ESLint and Prettier pipeline
- `pnpm run check-types`: run TypeScript checks
- `pnpm run test:quiet <file_path>`: run focused tests with quiet output
- `pnpm run generate`: generate GraphQL types for main and staging schemas
- `pnpm run fetch-schema`: fetch remote schemas
- `pnpm run fetch-local-schema`: fetch schema from the configured `API_URL`
- `pnpm run e2e`: run Playwright end-to-end tests

## Key Paths

- `sawa-dashboard/package.json`
- `sawa-dashboard/docs/configuration.md`
- `sawa-dashboard/docs/running-tests.md`
- `sawa-dashboard/src/graphql/`

## Rules and Patterns

- Use `pnpm run generate` after GraphQL query or schema contract changes.
- Use `pnpm run test:quiet <file_path>` for targeted test runs, per `sawa-dashboard/AGENTS.md`.
- `API_URL` from `sawa-dashboard/docs/configuration.md` controls local backend targeting for schema and runtime behavior.

## Risks

- Forgetting codegen after schema-affecting changes can leave `sawa-dashboard/src/graphql/` out of sync.
- Running the wrong test command can produce noisy output or skip the intended scope.
