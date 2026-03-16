# Dashboard Skill Evidence

- scope: shared
- purpose: Preserve confirmed local evidence for what the dashboard-development skill must cover and what it must not claim without support.
- read_when: Read immediately before authoring or revising `skills/dashboard-development/SKILL.md`.
- source_paths: `memory/dashboard/architecture.md`, `memory/dashboard/module-map.md`, `memory/dashboard/commands.md`, `memory/dashboard/patterns.md`, `memory/dashboard/risks.md`, `sawa-dashboard/AGENTS.md`, `sawa-dashboard/package.json`
- last_reviewed: 2026-03-14

## Confirmed Evidence

- `sawa-dashboard` is a React, TypeScript, Apollo, GraphQL, and Vite admin frontend.
- Local dashboard work is organized around feature modules plus shared layers such as `src/components/`, `src/graphql/`, `src/hooks/`, and `src/utils/`.
- The largest analyzed dashboard areas include `components`, `orders`, `extensions`, `discounts`, and `products`.
- Commands confirmed locally include `pnpm run dev`, `pnpm run build`, `pnpm run lint`, `pnpm run check-types`, `pnpm run test:quiet`, `pnpm run generate`, and schema-fetch commands.
- Local dashboard guidance explicitly prefers generated GraphQL artifacts to be treated as outputs, not edit targets.
- Existing dashboard-specific skill material already demonstrates focused style guidance and a more complex test-failure analysis workflow.

## Open Gaps

- No dedicated root skill currently defines how dashboard work should be activated and bounded within the new `skills/` program.
- The current evidence supports dashboard development broadly, but not every possible extension or app workflow that touches dashboard screens.

## Local Paths Reviewed

- `memory/dashboard/architecture.md`
- `memory/dashboard/module-map.md`
- `memory/dashboard/commands.md`
- `memory/dashboard/patterns.md`
- `memory/dashboard/risks.md`
- `sawa-dashboard/AGENTS.md`
- `sawa-dashboard/package.json`
- `sawa-dashboard/.claude/skills/saleor-dashboard-styles/SKILL.md`
