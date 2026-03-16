# Dashboard Architecture

- scope: dashboard
- purpose: Summarize the high-level structure and moving parts of `sawa-dashboard/`.
- read_when: Read first for any frontend task, especially when deciding where a change belongs.
- source_paths: `sawa-dashboard/AGENTS.md`, `sawa-dashboard/README.md`, `sawa-dashboard/package.json`, `sawa-dashboard/src/`
- last_reviewed: 2026-03-14

## Summary

`sawa-dashboard/` is a Saleor Dashboard-derived single-page application built with React, TypeScript, Apollo Client, GraphQL codegen, and Vite. The frontend is organized mainly by business feature under `sawa-dashboard/src/`, with shared infrastructure in directories like `src/components`, `src/graphql`, `src/hooks`, `src/services`, and `src/utils`.

The main architectural layers are:

- feature modules under `sawa-dashboard/src/` for areas like channels, discounts, orders, and products
- shared UI and utility layers under `sawa-dashboard/src/components/`, `sawa-dashboard/src/hooks/`, and `sawa-dashboard/src/utils/`
- GraphQL types and hooks under `sawa-dashboard/src/graphql/`
- docs and environment guidance under `sawa-dashboard/docs/`

The analyzed source tree shows that `sawa-dashboard/src/components/` is the largest shared frontend area, followed by large feature domains such as `src/orders/`, `src/extensions/`, `src/discounts/`, and `src/products/`. That matters because shared-component changes and order-related work have higher blast radius than isolated feature edits.

## Key Paths

- `sawa-dashboard/src/`
- `sawa-dashboard/src/components/`
- `sawa-dashboard/src/graphql/`
- `sawa-dashboard/src/hooks/`
- `sawa-dashboard/src/services/`
- `sawa-dashboard/docs/`
- `sawa-dashboard/src/orders/`
- `sawa-dashboard/src/discounts/`
- `sawa-dashboard/src/products/`

## Rules and Patterns

- Follow feature-based structure instead of scattering related files across unrelated technical folders.
- Treat generated GraphQL files in `sawa-dashboard/src/graphql/` as artifacts.
- Use project docs and package scripts to verify commands before changing developer workflow instructions.

## Risks

- Frontend changes often touch generated GraphQL outputs indirectly.
- Module boundaries are broad, so small UI changes can still require understanding feature-specific hooks and handlers.
