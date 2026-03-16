# Dashboard Risks

- scope: dashboard
- purpose: Highlight frontend-specific regression traps and maintenance hazards.
- read_when: Read before modifying schema-linked UI, large list screens, or shared frontend infrastructure.
- source_paths: `sawa-dashboard/AGENTS.md`, `sawa-dashboard/docs/multi-schema.md`, `sawa-dashboard/src/graphql/`, `sawa-dashboard/src/components/`
- last_reviewed: 2026-03-14

## Summary

High-risk frontend areas include generated GraphQL artifacts, multi-schema behavior, large list screens, and evolving typing conventions.

Analysis also shows that `sawa-dashboard/src/components/` is much larger than any single shared frontend area, with dense subdirectories like `ConditionalFilter` and `Datagrid`. Changes there can affect many features at once.

## Key Paths

- `sawa-dashboard/src/graphql/`
- `sawa-dashboard/docs/multi-schema.md`
- `sawa-dashboard/src/components/`
- `sawa-dashboard/src/channels/`
- `sawa-dashboard/src/discounts/`
- `sawa-dashboard/src/orders/`
- `sawa-dashboard/src/components/ConditionalFilter/`
- `sawa-dashboard/src/components/Datagrid/`

## Rules and Patterns

- Regenerate generated files after contract changes instead of hand-editing them.
- Re-check long-list UI behavior for scrolling, headers, and active-item visibility.
- Be careful around partially strict TypeScript areas and avoid papering over type issues.
- Treat shared datagrid and filtering components as high-blast-radius infrastructure.

## Risks

- Main vs staging schema confusion can cause the wrong hooks or types to be read.
- UI regressions on list-heavy screens may not show up until larger datasets are used.
- Changes to shared components can ripple into many feature modules.
- Order-related UI work is structurally dense and often spans many specialized dialogs and pages.
