# Dashboard Patterns

- scope: dashboard
- purpose: Record recurring frontend conventions so agents follow existing structure instead of inventing new patterns.
- read_when: Read before adding or editing feature-level React, GraphQL, form, or styling code in `sawa-dashboard/`.
- source_paths: `sawa-dashboard/AGENTS.md`, `sawa-dashboard/src/components/`, `sawa-dashboard/src/graphql/`, `sawa-dashboard/src/hooks/`, `sawa-dashboard/src/channels/`, `sawa-dashboard/src/discounts/`
- last_reviewed: 2026-03-14

## Summary

Recurring frontend patterns called out by local guidance:

- feature modules commonly group views, components, queries, mutations, handlers, and tests together
- GraphQL operations are paired with generated hooks and types
- forms commonly use React Hook Form
- styling guidance prefers CSS Modules
- tests should use explicit structure comments such as Arrange, Act, Assert when appropriate

## Key Paths

- `sawa-dashboard/src/components/`
- `sawa-dashboard/src/graphql/`
- `sawa-dashboard/src/hooks/`
- `sawa-dashboard/src/channels/`
- `sawa-dashboard/src/discounts/`

## Rules and Patterns

- Prefer named exports.
- Prefer `@saleor/macaw-ui-next` over legacy UI package usage.
- Prefer Lucide icons directly instead of deprecated Macaw icons.
- Respect the existing feature-based organization when placing code.
- Treat generated GraphQL files as outputs, not edit targets.

## Risks

- Mixing new and legacy UI approaches can create inconsistent behavior.
- Adding code to generated files or bypassing local module conventions creates maintenance drift quickly.
